# 04.Desktop Layout Algorithm

# AppManager Desktop Layout Algorithm

AppManager Desktop Layout Algorithm1. Course Objectives2. Core Source Code Analysis2.1 Coordinate Calculation Formula2.2 Page Turning Logic2.3 Touch and Swipe

## 1. Course Objectives

After applications are loaded, how does the system arrange them neatly on the screen? In this lesson, we will analyze the grid layout algorithm in `AppManager` and understand how icon coordinates are calculated.

## 2. Core Source Code Analysis

**File Path**: `src/canmv/port/builtin_py/yahboom/ybMain/main.py`

In the `AppManager.__init__` method, a set of key layout parameters are defined:

```python
class AppManager:
    def __init__(self, ...):
        # ...
        # Icon layout parameters
        self.icon_size = 115      # Icon size (115x115 pixels)
        self.icon_spacing_x = 30  # Horizontal spacing
        self.icon_spacing_y = 40  # Vertical spacing
        self.grid_start_x = 40    # Grid starting x coordinate
        self.grid_start_y = 100   # Grid starting y coordinate (avoid top status bar)
        self.icons_per_row = 4    # Number of icons per row
        self.rows_per_page = 1    # Number of rows per page

```

### 2.1 Coordinate Calculation Formula

Assuming this is the `i`-th application (counting from 0), how are its coordinates `(x, y)` calculated?

The standard grid algorithm is as follows:

1. 

**Calculate row and column numbers**:

```python
row = i // self.icons_per_row  # Which row
col = i % self.icons_per_row   # Which column

```

2. 

**Calculate pixel coordinates**:

```python
x = self.grid_start_x + col * (self.icon_size + self.icon_spacing_x)
y = self.grid_start_y + row * (self.icon_size + self.icon_spacing_y)

```

### 2.2 Page Turning Logic

Here we explain the page turning logic again
The code uses `self.current_page` and `self.page_count`.

```python
self.current_page = 1
self.page_count = 1
self.apps_per_page = self.icons_per_row * self.rows_per_page # How many Apps can fit per page

```

If the number of applications exceeds `apps_per_page`, the system will automatically create new pages. When swiping to turn pages, it's actually the entire container holding icons (Container) that performs horizontal displacement.

### 2.3 Touch and Swipe

Swipe detection variables are also defined in `AppManager`:

```python
# Add variables needed for swipe page turning
self.touch_start_x = 0
self.touch_start_y = 0
self.is_swiping = False
self.min_swipe_distance = 3

```

In other words, `AppManager` is not only responsible for static layout but also takes over global touch events. When it detects that the horizontal swipe distance exceeds the threshold, it will trigger page turning animation instead of clicking icons.