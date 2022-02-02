# build library
add_library(matrix ${PROJECT_SOURCE_DIR}/include/math/Matrix.h ${PROJECT_SOURCE_DIR}/src/math/Matrix.cpp)

# Create test executable
add_executable(matrix_test ${PROJECT_SOURCE_DIR}/tests/matrix_test.cpp)

# Linx the matrix library to the test executable
target_link_libraries(matrix_test matrix)
