cmake_minimum_required(VERSION 2.6)
PROJECT(boost-asio-proxy)

SET(Boost_USE_STATIC_LIBS OFF)
SET(Boost_USE_MULTITHREAD ON)
FIND_PACKAGE(Boost 1.42.0 REQUIRED COMPONENTS system thread regex)
IF(Boost_FOUND)
  INCLUDE_DIRECTORIES(${Boost_INCLUDE_DIRS})
  LINK_DIRECTORIES(${Boost_LIBRARY_DIRS})
ENDIF(Boost_FOUND)

SET(USED_LIBS ${Boost_SYSTEM_LIBRARY} ${Boost_THREAD_LIBRARY} ${Boost_REGEX_LIBRARY} -lpthread)

ADD_EXECUTABLE(proxy proxy.cpp proxy-server.cpp proxy-conn.cpp)
TARGET_LINK_LIBRARIES(proxy ${USED_LIBS})

