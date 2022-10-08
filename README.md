# STM32F103_SineWave_ADC_DMA_Ex03
Generating of a sinusoidal signal using PWM as a DAC, in parallel with ADC conversions., and in the last a UART transfer when triggered..

In this tutorial i´m going to show an application where the STM32F103 (blue pill) communicates with the PC Software Labview, using the serial port UART. 
The code burned in STM32 generates a sinusoidal signal at A0 port, and, at the same time, read the ADC port A1. These reads are stored in a buffer of 128 positions. 
When a string "next" is send by Labview and received by STM32, all the buffer, with the last 128 ADC conversions, is send from STM32 to Labview by serial port UART.


To create the sinusoidal wave and control the correct time of the ADC conversions i´ve used the Timers 2 and 4.  Furthermore, i´ve used a look up table where the values of the sine wave were stored. 

The Timer 2 controls the generation of the PWM signal . 
The Timer 4 controls the exact moment that the ADC conversion is done by DMA, and  the exact moment that the DMA transfer the value from look up table to timer 2 register

The figure below shows the thinking behind the code. 
![Lock-in Timers - English](https://user-images.githubusercontent.com/114233216/194731206-98592e6a-9aa4-45ea-a5d4-15d05d50d6a3.png)


1. Configuration of CLock

![1  Clock Config](https://user-images.githubusercontent.com/114233216/194729929-24a032da-cbbf-455c-9e9e-38a46fa51316.png)

2. Timer 2 Configuration

![2  Timer2a](https://user-images.githubusercontent.com/114233216/194730059-6da49eab-d9ed-49bd-9a4d-a4bb16f72869.png)
![2  Timer2b](https://user-images.githubusercontent.com/114233216/194730060-fecc569c-cdd9-4299-8236-18ddbddec228.png)


3. Timer 4 Configuration

![3  Timer4a](https://user-images.githubusercontent.com/114233216/194730064-8deb5b20-f2b7-4ded-a323-517737ea54e8.png)
![3  Timer4b](https://user-images.githubusercontent.com/114233216/194730067-0d990603-6589-4f55-89ce-ab7bd510393e.png)
![3  Timer4c](https://user-images.githubusercontent.com/114233216/194730068-8885b896-d30b-4791-9c0b-6854640486b0.png)


4. ADC Configuration

![4  ADC](https://user-images.githubusercontent.com/114233216/194730075-0100e3e7-d215-437e-88f1-d83c758ca43d.png)
![4  ADCa](https://user-images.githubusercontent.com/114233216/194730077-08feb7e7-2a16-4d77-8fcc-e0c717a1670c.png)


5. DMA Configuration

![5  DMA](https://user-images.githubusercontent.com/114233216/194730082-9fa8bf91-fccf-4532-b2f9-c60ae98d70a9.png)

6. UART COnfiguration

![6  UART](https://user-images.githubusercontent.com/114233216/194730093-0cc4f9be-80df-4f01-a776-ac677cdffa8c.png)


7. LabView Front

![prog_00](https://user-images.githubusercontent.com/114233216/194730105-c05f252f-1f3c-445b-a3e5-adfe47b58864.png)

8. Labview Code Diagram

![prog_01](https://user-images.githubusercontent.com/114233216/194730110-0fdd79f7-b040-4471-8a4a-63a9318c0cd0.png)

9. Result obtained in txt

![bloco_De_notas](https://user-images.githubusercontent.com/114233216/194730098-94338d85-c9c2-4a62-9209-ee3ef2653d47.png)




