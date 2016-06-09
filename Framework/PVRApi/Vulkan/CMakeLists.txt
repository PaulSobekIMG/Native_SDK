add_library (PVRApi OBJECT AssetStore.cpp
 BufferVk.cpp
 CommandBufferVk.cpp
 CommandPoolVk.cpp
 ComputePipelineVk.cpp
 ContextVk.cpp
 DescriptorSetVk.cpp
 EffectApi.cpp
 FboVk.cpp
 GpuCapabilities.cpp
 GraphicsPipelineVk.cpp
 PipelineLayoutVk.cpp
 RenderPassVk.cpp
 SamplerVk.cpp
 ShaderVk.cpp
 SyncVk.cpp
 TextureUtilsVk.cpp
 TextureVk.cpp
  )
target_include_directories (PVRApi PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../.. ${CMAKE_CURRENT_SOURCE_DIR}/../../../Builds/Include)
