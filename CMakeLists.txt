﻿cmake_minimum_required (VERSION 3.8)

set(CMAKE_C_COMPILER clang)
set(CMAKE_C_COMPILER_TARGET ${triple})
set(CMAKE_CXX_COMPILER clang++)
set(CMAKE_CXX_COMPILER_TARGET ${triple})
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17")

set(LCC_VERSION "0.0.0")
set(LINECRYPT_VERSION "1.1")

project (lcc LANGUAGES CXX VERSION ${LCC_VERSION})

add_executable (lcc
        "src/main.cpp"
        "src/lcc/program.cpp"
        "src/lcc/exceptions.cpp"
        "include/lcc/lexer_state.hpp"
        "src/lcc/instance.cpp"
        "include/lcc/value.hpp"
        "include/lcc/multi_stack.hpp"
        )
target_compile_features(lcc PUBLIC "cxx_std_17")
target_include_directories(lcc PUBLIC "include")
target_compile_definitions(lcc PRIVATE LCC_VERSION="${LCC_VERSION}")
target_compile_definitions(lcc PRIVATE LINECRYPT_VERSION="${LINECRYPT_VERSION}")