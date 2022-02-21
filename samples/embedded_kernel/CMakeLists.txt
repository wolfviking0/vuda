#
# CMakeLists.txt
#

ADD_EXECUTABLE(embedded_kernel embedded_kernel.cpp)

ADD_TEST(NAME embedded_kernel COMMAND embedded_kernel)
