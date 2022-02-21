#
# CMakeLists.txt
#

IF(NOT NO_CUDA)
    SET_SOURCE_FILES_PROPERTIES(embedded_kernel.cpp PROPERTIES LANGUAGE CUDA)
ENDIF()

ADD_EXECUTABLE(embedded_kernel embedded_kernel.cpp)

ADD_TEST(NAME embedded_kernel COMMAND embedded_kernel)
