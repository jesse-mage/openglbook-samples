cmake_minimum_required( VERSION 3.2 )

project( GLTools CXX )

add_library( GLTools OBJECT main.cpp )

target_include_directories( GLTools PUBLIC include
        $<BUILD_INTERFACE:${glew_cmake_SOURCE_DIR}/include>
        $<BUILD_INTERFACE:${freeglut_SOURCE_DIR}/include> )

target_link_libraries( GLTools PUBLIC GLU GL X11 libglew_static freeglut_static )

