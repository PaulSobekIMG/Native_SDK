if (APPLE)
	if (IOS)
		add_definitions(-DTARGET_OS_IPHONE=1)
	else()
		add_definitions(-DTARGET_OS_MAC=1)
	endif()
endif()

add_library (PVRNativeApi OBJECT ApiErrors.cpp
 BufferUtilsGles.cpp
 ConvertToApiTypes.cpp
 ExtensionLoaderGles.cpp
 LibraryLoaderGles.cpp
 ShaderUtils.cpp
 TextureUtils.cpp
  )
target_include_directories (PVRNativeApi PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../.. ${CMAKE_CURRENT_SOURCE_DIR}/../../../Builds/Include)
