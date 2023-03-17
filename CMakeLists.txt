cmake_minimum_required(VERSION 3.21...3.99)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")
include(Tools)
find_version_file("" ASTRAEUS_VERSION_FILE)
message(STATUS "Found version file: ${ASTRAEUS_VERSION_FILE}")
read_version("${ASTRAEUS_VERSION_FILE}" "" VERSION_STRING)

project("Astraus"
    VERSION "${VERSION_STRING}"
    DESCRIPTION "Lost in Space Plate Solver"
    HOMEPAGE_URL "https://github.com/dpilger26/Astraeus"
    LANGUAGES CXX
)

message(STATUS "Building ${PROJECT_NAME} version ${VERSION_STRING}")

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

if(NOT CMAKE_CXX_STANDARD)
    set(CMAKE_CXX_STANDARD 17)
endif()
message(STATUS "Compiling with C++ standard: ${CMAKE_CXX_STANDARD}")

set(CMAKE_EXPORT_COMPILE_COMMANDS ON CACHE INTERNAL "") # works


add_subdirectory(src)
if(BUILD_TESTS)
    add_subdirectory(test)
endif()