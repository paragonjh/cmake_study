cmake_minimum_required(VERSION 3.17.3)

project(myproject)

if (${JSON_VERSION} MATCHES "json1")
    message(STATUS "Use json1 library")
    add_subdirectory(json/json1)
    include_directories(json/json1)
elseif (${JSON_VERSION} MATCHES "json2")
    message(STATUS "Use json2 library")
    add_subdirectory(json/json2)
    include_directories(json/json2)
else ()
    message(FATAL_ERROR "Undefined json library")
endif()

add_executable(${CMAKE_PROJECT_NAME} main.cpp)
target_link_libraries(${CMAKE_PROJECT_NAME} json)


