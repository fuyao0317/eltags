# add_subdirectory(library)

add_subdirectory(library/stm32_periph)

add_library(src OBJECT main.c startup_stm32f10x_ld.s system_stm32f10x.c)

target_link_libraries(src PUBLIC stm32lib)
# target_include_directories(src PUBLIC stm32lib)
