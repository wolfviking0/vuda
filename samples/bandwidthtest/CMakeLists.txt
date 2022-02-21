#
# CMakeLists.txt
#

IF(NOT NO_CUDA)
    SET_SOURCE_FILES_PROPERTIES(bandwidthtest.cpp PROPERTIES LANGUAGE CUDA)
ENDIF()

ADD_EXECUTABLE(bandwidthtest bandwidthtest.cpp)

ADD_TEST(NAME bandwidthtest COMMAND bandwidthtest)
