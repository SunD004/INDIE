cmake_minimum_required(VERSION 2.6)
PROJECT(bomberman)

SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/release)
set(CMAKE_CXX_STANDARD 14)

#add files
FILE(GLOB SRCS src/*.cpp)
FILE(GLOB HDRS include/*.h)
#set les includes
INCLUDE_DIRECTORIES(
   ${PROJECT_SOURCE_DIR}/irrlicht/include/
   ${PROJECT_SOURCE_DIR}/include
)
##config du binaire
ADD_EXECUTABLE(bomberman
   ${SRCS}
   ${HDRS}
)
 

if(UNIX)
    TARGET_LINK_LIBRARIES(bomberman
        ${PROJECT_SOURCE_DIR}/irrlicht/linux/libIrrlicht.a
        -lXxf86vm
        -lX11
        -lGL
        -lpthread
    )
elseif(WIN32)
    TARGET_LINK_LIBRARIES(bomberman
        ${PROJECT_SOURCE_DIR}/irrlicht/windows/32/Irrlicht.dll
        -lXxf86vm
        -lX11
        -lGL
        -lpthread
    )
elseif(WIN64)
    TARGET_LINK_LIBRARIES(bomberman
        ${PROJECT_SOURCE_DIR}/irrlicht/windows/64/Irrlicht.dll
        -lXxf86vm
        -lX11
        -lGL
        -lpthread
    )
endif()