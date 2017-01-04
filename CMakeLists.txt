PROJECT(DataAugmentation)

CMAKE_MINIMUM_REQUIRED(VERSION 3.0)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra --fast-math -O3 -std=gnu++11 -fbuiltin -fdiagnostics-color=always -Wno-unused-parameter -Wno-unused-variable")

FIND_PACKAGE(OpenCV REQUIRED)
FIND_PACKAGE(Boost REQUIRED system filesystem program_options)


ADD_LIBRARY(Util Util.cpp)
ADD_LIBRARY(RandomRotation RandomRotation.cpp)
ADD_LIBRARY(DataAugmentation DataAugmentation.cpp)

ADD_EXECUTABLE(DataAugmenter main.cpp)

TARGET_LINK_LIBRARIES(DataAugmenter
    ${OpenCV_LIBS}
    ${Boost_LIBRARIES}
    
    DataAugmentation
    Util
    RandomRotation
)

