#
# CMakeLists.txt
#

SET(BINARY_DIR ${CMAKE_BINARY_DIR})
SET(SHADER_DIR ${CMAKE_CURRENT_SOURCE_DIR})
FILE(GLOB SHADERS ${SHADER_DIR}/*.comp)

SET(SPV_SHADERS)

FOREACH(SHADER IN LISTS SHADERS)
    GET_FILENAME_COMPONENT(FILENAME ${SHADER} NAME_WE)
    ADD_CUSTOM_COMMAND(
        OUTPUT ${BINARY_DIR}/${FILENAME}.spv
        COMMAND ${Vulkan_GLSLC_EXECUTABLE} ${SHADER} -o ${BINARY_DIR}/${FILENAME}.spv
        DEPENDS ${SHADER}
        COMMENT "Compiling ${FILENAME}"
    )
    LIST(APPEND SPV_SHADERS ${BINARY_DIR}/${FILENAME}.spv)
ENDFOREACH()

IF(NO_CUDA)
    ADD_CUSTOM_TARGET(shaders_threads_and_streams ALL DEPENDS ${SPV_SHADERS})
    ADD_EXECUTABLE(threads_and_streams threads_and_streams.cpp ${SHADERS})
    ADD_DEPENDENCIES(threads_and_streams shaders_threads_and_streams)
ELSE()
    SET_SOURCE_FILES_PROPERTIES(threads_and_streams.cpp PROPERTIES LANGUAGE CUDA)
    ADD_EXECUTABLE(threads_and_streams threads_and_streams.cpp)
ENDIF()

ADD_TEST(
    NAME threads_and_streams
    COMMAND ${CMAKE_CURRENT_BINARY_DIR}/threads_and_streams
    WORKING_DIRECTORY ${CMAKE_BINARY_DIR}
)
