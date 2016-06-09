if (WIN32)
	set(OS_SHELL_IMPL  EntryPoint/WinMain/main.cpp OS/Windows/ShellOS.cpp)
elseif (ANDROID)
	set(OS_SHELL_IMPL  ${ANDROID_NDK}/sources/android/native_app_glue/android_native_app_glue.c EntryPoint/android_main/main.cpp OS/Android/ShellOS.cpp)
elseif (APPLE)
	set(CMAKE_CXX_FLAGS "-x objective-c++")
	if (IOS)
		add_definitions(-DTARGET_OS_IPHONE=1)
		set(OS_SHELL_IMPL EntryPoint/UIApplicationMain/main.m EntryPoint/UIApplicationMain/AppController.mm OS/UIKit/ShellOS.mm)
	else()
		add_definitions(-DTARGET_OS_MAC=1)
		set(OS_SHELL_IMPL  EntryPoint/NSApplicationMain/main.m  EntryPoint/NSApplicationMain/AppController.mm OS/AppKit/ShellOS.mm)
	endif()
else()
# Default to Linux
set(OS_SHELL_IMPL  EntryPoint/main/main.cpp OS/X11/ShellOS.cpp)
endif()

add_library (PVRShell OBJECT CommandLine.cpp
${OS_SHELL_IMPL}
 Shell.cpp
 StateMachine.cpp
  )
target_include_directories (PVRShell PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/.. ${CMAKE_CURRENT_SOURCE_DIR}/../../Builds/Include)
