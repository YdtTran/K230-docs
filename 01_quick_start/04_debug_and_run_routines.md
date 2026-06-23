# 3. Debug and run routines

# Debug and run the routine

Debug and run the routinePrefaceSteps to run the routine1. Open CanMV IDE2. Connect K230 to the computer via USB cable3. Run the example codeOffline operation

## Preface

In this tutorial, we will learn how to use CanMV IDE to debug and run the routine code

Before starting this tutorial, please make sure that you have completed the installation of CanMV IDE and the burning of firmware mentioned in the previous chapter

## Steps to run the routine

### 1. Open CanMV IDE

Double-click to run the installed CanMV IDE

![1](1.png)

Click area ② to open the serial terminal

The purpose of the serial terminal is to facilitate us to view the debugging output during the program running process. Opening or closing the serial terminal will not affect the running effect of the program

### 2. Connect K230 to the computer via USB cable

After the connection is successful, the icon in the lower left corner of CanMV IDE will change

![image-20250401093544787](5.png)

If you do not turn on 【Auto Reconnect to CanMV】, you need to manually click the button above and wait for CanMV IDE to establish a connection with K230

If automatic connection is turned on, wait for a few seconds, CanMV IDE can successfully connect to K230, and the lower left corner will become as shown in the figure

![image-20250401094542962](6.png)

### 3. Run the example code

Let's take face detection as an example. Open the 【Source Code\07.Face】 directory in the downloaded data and find 01.face_detection.py

We double-click to open the file

1. The file name you may see is 01.face_detection, (no .py) because your computer system is not set to display file extensions

- It is strongly recommended to turn on this option during development. The methods for turning it on are different for different operating systems. Here we take win10 as an example

![image-20250508145653108](image-20250508145653108.png)

 

1. If you have not set the default open file with the py suffix, you can choose to use the system's built-in Notepad software to open the code

![image-20250401092641245](2.png)

![3](3.png)

We select all the code, press Ctrl + C on the keyboard, and copy all the code

Then return to CanMV IDE, **clear the default content**, press Ctrl + V, and paste the code we just copied

CanMV A new file in the IDE will have some default code content. Please select and delete all the default code before pasting.

![image-20250401093453328](4.png)

After pasting successfully, click the **green run button** in the lower left corner, and K230 will execute the face detection function.

![image-20250401095227420](7.png)

Click the red button in the lower left corner to exit the face detection function.

![image-20250401095323557](8.png)

So far, we have successfully used K230 **online** to run a program.

## Offline operation

Through the method mentioned above, we successfully let K230 run a face detection code in an online state (connected to CanMV IDE). At this time, the code is not saved on K230.

In actual scenarios, we often need to save the code offline in K230, and hope that K230 can automatically run the corresponding code after power on.

At this time, we only need to click 【Save open script to CanMV board (as main.py)】 in the toolbar in CanMV IDE

![image-20250401095850006](9.png)

Notes

1. Please click this button when the code stops running, otherwise the save may fail
2. If you want to delete the automatically running program, just delete the main.py file in the /sdcard/ directory of K230