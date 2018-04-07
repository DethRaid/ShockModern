cmake_minimum_required(VERSION 3.8)
project(systemshock)

# Initialize cmake options
set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
# set(CMAKE_BUILD_TYPE RELEASE)

set(CMAKE_INSTALL_PREFIX ${CMAKE_CURRENT_LIST_DIR})

set(SRC_DIR ${CMAKE_CURRENT_LIST_DIR}/Source)

enable_language(ASM)

file(GLOB 2D_SRC_C
        "${SRC_DIR}/Clip/*.C"
        "${SRC_DIR}/Flat 8/*.C"
        "${SRC_DIR}/Flat 8/*.c"
        "${SRC_DIR}/Gen/*.C"
        "${SRC_DIR}/GR/*.C"
        "${SRC_DIR}/RSD/*.C"
        "${SRC_DIR}/RSD/*.c"
        "${SRC_DIR}/*.C"
        "${SRC_DIR}/*.c"
        )

file(GLOB 2D_HEADERS
        "${SRC_DIR}/Clip/*.H"
        "${SRC_DIR}/Flat 8/*.H"
        "${SRC_DIR}/Gen/*.H"
        "${SRC_DIR}/GR/*.H"
        "${SRC_DIR}/RSD/*.H"
        "${SRC_DIR}/*.H"
        )

file(GLOB 2D_SRC_ASM
        "${SRC_DIR}/RSD/*.ASM"
        "${SRC_DIR}/*.s"
        )


add_library(2D ${2D_SRC_C} ${2D_SRC_ASM} ${2D_HEADERS})

target_include_directories(2D PRIVATE
        ${SRC_DIR}/GR
        ${SRC_DIR}/Clip
        ${SRC_DIR}/Flat 8
        ${SRC_DIR}/Gen
        ${SRC_DIR}/RSD
        ${SRC_DIR}
)