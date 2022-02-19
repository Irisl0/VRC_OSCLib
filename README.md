# VRC_OSCLib
## Library for using OSC control of VRChat
Request "pythonosc" https://pypi.org/project/python-osc/
```
 Copyright (c) 2013 Iris
 Released under the MIT license
 https://opensource.org/licenses/mit-license.php
```
## Reference

### AV3 SetParameter

```Python
AV3_SetInt(data = 0 , Parameter = "example" , IP = '127.0.0.1' ,PORT = 9000)
```
 - date : Transmission data (0 - 255)
 - Parameter : Parameter Name
 - IP : IP Address (Option)
 - PORT : Port Number (Option)

```Python
AV3_SetFloat(data = 0 , Parameter = "example" , IP = '127.0.0.1' ,PORT = 9000)
```
 - date : Transmission data (0 - 1.0)
 - Parameter : Parameter Name
 - IP : IP Address (Option)
 - PORT : Port Number (Option)

```Python
AV3_SetBool(data = False , Parameter = "example" , IP = '127.0.0.1' ,PORT = 9000)
```
 - date : Transmission data (0,1)
 - Parameter : Parameter Name
 - IP : IP Address (Option)
 - PORT : Port Number (Option)

### VRChat Imput Control
Refer to the VRChat official page for the values that can be entered.
https://docs.vrchat.com/v2022.1.1/docs/osc-as-input-controller

```Python
Control_Push(Button = "example" , IP = '127.0.0.1' ,PORT = 9000)
```
 - Button : Imput Button Name
 - IP : IP Address (Option)
 - PORT : Port Number (Option)


```Python
Control_Joystick(data = 0.0 ,axis = "example" , IP = '127.0.0.1' ,PORT = 9000)
```
 - date : Power (-1.0 - 1.0)
 - axis : Imput Axis Name
 - IP : IP Address (Option)
 - PORT : Port Number (Option)

### Direct Interface
```Python
Buttons(address = "/input/example" , IP = '127.0.0.1' ,PORT = 9000)
```
 - address : Taget OSC Address
 - IP : IP Address (Option)
 - PORT : Port Number (Option)


```Python
Int(data = 0 ,address = "/input/example" ,IP = '127.0.0.1' ,PORT = 9000)
```
 - date : Transmission data (0 - 255)
 - address : Taget OSC Address
 - IP : IP Address (Option)
 - PORT : Port Number (Option)

```Python
Float(data = 0.0 ,address = "/input/example" ,IP = '127.0.0.1' ,PORT = 9000)
```
 - date : Transmission data (0 - 1.0)
 - address : Taget OSC Address
 - IP : IP Address (Option)
 - PORT : Port Number (Option)

```Python
Bool(data = False ,address = "/input/Jump" , IP = '127.0.0.1' ,PORT = 9000)
```
 - date : Transmission data (0,1)
 - address : Taget OSC Address
 - IP : IP Address (Option)
 - PORT : Port Number (Option)

## Example scripts
Sample/VRC_OSCTSample.pyw
```Python
# Copyright (c) 2013 Iris
# Released under the MIT license
# https://opensource.org/licenses/mit-license.php

# Request "VRC_OSCLib"

import datetime
import sys

import VRC_OSCLib

import tkinter

# OSC Ax
def Stop():
    VRC_OSCLib.Control_Joystick(0 ,"Vertical")
    VRC_OSCLib.Control_Joystick(0 ,"Horizontal")
    VRC_OSCLib.Control_Joystick(0 ,"LookHorizontal")
    
def GoFront(Power = 1.0):
    VRC_OSCLib.Control_Joystick(1.0 ,"Vertical")
    
def GoBack(Power = 1.0):
    VRC_OSCLib.Control_Joystick(-Power ,"Vertical")

def GoLeft(Power = 1.0):
    VRC_OSCLib.Control_Joystick(-Power ,"Horizontal")
    
def GoRight(Power = 1.0):
    VRC_OSCLib.Control_Joystick(Power ,"Horizontal")

def LookLeft(Power = 0.5):
    VRC_OSCLib.Control_Joystick(-Power ,"LookHorizontal")
    
def LookRight(Power = 0.5):
    VRC_OSCLib.Control_Joystick(Power ,"LookHorizontal")

#OSC btn
def Jump():
    VRC_OSCLib.Control_Push("Jump")


#OSC bprm
def SetPramFloat():
    VRC_OSCLib.AV3_SetFloat(float(PrmData.get()) ,PrmName.get())

def SetPramInt():
    VRC_OSCLib.AV3_SetInt(int(PrmData.get()) ,PrmName.get())

def SetPramBool():
    VRC_OSCLib.AV3_SetBool(int(PrmData.get()) ,PrmName.get())

#Set Parameter

tki = tkinter.Tk()
tki.geometry('275x360')
tki.title('VRC_OSCSample')

Frame = tkinter.LabelFrame(tki, width=225, height=180, text="Imput")
Frame.place(x=25, y=10)#Imput

btnf = tkinter.Button(Frame, text='GoFront', command = GoFront)
btnf.place(x=80, y=10) #前進

btns = tkinter.Button(Frame, text='Stop', command = Stop)
btns.place(x=90, y=50) #停止

btnb = tkinter.Button(Frame, text='GoBack', command = GoBack)
btnb.place(x=80, y=90) #後退

btnlm = tkinter.Button(Frame, text='Left', command = GoLeft)
btnlm.place(x=30, y=50) #左移動

btnrm = tkinter.Button(Frame, text='Right', command = GoRight)
btnrm.place(x=150, y=50) #右移動

btnll = tkinter.Button(Frame, text='LookLeft', command = LookLeft)
btnll.place(x=10, y=10) #左を見る

btnrl = tkinter.Button(Frame, text='LookRight', command = LookRight)
btnrl.place(x=150, y=10) #右を見る

btnj = tkinter.Button(Frame, text='Jump', command = Jump)
btnj.place(x=85, y=130) #ジャンプ


FramePM = tkinter.LabelFrame(tki, width=225, height=150, text="Imput")
FramePM.place(x=25, y=200) #Imput

FramePMs = tkinter.LabelFrame(FramePM, width=140, height=45, text="パラメータ名")
FramePMs.place(x=42.5, y=0) #パラメータ

PrmName = tkinter.Entry(FramePMs, width=18)
PrmName.place(x=10, y=0) #name


FramePMd = tkinter.LabelFrame(FramePM, width=140, height=45, text="数値(0-1 or 0-255 or 0,1)")
FramePMd.place(x=42.5, y=50) #パラメータ

PrmData = tkinter.Entry(FramePMd, width=18)
PrmData.place(x=10, y=0) #data

btnj = tkinter.Button(FramePM, text='float送信', command = SetPramFloat)
btnj.place(x=10, y=100) #float送信
btnj = tkinter.Button(FramePM, text='int送信', command = SetPramInt)
btnj.place(x=85, y=100) #int送信
btnj = tkinter.Button(FramePM, text='bool送信', command = SetPramBool)
btnj.place(x=150, y=100) #bool送信

tki.mainloop()
```
