# 6.I2C communication

# I2C Communication

I2C CommunicationIntroductionwiringDriving OLEDExpanded contentSSD1306UART and IIC

 

## Introduction

In this tutorial, we will learn how to use the I2C interface of K230 to communicate

We will use K230's IIC1 to light up a 128*32 OLED screen as an example of IIC usage.

![image-20250401162400298](oled.png)

What is IIC (I2C, I²C)?

Like UART, which we learned in the previous section, IIC (I²C) is also a serial communication protocol. At the end of this tutorial, we will briefly understand the difference between these two communication protocols.

 

## wiring

We wire as shown in the figure:

![image-20250401162812664](1.png)

The actual pictures are as follows:

![image-20250401162303852](2.png)

 

## Driving OLED

Copy the following code into CanMV IDE and run

```python
# 导入 machine 模块中的 I2C 和 FPIOA 类
# (Import the I2C and FPIOA classes from the machine module)
from machine import I2C
from machine import FPIOA
​
# 导入 ssd1306 模块中的 SSD1306_I2C 类
# (Import the SSD1306_I2C class from the ssd1306 module)
from ybUtils.ssd1306 import SSD1306_I2C
​
# 导入时间模块
# (Import the time module)
import time
​
# 实例化 FPIOA 对象
# (Create an instance of the FPIOA object)
fpioa = FPIOA()
​
# 创建 I2C 实例，使用 I2C 通道 1
# (Create an I2C instance, using I2C channel 1)
i2c = I2C(1)
​
# 配置引脚功能:
# - 将 GPIO 引脚 34 映射到 I2C1_SCL 功能
# - 将 GPIO 引脚 35 映射到 I2C1_SDA 功能
# (Configure pin functions:
# - Map GPIO pin 34 to I2C1_SCL function
# - Map GPIO pin 35 to I2C1_SDA function)
fpioa.set_function(34, FPIOA.IIC1_SCL, oe=1, ie=1, pu=1, st=1, ds=15)
fpioa.set_function(35, FPIOA.IIC1_SDA, oe=1, ie=1, pu=1, st=1, ds=15)
​
# 创建 SSD1306 OLED 显示器实例
# (Create an SSD1306 OLED display instance)
# 设置 OLED 显示器的分辨率为 128x32
# (Set the OLED display resolution to 128x32)
oled = SSD1306_I2C(128, 32, i2c)
​
# 清除 OLED 显示器的内容
# (Clear the content of the OLED display)
oled.fill(0)
​
# 在 OLED 显示器上显示文字 "Hello Yahboom"，在坐标 (0, 10) 处
# (Display the text "Hello Yahboom" on the OLED display at coordinates (0, 10))
oled.text('Hello Yahboom', 0, 10)
​
# 遍历 OLED 显示器的所有像素
# (Iterate through all the pixels of the OLED display)
for x in range(128):
    for y in range(32):
        # 获取指定像素的值
        # (Get the value of the specified pixel)
        a = oled.pixel(x, y)
​
        # 如果像素值为 1（亮起），则打印坐标
        # (If the pixel value is 1 (lit up), print the coordinates)
        if a == 1:
            print(x, y)
​
# 更新 OLED 显示器的内容
# (Update the content of the OLED display)
oled.show()
​

```

You can see the effect shown in the picture on the OLED screen.

![image-20250401164242873](3.png)

 

The flowchart of code execution is as follows:

![flow](flow.jpeg)

 

## Expanded content

### SSD1306

SSD1306 is a monochrome OLED display controller chip, which is widely used in small display modules.

Driving SSD1306 to display Chinese requires additional processing, and the SSD1306 driver library in the K230 firmware does not support it.

### UART and IIC

IIC (I²C) is a serial communications bus developed by Philips for connecting low-speed peripherals to microcontrollers.

It only requires two lines: serial data line (SDA) and serial clock line (SCL), and can support multiple master devices and multiple slave devices.

The main differences between IIC and UART:

- IIC uses two wires (SDA and SCL) while UART uses two wires (TX and RX)
- IIC supports multi-device bus, UART is usually point-to-point communication
- IIC has master and slave devices, and the devices at both ends of UART have equal status
- IIC has an address addressing mechanism, but UART does not
- IIC is synchronized by clock, UART uses fixed baud rate

 

**How to choose to use IIC or UART** ?

Scenarios for using UART:

- Need simple point-to-point communication
- Long communication distance (up to tens of meters)
- Full-duplex communication is required (sending and receiving data at the same time)
- Does not require many connected devices
- The communication speed requirement is high but not critical (usually within 115200bps)
- For example: communicate with PC, debug output, connect GPS module, Bluetooth module, etc.

Scenarios for using IIC:

- Need to connect multiple devices on a single board (multiple masters and multiple slaves)
- PCB space is limited and IO ports need to be saved
- Short communication distance (usually within a board or between adjacent boards)
- Connect low-speed peripherals such as sensors, EEPROM, real-time clock, etc.
- The communication speed requirement is not high (100kbps for standard mode, 400kbps for fast mode)
- For example: connecting temperature and humidity sensors, accelerometers, OLED displays, etc.