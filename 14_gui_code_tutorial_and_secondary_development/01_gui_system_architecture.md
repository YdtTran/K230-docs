# 01.GUI System Architecture

# GUI System Architecture

GUI System Architecture1. Course Objectives2. Architecture Diagram3. Core Source Code Analysis3.1 Safe Boot Mechanism (Anti-Brick Logic)3.2 Starting the Core Engine

## 1. Course Objectives

In this lesson, we will analyze the overall architecture of the Yahboom K230 GUI system

## 2. Architecture DiagramYesNoPower OnExecute ybsdcard/main.pyKey Press Detected?Enter Safe ModeProvide REPL command line only, do not run GUIImport ybMain.mainExecute start methodInitialize display/touch/networkStart AppManager

## 3. Core Source Code Analysis

**File Path**: `src/ybsdcard/main.py`

This file is the **entry point** of the entire GUI system. When the device boots, the MicroPython firmware will automatically find and run `main.py`.

### 3.1 Safe Boot Mechanism (Anti-Brick Logic)

If you want to temporarily disable the GUI auto-start, or if there's a serious bug in `main.py` that causes the device to crash or freeze on boot, making it impossible to connect to the IDE for repair, you can skip the auto-start by pressing and holding the Key button for 3 seconds before powering on (press before power on --> power on --> release after 3 seconds).

K230's GUI system is designed with a safety backdoor**:

```python
import time
from ybUtils.YbKey import YbKey
​
# Initialize the button
key = YbKey()
abort_main = 0
​
# Check button state
if key.is_pressed():
    time.sleep_ms(10) # Debounce
    if key.is_pressed():
        abort_main = 1 # If button is pressed, mark as abort startup

```

**Code Analysis**:

1. **`YbKey()`**: The system initializes a button object.
2. **`key.is_pressed()`**: Detects whether the user has pressed the function key at the moment of startup.
3. **`abort_main = 1`**: If a press is detected, the variable is set to 1, meaning "don't start GUI, return control to the user".

### 3.2 Starting the Core Engine

If the user has not pressed the function key, the system will continue to load the GUI core:

```python
if not abort_main:
    from ybMain.main import *
    start()

```

**Code Analysis**:

1. **`if not abort_main`**: Only executes after the safety check passes.
2. **`from ybMain.main import *`**: Imports the core module `ybMain`. This is like when the Linux kernel finishes loading and starts `systemd` or the graphical interface.
3. **`start()`**: This is the startup function of the core engine. Once executed, the screen will light up and enter the graphical interface.