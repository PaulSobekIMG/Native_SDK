add_library (PVRAssets OBJECT FileIO/PFXReader.cpp
 FileIO/PODReader.cpp
 FileIO/TextureReaderBMP.cpp
 FileIO/TextureReaderDDS.cpp
 FileIO/TextureReaderKTX.cpp
 FileIO/TextureReaderPVR.cpp
 FileIO/TextureWriterLegacyPVR.cpp
 FileIO/TextureWriterPVR.cpp
 FileIO/PaletteExpander.cpp
 FileIO/TextureReaderTGA.cpp
 Model/Animation.cpp
 Model/Camera.cpp
 FileIO/TextureReaderXNB.cpp
 Model/Light.cpp
 Model/Mesh.cpp
 Model/Model.cpp
 ShadowVolume.cpp
 Texture/MetaData.cpp
 Texture/PixelFormat.cpp
 Texture/PVRTDecompress.cpp
 Texture/Texture.cpp
 Texture/TextureHeader.cpp
 Texture/TextureHeaderWithMetaData.cpp
  )
target_include_directories (PVRAssets PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/.. ${CMAKE_CURRENT_SOURCE_DIR}/../../Builds/Include)
