# 17.arduino_k230 license plate recognition

# arduino_k230 license plate recognition

arduino_k230 license plate recognitionk230 and arduino communication1. Experimental Prerequisites2. Experimental wiring3. Main code explanation4. Experimental Phenomenon

## k230 and arduino communication

### 1. Experimental Prerequisites

This tutorial uses Arduino, and the corresponding routine path is [14.export\arduino-K230\17.Arduino_k230_licence_det_rec].

K230 needs to run the [14.export\CanmvIDE-K230\17.licence_rec.py] program to start the experiment. It is recommended to download it as an offline program.

 

Items needed:

Windows computer, Arduino, USB to TTL module, K230 visual module (including TF card with image burned in), type-C data cable, connecting cable (Dupont cable)

 

### 2. Experimental wiring

|  |  |
| --- | --- |
|  |  |
|  |  |

|  |  |
| --- | --- |
|  |  |
|  |  |

![image-20250430112815670](https://www.yahboom.net/public/upload/upload-html/1753872299/arduin.png)

### 3. Main code explanation

```python
void Pto_Data_Parse(uint8_t *data_buf, uint8_t num)
{
    uint8_t pto_head = data_buf[0];
    uint8_t pto_tail = data_buf[num-1];
    if (!(pto_head == PTO_HEAD && pto_tail == PTO_TAIL))
    {
          Serial.print("pto error:pto_head=0x");
    Serial.print(pto_head, HEX);
    Serial.print(" , pto_tail=0x");
    Serial.println(pto_tail, HEX);
        return;
    }
    uint8_t data_index = 1;
    uint8_t field_index[PTO_BUF_LEN_MAX] = {0};
    int i = 0;
    int values[PTO_BUF_LEN_MAX] = {0};
    char msg[PTO_BUF_LEN_MAX] = {0};
    for (i = 1; i < num-1; i++)
    {
        if (data_buf[i] == ',')
        {
            data_buf[i] = 0;
            field_index[data_index] = i;
            data_index++;
        }
    }
    
    for (i = 0; i < data_index; i++)
    {
        if (i == 2)
        {
            memcpy(msg, (char*)data_buf+field_index[i]+1, values[0]-field_index[i]-2);
        }
        else
        {
            values[i] = Pto_Char_To_Int((char*)data_buf+field_index[i]+1);
        }
    }
    
    uint8_t pto_len = values[0];
    
    if (pto_len != num)
    {
        Serial.print("pto_len error:");
    Serial.print(pto_len);
    Serial.print(" , data_len:");
    Serial.println(num);
        return;
    }
    uint8_t pto_id = values[1];
    if (pto_id != PTO_FUNC_ID)
    {
        Serial.print("pto_id error:");
    Serial.print(pto_id);
    Serial.print(" , func_id:");
    Serial.println(PTO_FUNC_ID);
        return;
    }
​
    Serial.print("licence_rec:'");
    Serial.print(msg);
    Serial.println("'");
    
}

```

The above function is used to parse K230 data. Only when it complies with specific protocols can the corresponding data be parsed.

- licence_rec: msg is the license plate character information.

 

### 4. Experimental Phenomenon

1. After connecting the cables, the k230 visual module runs offline
After K230 is connected to Canmv IDE, open the corresponding program, click [Save open script to CanMV board (as main.py)] on the toolbar, and then restart K230.

  ![image-20250429194108060](https://www.yahboom.net/public/upload/upload-html/1753872299/image-20250429194108060.png)

1. Arduino upload routine code (**Note that if the upload fails, disconnect the RXD connection on the Arduino connected to the k230 first, and then plug it back after the upload is successful**)

![image-20250716174422578](https://www.yahboom.net/public/upload/upload-html/1753872299/image-20250716174422578.png) 

1. The serial port assistant is set to the interface shown in the figure
![image-2023060600004](https://www.yahboom.net/public/upload/upload-html/1753872299/2023060600004.png)
2. When the K230 camera recognizes characters, the serial port assistant will print out the information transmitted from K230 to Arduino.

- licence_rec: msg is the license plate character information.

As shown in the figure below
  ![image-20250430122141460](https://www.yahboom.net/public/upload/upload-html/1753872299/image-20250430122141460.png)

 

Note: If you find that Chinese characters are displayed in garbled form, you need to change the character set encoding of the serial port assistant to 'UTF-8' encoding.

![image-20250430122343249](https://www.yahboom.net/public/upload/upload-html/1753872299/image-20250430122343249.png)