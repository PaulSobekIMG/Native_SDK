if(IOS)
add_definitions(-DTARGET_OS_IPHONE=1)
endif()

add_library (PVRGlue OBJECT ExtensionLoaderVulkanGlue.cpp
 NativeLibraryVulkanGlue.cpp
 PlatformContextVulkanGlue.cpp
  )
target_include_directories (PVRGlue PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../.. ${CMAKE_CURRENT_SOURCE_DIR}/../../../Builds/Include)
