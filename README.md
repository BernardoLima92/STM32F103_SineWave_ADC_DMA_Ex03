# STM32F103_SineWave_ADC_DMA_Ex03
Generating of a sinusoidal signal using PWM as a DAC, in parallel with ADC conversions., and in the last a UART transfer when triggered..

In this tutorial i´m going to show an application where the STM32F103 (blue pill) communicates with the PC Software Labview, using the serial port UART. 
The code burned in STM32 generates a sinusoidal signal at A0 port, and, at the same time, read the ADC port A1. These reads are stored in a buffer of 128 positions. 
When a string "next" is send by Labview and received by STM32, all the buffer, with the last 128 ADC conversions, is send from STM32 to Labview by serial port UART.


To create the sinusoidal wave and control the correct time of the ADC conversions i´ve used the Timers 2 and 4.  Furthermore, i´ve used a look up table where the values of the sine wave were stored. 

The Timer 2 controls the exact moment that the DMA transfer the value from look up table to timer 2 register. 
The Timer 4 controls the exact moment that the ADC conversion is done. 





