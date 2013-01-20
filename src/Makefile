# Filename: Makefile
#
# Purpose:  Makefile for gpio_interrupt_led_module.c
#
# Author:   Pierre LE COZ


ifneq (${KERNELRELEASE},)

	obj-m += gpio_interrupt_led_module.o


else

	# target architecture
	ARCH          ?= arm

	# Linux kernel source
	KERNEL_DIR    ?= /home/petersmooth/XenoPi/linux-rpi

	# GCC cross-compiler path 
	CROSS_COMPILE ?= /usr/local/cross-rpi/usr/bin/arm-linux-

	# gpio_interrupt_led_module.c module directory
	MODULE_DIR    := $(shell pwd)

	# Show all possible warnings
	CFLAGS        := -Wall


all: modules

modules:
	${MAKE} -C ${KERNEL_DIR} ARCH=${ARCH} CROSS_COMPILE=${CROSS_COMPILE} SUBDIRS=${MODULE_DIR} modules


# Clean output files

clean:
	rm -f  *.o  .*.o  .*.o.* *.ko  .*.ko  *.mod.* .*.mod.* .*.cmd
	rm -f Module.symvers Module.markers modules.order
	rm -rf .tmp_versions
endif


# EOF
