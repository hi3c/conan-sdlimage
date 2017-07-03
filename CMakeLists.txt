cmake_minimum_required(VERSION 3.6 FATAL_ERROR)
project(SDL2_image)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

option(BUILD_SHARED_LIBS "" ON)

find_package(Threads REQUIRED)

add_library(SDL2_image
  IMG_bmp.c
  IMG.c
  IMG_lbm.c
  IMG_pcx.c
  IMG_png.c
  IMG_pnm.c
  IMG_tga.c
  IMG_tif.c
  IMG_xcf.c
  IMG_xpm.c
  IMG_xv.c
  IMG_xxx.c
  IMG_jpg.c
  IMG_gif.c
  IMG_webp.c
)

target_link_libraries(SDL2_image CONAN_PKG::libpng CONAN_PKG::SDL2 Threads::Threads)
set_target_properties(SDL2_image PROPERTIES POSITION_INDEPENDENT_CODE TRUE)
target_compile_definitions(SDL2_image PUBLIC LOAD_PNG)
