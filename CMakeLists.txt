cmake_minimum_required(VERSION 3.12)

# Pull in Pico SDK
include(pico_sdk_import.cmake)

project(blink C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(PICO_BOARD pico_w)
set(PICO_EXAMPLES_PATH ${PROJECT_SOURCE_DIR})

# Initialize the SDK
pico_sdk_init()

add_executable(blink
        blink.c
        )
# Pull in our pico_stdlib 
target_link_libraries(blink pico_stdlib pico_cyw43_arch_none)

#create map/bin/hex file etc.
pico_add_extra_outputs(blink)

#enable USB serial output
pico_enable_stdio_usb(blink 1)

pico_enable_stdio_uart(blink 0)