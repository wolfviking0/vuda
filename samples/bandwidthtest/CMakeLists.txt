#
# CMakeLists.txt
#

ADD_EXECUTABLE(bandwidthtest bandwidthtest.cpp)

ADD_TEST(NAME bandwidthtest COMMAND bandwidthtest)
