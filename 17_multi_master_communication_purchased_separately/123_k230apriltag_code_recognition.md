# 4.k230Apriltag code recognition

# k230Apriltag code recognition

k230Apriltag code recognitionk230 and RDK X5 communication1. Experimental Prerequisites2. Experimental wiring3. Main code explanation4. Experimental Phenomenon

 

## k230 and RDK X5 communication

### 1. Experimental Prerequisites

This tutorial uses the RDK X5 development board, and the corresponding example path is [14.export\RDK-K230\04_k230_apriltag.py].

K230 needs to run the [14.export\CanmvIDE-K230\04.find_apriltag.py] program to start the experiment. It is recommended to download it as an offline program.

 

Things you need:

Windows computer
RDK X5 development board
USB to TTL module
K230 visual module (including TF card with image burned in)
Type-C data cable
Connection cable

 

### 2. Experimental wiring

|  |  |
| --- | --- |
|  |  |
|  |  |
|  |  |
|  |  |

![image-20250430160757147](image-20250430160757147.png)

### 3. Main code explanation

```python
import serial
​
com="/dev/ttyUSB0"
ser = serial.Serial(com, 115200)
​
FUNC_ID = 4
​
def parse_data(data):
    if data[0] == ord('$') and data[len(data)-1] == ord('#'):
        data_list = data[1:len(data)-1].decode('utf-8').split(',')
        data_len = int(data_list[0])
        data_id = int(data_list[1])
        if data_len == len(data) and data_id == FUNC_ID:
            # print(data_list)
            x = int(data_list[2])
            y = int(data_list[3])
            w = int(data_list[4])
            h = int(data_list[5])
            id = int(data_list[6])
            degrees = int(data_list[7])
            return x, y, w, h, id, degrees
        elif (data_len != len(data)):
            print("data len error:", data_len, len(data))
        elif(data_id != FUNC_ID):
            print("func id error:", data_id, FUNC_ID)
    return -1, -1, -1, -1, -1, -1
​
while True:
    if ser.in_waiting:
        data = ser.readline()
        # print("rx:", data)
        x, y, w, h, id, degrees = parse_data(data.rstrip(b'\n'))
        print("apriltag:x:%d, y:%d, w:%d, h:%d, id:%d, degrees:%d" % (x, y, w, h, id, degrees))

```

The above program is for parsing K230 data. Only when it complies with specific protocols can the corresponding data be parsed.

in

- x: is the horizontal coordinate of the upper left corner of the recognized box
- y: is the vertical coordinate of the upper left corner of the recognized box
- w: is the width of the recognized frame
- h: is the length of the recognized frame
- id: is the tag number of apriltag
- degrees: is the rotation angle of apriltag

 

### 4. Experimental Phenomenon

1. After connecting the cables, the k230 visual module runs offline.  After K230 is connected to Canmv IDE, open the corresponding program, click [Save open script to CanMV board (as main.py)] on the toolbar, and then restart K230.

![image-20250429194108060](image-20250429194108060.png)

1. Transfer the program file to the system, open the terminal and enter the corresponding directory, then run the following command to start the program.

```python
python3 04_k230_apriltag.py

```

1. When the K230 camera image recognizes the AprilTag code, the terminal will parse and print out the information transmitted by the K230.

  in

- 

x: is the horizontal coordinate of the upper left corner of the recognized box
- 

y: is the vertical coordinate of the upper left corner of the recognized box
- 

w: is the width of the recognized frame
- 

h: is the length of the recognized frame
- 

id: is the tag number of apriltag
- 

degrees: is the rotation angle of apriltag

As shown in the figure below

![image-20250430114049270](image-20250430114049270.png)