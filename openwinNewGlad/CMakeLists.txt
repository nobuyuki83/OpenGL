# CMakeのバージョンを設定
cmake_minimum_required(VERSION 2.8)

# プロジェクト名と使用する言語を設定
project(openwinNewGlad CXX)

set(CMAKE_CXX_FLAGS "-Wall -Wno-deprecated-declarations -g")

set(GLFW_LIBRARY    /Users/Chihiro/Desktop/OpenGL/glfw/src/libglfw3.a)
#get_filename_component(GLFW_LIBRARY ${GLFW_LIBRARY} ABSOLUTE)

find_package(OpenGL REQUIRED)

# a.outという実行ファイルをmain.cppとhello.cppから作成
add_executable(a.out 
  ../glad/src/glad.c
  main.cpp)

include_directories(
  ../glfw/include
  ../glad/include)

find_library( COCOA_LIBRARY Cocoa )
find_library( IOKIT_LIBRARY IOKit )
find_library( COREVIDEO_LIBRARY CoreVideo )
target_link_libraries(a.out
    ${OPENGL_LIBRARY}
    ${GLFW_LIBRARY}
    ${COCOA_LIBRARY}
    ${IOKIT_LIBRARY}
    ${COREVIDEO_LIBRARY}
  )
