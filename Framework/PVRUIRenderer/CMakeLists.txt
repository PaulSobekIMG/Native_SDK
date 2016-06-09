add_library (PVRUIRenderer OBJECT Sprite.cpp
 UIRenderer.cpp
  )
target_include_directories (PVRUIRenderer PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/.. ${CMAKE_CURRENT_SOURCE_DIR}/../../Builds/Include)
