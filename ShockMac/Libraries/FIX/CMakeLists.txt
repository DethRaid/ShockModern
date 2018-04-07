cmake_minimum_required(VERSION 3.8)
project(systemshock)

# Initialize cmake options
set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/../../Build/FIX)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/../../Build/FIX)
# set(CMAKE_BUILD_TYPE RELEASE)

set(CMAKE_INSTALL_PREFIX ${CMAKE_CURRENT_LIST_DIR})

set(FIX_SRC_DIR ${CMAKE_CURRENT_LIST_DIR}/Source)
set(FIX_HEADERS_DIR ${FIX_SRC_DIR})

enable_language(ASM)

add_subdirectory(${CMAKE_CURRENT_LIST_DIR}/../H ${CMAKE_CURRENT_LIST_DIR}/../../Build/H)

file(GLOB FIX_SRC_C
        "${FIX_SRC_DIR}/*.c"
        )

file(GLOB FIX_HEADERS
        "${FIX_SRC_DIR}/*.h"
        )

file(GLOB FIX_SRC_ASM
        "${FIX_SRC_DIR}/*.s"
        )

add_library(FIX SHARED ${FIX_SRC_C} ${FIX_SRC_ASM} ${FIX_HEADERS} ${H_HEADERS})

target_include_directories(FIX PRIVATE
        ${FIX_HEADERS_DIR}
        ${H_HEADERS_DIR}
        )

message(${CMAKE_CURRENT_LIST_DIR}/../H)