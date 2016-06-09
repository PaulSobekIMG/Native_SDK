if(APPLE)
	if(IOS)
		add_definitions(-DTARGET_OS_IPHONE=1)
	else()
		add_definitions(-DTARGET_OS_MAC=1)
	endif()
endif()

add_library (PVRApi OBJECT ApiCommandsGles.cpp
 CommandBufferGles.cpp
 AssetStore.cpp
 BufferGles.cpp
 CommandPoolGles.cpp
 ComputePipelineGles.cpp
 ContextGles.cpp
 DescriptorSetGles.cpp
 EffectApi.cpp
 FboGles.cpp
 GpuCapabilities.cpp
 GraphicsPipelineGles.cpp
 PipelineConfigStateCreateParam.cpp
 PipelineConfigStates.cpp
 PipelineLayoutGles.cpp
 RenderPassGles.cpp
 SamplerGles.cpp
 ShaderGles.cpp
 Sync.cpp
 TextureGles.cpp
 TextureUtilsGles.cpp
  )
target_include_directories (PVRApi PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../.. ${CMAKE_CURRENT_SOURCE_DIR}/../../../Builds/Include)
