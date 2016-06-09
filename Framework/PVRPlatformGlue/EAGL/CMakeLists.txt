add_library (PVRGlue OBJECT EaglPlatformContext.mm 
 EaglGetProcAddress.cpp
  )
target_include_directories (PVRGlue PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../.. ${CMAKE_CURRENT_SOURCE_DIR}/../../../Builds/Include)
