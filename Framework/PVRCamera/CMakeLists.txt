add_library (PVRCamera OBJECT CameraInterface_Dummy.cpp)
target_include_directories (PVRCamera PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/.. ${CMAKE_CURRENT_SOURCE_DIR}/../../Builds/Include)
