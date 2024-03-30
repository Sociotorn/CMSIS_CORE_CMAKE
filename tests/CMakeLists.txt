cmake_minimum_required(VERSION 3.2)

set(CMAKE_TOOLCHAIN_FILE "toolchain.cmake")
set(CMAKE_VERBOSE_MAKEFILE ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS true)

project(TEST_CMSIS)

set(TEST_SOURCES
    testcm7.c
)

enable_language(C ASM CXX)
set(CMAKE_C_STANDARD 17)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

#SET(ARM_CM7 true)
add_compile_options(
    -Os
    -g3
    -Wall
    -mcpu=cortex-m7
)

add_link_options(
    -specs=nosys.specs
)

add_subdirectory(.. ../build/CMSIS)
# set(EXECUTABLE ${PROJECT_NAME}.elf)

# add_executable(${EXECUTABLE} ${TEST_SOURCE})
# target_include_directories(${EXECUTABLE} PRIVATE .)

# target_link_libraries(${EXECUTABLE} CMSIS)

foreach(TEST_SOURCE ${TEST_SOURCES})
    # Get the base name of the test source file (without the directory and extension)
    get_filename_component(TEST_NAME ${TEST_SOURCE} NAME_WE)

    set(TEST_EXECUTABLE "${TEST_NAME}.elf")

    # Add an executable target for each test source
    add_executable(${TEST_EXECUTABLE} ${TEST_SOURCE})

    target_include_directories(${TEST_EXECUTABLE} PRIVATE .)

    target_link_libraries(${TEST_EXECUTABLE} CMSIS)

    add_custom_command(TARGET ${TEST_EXECUTABLE}
        POST_BUILD
        COMMAND ${CMAKE_SIZE_UTIL} ${TEST_EXECUTABLE})

# Optional: Create hex, bin and S-Record files after the build
    add_custom_command(TARGET ${TEST_EXECUTABLE}
        POST_BUILD
        COMMAND ${CMAKE_OBJCOPY} -O srec --srec-len=64 ${TEST_EXECUTABLE} ${TEST_NAME}.s19
        COMMAND ${CMAKE_OBJCOPY} -O ihex ${TEST_EXECUTABLE} ${TEST_NAME}.hex
        COMMAND ${CMAKE_OBJCOPY} -O binary ${TEST_EXECUTABLE} ${TEST_NAME}.bin)
endforeach()