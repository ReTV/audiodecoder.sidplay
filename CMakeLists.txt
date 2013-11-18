project(audiodecoder.sidplay)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(xbmc REQUIRED)
find_package(Sidplay2)
find_package(Resid)

add_definitions(-DHAVE_UNIX)

set(SID_SOURCES src/SIDCodec.cpp)

list(APPEND DEPLIBS ${SIDPLAY2_LIBRARIES}
                    ${RESID_LIBRARIES})
include_directories(${XBMC_INCLUDE_DIR}
                    ${RESID_INCLUDE_DIRS}
                    ${SIDPLAY2_INCLUDE_DIRS})

build_addon(audiodecoder.sidplay SID DEPLIBS)