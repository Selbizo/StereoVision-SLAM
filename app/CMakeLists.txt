# Добавляем путь к библиотекам, если CMake его не находит
link_directories(/usr/local/lib)

add_executable(run_stereo_visual_SLAM run_stereo_vision_SLAM.cpp)
target_link_options(run_stereo_visual_SLAM PRIVATE -Wl,--no-as-needed)
target_link_libraries(run_stereo_visual_SLAM
    StereoVisionSLAM
    ${THIRD_PARTY_LIBS}
    fmt::fmt
    /usr/local/lib/libpcl_common.so   # абсолютный путь
)

add_executable(run_dense_reconstruction run_dense_reconstruction.cpp)
target_link_options(run_dense_reconstruction PRIVATE -Wl,--no-as-needed)
target_link_libraries(run_dense_reconstruction
    StereoVisionSLAM
    ${THIRD_PARTY_LIBS}
    fmt::fmt
    /usr/local/lib/libpcl_common.so
)