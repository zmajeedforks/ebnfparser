# wasm/CMakeLists.txt

# webassembly cmakefile

cmake_minimum_required(VERSION 4.2)
project(ebnfparser_wasm CXX)

set(CMAKE_CXX_STANDARD 26)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(ebnfparse_wasm ../src/parser_api/ebnf_parse.cpp)

target_link_options(ebnfparse_wasm PRIVATE
    "--bind"
    "-sMODULARIZE=1"
    "-sEXPORT_ES6=1"
    "-sENVIRONMENT=node,web"
    "-sFILESYSTEM=0"
    "-O3"
)

set_target_properties(ebnfparse_wasm PROPERTIES SUFFIX ".mjs")
