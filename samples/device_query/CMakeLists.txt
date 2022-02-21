#
# CMakeLists.txt
#

IF(NOT NO_CUDA)
    SET_SOURCE_FILES_PROPERTIES(device_query.cpp PROPERTIES LANGUAGE CUDA)
ENDIF()

ADD_EXECUTABLE(device_query device_query.cpp)

ADD_TEST(NAME device_query COMMAND device_query)
