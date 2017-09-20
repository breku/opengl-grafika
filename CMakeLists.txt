cmake_minimum_required(VERSION 3.8)
project(tutorial1)



set(CMAKE_CXX_STANDARD 11)

file(GLOB COMMON_SRC common/*.cpp)
file(GLOB shaders SimpleTransform.vertexshader SingleColor.fragmentshader)

set(SOURCE_FILES main.cpp ${COMMON_SRC} ${shaders})




find_package(OpenGL REQUIRED)
find_package(glfw3 3.2 REQUIRED)
find_package(GLEW REQUIRED)


if(NOT ${OPENGL_FOUND})
    message("OPENGL not found")
endif()

include_directories(
        ${PROJECT_SOURCE_DIR}
        ${GLEW_INCLUDE_DIR}
        ${OPENGL_INCLUDE_DIR}
        ${GLFW_INCLUDE_DIRS}
)

message(Directories)
message(PROJECT_SOURCE_DIR=${PROJECT_SOURCE_DIR})
message(GLEW_INCLUDE_DIR=${GLEW_INCLUDE_DIR})
message(OPENGL_INCLUDE_DIR=${OPENGL_INCLUDE_DIR})
message(GLFW_INCLUDE_DIRS=${GLFW_INCLUDE_DIRS})
message(Libraries)
message(----------------------------------)
message(OPENGL_LIBRARY=${OPENGL_LIBRARY})
message(GLEW_LIBRARY=${GLEW_LIBRARY})
message(OPENGL_gl_LIBRARY=${OPENGL_gl_LIBRARY})
message(OPENGL_glu_LIBRARY=${OPENGL_glu_LIBRARY})
message(glfw=${glfw})



add_executable(tutorial1 ${SOURCE_FILES})

target_link_libraries(${PROJECT_NAME}
        ${OPENGL_LIBRARY}
        ${GLEW_LIBRARY}
        ${OPENGL_gl_LIBRARY}
        ${OPENGL_glu_LIBRARY}
        glfw

        )

