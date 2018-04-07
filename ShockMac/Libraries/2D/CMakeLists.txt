cmake_minimum_required(VERSION 3.8)
project(systemshock)

# Initialize cmake options
set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/../../Build/2D)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/../../Build/2D)
# set(CMAKE_BUILD_TYPE RELEASE)

set(CMAKE_INSTALL_PREFIX ${CMAKE_CURRENT_LIST_DIR})

set(2D_SRC_DIR ${CMAKE_CURRENT_LIST_DIR}/Source)
set(2D_HEADERS_DIR
        ${2D_SRC_DIR}/clip
        ${2D_SRC_DIR}/Flat 8
        ${2D_SRC_DIR}/gen
        ${2D_SRC_DIR}/gr
        ${2D_SRC_DIR}/rsd
        ${2D_SRC_DIR})

enable_language(ASM)

add_subdirectory(${CMAKE_CURRENT_LIST_DIR}/../FIX ${CMAKE_CURRENT_LIST_DIR}/../../Build/FIX)

file(GLOB 2D_SRC_C
        "${2D_SRC_DIR}/clip/*.c"
        "${2D_SRC_DIR}/Flat 8/*.c"
        "${2D_SRC_DIR}/gen/*.c"
        "${2D_SRC_DIR}/gr/*.c"
        "${2D_SRC_DIR}/rsd/*.c"
        "${2D_SRC_DIR}/*.c"
        )

file(GLOB 2D_HEADERS
        "${2D_SRC_DIR}/clip/*.h"
        "${2D_SRC_DIR}/Flat 8/*.h"
        "${2D_SRC_DIR}/gen/*.h"
        "${2D_SRC_DIR}/gr/*.h"
        "${2D_SRC_DIR}/rsd/*.h"
        "${2D_SRC_DIR}/*.h"
        )

file(GLOB 2D_SRC_ASM
        "${2D_SRC_DIR}/rsd/*.asm"
        "${2D_SRC_DIR}/*.s"
        )

add_library(2D SHARED ${2D_SRC_C} ${2D_SRC_ASM} ${2D_HEADERS} ${FIX_HEADERS})

target_include_directories(2D PRIVATE
        ${2D_HEADERS_DIR}
        ${FIX_HEADERS_DIR}
)

target_link_libraries(2D FIX)
