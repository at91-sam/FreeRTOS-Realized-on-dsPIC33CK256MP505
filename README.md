# FreeRTOS-Realized-on-dsPIC33CK256MP505
Objective:
==========
This repository contains a simple FreeRTOS project on MCU dsPIC33CK256MP505.

Related Documentation:
=====================
1) [dsPIC33CK256MP508-Family-Data-Sheet-DS70005349H](http://ww1.microchip.com/downloads/en/DeviceDoc/dsPIC33CK256MP508-Family-Data-Sheet-DS70005349H.pdf)

Software Used:
==============
1) [MPLAB® X IDE 5.40](microchip.com/mplab/mplab-x-ide)
2) [MPLAB® XC16 1.60](microchip.com/mplab/compilers)
3) [MPLAB® Code Configurator (MCC) 4.0.1](microchip.com/mplab/mplab-code-configurator)
4) [MPLAB® Code Configurator (MCC) Device Libraries PIC24 / dsPIC33 / PIC32MM MCUs 1.169.2](microchip.com/mplab/mplab-code-configurator)
5) [Microchip dsPIC33CK-MP Series Device Support 1.5.135](packs.download.microchip.com/)

Hardware Used:
=============
1) [dsPIC33C Digital Power Starter Kit (Part Number: DM330017-3)](https://www.microchip.com/developmenttools/ProductDetails/DM330017-3)

Setup:
======
All the software code except main.c was generated by mcc.

Just realized one tusk Task_100us, and one 500ms Timer interrupt, and task do simple work like toggle IO.

configMAX_SYSCALL_INTERRUPT_PRIORITY is 4, so if 500ms timer interrupt priority is <=4, then 500ms timer interrupt will be masked by FreeRTOS when call something like portDISABLE_INTERRUPTS(). You should know that __delay_ms(5000) in 500ms Timer interrupt should not be replaced by blocked delay ( vTaskDelay(50000) ).

Note:
FreeRTOSConfig.h should be modified in your real application code if you referred to this project, for example, configMINIMAL_STACK_SIZE, configTOTAL_HEAP_SIZE.

Operation:
==========
When run this example, TP50 and LD5 will be toggled in Task_100us and 500ms Timer interrupt separetly.


Summary:
========
Actually, this is one example for dsPIC33CK256MP505, you could use these code for other Microchip's 16bit MCU.
