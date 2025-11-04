### Project 5 Line Tracking Sensor

**1.Description**

![](media/image-20251101095556348.png)

The line tracking sensor is actually an infrared sensor. There is a 3-channel line tracking in front of the driver base board of the car, and the component used here is TCRT5000 IR tube. It works by using the different reflectance of IR light on colors and then converting the intensity of the reflected signal into an electric current signal.

Black is active at high voltage, while white is active at low voltage when detecting. The detection height is 0-3 cm. There are three blue rotary potentiometers to adjust the detection sensitivity of the sensor.

**2.Component Knowledge**

- Working voltage: 3.3-5V (DC) 
- Interface: 5PIN interface (connect to A0,A1,A2 ) 
- Output signal: Digital signals(The analog port can also be used as a digital signal, A0 corresponds to D13 and A1 corresponds to D14 ) 
- Height detection: 0-3 cm

**Principle:** It works by using the different reflectance of IR ray on color s and then converting the intensity of the reflected signal into an elec tric current signal. When powering on, the diode emits IR light. FB- is the potentiometer, adjusting it can get a threshold voltage for the 4, 6 and 8 pins of the voltage comparator LM339D. The voltage value ca n be determined according to the actual situation.

When infrared diode receives the infrared light, they will generate a current, and as the infrared light changes from weak to strong, the current increases from small to large. However, when there is no infrared light or it is very weak, the output signal is close to VCC.

After passing the LM339D comparator, the receiving detection pin outputs a high level. When the light intensity and the current increase, the output voltage will become smaller, when it is small to a certain extent, the pin will become low level.

Furthermore, if black or no object is detected, the signal end of the M CU will receive a high level. While a white object is detected, a low le vel will be received.

![](media/image-20251101095822717.png)

**3.Test Code**

![](media/image-20251101150943128.png)

**4.Test Result**

After compiling and uploading the code, turn the DIP switch to ON end and open the serial monitor and click ![](media/image-20251101100006707.png)to set the baud rate to 9600. We can see the digital signal received by the three-channel line tracking sensor printed on the monitor. When we cover it with white paper, the output is 0, when using black paper or hanging the car, the output is 1.

![](media/image-20251101100039729.png)