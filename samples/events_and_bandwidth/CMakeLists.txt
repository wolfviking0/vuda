#
# CMakeLists.txt
#

ADD_EXECUTABLE(events_and_bandwidth events_and_bandwidth.cpp)

ADD_TEST(NAME events_and_bandwidth COMMAND events_and_bandwidth)
