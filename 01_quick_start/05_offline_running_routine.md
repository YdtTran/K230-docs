# 4. Offline running routine

## Offline operation

Through the method mentioned above, we successfully let K230 run a face detection code in an online state (connected to CanMV IDE). At this time, the code is not saved on K230.

In actual scenarios, we often need to save the code offline in K230, and hope that K230 can automatically run the corresponding code after power on.

At this time, we only need to click 【Save open script to CanMV board (as main.py)】 in the toolbar in CanMV IDE

![image-20250401095850006](https://www.yahboom.net/public/upload/upload-html/1747302612/9.png)

Notes

1. Please click this button when the code stops running, otherwise the save may fail
2. If you want to delete the automatically running program, just delete the main.py file in the /sdcard/ directory of K230