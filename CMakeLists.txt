add_subdirectory(CMSIS)

add_library(CMSIS INTERFACE)

target_link_libraries(CMSIS INTERFACE CMSIS_CORE)