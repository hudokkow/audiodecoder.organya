project(audiodecoder.organya)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(kodi REQUIRED)
find_package(p8-platform REQUIRED)

include_directories(${KODI_INCLUDE_DIR}
                    ${p8-platform_INCLUDE_DIRS}
                    ${PROJECT_SOURCE_DIR}/lib/liborganya)

add_subdirectory(lib/liborganya)

set(ORG_SOURCES src/OrganyaCodec.cpp
                src/RingBuffer.cpp)

set(DEPLIBS ${p8-platform_LIBRARIES} organya)

build_addon(audiodecoder.organya ORG DEPLIBS)

include(CPack)
