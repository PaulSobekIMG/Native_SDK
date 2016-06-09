cmake_minimum_required(VERSION 3.0)

if (NOT DEFINED "API")
	message(FATAL_ERROR "Please specify target API: -DAPI=Vulkan or -DAPI=OGLES")
endif ()

if (${API} STREQUAL "Vulkan")
	set(VULKANBUILD 1)
elseif (${API} STREQUAL "OGLES")
	set(OGLESBUILD 1)
else()
	message(FATAL_ERROR "Please specify target API: -DAPI=Vulkan or -DAPI=OGLES")
endif ()


if (NOT WIN32)
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
endif()


if (ANDROID)
	include_directories(${ANDROID_NDK}/sources/android/native_app_glue)
endif()


add_subdirectory (PVRAssets)
add_subdirectory (PVRCamera)
add_subdirectory (PVRCore)
add_subdirectory (PVRShell)

if (${VULKANBUILD})
	add_subdirectory (PVRApi/Vulkan)
	add_subdirectory (PVRNativeApi/Vulkan)
	add_subdirectory (PVRPlatformGlue/Vulkan)
else() # GLES
	add_subdirectory (PVRApi/OGLES)
	add_subdirectory (PVRNativeApi/OGLES)
	if (IOS)
		add_subdirectory (PVRPlatformGlue/EAGL)
	else()
		add_subdirectory (PVRPlatformGlue/EGL)
	endif()
endif()

if (APPLE)
include(CMakeFindFrameworks)
if (IOS)
# Have to set manually  by link line 
else()
	cmake_find_frameworks(Cocoa)
	cmake_find_frameworks(AppKit)
	cmake_find_frameworks(CoreData)
	cmake_find_frameworks(Foundation)
	cmake_find_frameworks(QuartzCore)
endif()
endif()

if (WIN32)
set(FRAMEWORK_LINK_LIBS PARENT_SCOPE)
elseif (ANDROID)
set(FRAMEWORK_LINK_LIBS log android PARENT_SCOPE)
elseif(APPLE) 
	if(IOS)
		find_library(CORE_GRAPHICS_LIBRARY CoreGraphics)
		if (NOT CORE_GRAPHICS_LIBRARY)
			message(FATAL_ERROR "CoreGraphics not found")
		endif()
		find_library(FOUNDATION_LIBRARY Foundation)
		if (NOT FOUNDATION_LIBRARY)
			message(FATAL_ERROR "Foundation not found")
		endif()
		find_library(OPENGLES_LIBRARY OpenGLES)
		if (NOT OPENGLES_LIBRARY)
			message(FATAL_ERROR "OpenGLES not found")
		endif()
		find_library(QUARTZ_CORE_LIBRARY QuartzCore)
		if (NOT QUARTZ_CORE_LIBRARY)
			message(FATAL_ERROR "QuartzCore not found")
		endif()
		find_library(UIKIT_LIBRARY UIKit)
		if (NOT UIKIT_LIBRARY)
			message(FATAL_ERROR "UIKit not found")
		endif()
		mark_as_advanced(
			CORE_GRAPHICS_LIBRARY
			FOUNDATION_LIBRARY
			OPENGLES_LIBRARY
			QUARTZ_CORE_LIBRARY
			UIKIT_LIBRARY
		)
		set(FRAMEWORK_LINK_LIBS
			${CORE_GRAPHICS_LIBRARY}
			${FOUNDATION_LIBRARY}
			${OPENGLES_LIBRARY}
			${QUARTZ_CORE_LIBRARY}
			${UIKIT_LIBRARY} PARENT_SCOPE
		)
		
	else()
		include_directories(/System/Library/Frameworks)
		find_library(APP_KIT_LIBRARY AppKit)
		if (NOT APP_KIT_LIBRARY)
				message(FATAL_ERROR "AppKit not found")
		endif()
		find_library(CORE_DATA_LIBRARY CoreData)
		if (NOT CORE_DATA_LIBRARY)
				message(FATAL_ERROR "CoreData not found")
		endif()
		find_library(FOUNDATION_LIBRARY Foundation)
		if (NOT FOUNDATION_LIBRARY)
				message(FATAL_ERROR "Foundation not found")
		endif()
		find_library(QUARTZ_CORE_LIBRARY QuartzCore)
		if (NOT QUARTZ_CORE_LIBRARY)
				message(FATAL_ERROR "QuartzCore not found")
		endif()
		find_library(COCOA_LIBRARY Cocoa)
		if (NOT COCOA_LIBRARY)
				message(FATAL_ERROR "Cocoa not found")
		endif()
		mark_as_advanced(APP_KIT_LIBRARY
				CORE_DATA_LIBRARY
				FOUNDATION_LIBRARY
				QUARTZ_CORE_LIBRARY
				COCOA_LIBRARY)
		set(FRAMEWORK_LINK_LIBS
				${APP_KIT_LIBRARY}
				${CORE_DATA_LIBRARY}
				${FOUNDATION_LIBRARY}
				${QUARTZ_CORE_LIBRARY}
				${COCOA_LIBRARY} PARENT_SCOPE)		
	endif()
else() # Linux
set(FRAMEWORK_LINK_LIBS X11 Xau rt dl PARENT_SCOPE)
endif()

