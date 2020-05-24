find_program(PYTHON "python" REQUIRED)

find_file(HAVE_STRING_H NAMES string.h)
if(HAVE_STRING_H)
    add_definitions(-DHAVE_STRING_H)
endif()

set(OPTABLE ${CMAKE_CURRENT_SOURCE_DIR}/docs/x86/optable.xml)

add_library(udis86 STATIC
    itab.c
    decode.c
    syn.c
    syn-intel.c
    syn-att.c
    udis86.c)

add_custom_command(
    OUTPUT itab.c itab.h
    COMMAND ${PYTHON}
    ARGS ${CMAKE_CURRENT_SOURCE_DIR}/scripts/ud_itab.py ${OPTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/libudis86
    DEPENDS
        ${OPTABLE}
        ../scripts/ud_itab.py
        ../scripts/ud_opcode.py)
