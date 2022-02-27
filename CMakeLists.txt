cmake_minimum_required(VERSION 3.0)
project(testy)


add_compile_options(-Wall -Wextra -pedantic -Werror)

include(FetchContent)
FetchContent_Declare(
        googletest
        GIT_REPOSITORY https://github.com/google/googletest.git
        GIT_TAG main
)

FetchContent_MakeAvailable(googletest)
enable_testing()

add_library(sampleAppLib src/hello.cpp)


add_executable(sampleTest ut/sampleTest.cpp src/main.cpp )
add_executable(sampleApp src/main.cpp)

target_link_libraries(sampleTest sampleAppLib gtest gmock_main gmock)
target_link_libraries(sampleApp sampleAppLib)

include_directories(include)
