# 17.microbit_k230 license plate recognition

# microbit_k230 license plate recognition

microbit_k230 license plate recognitionK230 and microbit communication1. Experimental Prerequisites2. Experimental wiring3. Main code explanation4. Experimental phenomenon

## K230 and microbit communication

### 1. Experimental Prerequisites

This tutorial uses a Microbit, and the corresponding example program path is [14.export\microbit-K230\17.Microbit_k230_licence_det_rec].

To begin the experiment, you must run the [14.export\CanmvIDE-K230\17.licence_rec.py] program on the K230. It is recommended that you download the program for offline operation.

 

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

![image-20250430112815670](Microbit.png)

### 3. Main code explanation

![image-20250730120221431](image-20250730120221431.png)

From the code, we can simply configure the serial port and call the relevant serial port and K230 building blocks to obtain data.

- licence_rec: msg is the license plate character information.

If you want to open the source code of this tutorial, please drag the microbit source code corresponding to this tutorial into the makecode online programming webpage of the browser. The online programming website is: [https://makecode.microbit.org/#](https://makecode.microbit.org/#)

### 4. Experimental phenomenon

1. After connecting the cables, the k230 visual module runs offline
After K230 is connected to Canmv IDE, open the corresponding program, click [Save open script to CanMV board (as main.py)] on the toolbar, and then restart K230.

  ![image-20250429194108060](image-20250429194108060.png)

1. Find the hex program of this tutorial, right-click the hex program, and upload the hex program of this tutorial to the microbit

![image-20250716174422578](image.png) 

1. The serial port assistant is set to the interface shown in the figure
![image-2023060600004](2023060600004.png)
2. When the K230 camera recognizes characters, the serial port assistant will print out the information transmitted from K230 to microbit.

- licence_rec: msg is the license plate character information.

As shown in the figure below
  ![image-20250718192046658](image-20250718192046658.png)

 

Note: If you find that Chinese characters are displayed in garbled form, you need to change the character set encoding of the serial port assistant to 'UTF-8' encoding.

![image-20250430122343249](image-20250430122343249.png)