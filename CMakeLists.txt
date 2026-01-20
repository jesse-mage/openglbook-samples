cmake_minimum_required( VERSION 3.25 )

project( GL-cookbook CXX C )

include( utils )

find_package( OpenGL REQUIRED )

# add packages
add_package( ${GLEW_PACKAGE} )
add_package( ${FREEGLUT_PACKAGE} )

# add subdirectories
add_subdirectory( external )

set( source   chapter-1/chapter.1.1.c
              chapter-1/chapter.1.2.c
              chapter-1/chapter.1.3.c
              chapter-2/chapter.2.1.c
              chapter-2/chapter.2.2.c
              chapter-2/chapter.2.3.c
              chapter-2/chapter.2.4.c
              chapter-3/chapter.3.0.1.c
              chapter-3/chapter.3.0.2.c
              chapter-3/chapter.3.1.c
              chapter-3/chapter.3.2.c )

set( programs chapter11c
              chapter12c
              chapter13c
              chapter21c
              chapter22c
              chapter23c
              chapter24c
              chapter301c
              chapter302c
              chapter31c
              chapter32c )

foreach( program file IN ZIP_LISTS programs source )
  add_executable( ${program} ${file} )
  target_link_libraries( ${program} PRIVATE GLTools )
endforeach()

add_executable( chapter41c chapter-4/chapter.4.1.c chapter-4/Utils.c )
target_link_libraries( chapter41c PRIVATE GLTools )

