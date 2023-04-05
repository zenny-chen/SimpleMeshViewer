cmake_minimum_required(VERSION 3.15)

project(SimpleViewer  LANGUAGES  CXX)

if(WIN32)
    add_compile_definitions(_CRT_SECURE_NO_DEPRECATE=1)
endif()

if(NOT DEFINED CMAKE_CXX_STANDARD)
    # Visual Studio 2019/2022 uses C++14 standard by default
    set(CMAKE_CXX_STANDARD  14)
endif()

if(NOT DEFINED CMAKE_OSX_ARCHITECTURES)
    find_path(FREEGLUT_ROOT  REQUIRED)
    include_directories(${FREEGLUT_ROOT}/include)
    link_directories(${FREEGLUT_ROOT}/lib)
endif()

set(MESH_LIB_DIR  ${CMAKE_SOURCE_DIR}/MeshLib/core)

file(GLOB  bmp_header ${MESH_LIB_DIR}/bmp/*.h)
file(GLOB  bmp_src ${MESH_LIB_DIR}/bmp/*.cpp)
file(GLOB  geometry_header ${MESH_LIB_DIR}/Geometry/*.h)
file(GLOB  mesh_header ${MESH_LIB_DIR}/Mesh/*.h)
file(GLOB  parser_header ${MESH_LIB_DIR}/Parser/*.h)
file(GLOB  viewer_header ${MESH_LIB_DIR}/viewer/*.h)

source_group("bmp"  FILES ${bmp_src} ${bmp_header})
source_group("Geometry"  FILES ${geometry_header})
source_group("Mesh"  FILES ${mesh_header})
source_group("Parser"  FILES ${parser_header})
source_group("viewer"  FILES ${viewer_header})

add_executable(SimpleViewer
                ${bmp_src}
                ${bmp_header}
                ${geometry_header}
                ${mesh_header}
                ${parser_header}
                ${viewer_header}
                ${CMAKE_SOURCE_DIR}/Viewer/view_mesh.cpp
              )

if(NOT DEFINED CMAKE_OSX_ARCHITECTURES)
    target_link_libraries(SimpleViewer  freeglut_static.lib)
endif()

include_directories(${MESH_LIB_DIR})

install(TARGETS  SimpleViewer DESTINATION bin)

