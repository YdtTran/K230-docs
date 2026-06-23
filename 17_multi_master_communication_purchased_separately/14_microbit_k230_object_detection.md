# 14.microbit_k230 object detection

# microbit_k230 object detection

microbit_k230 object detectionK230 and microbit communication1. Experimental Prerequisites2. Experimental wiring3. Main code explanation4. Experimental phenomenon

## K230 and microbit communication

### 1. Experimental Prerequisites

This tutorial uses a micro:bit. The corresponding example program path is [14.export\microbit-K230\14.Microbit_k230_object_detect].

To begin the experiment, you must run the [14.export\CanmvIDE-K230\14.object_detect_yolov8n.py] program on the K230. We recommend downloading it as an offline program.

 

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

![image-20250430112815670](https://www.yahboom.net/public/upload/upload-html/1753874883/Microbit.png)

### 3. Main code explanation

![image-20250729191321790](https://www.yahboom.net/public/upload/upload-html/1753874883/image-20250729191321790.png)

As can be seen from the code, simply configure the serial port and call the relevant serial port and K230 building blocks to obtain data.

- x: The horizontal coordinate of the top left corner of the recognized box
- y: The vertical coordinate of the top left corner of the recognized box
- w: The width of the recognized box
- h: The height of the recognized box
- msg: The object type

 

### 4. Experimental phenomenon

1. After connecting the cables, the K230 vision module runs offline.
After connecting the K230 to the CanMV IDE, open the program, click [Save open script to CanMV board (as main.py)] on the toolbar, and then restart the K230.

  ![image-20250429194108060](https://www.yahboom.net/public/upload/upload-html/1753874883/image-20250429194108060.png)

1. Find the hex program of this tutorial, right-click the hex program, and upload the hex program of this tutorial to the microbit![image-20250716172101714](https://www.yahboom.net/public/upload/upload-html/1753874883/image.png) 
2. The serial port assistant is set to the interface shown in the figure
![image-2023060600004](https://www.yahboom.net/public/upload/upload-html/1753874883/2023060600004.png)
3. When the K230 camera detects an object, the serial port assistant will print out the information transmitted from the K230 to the micro:bit.

- x: The horizontal coordinate of the top left corner of the recognized box
- y: The vertical coordinate of the top left corner of the recognized box
- w: The width of the recognized box
- h: The height of the recognized box
- msg: The object type

As shown in the figure below
  ![image-20250718183707857](https://www.yahboom.net/public/upload/upload-html/1753874883/image-20250718183707857.png)