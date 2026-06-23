# 2. Use online platforms for training

# Training using the online platform

Training using the online platformIntroduction1. Prepare training data2. Train the model on the training platform3. Use the code and model we downloadedThe following is the latest version of the tutorial on 2025.06.10The following is an old version tutorial, which is only used for reference and backup.4. Effect Optimization

## Introduction

In this section, we will introduce the online cloud platform provided by CanMV for model training. We take the commonly used detection model as an example to let K230 recognize two items, my bracelet and screwdriver

## 1. Prepare training data

We use the routine code in the [2.Basic Tutorial - 19.Camera] section to take pictures. For specific operations, please refer to the tutorial in the [2.Basic Tutorial - 19.Camera] section

## 2. Train the model on the training platform

Online training platform address: [https://www.kendryte.com/en/training/dataset](https://www.kendryte.com/en/training/dataset)

Click the Register button

![image-20250225155832068](https://www.yahboom.net/public/upload/upload-html/1751370018/2.png)

Fill in your personal information and click Register

![image-20250225160159653](https://www.yahboom.net/public/upload/upload-html/1751370018/3.png)

After successful registration, you will be automatically logged in. We click "Create training set"

![image-20250225160303687](https://www.yahboom.net/public/upload/upload-html/1751370018/4.png)

![image-20250225175754363](https://www.yahboom.net/public/upload/upload-html/1751370018/5.png)

Click Edit

![image-20250225175843607](https://www.yahboom.net/public/upload/upload-html/1751370018/6.png)

Click to upload image

![image-20250225180913788](https://www.yahboom.net/public/upload/upload-html/1751370018/7.png)

After uploading the picture, we click the Annotate button

![image-20250225181048572](https://www.yahboom.net/public/upload/upload-html/1751370018/8.png)

1. We first select the label box, enter a label name, and then press Enter.
2. Then we can use the mouse to mark the object to be detected on the picture.
3. ![image-20250513191203281](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250513191203281.png)

![image-20250225181440607](https://www.yahboom.net/public/upload/upload-html/1751370018/9.png)

![image-20250225181918876](https://www.yahboom.net/public/upload/upload-html/1751370018/10.png)

After all the markings are completed, we click the return button

![image-20250225182125960](https://www.yahboom.net/public/upload/upload-html/1751370018/11.png)

We click the training button

![image-20250225182204839](https://www.yahboom.net/public/upload/upload-html/1751370018/12.png)

Fill in the content as shown in the picture and click OK

![image-20250225182316446](https://www.yahboom.net/public/upload/upload-html/1751370018/13.png)

Waiting for training (need to queue if there are many people)

![image-20250225182341826](https://www.yahboom.net/public/upload/upload-html/1751370018/14.png)

The training takes a long time and it is uncertain how long it will take. Closing the webpage or turning off the computer will not affect the training. You can do other things first.

![image-20250225192643341](https://www.yahboom.net/public/upload/upload-html/1751370018/15.png)

After waiting for the training to end, the interface is as follows

![image-20250225202216056](https://www.yahboom.net/public/upload/upload-html/1751370018/16.png)

We return to the place before starting training, find the training record, and click Download

![image-20250225202313192](https://www.yahboom.net/public/upload/upload-html/1751370018/17.png)

## 3. Use the code and model we downloaded

### The following is the latest version of the tutorial on 2025.06.10

Note: If you are using firmware 1.3.3 or earlier, please update to the latest version. The latest version of the firmware can be downloaded from our official website tutorial page

The downloaded compressed package is as follows

![image-20250624164948621](https://www.yahboom.net/public/upload/upload-html/1751370018/n1.png)

The [det_results] directory contains the results of our test verification, we can open it and take a look.

Here are the results of the verification test. If the object in the picture is correctly framed, then basically there is no big problem with the trained model

![image-20250624165057206](https://www.yahboom.net/public/upload/upload-html/1751370018/n2.png)

Then we open the [mp_deployment_source] folder, which contains our model file and configuration file

![image-20250624165212053](https://www.yahboom.net/public/upload/upload-html/1751370018/n3.png)

Then we return to the sdcard directory of CanMV and create a new folder named [mp_deployment_source]

Put this in the compressed package Unzip the two files to this folder (first unzip to your computer, then copy to the mp_deployment_source folder)

![image-20250624172112685](https://www.yahboom.net/public/upload/upload-html/1751370018/n4.png)

Then open the example source code summary [13.training/deploy_det_video.py]

Change display_mode to "lcd"

![image-20250624174113980](https://www.yahboom.net/public/upload/upload-html/1751370018/n5.png)

After the modification, click the run button in the lower left corner of the IDE to see the effect of the case running.

Note: After testing, the new version of the tutorial may drop frames after deployment. At this time, you can try to use the old version of the tutorial to deploy.

The det_video.py file required by the old version of the tutorial has been placed in [Source Code Summary / 13.training / det_video.py]

### The following is an old version tutorial, which is only used for reference and backup.

The downloaded file is a compressed file with the following contents

![image-20250225202423490](https://www.yahboom.net/public/upload/upload-html/1751370018/19.png)

We can first look at the det_results folder, which contains the results of the verification test. If the objects in the picture are correctly framed, then basically there is no big problem with the trained model.

Next, we unzip mp_deployment_source and create a mp_deployment_source folder in the /sdcard/ directory of K230, and put the unzipped contents into it.

(Mainly put the model file ending with .kmodel and the configuration file ending with .json in it. The remaining two py files are used for running and can be left out)

![image-20250225215951013](https://www.yahboom.net/public/upload/upload-html/1751370018/20.png)

Then we open CanMV IDE, copy the code of det_video.py and run it, and we can see that K230 can detect the objects we just marked.

Here we need to make some modifications to det_video.py:

The original code is as follows:

```python
display_mode="hdmi"
if display_mode=="lcd":
DISPLAY_WIDTH = ALIGN_UP(800, 16)
DISPLAY_HEIGHT = 480
else:
DISPLAY_WIDTH = ALIGN_UP(1920, 16)
DISPLAY_HEIGHT = 1080
​
OUT_RGB888P_WIDTH = ALIGN_UP(1280, 16)
OUT_RGB888P_HEIGH = 720

```

Modified to:

```python
display_mode="lcd"
if display_mode=="lcd":
DISPLAY_WIDTH = ALIGN_UP(640, 16)
DISPLAY_HEIGHT = 480
else:
DISPLAY_WIDTH = ALIGN_UP(1920, 16)
DISPLAY_HEIGHT = 1080
​
OUT_RGB888P_WIDTH = ALIGN_UP(1280, 16)
OUT_RGB888P_HEIGH = 720

```

 

![image-20250225220609877](https://www.yahboom.net/public/upload/upload-html/1751370018/21.png)

 

## 4. Effect Optimization

At this time, we find that there are too many overlapping frames, so we can try to reduce the nms threshold in deploy_config, so that there will be fewer duplicate frames.

![image-20250225220952375](https://www.yahboom.net/public/upload/upload-html/1751370018/23.png)

![image-20250225220832690](https://www.yahboom.net/public/upload/upload-html/1751370018/22.png)