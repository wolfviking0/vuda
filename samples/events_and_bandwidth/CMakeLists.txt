#
# CMakeLists.txt
#

IF(NOT NO_CUDA)
    SET_SOURCE_FILES_PROPERTIES(events_and_bandwidth.cpp PROPERTIES LANGUAGE CUDA)
ENDIF()

ADD_EXECUTABLE(events_and_bandwidth events_and_bandwidth.cpp)

ADD_TEST(NAME events_and_bandwidth COMMAND events_and_bandwidth)
