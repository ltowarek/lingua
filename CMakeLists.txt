cmake_minimum_required(VERSION 3.28)

project(poc)

find_package(fmt CONFIG REQUIRED)

find_package(antlr4-generator REQUIRED)
find_package(antlr4-runtime REQUIRED)

antlr4_generate(
    poc_lexer
    ${CMAKE_CURRENT_SOURCE_DIR}/TLexer.g4
    LEXER
    FALSE
    FALSE
    "poc"
)

antlr4_generate(
    poc_parser
    ${CMAKE_CURRENT_SOURCE_DIR}/TParser.g4
    PARSER
    FALSE
    TRUE
    "poc"
    "${ANTLR4_TOKEN_FILES_poc_lexer}"
    "${ANTLR4_TOKEN_DIRECTORY_poc_lexer}"
)

include_directories( ${PROJECT_BINARY_DIR} ${ANTLR4_INCLUDE_DIR} ${ANTLR4_INCLUDE_DIR_poc_lexer} ${ANTLR4_INCLUDE_DIR_poc_parser} )

add_executable(poc poc.cpp ${ANTLR4_SRC_FILES_poc_lexer} ${ANTLR4_SRC_FILES_poc_parser})

target_link_libraries(poc PRIVATE fmt::fmt antlr4_static)
