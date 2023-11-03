cmake_minimum_required(VERSION 3.15)

project(CLUEstering LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Python COMPONENTS Interpreter Development.Module REQUIRED)
add_subdirectory(pybind11)

set(HEADER_FILES
    include/Clustering.h
    include/deltaPhi.h
    include/Kernels.h
    include/Point.h
    include/Tiles.h
)

pybind11_add_module(CLUEstering
    ${HEADER_FILES}
    binding.cc
)

include(GNUInstallDirs)
install(TARGETS CLUEstering
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

