cmake_minimum_required(VERSION 3.15...3.26)
project(${SKBUILD_PROJECT_NAME} VERSION ${SKBUILD_PROJECT_VERSION} LANGUAGES CXX)

set(PYBIND11_FINDPYTHON ON)
find_package(Python COMPONENTS Interpreter Development.Module REQUIRED)
find_package(pybind11 CONFIG REQUIRED)

pybind11_add_module(render_utils render_utils/main.cpp)

target_compile_definitions(render_utils
    PRIVATE VERSION_INFO="${PROJECT_VERSION}"
)

install(TARGETS render_utils LIBRARY DESTINATION .)