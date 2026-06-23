# 13. RTSP real-time image transmission combined with AIDemo

# RTSP real-time image transmission combined with AIDemo

RTSP real-time image transmission combined with AIDemoEffect DemonstrationSample CodeModification steps1. Preparation1.1 Configure WiFi settings2. Modify _do_rtsp_stream()3. Copy FaceLandMark and related classes4. Modify FaceLandMark and related classesNotes [Must Read]

 

## Effect Demonstration

Note: The WIFI chip on the K230 has limited performance. Please use the image transmission near a WIFI signal hotspot.

*This example is experimental and may not run with high quality in different network environments.

When we run the modified example in this section, the console will have output information similar to the following:

[WIFI] Connecting to network...
[WIFI] 连接网络中 ...
[RTSP] Starting...
[RTSP] 启动中 ...
find sensor gc2093_csi2, type 9, output 1920x1080@60
sensor(0), mode 0, buffer_num 4, buffer_size 0
rtsp server start: rtsp://192.168.2.116:8554/face
[RTSP] Started successfully!
[RTSP] 启动成功！

This address is the RTSP streaming address.

We can use a player that supports RTSP streaming to remotely play the K230 screen. This section takes face key point detection as an example.

You can use VLC Media Player or the rtsp_player we provide. Both software are in our download area [Software Tools]

1. 

It is recommended to use rtsp_player first, which has simple functions and does not require complicated configuration. Just double-click to open it.

