cmake_minimum_required(VERSION 3.15)

project(ed_solver LANGUAGES CXX)

include(FetchContent)

find_package(Python REQUIRED COMPONENTS Interpreter Development.Module)

execute_process(
    COMMAND ${Python_EXECUTABLE} -c "import sysconfig; print(sysconfig.get_config_var('EXT_SUFFIX'))"
    OUTPUT_VARIABLE PYTHON_EXT_SUFFIX
    OUTPUT_STRIP_TRAILING_WHITESPACE
)

FetchContent_Declare(
    pybind11
    GIT_REPOSITORY https://github.com/pybind/pybind11.git
    GIT_TAG v3.0.1
)

FetchContent_Declare(
    Eigen3
    GIT_REPOSITORY https://gitlab.com/libeigen/eigen.git
    GIT_TAG 5.0.1
)

FetchContent_MakeAvailable(pybind11 Eigen3)

pybind11_add_module(_ed_solver
    bindings.cpp
    src/solver.cpp
    src/helpers.cpp
)

target_compile_features(_ed_solver PRIVATE cxx_std_17)
target_link_libraries(_ed_solver PRIVATE Eigen3::Eigen)

set_target_properties(_ed_solver PROPERTIES
    PREFIX ""
    SUFFIX "${PYTHON_EXT_SUFFIX}"
    LIBRARY_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/ed_solver"
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/ed_solver"
    ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/ed_solver"
)


install(
    TARGETS _ed_solver
    LIBRARY DESTINATION ed_solver
    RUNTIME DESTINATION ed_solver
    ARCHIVE DESTINATION ed_solver
)

install(
    FILES ed_solver/__init__.py
    DESTINATION ed_solver
)

message(STATUS "Building _ed_solver in: ${CMAKE_CURRENT_SOURCE_DIR}/ed_solver")
