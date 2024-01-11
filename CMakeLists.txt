cmake_minimum_required(VERSION 3.23)
set(CMAKE_CXX_STANDARD 23)

project(cpp_algorithms)

aux_source_directory(source/utility SRC_UTIL_LIST)
aux_source_directory(source/sort SRC_SORT_LIST)
aux_source_directory(source/link_list SRC_LINK_LIST)
aux_source_directory(source/string SRC_STR_LIST)
aux_source_directory(source/tree SRC_TREE_LIST)
aux_source_directory(source/graph SRC_GRAPH_LIST)
aux_source_directory(source/greedy SRC_GREEDY_LIST)
aux_source_directory(source/dynamic_programming SRC_DP_LIST)
aux_source_directory(source/other SRC_OTHER_LIST)

file(GLOB HEADERS "*.h")
include_directories(${HEADERS})

# lib
link_libraries(ws2_32)

# boost
set(BOOST_ROOT F:/boost/boost_1_84_0)
find_package(Boost 1.84.0 REQUIRED COMPONENTS)
if(Boost_FOUND)
    message(Boost_INCLUDE_DIRS " ${Boost_INCLUDE_DIRS}")
    message(Boost_LIBRARY_DIRS " ${Boost_LIBRARY_DIRS}")
    include_directories(${Boost_INCLUDE_DIRS})
    link_directories(${Boost_LIBRARY_DIRS})
endif()

add_executable(
        cpp_algorithms
        ${SRC_UTIL_LIST}
        ${SRC_SORT_LIST}
        ${SRC_LINK_LIST}
        ${SRC_STR_LIST}
        ${SRC_TREE_LIST}
        ${SRC_GRAPH_LIST}
        ${SRC_GREEDY_LIST}
        ${SRC_DP_LIST}
        ${SRC_OTHER_LIST}
        source/main.cpp
)
