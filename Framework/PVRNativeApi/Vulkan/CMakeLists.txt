add_library (PVRNativeApi OBJECT ApiErrors.cpp
 BufferUtilsVk.cpp
 ImageUtilsVk.cpp
 ShaderUtilsVk.cpp
 TextureUtilsVk.cpp
 VulkanBindings.cpp
  )
target_include_directories (PVRNativeApi PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../.. ${CMAKE_CURRENT_SOURCE_DIR}/../../../Builds/Include)
