cmake_minimum_required(VERSION 3.16)

set(PROJECT_NAME ftps)

project(${PROJECT_NAME} VERSION 1.0
             DESCRIPTION "FTPS"
             LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_compile_options(-Wall -Werror -g -Og)

configure_file(version.hpp.in ../include/${PROJECT_NAME}/version.hpp)

add_executable(ftp_client)
add_executable(ftp_server)

file(GLOB headers ${PROJECT_SOURCE_DIR}/include/${PROJECT_NAME}/*.hpp)

target_sources(ftp_client PUBLIC ${headers})
target_sources(ftp_server PUBLIC ${headers})

target_compile_features(ftp_client PRIVATE cxx_std_17)
target_compile_features(ftp_server PRIVATE cxx_std_17)

target_include_directories(ftp_client PUBLIC
                           ${PROJECT_SOURCE_DIR}/include
                          )

target_include_directories(ftp_server PUBLIC
                           ${PROJECT_SOURCE_DIR}/include
                          )

add_subdirectory(src)