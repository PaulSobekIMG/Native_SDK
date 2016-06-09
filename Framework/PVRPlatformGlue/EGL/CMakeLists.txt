if (APPLE)
add_definitions(-DTARGET_OS_MAC=1)
endif()

add_library (PVRGlue OBJECT ExtensionLoaderEgl.cpp
 EglPlatformContext.cpp
 NativeLibraryEgl.cpp
  )
target_include_directories (PVRGlue PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../.. ${CMAKE_CURRENT_SOURCE_DIR}/../../../Builds/Include)
