add_executable(udcli udcli.c)
target_include_directories(udcli PRIVATE .. ${CMAKE_CURRENT_BINARY_DIR})
target_link_libraries(udcli PRIVATE udis86)
