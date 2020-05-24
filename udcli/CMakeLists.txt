add_executable(udcli udcli.c)
target_include_directories(udcli PRIVATE ..)
target_link_libraries(udcli PRIVATE udis86)
