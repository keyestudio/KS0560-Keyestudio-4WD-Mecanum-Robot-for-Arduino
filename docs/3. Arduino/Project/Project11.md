### Project 11 IR Remote Control Smart Car

![](media/image-20251031160814755.png)

**1.Description**

 In this project, we will work to control the car using an IR remote control.

**2.Flow Diagram**

![](media/image-20251031161157688.png)

**3.Test Code**

```
#include "MecanumCar_v2.h"
mecanumCar mecanumCar(3, 2);  //sda-->D3,scl-->D2
#include "ir.h"
IR IRreceive(A3);//IR receiver is connected to A3

void setup()
{
  Serial.begin(9600); //Set baud rate to 9600
  mecanumCar.Init(); //Initialize the seven-color LED and motor drive
}

void loop() 
{
  int key = IRreceive.getKey();
  if (key != -1) 
  {
    Serial.println(key);
    switch (key)
    {
      case 64: mecanumCar.Stop();       break;  //Stop
      case 70: mecanumCar.Advance();    break;  //Advance
      case 21: mecanumCar.Back();       break;  //Move back
      case 68: mecanumCar.Turn_Left();  break;  //Turn left
      case 67: mecanumCar.Turn_Right(); break;  //Turn right
    }
  }
}
```

**4.Test Result**

After uploading the test code and turning the DIP switch to the ON end and powering up. When we press the button ![](media/image-20251031161442170.png)on the remote control, the car moves forward, then ![](media/image-20251031161519495.png),,the car turns left,![](media/image-20251031161707391.png),the car moves back,![](media/image-20251031161747116.png),the car turns right,![](media/image-20251031161816571.png),the car stops.

**5.Code Explanation**

```
switch (key)
{
	case num: ...... break;
}
// The switch statement, used with case, executes the statement after case when the variable in parentheses is the value after case.
```

```
case 64: mecanumCar.Stop();  //The car will stop
```

```
case 70: mecanumCar.Advance();   //The car will go forward
```

```
case 21: mecanumCar.Back();  //The car will move back
```

```
case 68: mecanumCar.Turn_Left();  //The car will turn left
```

```
case 67: mecanumCar.Turn_Right(); //The car will turn right
```







