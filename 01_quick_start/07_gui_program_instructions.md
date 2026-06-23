# 6. GUI Program Instructions

# GUI Program Instructions

GUI Program InstructionsIntroductionVersion NotesBasic useFirst power onset upWireless networksoundMy DevicesshowlanguageAI ApplicationscameraGalleryGraphics DetectionHardware interface testAdvanced UseModify the lock screen imageLLM Large Language ModelCustomize APP name/icon/functionFAQ

 

## Introduction

To help you quickly experience the functions of YAHBOOM K230, the screen version of the image has a built-in GUI program that starts automatically when the computer is turned on. The GUI program has some commonly used routines built in, so you can easily select AI functions to experience. Due to the limitations of K230's graphics rendering capabilities and the complexity of the GUI program, please read this document carefully to better understand and use the GUI program.

 

## Version Notes

The GUI program version corresponding to the current document is 【YAHBOOM K230 GUI 1.0】

You can find the system version corresponding to the current image in 【Settings/My Device/OS Version】 of the GUI program

 

## Basic use

### First power on

After getting our K230, we can directly power it through the type-c interface.

If the other end is to be connected to the computer USB port, please use the USB3.0 port (usually the inside of the interface is blue), otherwise the power supply may not reach the 5V required by K230

It takes about **[5~10 seconds]** for K230 to initialize for the first time , which is normal

After the initialization is successful, the RGB light on the top of K230 will turn blue and the screen will display the loading information.

The first time you use it, you need to configure the language information. After configuration, it will automatically restart. Just wait.

