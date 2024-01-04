cmake_minimum_required(VERSION 3.13)

# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico_sdk_import.cmake)

project(cool_down_the_concrete_jungle)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

add_executable(test
    test.c
)

# Add pico_stdlib library which aggregates commonly used features
target_link_libraries(test pico_stdlib)

# enable usb output, disable uart output
pico_enable_stdio_usb(test 1)
pico_enable_stdio_uart(test 0)

# create map/bin/hex/uf2 file in addition to ELF.
pico_add_extra_outputs(test)