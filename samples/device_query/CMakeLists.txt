#
# CMakeLists.txt
#

ADD_EXECUTABLE(device_query device_query.cpp)

ADD_TEST(NAME device_query COMMAND device_query)
