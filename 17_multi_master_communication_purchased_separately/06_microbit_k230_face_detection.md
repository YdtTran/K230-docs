# 6.microbit_k230 face detection

# microbit_k230 face detection

microbit_k230 face detectionK230 and microbit communication1. Experimental Prerequisites2. Experimental wiring3.  Main code explanation4. Experimental Phenomenon

## K230 and microbit communication

### 1. Experimental Prerequisites

This tutorial uses microbit, and the corresponding routine path is [14.export\microbit-K230\6.Microbit_k230_face_detect].

K230 needs to run the [14.export\CanmvIDE-K230\06.face_detection.py] program to start the experiment. It is recommended to download it as an offline program.

 

Items needed:

Windows computer,  microbit,  USB to TTL module,  K230 vision module (including TF card with image burned),  type-C data cable, connecting cable (Dupont cable),  alligator clip,  import K230AI library: [https://github.com/YahboomTechnology/K230-Module.git](https://github.com/YahboomTechnology/K230-Module.git)

 

### 2. Experimental wiring

|  |  |
| --- | --- |
|  |  |
|  |  |

|  |  |
| --- | --- |
|  |  |
|  |  |

![image-20250430112815670](https://www.yahboom.net/public/upload/upload-html/1753873470/Microbit.png)

### 3.  Main code explanation

![image-20250728103800290](https://www.yahboom.net/public/upload/upload-html/1753873470/image-20250728103800290.png) 

From the code, we can simply configure the serial port and call the relevant serial port and K230 building blocks to obtain data.

- x: is the horizontal coordinate of the upper left corner of the identified box
- y: is the vertical coordinate of the upper left corner of the identified box
- w: is the width of the identified box
- h: is the length of the identified box

If you want to open the source code of this tutorial, please drag the microbit source code corresponding to this tutorial into the makecode online programming webpage of the browser. The online programming website is: [https://makecode.microbit.org/#](https://makecode.microbit.org/#)

### 4. Experimental Phenomenon

1. After connecting the cables, the k230 visual module runs offline
After K230 is connected to Canmv IDE, open the corresponding program, click [Save open script to CanMV board (as main.py)] on the toolbar, and then restart K230.

  ![image-20250429194108060](https://www.yahboom.net/public/upload/upload-html/1753873470/image-20250429194108060.png)

1. Find the hex program of this tutorial, right-click the hex program, and upload the hex program of this tutorial to the microbit

![image-20250715190851818](https://www.yahboom.net/public/upload/upload-html/1753873470/image.png) 

1. 

The serial port assistant is set to the interface shown in the figure
![image-2023060600004](https://www.yahboom.net/public/upload/upload-html/1753873470/2023060600004.png)
2. 

  1. When the K230 camera recognizes a face, the serial port assistant will print out the information transmitted from K230 to microbit.

- 

x: is the horizontal coordinate of the upper left corner of the identified box
- 

y: is the vertical coordinate of the upper left corner of the identified box
- 

w: is the width of the identified box
- 

h: is the length of the identified box

As shown in the figure below
![image-20250717181712512](https://www.yahboom.net/public/upload/upload-html/1753873470/image-20250717181712512.png)