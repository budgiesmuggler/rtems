ACLOCAL_AMFLAGS = -I ../../../../aclocal

include $(top_srcdir)/../../../../automake/compile.am

ALT=../shared/alt
ALT_HAL_SRC=$(ALT)/HAL/src
ALT_HAL_INC=$(ALT)/HAL/inc
ALT_DRV_SRC=$(ALT)/drivers/src
ALT_DRV_INC=$(ALT)/drivers/inc

AM_CPPFLAGS += -I $(srcdir)/$(ALT)
AM_CPPFLAGS += -I $(srcdir)/$(ALT_HAL_INC)
AM_CPPFLAGS += -I $(srcdir)/$(ALT_DRV_INC)
AM_CPPFLAGS += -Dalt_irq_handler=__ISR_Handler

dist_project_lib_DATA = bsp_specs

include_bspdir = $(includedir)/bsp

include_HEADERS = include/bsp.h
include_HEADERS += include/alt_linker.h
include_HEADERS += include/alt_system.h
include_HEADERS += ../../shared/include/tm27.h

include_HEADERS += $(ALT_HAL_INC)/nios2.h

nodist_include_HEADERS = include/bspopts.h
nodist_include_bsp_HEADERS = ../../shared/include/bootcard.h
nodist_include_bsp_HEADERS += ../../shared/include/console-polled.h
DISTCLEANFILES = include/bspopts.h

include_HEADERS += ../../shared/include/coverhd.h

EXTRA_DIST = times
noinst_LIBRARIES = libbspstart.a
libbspstart_a_SOURCES = start/crtnn.s
libbspstart_a_SOURCES += start/start.S
project_lib_DATA = start.$(OBJEXT) crtnn.$(OBJEXT)

dist_project_lib_DATA += startup/linkcmds

noinst_LIBRARIES += libbsp.a
libbsp_a_SOURCES =
# Altera sources
libbsp_a_SOURCES += \
    $(ALT_HAL_SRC)/alt_dcache_flush.c \
    $(ALT_HAL_SRC)/alt_dcache_flush_all.c \
    $(ALT_HAL_SRC)/alt_exception_entry.S \
    $(ALT_HAL_SRC)/alt_exception_muldiv.S \
    $(ALT_HAL_SRC)/alt_exception_trap.S \
    $(ALT_HAL_SRC)/alt_icache_flush.c \
    $(ALT_HAL_SRC)/alt_icache_flush_all.c \
    $(ALT_HAL_SRC)/alt_instruction_exception_entry.c \
    $(ALT_HAL_SRC)/alt_instruction_exception_register.c \
    $(ALT_HAL_SRC)/alt_irq_entry.S \
    $(ALT_HAL_SRC)/alt_load.c \
    $(ALT_HAL_SRC)/alt_software_exception.S
# startup
libbsp_a_SOURCES += \
    startup/bspstart.c \
    ../../shared/bspclean.c \
    ../../shared/bsplibc.c \
    ../../shared/bspreset_loop.c \
    ../../shared/bsppost.c \
    ../../shared/bsppretaskinghook.c \
    ../../shared/bspgetworkarea.c \
    ../../shared/bootcard.c \
    ../../shared/sbrk.c \
    ../../shared/setvec.c \
    ../../shared/gnatinstallhandler.c \
    ../../shared/bsppredriverhook.c

# clock
libbsp_a_SOURCES += clock/clock.c ../../../shared/clockdrv_shell.h
# console
libbsp_a_SOURCES += console/console.c ../../shared/console-polled.c
# timer
libbsp_a_SOURCES += timer/timer.c

include $(srcdir)/preinstall.am
include $(top_srcdir)/../../../../automake/local.am
