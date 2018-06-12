# sets cmake minimu version
cmake_minimum_required(VERSION 3.0)
# Have CMake find our pthreads library within our toolchain (required for this library)
set(CMAKE_THREAD_PREFER_PTHREAD TRUE)
find_package(Threads REQUIRED)

add_library (wiringPi INTERFACE)
file(GLOB SRC_FILES wiringPi/*.c)
target_sources(wiringPi INTERFACE
    ${SRC_FILES}
)
# be sure to include the current source directory for header files
target_include_directories (wiringPi INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/wiringPi)
# add the following required libraries:
# Threads, Math, Crypt, and RealTime
target_link_libraries(wiringPi INTERFACE ${CMAKE_THREAD_LIBS_INIT} crypt m rt)
