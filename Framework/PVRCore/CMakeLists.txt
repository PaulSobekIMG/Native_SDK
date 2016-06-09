if (WIN32)
	set(OS_IMPL Windows/StackTraceWindows.cpp
	Windows/WindowsResourceStream.cpp)
elseif(ANDROID)
	set(OS_IMPL Android/AndroidAssetStream.cpp)
elseif(APPLE)
	set(CMAKE_CXX_FLAGS "-x objective-c++")
	set (OS_IMPL NativeLibraryApple.mm)
elseif()
	# Default is Linux
endif()

add_library (PVRCore OBJECT BufferStream.cpp
 ConsoleMessenger.cpp
 FilePath.cpp
 FileStream.cpp
 FileWrapStream.cpp
 Log.cpp
 NativeLibrary.cpp
 StringFunctions.cpp
 Time.cpp
 UnicodeConverter.cpp
 ${OS_IMPL}
  )
target_include_directories (PVRCore PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/.. ${CMAKE_CURRENT_SOURCE_DIR}/../../Builds/Include)
