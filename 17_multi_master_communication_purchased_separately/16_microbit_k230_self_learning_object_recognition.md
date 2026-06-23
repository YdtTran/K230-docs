# 16.microbit_k230 self-learning object recognition

# microbit_k230 self-learning object recognition

microbit_k230 self-learning object recognitionK230 and microbit communication1.  Experimental Prerequisites2. Experimental wiring3. Main code explanation4. Experimental phenomenon

## K230 and microbit communication

### 1.  Experimental Prerequisites

This tutorial uses a micro:bit. The corresponding example program path is [14.export\microbit-K230\16.Microbit_k230_self_learning].

To begin the experiment, you must run the [14.export\CanmvIDE-K230\16.self_learning.py] program on the K230. We recommend downloading the program for offline operation.

 

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

![image-20250430112815670](https://www.yahboom.net/public/upload/upload-html/1753875032/Microbit.png)

### 3. Main code explanation

![image-20250730112759939](https://www.yahboom.net/public/upload/upload-html/1753875032/image-20250730112759939.png)

From the code, we can simply configure the serial port and call the relevant serial port and K230 building blocks to obtain data.

- category: The identified name
- score: The score

If you want to open the source code of this tutorial, please drag the microbit source code corresponding to this tutorial into the makecode online programming webpage of the browser. The online programming website is: [https://makecode.microbit.org/#](https://makecode.microbit.org/#)

### 4. Experimental phenomenon

1. After connecting the cables, the k230 visual module runs offline
After K230 is connected to Canmv IDE, open the corresponding program, click [Save open script to CanMV board (as main.py)] on the toolbar, and then restart K230.

  ![image-20250429194108060](https://www.yahboom.net/public/upload/upload-html/1753875032/image-20250429194108060.png)

When you power on the K230, a purple box will appear on the screen. Align the box with the objects you want to learn. There are two objects in total. Follow the on-screen instructions to learn both objects.

After learning both objects, if the corresponding object appears in the box, the object name and score will be displayed.

1. Find the hex program of this tutorial, right-click the hex program, and upload the hex program of this tutorial to the microbit

![image-20250716174052217](https://www.yahboom.net/public/upload/upload-html/1753875032/image.png) 

1. 

The serial port assistant is set to the interface shown in the figure
![image-2023060600004](https://www.yahboom.net/public/upload/upload-html/1753875032/2023060600004.png)
2. 

  1. When the K230 camera detects an object, the serial port assistant will print out the information transmitted from the K230 to the micro:bit.

- 

category: The identified name
- 

score: The score

As shown in the figure below
![image-20250718191057275](https://www.yahboom.net/public/upload/upload-html/1753875032/image-20250718191057275.png)