![image-20250425142147344](https://www.yahboom.net/public/upload/upload-html/1747646647/1.png)

![image-20250425142347611](https://www.yahboom.net/public/upload/upload-html/1747646647/2.png)

Swipe left or right in the blank area (the area pointed by the arrow in the picture) to turn the page.

Click the corresponding icon to enter the corresponding program function.

### set up

Version 1.0 provides five categories: [Wireless Network], [Sound], [My Device], [Display] and [Language & Language]. We will explain them one by one.

#### Wireless network

If you are not using a large model, it is recommended not to turn on the WIFI network.

![image-20250425142654372](https://www.yahboom.net/public/upload/upload-html/1747646647/3.png)

In this interface, we can choose to turn on/off the WIFI network

![image-20250425142850360](https://www.yahboom.net/public/upload/upload-html/1747646647/4.png)

![image-20250425143048407](https://www.yahboom.net/public/upload/upload-html/1747646647/5.png)

##### FAQ Description:

If you cannot connect to WIFI & the system freezes, please check:

1. Is the WIFI password entered correctly?
2. Is the WIFI 2.4Ghz?
3. The WIFI chip may occasionally experience connection anomalies. Please try to **power off** the K230 and wait for **15 seconds** before trying to connect again.

#### sound

Drag the volume adjustment progress bar to change the system volume

![image-20250425145438628](https://www.yahboom.net/public/upload/upload-html/1747646647/6.png)

Note 1: The current version of the GUI program does not have any part that needs to play sound.

Note 2: In the current version, the slider has a high probability of automatically jumping to 0 when dragging. You can "click" the position of the progress bar instead of "dragging", which will reduce the possibility of automatically jumping to 0.

#### My Devices

In this interface, you can see some basic information of the current K230, which will not be described in detail here.

![image-20250425145755271](https://www.yahboom.net/public/upload/upload-html/1747646647/7.png)

#### show

Adjust brightness [not supported in current version] and resolution

Note: The resolution here refers to the capture resolution of camera channel 3, which generally does not need to be modified.

![image-20250425145923370](https://www.yahboom.net/public/upload/upload-html/1747646647/8.png)

#### language

The current version supports two options: Chinese (Chinese) and English (English).

The language switching function will take effect after restarting

![image-20250425150115219](https://www.yahboom.net/public/upload/upload-html/1747646647/9.png)

 

### AI Applications

The usage methods of AI applications are very similar. Here we take AI face recognition application as an example

![image-20250425150409566](https://www.yahboom.net/public/upload/upload-html/1747646647/10.png)

① is the list on the left, which lists all the sub-functions included in the AI Face App

② is a rough effect diagram

③ is example program introduction text

④ is the case [Boot! ] button. Click this button to enter the corresponding function

### camera

Camera applications are often used to take photos as data for model training

The location where the photos are saved will be displayed on the start screen

For example, in the case shown in the figure, after entering the photo taking process, the picture will be saved in the directory [/data/photo/8509972215/]

![image-20250425160702981](https://www.yahboom.net/public/upload/upload-html/1747646647/12.png)

 

### Gallery

The photo album app will display all images with a resolution of 640*480 and a suffix of [png] in the [data] partition.

Pictures that do not meet the above description will not be displayed in the album application

### Graphics Detection

Contains two functions: [Rectangle Detection] and [Line Segment Detection]

It should be noted that running graphics detection requires changing the camera resolution, which is a more troublesome step.

Therefore, **it is recommended that you use the separate routines in the tutorial to experiment with graphics detection related functions.**

![image-20250425160933271](https://www.yahboom.net/public/upload/upload-html/1747646647/13.png)

### Hardware interface test

Mainly includes [Buzzer Test], [PWM Test] and [RGB Tight Test]

![image-20250425161147160](https://www.yahboom.net/public/upload/upload-html/1747646647/14.png)

Note 1: If the RGB light does not change after dragging the slider bar, please try to turn off and then turn on the RGB light option again (① in the picture)

Note 2: The blue slider bar at ② is not sensitive to touch, which is a common bug and will be gradually resolved in subsequent versions.

 

## Advanced Use

The use of advanced parts requires a certain foundation. If some configurations are modified and cause abnormalities, please re-burn the factory image

### Modify the lock screen image

Modify the /sdcard/resources/wallpaper.png file

![image-20250425161749014](https://www.yahboom.net/public/upload/upload-html/1747646647/15.png)

Note: Only 640x480 png images are supported and cannot have a transparent background

Note 2: You can also modify the /sdcard/configs/sys_config.json configuration file

### LLM Large Language Model

We provide a large language model interface that supports API calls from iFlytek Spark and the aggregation platform OpenRouter

Before this, you need to manually apply for and configure the API Key for the large model.

Please refer to these two tutorials for the specific methods of applying for API Key and using the LLM interface.

iFlytek Spark:

Note: iFlytek Spark is only available to users in China

OpenRouter: [11. Network Basics / 14. Calling OpenRouter Large Model Aggregation Service]

The process of calling a large model is relatively complicated. Please make sure to study these two lessons first before making further attempts.

If you want to experience the functions of the large model, it is recommended to read the above two courses directly and use the corresponding example source code to experience

It is difficult to call large model operations in GUI programs

We assume that we have applied for the API Key of iFlytek Spark: "key-123465789"

We found the configuration file /sdcard/configs/sys_config.json

Then copy it to a directory on your computer.

The files in the k230 cannot be opened and modified directly, so you must first copy a copy to the local computer, and then modify it and put it back to the corresponding path of the SD card to overwrite the original file.

The default content is as follows:

![image-20250425163259986](https://www.yahboom.net/public/upload/upload-html/1747646647/16.png)

Format the file

If you are using the VSCode editor, you can use the Alt+Shift+F shortcut to format

You can also search for [JSON file online formatting tool] on the Internet.

No further description is given here

Then find AI --> LLM

![image-20250425163753457](https://www.yahboom.net/public/upload/upload-html/1747646647/17.png)

**Change the value of api_key** to **the "key-123465789"** you just obtained.

Change the value of **api_type to** **"spark"**

If you want to use openrouter, just change api_type to "openrouter"

Change the value of api_model to the model you want to use. Here I take the free model lite of iFlytek Spark as an example.

After modifying, let’s save it.

Then overwrite the modified sys_config.json file with the /sdcard/resources/sys_config.json file

Then we restart K230, enter the GUI program, connect to WIFI, and start communicating with the large model.

```python
Please note that the API_KEY in the example cannot be used directly. Please apply for a correct API_KEY yourself.

```

![image-20250425165040360](https://www.yahboom.net/public/upload/upload-html/1747646647/18.png)

### Customize APP name/icon/function

All apps in the GUI program are open source, and the code is located in the /sdcard/apps/ directory

The code is developed based on LVGL 8.3

If you have a certain coding foundation, you can try to deeply customize or optimize these apps.

This part of the custom content has too many functions, and we are temporarily unable to provide in-depth and detailed technical support services

![image-20250425170549243](https://www.yahboom.net/public/upload/upload-html/1747646647/19.png)

## FAQ

1. 

System stuck

A: Please try restarting. If the freezing problem is easy to reproduce, please report the situation to the technical support group. We will release an update patch in the subsequent version after statistics.
2. 

K230 does not respond after power on, but can connect to CanMV IDE normally

A: Please connect K230 to the computer, open the /sdcard/ directory, and check if there is a file named bad_main.py. If there is, please rename it to main.py, then disconnect. Reconnect after five seconds.
3. 

How to turn off the automatic startup of GUI programs?

  1. Temporary shutdown: Keep pressing the Key key before powering on until successfully connected to the CanMV IDE
  2. Permanently shut down: delete the main.py file in the /sdcard/ directory

4. 

How to restore the original state?

A: You can re-burn the image file (firmware)