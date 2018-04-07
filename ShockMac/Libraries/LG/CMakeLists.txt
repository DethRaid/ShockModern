cmake_minimum_required(VERSION 3.8)
project(systemshock)

# Initialize cmake options
set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/../../Build/LG)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/../../Build/LG)
# set(CMAKE_BUILD_TYPE RELEASE)

set(CMAKE_INSTALL_PREFIX ${CMAKE_CURRENT_LIST_DIR})

set(LG_SRC_DIR ${CMAKE_CURRENT_LIST_DIR}/Source)
set(LG_HEADERS_DIR ${LG_SRC_DIR})

enable_language(ASM)

file(GLOB LG_SRC_C
        "${LG_SRC_DIR}/*.c"
        )

file(GLOB LG_HEADERS
        "${LG_SRC_DIR}/*.h"
        )

file(GLOB LGSRC_ASM
        "${LG_SRC_DIR}/*.s"
        )


add_library(LG SHARED ${LG_SRC_C} ${LG_SRC_ASM} ${LG_HEADERS})

target_include_directories(LG PRIVATE
        ${LG_HEADERS_DIR}
        )