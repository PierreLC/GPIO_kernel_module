GPIO_kernel_module
==================


Filename: gpio_interrupt_led_module.c    
                                                                   
Author:   Pierre LE COZ
		
Purposet: Test and demonstrate how to use GPIOs, interrupts and timers in a linux kernel module. 
	     
Date:     January 2013

Informations: This is a linux loadable kernel module.
As user space cannot provide access to the GPIO, it is necessary 
to develop code for the kernel to manage interrupts and GPIO pin values.
The cross-compiler produces a .ko file that can be loaded in the kernel using "insmod" command.
"rmmod" removes the module from kernel. 
The module is tested on a ARM developement platform embedding a minimal linux system.
A RS-232 to USB cable allows to controle the board from the development computer.  
The module is build using a cross-toolchaine created with Buildroot. 

What the module does: A small electronic circuit is connected to the GPIO.
The circuit is made of a push button with its debouncing circuitry and 2 Leds, LED1 and LED2.
Once the module is loaded (using "insmod"), the LED1 lights up. 
Pressing the push button makes an interrupt request. When the interrupt is received, 
the handler call a function that switches leds states: LED1 shut off and LED2 lights up. 
A new press will set the system in its original state (LED1 on, LED2 off) etc.
A kernel timer schedules the switching function call 1 second after the button press.
Finally, Running "cat /proc/interrupts" allows to see interrupts seen from the kernel.      
