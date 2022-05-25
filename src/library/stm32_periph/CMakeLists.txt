aux_source_directory(src files)

add_library(stm32lib STATIC ${files} ../cmsis/CoreSupport/core_cm3.c)
target_include_directories(stm32lib PUBLIC inc)
