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

set(SRC_DIR ${CMAKE_CURRENT_LIST_DIR}/Source)

enable_language(ASM)

add_subdirectory(${CMAKE_CURRENT_LIST_DIR}/../FIX ${CMAKE_CURRENT_LIST_DIR}/../../Build/FIX)

file(GLOB 2D_SRC_C
        "${SRC_DIR}/clip/*.c"
        "${SRC_DIR}/Flat 8/*.c"
        "${SRC_DIR}/gen/*.c"
        "${SRC_DIR}/gr/*.c"
        "${SRC_DIR}/rsd/*.c"
        "${SRC_DIR}/*.c"
        )

file(GLOB 2D_HEADERS
        "${SRC_DIR}/clip/*.h"
        "${SRC_DIR}/Flat 8/*.h"
        "${SRC_DIR}/gen/*.h"
        "${SRC_DIR}/gr/*.h"
        "${SRC_DIR}/rsd/*.h"
        "${SRC_DIR}/*.h"
        )

file(GLOB 2D_SRC_ASM
        "${SRC_DIR}/rsd/*.asm"
        "${SRC_DIR}/*.s"
        )

add_library(2D SHARED ${2D_SRC_C} ${2D_SRC_ASM} ${2D_HEADERS})

target_include_directories(2D PRIVATE
        ${SRC_DIR}/clip
        ${SRC_DIR}/Flat 8
        ${SRC_DIR}/gen
        ${SRC_DIR}/gr
        ${SRC_DIR}/rsd
        ${SRC_DIR}
        ${FIX_HEADERS}
)

target_link_libraries(2D FIX)
