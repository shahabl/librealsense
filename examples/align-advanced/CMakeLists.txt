# License: Apache 2.0. See LICENSE file in root directory.
# Copyright(c) 2019 Intel Corporation. All Rights Reserved.
#  minimum required cmake version: 3.1.0
cmake_minimum_required(VERSION 3.1.0)

project(RealsenseExamplesAlignAdvanced)

if(BUILD_GRAPHICAL_EXAMPLES)
    add_executable(rs-align-advanced rs-align-advanced.cpp ../../third-party/imgui/imgui.cpp ../../third-party/imgui/imgui_draw.cpp ../../third-party/imgui/imgui_impl_glfw.cpp)
    set_property(TARGET rs-align-advanced PROPERTY CXX_STANDARD 11)
    set(CMAKE_BUILD_TYPE Debug)

    # Locate the OpenCV lib
    find_package( OpenCV REQUIRED )
    message("-------------------")
    message(${OpenCV_LIBS})
    message(${DEPENDENCIES})
    message("==================")

    #link_directories(/opt/intel/openvino/opencv/lib/)
    target_link_libraries(rs-align-advanced ${DEPENDENCIES} ${OpenCV_LIBS} opencv_calib3d opencv_rgbd)
    include_directories(rs-align-advanced ../../common ../../third-party/imgui)
    set_target_properties (rs-align-advanced PROPERTIES FOLDER Examples)
    install(TARGETS rs-align-advanced RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
endif()
