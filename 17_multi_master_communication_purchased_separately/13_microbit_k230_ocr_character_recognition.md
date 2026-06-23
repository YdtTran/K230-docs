# 13.microbit_k230 OCR character recognition

# microbit_k230 OCR character recognition

microbit_k230 OCR character recognitionK230 and microbit communication1. Experimental Prerequisites2. Experimental wiring3. Main code explanation4. Experimental phenomenon

## K230 and microbit communication

### 1. Experimental Prerequisites

This tutorial uses a micro:bit. The corresponding example program path is [14.export\microbit-K230\13.Arduino_k230_ocr_rec].

To begin the experiment, you must run the [14.export\CanmvIDE-K230\13.ocr_rec.py] program on the K230. We recommend downloading the program for offline operation.

 

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

![image-20250430112815670](https://www.yahboom.net/public/upload/upload-html/1753874845/Microbit.png)

### 3. Main code explanation

![image-20250729184320113](https://www.yahboom.net/public/upload/upload-html/1753874845/image-20250729184320113.png)

As can be seen from the code, simply configure the serial port and call the relevant serial port and K230 building blocks to obtain data.

- 

msg: is the OCR character information.

 

If you want to open the source code of this tutorial, please drag the microbit source code corresponding to this tutorial into the makecode online programming webpage of the browser. The online programming website is: [https://makecode.microbit.org/#](https://makecode.microbit.org/#)

### 4. Experimental phenomenon

1. After connecting the cables, the k230 visual module runs offline
After K230 is connected to Canmv IDE, open the corresponding program, click [Save open script to CanMV board (as main.py)] on the toolbar, and then restart K230.

  ![image-20250429194108060](https://www.yahboom.net/public/upload/upload-html/1753874845/image-20250429194108060.png)

1. Find the hex program of this tutorial, right-click the hex program, and upload the hex program of this tutorial to the microbit

![image-20250716170855785](https://www.yahboom.net/public/upload/upload-html/1753874845/image.png) 

1. The serial port assistant is set to the interface shown in the figure
![image-2023060600004](https://www.yahboom.net/public/upload/upload-html/1753874845/2023060600004.png)
2. When the K230 camera recognizes characters, the serial port assistant will print out the information transmitted from K230 to microbit.

- msg: is the OCR character information.

As shown in the figure below
  ![image-20250718122208435](https://www.yahboom.net/public/upload/upload-html/1753874845/image-20250718122208435.png)