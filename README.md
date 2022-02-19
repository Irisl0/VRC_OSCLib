# VRC_OSCLib
## Library for using OSC control of VRChat
Request "pythonosc" https://pypi.org/project/python-osc/

 Copyright (c) 2013 Iris
 Released under the MIT license
 https://opensource.org/licenses/mit-license.php

## Reference

### AV3 SetParameter

```Python
AV3_SetInt(data = 0 , Parameter = "example" , IP = '127.0.0.1' ,PORT = 9000)
```
date : Transmission data (0 - 255)
Parameter : Parameter Name
IP : IP Address (Option)
PORT : Port Number (Option)

```Python
AV3_SetFloat(data = 0 , Parameter = "example" , IP = '127.0.0.1' ,PORT = 9000)
```
date : Transmission data (0 - 1.0)
Parameter : Parameter Name
IP : IP Address (Option)
PORT : Port Number (Option)

```Python
AV3_SetBool(data = False , Parameter = "example" , IP = '127.0.0.1' ,PORT = 9000)
```
date : Transmission data (0,1)
Parameter : Parameter Name
IP : IP Address (Option)
PORT : Port Number (Option)

### VRChat Imput Control
Refer to the VRChat official page for the values that can be entered.
https://docs.vrchat.com/v2022.1.1/docs/osc-as-input-controller

```Python
Control_Push(Button = "example" , IP = '127.0.0.1' ,PORT = 9000)
```
Button : Imput Button Name
IP : IP Address (Option)
PORT : Port Number (Option)


```Python
Control_Joystick(data = 0.0 ,axis = "example" , IP = '127.0.0.1' ,PORT = 9000)
```
date : Power (-1.0 - 1.0)
axis : Imput Axis Name
IP : IP Address (Option)
PORT : Port Number (Option)

### Direct Interface
```Python
Buttons(address = "/input/example" , IP = '127.0.0.1' ,PORT = 9000)
```
address : Taget OSC Address
IP : IP Address (Option)
PORT : Port Number (Option)


```Python
Int(data = 0 ,address = "/input/example" ,IP = '127.0.0.1' ,PORT = 9000)
```
date : Transmission data (0 - 255)
address : Taget OSC Address
IP : IP Address (Option)
PORT : Port Number (Option)

```Python
Float(data = 0.0 ,address = "/input/example" ,IP = '127.0.0.1' ,PORT = 9000)
```
date : Transmission data (0 - 1.0)
address : Taget OSC Address
IP : IP Address (Option)
PORT : Port Number (Option)

```Python
Bool(data = False ,address = "/input/Jump" , IP = '127.0.0.1' ,PORT = 9000)
```
date : Transmission data (0,1)
address : Taget OSC Address
IP : IP Address (Option)
PORT : Port Number (Option)