![image-20250122111524819](https://www.yahboom.net/public/upload/upload-html/1747309054/15.png)
2. 

VLC Media Player is a versatile and powerful video player, but the settings are relatively cumbersome.

We open VLC Media Player, click "Media" -> "Open Network Stream"

![image-20250122112119731](https://www.yahboom.net/public/upload/upload-html/1747309054/16.png)

Enter the URL address and change the delay to a lower value in "Show more options", about 10~100ms

![image-20250122112322584](https://www.yahboom.net/public/upload/upload-html/1747309054/17.png)

After the modification is completed, click the [Play] button in the lower right corner to remotely play the video transmitted by K230

![image-20250122112517559](https://www.yahboom.net/public/upload/upload-html/1747309054/18.png)

If the playback performance is poor, one way is to ensure the network speed and connection stability, and the other is to try to optimize it in "Preferences".

![image-20250122114030653](https://www.yahboom.net/public/upload/upload-html/1747309054/19.png)

 

## Sample Code

Here is a modified image transmission code based on face detection

Put it in [Source code summary/11.Network/07.rtsp/rtsp_face_detect.py]

Modify the WIFI parameters and run to see the effect

```python
if __name__ == "__main__":
    print("连接网络中 Connecting to network ...")
    Connect_WIFI("ssid", "password")
    print("启动中 Starting ...")

```

 

## Modification steps

### 1. Preparation

In this tutorial, we will introduce how to remotely transmit the images recognized by AIDemo through RTSP.

*This tutorial is somewhat challenging for beginners and requires you to have a certain code foundation and programming skills.*

Let's take face_landmark (face key point detection) as an example.

The required code is:

1. empty_rtsp_demo.py [located in source code/ 11.Network / 07.rtsp / empty_rtsp_demo.py]
2. face_landmark.py [located in source code/07.Face/02.face_landmark.py]

First, we copy a copy of the empty_rtsp_demo.py file and rename it to empty_rtsp_demo_face_landmark.py

#### 1.1 Configure WiFi settings

We scroll down to the bottom of the code and find the if name == "main" part

Modify the parameters of the Connect_WIFI() method to our own WIFI name and password (preferably in pure English)

```python
if __name__ == "__main__":
    print("[WIFI] 连接网络中 Connecting wifi ...")
    isConnected = Connect_WIFI("Your_SSID", "Your_PASSWORD")
    if isConnected:
        print("[WIFI] 连接网络成功 Connect successfully")
    else:
        import sys
        print("[WIFI] 连接网络失败！请检查配置 Error Please check your wifi information")
        time.sleep_ms(10)
        sys.exit()
​
    print("[RTSP] 启动中 .. | Starting ...")
    time.sleep(1)

```

 

### 2. Modify _do_rtsp_stream()

After copying, we open face_landmark.py, find the exce_demo() method, and copy the part in the red box (all the code before try-while)

![image-20250121182813138](https://www.yahboom.net/public/upload/upload-html/1747309054/1.png)

Open the newly created [empty_rtsp_demo_face_landmark.py] file and find the [_do_rtsp_stream()] method

Replace the content in the brown box below with the content in the red box we copied

![image-20250121183246966](https://www.yahboom.net/public/upload/upload-html/1747309054/2.png)

The replaced code is as follows

![image-20250121183410475](https://www.yahboom.net/public/upload/upload-html/1747309054/3.png)

Modify [display_size] to [1280,720], the modified result is as follows

![image-20250121183608955](https://www.yahboom.net/public/upload/upload-html/1747309054/4.png)

The following code also needs to be modified. We change [face_det] to [flm] (the commented-out part in the figure is before the modification) (refer to exce_demo() for modification. This modification is a preliminary modification and will be further modified later)

![image-20250121183840840](https://www.yahboom.net/public/upload/upload-html/1747309054/5.png)

 

At this point, the modification of the [_do_rtsp_stream()] part is completed

 

### 3. Copy FaceLandMark and related classes

In this section, we use three classes to achieve AI visual effects, so we need to copy all three classes.

Because the code is too long, I used folding. We need to copy all the codes of these three classes.

![image-20250121184314272](https://www.yahboom.net/public/upload/upload-html/1747309054/6.png)

After copying, we paste it into the [empty_rtsp_demo_face_landmark.py] file

![image-20250121184422460](https://www.yahboom.net/public/upload/upload-html/1747309054/7.png)

 

Let's go back to the [face_landmark.py] file and find the while loop in exce_demo

Now we need to transplant this part into the RTSP streaming process. For easy viewing, I put this part of the screenshot on the side.

![image-20250121185016078](https://www.yahboom.net/public/upload/upload-html/1747309054/8.png)

 

Then we go back to [empty_rtsp_demo_face_landmark.py] and find the brown box part

![image-20250121185223010](https://www.yahboom.net/public/upload/upload-html/1747309054/9.png)

We modify the part in the brown box according to the writing method in the screenshot. The modified code is as follows:

![image-20250121185645314](https://www.yahboom.net/public/upload/upload-html/1747309054/10.png)

res = flm.run(np_img) changed to det_boxes,landmark_res = flm.run(np_img)

flm.draw_result(rtsp_show_img, res) changed to flm.draw_result(rtsp_show_img,det_boxes,landmark_res)

**Note that pl should be changed to rtsp_show_img**

 

### 4. Modify FaceLandMark and related classes

We find the [draw_result] method in the [FaceLandMark] class

![image-20250121190102715](https://www.yahboom.net/public/upload/upload-html/1747309054/11.png)

1. 

Modify the pl in the parameter to img
2. 

Delete the line pl.osd_img.clear()
3. 

Find the line draw_img.draw_circle(), change it to img.draw_circle(), and delete line 285

![image-20250121190847984](https://www.yahboom.net/public/upload/upload-html/1747309054/12.png)

![image-20250121191019312](https://www.yahboom.net/public/upload/upload-html/1747309054/13.png)

This requires a case-by-case discussion

1. 

If the routine draws very few lines (such as face detection or face recognition), then the image is most likely drawn directly on img [the key feature is the appearance of methods such as img.draw_xxxx()]

In this case, you can change it here
2. 

If the routine draws a lot of lines (such as drawing key points of a face), in addition to the direct draw_Xxxx(), there may also be drawing functions such as [aidemo.xxxx()]. In this case, we need to flexibly modify the code. The idea is to directly obtain the recognized key points, and then manually add a method to draw on the image.

 

1. 

This example draws a complex image, in which the original code of the eye part uses the draw_circle method. We can directly follow step 3 [find the line draw_img.draw_circle() and modify it to img.draw_circle()]. However, the aidemo.polylines() and aidemo.contours() methods are used at other key points. The parameters of these two methods must be the nparray converted from the rgb888 type of image, which does not match the image parameter img we passed in (img is in Yuv420sp format, and RTSP real-time image transmission can only use images in this format), so we need to add a drawing function ourselves. In this example, after obtaining the key points, we use the draw_circle method to manually draw these key points

![image-20250122105102914](https://www.yahboom.net/public/upload/upload-html/1747309054/14.png)

 

## Notes [Must Read]

Q: Why does my K230 CanMV IDE show that [RTSP] is started successfully and there is address information, but the video cannot be connected?

1. If the address is 0.0.0.0, there is probably a problem with the network connection. Please check whether you can connect to WIFI correctly.
2. Please make sure that the computer or mobile phone you want to watch remotely is connected to the same WIFI as K230 (or in the same LAN)
3. After testing, only two or less devices can be connected at the same time. Any more than this number cannot be connected.
4. After eliminating the above situations, if you still cannot connect to RTSP, please disconnect the K230 from the power supply and press the RST reset button. Wait for 10 seconds and then power on again to run the program.

 

Q: Why does the color I draw not match what I set?

A: Because the current img drawing method is not compatible with the image format used for streaming (Yuv420sp), the colors in the RGB format cannot be parsed normally. There is currently no good solution to this problem.

 

Q: Why do I draw multiple rectangles on the image?

A: Please make sure that display_size is set to [1280x720]

 

Q: I experience high latency when watching videos on the mobile version of VLC for Android?

A: This is determined by the player settings. We did not find any relevant settings in this app.