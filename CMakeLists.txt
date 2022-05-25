cmake_minimum_required(VERSION 3.18)
enable_language(C ASM)
project(eltags)
set(CMAKE_SYSTEM_NAME Generic)
set(CMAKE_C_COMPILER arm-none-eabi-gcc)
set(CMAKE_ASM_COMPILER arm-none-eabi-gcc)

# add_compile_definitions(STM32F10X_LD USE_STDPERIPH_DRIVER __CNUC__)
add_compile_definitions(STM32F10X_LD USE_STDPERIPH_DRIVER)
add_compile_options(-mcpu=cortex-m3 --specs=nosys.specs -mthumb -mfloat-abi=soft)
set(ld_file src/stm32_flash.ld)
add_link_options(-T${ld_file} --specs=nosys.specs)

set(CMAKE_EXPORT_COMPILE_COMMANDS TRUE)

include_directories(include)
include_directories(src/library/cmsis/CoreSupport/)

add_subdirectory(src)

add_executable(eltags)
target_link_libraries(eltags PUBLIC src)


