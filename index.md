# K230 Vision Module - Index tra cứu nhanh

File này gom tắt nội dung tài liệu theo từng section để truy vấn nhanh. Mỗi mục gồm tóm tắt, từ khóa và link tới bài gốc.

Phạm vi đã index: toàn bộ chương 01-18.

## 01. Quick Start

Tóm tắt chương: thiết lập ban đầu cho module K230, gồm cấp nguồn, ghi firmware, cài môi trường CanMV, chạy/debug routine, chạy offline, nhập môn MicroPython, dùng GUI và lắp phụ kiện cơ khí.

Từ khóa chung: K230, Quick Start, power, Type-C, USB3.0, 5V, CanMV IDE, firmware, TF card, SD card, burning tool, driver, Zadig, offline run, boot.py, main.py, MicroPython, GUI, bracket, PTZ.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [0.Get start](01.%201.%20Quick%20Start/01_0.Get%20start.md) | Yêu cầu cấp nguồn cho K230: dùng Type-C hoặc cổng giao tiếp, điện áp 5V; bản có màn hình chạy AI khoảng 0.8A, bản không màn hình khoảng 0.6A; khuyến nghị USB3.0 hoặc adapter 5V1A/2A/3A. | nguồn, 5V, Type-C, USB3.0, dòng điện, deluxe, standard |
| [1. K230 firmware download and burning](01.%201.%20Quick%20Start/02_1.%20K230%20firmware%20download%20and%20burning.md) | Hướng dẫn tải firmware CanMV K230 Yahboom, chuẩn bị TF card >4GB, cài driver K230 USB Boot bằng Zadig, mở K230BurningTool, chọn image và target SD Card rồi burn firmware. Sau khi burn, kiểm tra OpenMV Cam USB COM Port trong Device Manager. | firmware, CanMV_K230, burn, TF card, Zadig, K230BurningTool, USB Boot, OpenMV Cam COM |
| [2. Install the programming environment](01.%201.%20Quick%20Start/03_2.%20Install%20the%20programming%20environment.md) | Cài CanMV IDE trên Windows, kết nối K230 qua USB, nhận cổng COM và chuẩn bị môi trường lập trình/chạy code MicroPython. | CanMV IDE, install, Windows, COM port, USB, programming environment |
| [3. Debug and run routines](01.%201.%20Quick%20Start/04_3.%20Debug%20and%20run%20routines.md) | Cách mở routine mẫu trong CanMV IDE, kết nối thiết bị, chạy thử, xem frame buffer/serial terminal và dừng chương trình khi debug. | debug, run routine, sample code, serial terminal, frame buffer, CanMV |
| [4. Offline running routine](01.%201.%20Quick%20Start/05_4.%20Offline%20running%20routine.md) | Chạy chương trình không cần IDE bằng cách lưu code vào thiết bị/TF card theo cơ chế tự chạy khi khởi động. Hữu ích sau khi đã debug online xong. | offline, auto run, save to board, boot, main.py, TF card |
| [5. Micropython Quick Start](01.%201.%20Quick%20Start/06_5.%20Micropython%20Quick%20Start.md) | Nhập môn MicroPython/Python 3: kiểu dữ liệu, toán tử, chuỗi, list/tuple/dict/set, điều khiển luồng, vòng lặp, exception, iterator, function, module, class, kế thừa; cuối bài dẫn tới API Manual CanMV K230. | MicroPython, Python 3, list, dict, set, tuple, function, module, class, exception, iterator, API Manual |
| [6. GUI Program Instructions](01.%201.%20Quick%20Start/07_6.%20GUI%20Program%20Instructions.md) | Hướng dẫn sử dụng chương trình GUI đi kèm K230: thao tác chọn/chạy ứng dụng, giao diện, điều khiển chương trình và các lưu ý khi dùng bản có màn hình. | GUI, app launcher, screen, menu, application, run program |
| [7.K230 module bracket installation tutorial](01.%201.%20Quick%20Start/08_7.K230%20module%20bracket%20installation%20tutorial.md) | Hướng dẫn lắp giá đỡ/module bracket cho K230, phục vụ cố định camera/module khi thử nghiệm. | bracket, mount, installation, holder, hardware |
| [8.K230 module 2DOF PTZ installation tutorial](01.%201.%20Quick%20Start/09_8.K230%20module%202DOF%20PTZ%20installation%20tutorial.md) | Hướng dẫn lắp cụm PTZ 2 bậc tự do cho K230 để dùng trong các bài tracking/servo/pan-tilt. | PTZ, 2DOF, pan tilt, servo, installation, tracking |

## 02. Basic Courses

Tóm tắt chương: kiến thức phần cứng và API cơ bản trên K230: ánh xạ chân FPIOA, GPIO/RGB/buzzer/button, UART/I2C/PWM, watchdog/timer, thuật toán FFT, mã hóa SHA256/AES, đa luồng, đọc ghi file, hiển thị ảnh/cảm ứng/camera và xử lý lật ảnh.

Từ khóa chung: FPIOA, GPIO, UART, IIC, I2C, PWM, WDT, Timer, SHA256, AES, thread, file IO, image display, touch, camera, Sensor, Display, MediaManager, flip.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1.FPIOA pin assignment](02.%202.%20Basic%20Courses/01_1.FPIOA%20pin%20assignment.md) | Giải thích FPIOA/IOMUX để ánh xạ pin vật lý sang chức năng UART/IIC/PWM/GPIO. Có ví dụ `FPIOA().help()`, `get_pin_num()`, `get_pin_func()` và sơ đồ chân Yahboom K230, gồm header 12 pin và cổng giao tiếp UART1. | FPIOA, IOMUX, pin mux, GPIO42, GPIO43, UART1, IIC0, IIC1, PWM, pinout |
| [2.RGB lights](02.%202.%20Basic%20Courses/02_2.RGB%20lights.md) | Điều khiển đèn RGB tích hợp bằng GPIO/FPIOA: cấu hình chân, bật/tắt từng kênh màu và tạo màu hiển thị cơ bản. | RGB LED, GPIO, FPIOA, output, red, green, blue |
| [3.Buzzer](02.%202.%20Basic%20Courses/03_3.Buzzer.md) | Điều khiển buzzer bằng chân GPIO/PWM để phát âm thanh hoặc cảnh báo, gồm khởi tạo pin và thay đổi trạng thái/tần số. | buzzer, beep, GPIO, PWM, alarm, sound |
| [4.Buttons](02.%202.%20Basic%20Courses/04_4.Buttons.md) | Đọc nút nhấn bằng GPIO input, cấu hình FPIOA, kiểm tra trạng thái nhấn/thả và dùng trong vòng lặp chương trình. | button, key, GPIO input, pull, read, debounce |
| [5.Serial communication](02.%202.%20Basic%20Courses/05_5.Serial%20communication.md) | Giao tiếp UART/serial trên K230: ánh xạ TXD/RXD bằng FPIOA, khởi tạo UART với baudrate, gửi/nhận dữ liệu qua cổng giao tiếp. | UART, serial, TXD, RXD, baudrate, YbUart, communication |
| [6.I2C communication](02.%202.%20Basic%20Courses/06_6.I2C%20communication.md) | Sử dụng I2C/IIC: cấu hình SDA/SCL qua FPIOA, khởi tạo bus, quét thiết bị và đọc/ghi dữ liệu ngoại vi. | I2C, IIC, SDA, SCL, bus scan, read, write, sensor |
| [7.PWM](02.%202.%20Basic%20Courses/07_7.PWM.md) | Tạo tín hiệu PWM để điều khiển độ sáng, âm thanh hoặc servo: cấu hình pin PWM, đặt frequency/duty và thay đổi duty cycle. | PWM, duty, frequency, pulse, servo, brightness |
| [8.WDT watchdog](02.%202.%20Basic%20Courses/08_8.WDT%20watchdog.md) | Dùng watchdog timer để tự reset khi chương trình treo: khởi tạo WDT, đặt timeout và feed định kỳ trong vòng lặp. | WDT, watchdog, timeout, feed, reset, reliability |
| [9.Timer](02.%202.%20Basic%20Courses/09_9.Timer.md) | Sử dụng Timer để tạo tác vụ định kỳ/callback theo thời gian, phục vụ đo thời gian hoặc xử lý không chặn. | Timer, callback, periodic, one-shot, interval, time |
| [10.Fourier Transform](02.%202.%20Basic%20Courses/10_10.Fourier%20Transform.md) | Giới thiệu biến đổi Fourier/FFT cho xử lý tín hiệu, thường dùng phân tích tần số âm thanh hoặc dữ liệu dao động. | Fourier, FFT, signal, frequency, spectrum, audio |
| [11.SHA256 encryption](02.%202.%20Basic%20Courses/11_11.SHA256%20encryption.md) | Tạo hash SHA256 cho chuỗi/dữ liệu, phục vụ kiểm tra toàn vẹn hoặc nhận dạng dữ liệu. | SHA256, hash, digest, hashlib, integrity |
| [12.AES encryption](02.%202.%20Basic%20Courses/12_12.AES%20encryption.md) | Mã hóa/giải mã dữ liệu bằng AES, gồm khóa, dữ liệu đầu vào và xử lý kết quả mã hóa. | AES, encrypt, decrypt, key, crypto, cipher |
| [13.Multithreading](02.%202.%20Basic%20Courses/13_13.Multithreading.md) | Chạy nhiều luồng trong MicroPython để tách tác vụ như đọc cảm biến, xử lý ảnh, hiển thị hoặc giao tiếp. | thread, _thread, multithreading, concurrency, task |
| [14.File reading and writing](02.%202.%20Basic%20Courses/14_14.File%20reading%20and%20writing.md) | Đọc/ghi file trên filesystem/TF card bằng API file Python, gồm mở file, ghi nội dung, đọc lại và đóng file. | file IO, open, read, write, close, filesystem, TF card |
| [15.Image Display](02.%202.%20Basic%20Courses/15_15.Image%20Display.md) | Hiển thị ảnh lên màn hình/IDE bằng `Display` và `MediaManager`, khởi tạo ảnh, vẽ hoặc load image rồi `Display.show_image()`. | image, Display, ST7701, show_image, MediaManager, LCD |
| [16.Touch Display](02.%202.%20Basic%20Courses/16_16.Touch%20Display.md) | Đọc tọa độ cảm ứng trên màn hình, xử lý sự kiện chạm và kết hợp hiển thị để tạo tương tác. | touch, touchscreen, coordinate, event, display |
| [17.Camera display](02.%202.%20Basic%20Courses/17_17.Camera%20display.md) | Khởi tạo camera bằng `Sensor`, cấu hình pixformat/framesize, snapshot và hiển thị luồng camera lên LCD hoặc IDE. | camera, Sensor, snapshot, RGB565, framesize, Display |
| [18.Image Flip](02.%202.%20Basic%20Courses/18_18.Image%20Flip.md) | Lật/đảo ảnh từ camera hoặc image buffer để điều chỉnh hướng hiển thị, phù hợp khi module lắp ngược hoặc cần mirror. | image flip, mirror, vflip, hflip, rotate, camera |
| [19.Camera](02.%202.%20Basic%20Courses/19_19.Camera.md) | Tổng quan cấu hình camera K230: reset sensor, chọn channel, pixformat, framesize, snapshot, stream và giải phóng tài nguyên. | Sensor, camera API, channel, CAM_CHN, snapshot, MediaManager |

## 03. Draw the image

Tóm tắt chương: các API vẽ lên `image.Image` để tạo overlay/hình minh họa: line, circle, rectangle, ellipse, arrow, crosshair, text và keypoints. Hầu hết bài dùng `Display.init()`, `MediaManager.init()` và `Display.show_image()`.

Từ khóa chung: image drawing, overlay, draw_line, draw_circle, draw_rectangle, draw_ellipse, draw_arrow, draw_cross, draw_string, draw_string_advanced, draw_keypoints, Display, ARGB8888.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1. Draw the lines](03.%203.%20Draw%20the%20image/01_1.%20Draw%20the%20lines.md) | Dùng `image.draw_line(x0, y0, x1, y1, color)` để vẽ đoạn thẳng; ví dụ ghép nhiều line thành chữ Yahboom trên nền trắng. | draw_line, line, x0, y0, x1, y1, thickness, Yahboom |
| [2. Draw the circle](03.%203.%20Draw%20the%20image/02_2.%20Draw%20the%20circle.md) | Dùng `image.draw_circle(x, y, radius, color, thickness, fill)` để vẽ vòng tròn hoặc hình tròn tô kín; ví dụ vẽ bánh xe/vòng tròn đồng tâm. | draw_circle, circle, radius, fill, thickness |
| [3. Draw the rectangle](03.%203.%20Draw%20the%20image/03_3.%20Draw%20the%20rectangle.md) | Dùng `image.draw_rectangle(x, y, w, h, color, thickness, fill)` để vẽ khung hoặc hình chữ nhật tô màu; thường dùng làm bounding box. | draw_rectangle, rectangle, bounding box, x, y, w, h |
| [4. Draw the ellipse](03.%203.%20Draw%20the%20image/04_4.%20Draw%20the%20ellipse.md) | Dùng `image.draw_ellipse(cx, cy, rx, ry, color, thickness)` để vẽ ellipse theo tâm và bán trục, phục vụ overlay hình học. | draw_ellipse, ellipse, cx, cy, rx, ry |
| [5. Draw the arrow](03.%203.%20Draw%20the%20image/05_5.%20Draw%20the%20arrow.md) | Dùng `image.draw_arrow(x0, y0, x1, y1, color, thickness)` để vẽ mũi tên chỉ hướng/chuyển động trên ảnh. | draw_arrow, arrow, direction, vector, thickness |
| [6. Draw the crosshairs](03.%203.%20Draw%20the%20image/06_6.%20Draw%20the%20crosshairs.md) | Dùng `image.draw_cross(x, y, color, size, thickness)` để đánh dấu tâm/điểm mục tiêu, thường kết hợp detection/tracking. | draw_cross, crosshair, center mark, target, size |
| [7. Draw text](03.%203.%20Draw%20the%20image/07_7.%20Draw%20text.md) | Dùng `draw_string_advanced()` để vẽ text nâng cao, hỗ trợ tiếng Trung và font tùy chỉnh; `draw_string()` là API cơ bản. | draw_string, draw_string_advanced, text, font, Chinese, label |
| [8. Draw key points](03.%203.%20Draw%20the%20image/08_8.%20Draw%20key%20points.md) | Tìm ORB keypoints bằng `find_keypoints()` trên ảnh grayscale và vẽ bằng `draw_keypoints()`; có thể dùng `match_descriptor()` để so khớp đặc trưng. | keypoints, ORB, find_keypoints, draw_keypoints, grayscale, descriptor, match |

## 04. Graphics detection

Tóm tắt chương: nhận dạng hình học cơ bản từ ảnh camera: line segment, rectangle, circle, edge và line inspection/fast linear regression. Các bài dùng pipeline camera, xử lý ảnh ở độ phân giải nhỏ rồi scale tọa độ để vẽ overlay lên màn hình.

Từ khóa chung: graphics detection, Hough, find_line_segments, find_rects, find_circles, edge detection, linear regression, PipeLine, Sensor, Display, ROI, threshold.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1. Line segment detection](04.%204.%20Graphics%20detection/01_1.%20Line%20segment%20detection.md) | Dùng `img.find_line_segments(merge_distance, max_theta_diff)` để phát hiện đoạn thẳng, scale tọa độ 160x120 lên 640x480 và vẽ line đỏ lên OSD. | find_line_segments, Hough Transform, merge_distance, max_theta_diff, scale_coordinates |
| [2. Rectangle Detection](04.%204.%20Graphics%20detection/02_2.%20Rectangle%20Detection.md) | Phát hiện hình chữ nhật trong ảnh camera, lấy tọa độ các cạnh/góc và vẽ khung nhận dạng lên màn hình. | rectangle detection, find_rects, corners, ROI, bounding box |
| [3. Circle detection](04.%204.%20Graphics%20detection/03_3.%20Circle%20detection.md) | Phát hiện hình tròn, thường dùng tham số threshold/x_margin/y_margin/r_margin để lọc và vẽ vòng tròn/tâm lên ảnh. | circle detection, find_circles, radius, x_margin, y_margin, r_margin |
| [4. Object edge detection](04.%204.%20Graphics%20detection/04_4.%20Object%20edge%20detection.md) | Nhận dạng biên vật thể trong ảnh; dùng để tìm đường viền/edge phục vụ phân tích hình dạng hoặc tiền xử lý vision. | edge detection, edge, outline, threshold, image processing |
| [5. Line inspection basics: fast linear regression](04.%204.%20Graphics%20detection/05_5.%20Line%20inspection%20basics%EF%BC%9Afast%20linear%20regression.md) | Kiểm tra/đo đường thẳng bằng fast linear regression, phù hợp line patrol hoặc xác định hướng đường trong ảnh. | linear regression, line inspection, line patrol, regression, angle |

## 05. Color recognition

Tóm tắt chương: nhận dạng màu bằng LAB threshold và `find_blobs()`, đếm vật thể theo màu, nhận dạng nhiều màu và ứng dụng dò line màu cho K230.

Từ khóa chung: color recognition, LAB threshold, find_blobs, blobs, color_index, THRESHOLDS, object counting, multi-color, line patrol, Threshold Editor, CanMV IDE.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1. Color recognition](05.%205.%20Color%20recognition/01_1.%20Color%20recognition.md) | Dùng `img.find_blobs([threshold])` với ngưỡng LAB trong `THRESHOLDS` để nhận dạng màu đỏ/xanh lá/xanh dương/custom; vẽ rectangle và cross lên blob, hiển thị FPS. Có hướng dẫn dùng Threshold Editor để lấy ngưỡng màu mới. | find_blobs, LAB, THRESHOLDS, color_index, Threshold Editor, blob, FPS |
| [2. Object Counting](05.%205.%20Color%20recognition/02_2.%20Object%20Counting.md) | Đếm số vật thể theo màu bằng cách lấy danh sách blobs sau `find_blobs()`, lọc nhiễu theo kích thước/area và hiển thị số lượng. | object counting, blobs count, area, pixels, filter, color objects |
| [3. Multi-color recognition](05.%205.%20Color%20recognition/03_3.%20Multi-color%20recognition.md) | Nhận dạng nhiều màu trong cùng chương trình bằng nhiều ngưỡng LAB, gán màu hiển thị riêng và vẽ bounding box/cross cho từng nhóm blob. | multi-color, multiple thresholds, red, green, blue, blob labels |
| [4. K230 Color Line Patrol](05.%205.%20Color%20recognition/04_4.%20K230%20Color%20Line%20Patrol.md) | Ứng dụng dò đường màu: nhận dạng line bằng threshold màu, tính vị trí/tâm vùng màu để phục vụ robot line following hoặc điều khiển hướng. | color line patrol, line following, color tracking, center, robot, threshold |

## 06. CV_lite Image Processing Special Topic

Tóm tắt chương: `cv_lite` là module xử lý ảnh nhẹ, dựa trên một phần OpenCV nhưng tối ưu cho K230. Chương này tập trung vào API tăng tốc cho ảnh grayscale/RGB888: tìm blob, hình tròn, góc, cạnh, hình chữ nhật, nhị phân hóa, chỉnh phơi sáng, histogram, morphology, blur, PnP ranging và cân bằng trắng.

Từ khóa chung: cv_lite, OpenCV, ulab.numpy.ndarray, to_numpy_ref, image.ALLOC_REF, RGB888, grayscale, blobs, Canny, Hough, morphology, erosion, dilation, opening, closing, top hat, black hat, gradient, Gaussian, histogram, PnP, white balance.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1.Introduction to cv_lite](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/01_1.Introduction%20to%20cv_lite.md) | Giới thiệu `cv_lite` như module xử lý ảnh nhẹ/tăng tốc cho K230, dùng `to_numpy_ref()` để lấy ndarray và gói kết quả về `image.Image(..., alloc=image.ALLOC_REF, data=...)` để tránh copy bộ nhớ. | cv_lite, OpenCV, ndarray, to_numpy_ref, ALLOC_REF, RGB888 |
| [2.cv_lite API Reference Manual](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/02_2.cv_lite%20API%20Reference%20Manual.md) | Tài liệu tham chiếu API: `grayscale_find_blobs`, `rgb888_find_blobs`, `find_circles`, `find_rectangles`, `find_edges`, threshold binary, exposure, white balance, morphology, blur, histogram và corner detection. | API reference, grayscale_find_blobs, rgb888_find_circles, rgb888_erode, rgb888_gaussian_blur |
| [3.Color Block Recognition - Grayscale Image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/03_3.Color%20Block%20Recognition%20-%20Grayscale%20Image.md) | Tìm vùng sáng/tối trên ảnh grayscale bằng `cv_lite.grayscale_find_blobs()`, dùng threshold min/max, `min_area` và `kernel_size` để lọc nhiễu. | grayscale_find_blobs, blob, threshold, min_area, kernel_size, connected region |
| [4.Color Block Recognition - Color Image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/04_4.Color%20Block%20Recognition%20-%20Color%20Image.md) | Tìm vùng màu trên ảnh RGB888 bằng `cv_lite.rgb888_find_blobs()`, truyền threshold theo kênh màu và vẽ khung vùng phát hiện. | rgb888_find_blobs, RGB888, color block, threshold, blob detection |
| [5.Circle Recognition - Grayscale Image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/05_5.Circle%20Recognition%20-%20Grayscale%20Image.md) | Phát hiện hình tròn trên ảnh grayscale bằng Hough circle qua `cv_lite.grayscale_find_circles()`, cấu hình `dp`, `minDist`, `param1`, `param2`, `minRadius`, `maxRadius`. | grayscale_find_circles, Hough Circle, dp, minDist, radius |
| [6.Circle Recognition - Color Image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/06_6.Circle%20Recognition%20-%20Color%20Image.md) | Phát hiện hình tròn trên ảnh RGB888 bằng `cv_lite.rgb888_find_circles()`, trả danh sách tâm và bán kính để vẽ overlay. | rgb888_find_circles, circle, Hough, center, radius |
| [7.Corner Recognition - Grayscale Image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/07_7.Corner%20Recognition%20-%20Grayscale%20Image.md) | Nhận dạng góc trên ảnh grayscale, dùng cho marker/hình học/tiền xử lý nhận dạng khung. | grayscale corner, find_corners, corner detection, feature point |
| [8.Corner Recognition - Color Image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/08_8.Corner%20Recognition%20-%20Color%20Image.md) | Nhận dạng góc trên ảnh RGB888 bằng API corner của `cv_lite`, dùng để đánh dấu điểm đặc trưng trong ảnh màu. | rgb888_find_corners, RGB888, corner, feature, point |
| [9.Edge Recognition - Grayscale Image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/09_9.Edge%20Recognition%20-%20Grayscale%20Image.md) | Dò biên Canny trên ảnh grayscale bằng `cv_lite.grayscale_find_edges(image_shape, img_np, threshold1, threshold2)`; `threshold1` bắt cạnh yếu, `threshold2` lọc cạnh mạnh. | grayscale_find_edges, Canny, threshold1, threshold2, edge |
| [10. Edge Recognition - Color Image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/10_10.%20Edge%20Recognition%20-%20Color%20Image.md) | Dò biên trên ảnh màu RGB888 bằng `cv_lite.rgb888_find_edges()`, phù hợp tiền xử lý detection khi vẫn cần nguồn ảnh màu. | rgb888_find_edges, Canny, RGB888, edge detection |
| [11. Rectangle Recognition - Grayscale Image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/11_11.%20Rectangle%20Recognition%20-%20Grayscale%20Image.md) | Dò hình chữ nhật grayscale bằng `cv_lite.grayscale_find_rectangles()`, dùng Canny thresholds, `approx_epsilon`, `area_min_ratio`, `max_angle_cos`, `gaussian_blur_size`; trả `[x, y, w, h]`. | grayscale_find_rectangles, rectangle, Canny, approx_epsilon, max_angle_cos |
| [12.Rectangle Recognition - Color Image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/12_12.Rectangle%20Recognition%20-%20Color%20Image.md) | Dò hình chữ nhật trên ảnh RGB888 bằng API rectangle của `cv_lite`, có lọc diện tích/góc và tiền xử lý blur. | rgb888_find_rectangles, RGB888, rectangle, area_min_ratio, gaussian_blur |
| [13.Rectangle recognition combined with corner recognition - grayscale image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/13_13.Rectangle%20recognition%20combined%20with%20corner%20recognition%20-%20grayscale%20image.md) | Kết hợp nhận dạng chữ nhật và góc trên ảnh grayscale để đánh dấu khung cùng các corner, hữu ích khi cần kiểm chứng hình học. | rectangle + corner, grayscale, corners, geometry, validation |
| [14.Rectangle recognition combined with corner recognition - color image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/14_14.Rectangle%20recognition%20combined%20with%20corner%20recognition%20-%20color%20image.md) | Kết hợp rectangle detection và corner detection trên ảnh RGB888, phục vụ marker/khung vật thể trong ảnh màu. | RGB888, rectangle, corner, marker, frame detection |
| [15.Image Binarization - Grayscale](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/15_15.Image%20Binarization%20-%20Grayscale.md) | Nhị phân hóa ảnh grayscale bằng `cv_lite.grayscale_threshold_binary()`: pixel dưới `thresh` thành 0, pixel >= `thresh` thành `maxval`. | grayscale_threshold_binary, binary, thresh, maxval, black white |
| [16.Image Binarization - Color Image](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/16_16.Image%20Binarization%20-%20Color%20Image.md) | Nhị phân hóa ảnh RGB888 bằng `cv_lite.rgb888_threshold_binary()`, thường chuyển/lọc theo độ sáng hoặc ngưỡng màu để tạo mask. | rgb888_threshold_binary, binary mask, RGB888, threshold |
| [17.Exposure Adjustment](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/17_17.Exposure%20Adjustment.md) | Chỉnh độ phơi sáng/độ sáng ảnh RGB888 bằng `rgb888_adjust_exposure` hoặc bản fast, dùng khi ảnh quá tối/sáng trước detection. | rgb888_adjust_exposure, exposure, brightness, adjust_exposure_fast |
| [18.Image Black Hat Operations](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/18_18.Image%20Black%20Hat%20Operations.md) | Morphology black-hat: làm nổi chi tiết tối trên nền sáng bằng hiệu giữa closing và ảnh gốc; hữu ích xử lý chữ/đốm tối. | black hat, rgb888_blackhat, morphology, dark details, closing |
| [19.Image Color Histogram](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/19_19.Image%20Color%20Histogram.md) | Tính histogram màu RGB888 bằng `rgb888_calc_histogram`, hỗ trợ phân tích phân bố màu/độ sáng hoặc chọn threshold. | histogram, rgb888_calc_histogram, color distribution, bins |
| [20.Image Closing](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/20_20.Image%20Closing.md) | Morphology closing: dilation rồi erosion để lấp lỗ nhỏ, nối vùng foreground và làm mượt contour. | closing, rgb888_close, dilation, erosion, fill holes, morphology |
| [21.Image Expansion](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/21_21.Image%20Expansion.md) | Dilation/giãn nở ảnh RGB888 bằng `cv_lite.rgb888_dilate()`, mở rộng vùng trắng, nối vùng bị đứt; có `kernel_size`, `iterations`, `threshold_value`. | dilation, rgb888_dilate, expansion, kernel_size, iterations, Otsu |
| [22.Image Corrosion](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/22_22.Image%20Corrosion.md) | Erosion/co ảnh bằng `cv_lite.rgb888_erode()`, loại nhiễu trắng nhỏ và thu hẹp foreground. | erosion, corrosion, rgb888_erode, noise removal, morphology |
| [23.Gaussian Blur](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/23_23.Gaussian%20Blur.md) | Làm mờ Gaussian bằng `cv_lite.rgb888_gaussian_blur_fast()`, dùng kernel lẻ để giảm nhiễu tự nhiên trước edge/detection. | Gaussian blur, rgb888_gaussian_blur_fast, smoothing, denoise, kernel_size |
| [24.Gradient Transformation](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/24_24.Gradient%20Transformation.md) | Morphological gradient: làm nổi biên bằng chênh lệch dilation và erosion, giúp tách đường viền vật thể. | gradient, rgb888_gradient, morphology, contour, edge enhancement |
| [25.Mean Fuzzy](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/25_25.Mean%20Fuzzy.md) | Mean blur/lọc trung bình bằng `cv_lite.rgb888_mean_blur_fast()`, giảm nhiễu nhanh nhưng có thể mất chi tiết hơn Gaussian. | mean blur, rgb888_mean_blur_fast, average filter, denoise, kernel_size |
| [26.Image Opening](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/26_26.Image%20Opening.md) | Morphology opening: erosion rồi dilation để loại nhiễu nhỏ/đốm sáng mà vẫn giữ cấu trúc chính. | opening, rgb888_open, erosion, dilation, small noise, morphology |
| [27.Image Top Hat Operation](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/27_27.Image%20Top%20Hat%20Operation.md) | Top-hat: ảnh gốc trừ opening để làm nổi vùng sáng nhỏ và giảm nền chiếu sáng không đều. | top hat, rgb888_tophat, bright details, uneven lighting, morphology |
| [28.PnP ranging](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/28_28.PnP%20ranging.md) | Đo khoảng cách/pose bằng PnP dựa trên điểm ảnh và tọa độ thực; thường kết hợp nhận dạng hình chữ nhật/corner để ước lượng khoảng cách vật thể. | PnP, ranging, pose, distance, camera calibration, solvePnP |
| [29.Find rectangles and measure distances](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/29_29.Find%20rectangles%20and%20measure%20distances.md) | Ứng dụng kết hợp tìm hình chữ nhật và đo khoảng cách, dùng detection hình học làm đầu vào cho tính toán khoảng cách. | rectangle ranging, distance measurement, find rectangles, PnP |
| [30.Image grayscale world white balance](06.%206.CV_lite%20Image%20Processing%20Special%20Topic/30_30.Image%20grayscale%20world%20white%20balance.md) | Cân bằng trắng theo gray-world cho ảnh RGB888 bằng API `rgb888_white_balance_gray_world_*`, giúp màu ổn định hơn trước nhận dạng màu. | white balance, gray world, rgb888_white_balance_gray_world_fast, color correction |

## 07. Code type recognition

Tóm tắt chương: nhận dạng các loại mã bằng camera K230: barcode, QR code, AprilTag và DM/Data Matrix. Các bài thường dùng `Sensor`, ảnh grayscale/RGB, gọi hàm tìm mã trong `image`, đọc payload, góc xoay và vẽ kết quả lên màn hình.

Từ khóa chung: barcode, QR code, AprilTag, DM code, Data Matrix, code recognition, payload, rotation, Sensor, Display, grayscale.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1.Barcode recognition](<07. 7. Code type recognition/01_1.Barcode recognition.md>) | Nhận dạng barcode/1D code từ camera, đọc nội dung mã, vị trí và hiển thị kết quả trên màn hình hoặc serial. | barcode, 1D code, find_barcodes, payload, scan |
| [2.QR code recognition](<07. 7. Code type recognition/02_2.QR code recognition.md>) | Nhận dạng QR code hai chiều, giải mã payload và vẽ vùng mã trên ảnh camera. | QR code, find_qrcodes, payload, two-dimensional code |
| [3.AprilTag tag recognition](<07. 7. Code type recognition/03_3.AprilTag tag recognition.md>) | Nhận dạng AprilTag, lấy ID/tag family/vị trí/góc, dùng cho định vị marker hoặc robot vision. | AprilTag, marker, tag ID, pose, fiducial |
| [4.DM code recognition](<07. 7. Code type recognition/04_4.DM code recognition.md>) | Nhận dạng DM/Data Matrix code, so sánh với QR; DM phù hợp mã nhỏ/traceability công nghiệp nhưng tỉ lệ nhận dạng thấp hơn QR, có thể cần xoay mã/camera. | DM code, Data Matrix, industrial code, rotation angle, traceability |

## 08. Face Recognition

Tóm tắt chương: các routine AI về khuôn mặt: cấu trúc chung của AI vision code, face detection, facial keypoint, face orientation, face 3D, gaze direction và đăng ký/nhận dạng khuôn mặt. Pattern chính là `PipeLine`, `AIBase`, `AI2D`, `nncase_runtime`, `.kmodel`, preprocess, inference, postprocess và draw result.

Từ khóa chung: face detection, face recognition, keypoints, gaze, head pose, face 3D, register face, KPU, kmodel, AIBase, AI2D, PipeLine, anchors, NMS.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1.[Must-read] General code structure and prerequisite knowledge of AI vision routines](<08. 8. Face Recognition/01_1.[Must-read] General code structure and prerequisite knowledge of AI vision routines.md>) | Bài nền tảng về cấu trúc code AI vision: import `PipeLine`, `ScopedTiming`, `AIBase`, `AI2D`, `nncase_runtime`, `ulab.numpy`, `aidemo`; cấu hình model path, anchors, preprocess, chạy `run(img)`, `draw_result()` và `deinit()`. | AI vision structure, PipeLine, AIBase, AI2D, nncase, KPU, kmodel, preprocess, postprocess |
| [2.Face Detection](<08. 8. Face Recognition/02_2.Face Detection.md>) | Dùng model `face_detection_320.kmodel` để phát hiện khuôn mặt, postprocess qua `aidemo.face_det_post_process`, trả bounding box `(x, y, w, h)` và vẽ khung mặt. | face detection, face_detection_320.kmodel, anchors, confidence, NMS, bounding box |
| [3.Facial key point recognition](<08. 8. Face Recognition/03_3.Facial key point recognition.md>) | Nhận dạng điểm đặc trưng khuôn mặt như mắt, mũi, miệng; thường chạy sau face detection để lấy ROI mặt và vẽ keypoints. | facial keypoints, landmark, eyes, nose, mouth, face ROI |
| [4.Face orientation detection](<08. 8. Face Recognition/04_4.Face orientation detection.md>) | Ước lượng hướng/khoảng quay khuôn mặt, phục vụ nhận biết quay trái/phải/ngẩng/cúi hoặc điều khiển theo hướng mặt. | face orientation, head pose, yaw, pitch, roll, direction |
| [5.Face 3D Network](<08. 8. Face Recognition/05_5.Face 3D Network.md>) | Mạng face 3D cho phân tích mặt nâng cao, dùng model AI để suy luận đặc trưng/pose 3D từ ảnh khuôn mặt. | face 3D, 3D face network, pose, landmarks, kmodel |
| [6.Gaze direction detection](<08. 8. Face Recognition/06_6.Gaze direction detection.md>) | Nhận dạng hướng nhìn/gaze dựa trên khuôn mặt/mắt, dùng cho tương tác người-máy hoặc tracking ánh nhìn. | gaze direction, eye gaze, looking direction, face tracking |
| [7.Register for face recognition](<08. 8. Face Recognition/07_7.Register for face recognition.md>) | Đăng ký khuôn mặt để nhận dạng: thu thập/ghi đặc trưng face, so khớp embedding và quản lý dữ liệu nhận dạng. | face register, face recognition, embedding, database, identity |

## 09. Human body characteristics

Tóm tắt chương: các bài AI nhận dạng người/bàn tay/cử chỉ: human detection, pose/keypoints, posture, fall detection, palm detection, palm keypoints/classification, gesture, dynamic gesture và rock-paper-scissors. Phần lớn dùng `.kmodel`, `PipeLine`, `AIBase`, confidence threshold và NMS.

Từ khóa chung: human body, pose, keypoint, fall detection, palm, hand, gesture, dynamic gesture, Rock Paper Scissors, YOLOv8 pose, KPU, kmodel.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1. Human body detection](<09. 9. Human body characteristics/01_1. Human body detection.md>) | Phát hiện người trong ảnh camera, vẽ bounding box và dùng làm nền cho các bài posture/fall/tracking. | human detection, person, bounding box, KPU, confidence |
| [2. Human key point detection](<09. 9. Human body characteristics/02_2. Human key point detection.md>) | Dùng `yolov8n-pose.kmodel` để nhận dạng keypoints cơ thể nhiều người, vẽ skeleton/điểm khớp trên ảnh. | human keypoints, YOLOv8 pose, skeleton, joints, pose estimation |
| [3. Human posture recognition](<09. 9. Human body characteristics/03_3. Human posture recognition.md>) | Phân loại tư thế người dựa trên keypoints hoặc model nhận dạng, dùng cho đứng/ngồi/nằm/các posture cụ thể. | posture recognition, pose classification, keypoints, action |
| [4. Fall detection](<09. 9. Human body characteristics/04_4. Fall detection.md>) | Nhận dạng trạng thái té/ngã bằng body detection/keypoints, phục vụ cảnh báo an toàn. | fall detection, alarm, human pose, safety, elderly care |
| [5. Palm detection](<09. 9. Human body characteristics/05_5. Palm detection.md>) | Dùng `hand_det.kmodel` để phát hiện lòng bàn tay, postprocess anchors/NMS và vẽ box; nền cho gesture/keypoint. | palm detection, hand_det.kmodel, hand, anchors, NMS |
| [6. Palm key point detection](<09. 9. Human body characteristics/06_6. Palm key point detection.md>) | Nhận dạng keypoints bàn tay/ngón tay sau khi phát hiện palm, dùng cho phân tích cử chỉ. | palm keypoints, hand landmarks, fingers, gesture input |
| [7. Palm key point classification](<09. 9. Human body characteristics/07_7. Palm key point classification.md>) | Phân loại trạng thái bàn tay dựa trên keypoints, làm đầu vào cho nhận dạng gesture tĩnh. | hand keypoint classification, gesture class, palm landmarks |
| [8. Gesture Recognition](<09. 9. Human body characteristics/08_8. Gesture Recognition.md>) | Nhận dạng cử chỉ tay tĩnh bằng palm detection + keypoint/classification model. | gesture recognition, static gesture, hand, classifier |
| [9. Dynamic gesture recognition](<09. 9. Human body characteristics/09_9. Dynamic gesture recognition.md>) | Nhận dạng cử chỉ động theo chuỗi thời gian/frame, phù hợp vẫy tay, swipe hoặc điều khiển không chạm. | dynamic gesture, temporal, sequence, motion gesture |
| [10. Rock, Paper, Scissors](<09. 9. Human body characteristics/10_10. Rock, Paper, Scissors.md>) | Game oẳn tù tì dùng palm detection và hand keypoint classification để nhận dạng đá/kéo/bao, có logic task `GuessApp`. | rock paper scissors, hand gesture, GuessApp, palm, game |

## 10. Scenario Application

Tóm tắt chương: ứng dụng AI cấp cao: OCR detection/recognition, YOLOv8 target detection/segmentation, self-learning object recognition, license plate detection/recognition, target tracking, fruit/garbage classification và road sign recognition.

Từ khóa chung: OCR, YOLOv8, segmentation, object detection, tracking, license plate, classification, road sign, KPU, kmodel, deploy_config.json, AnchorBaseDet, GFLDet.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1.OCR character detection](<10. 10. Scenario Application/01_1.OCR character detection.md>) | Phát hiện vùng chữ/ký tự trong ảnh, thường là bước đầu trước OCR recognition. | OCR detection, text box, character detection, text region |
| [2.OCR character recognition](<10. 10. Scenario Application/02_2.OCR character recognition.md>) | Nhận dạng nội dung ký tự sau khi phát hiện vùng chữ, xuất text kết quả. | OCR recognition, text recognition, character, string |
| [3.yolov8n target detection](<10. 10. Scenario Application/03_3.yolov8n target detection.md>) | Object detection bằng YOLOv8n, đọc model/config, chạy KPU inference, postprocess NMS và vẽ box/label. | YOLOv8n, target detection, object detection, NMS, anchors |
| [4.yolov8n segmentation](<10. 10. Scenario Application/04_4.yolov8n segmentation.md>) | Segmentation bằng YOLOv8n để lấy mask vùng vật thể thay vì chỉ bounding box. | YOLOv8 segmentation, mask, instance segmentation, object mask |
| [5. Self-learning object recognition](<10. 10. Scenario Application/05_5. Self-learning object recognition.md>) | Tự học/đăng ký vật thể mới và nhận dạng lại dựa trên đặc trưng đã lưu, phù hợp demo nhận dạng đối tượng tùy chọn. | self-learning, object recognition, feature, register object |
| [6. License plate detection](<10. 10. Scenario Application/06_6. License plate detection.md>) | Phát hiện vùng biển số xe trong ảnh camera, tạo ROI cho bước nhận dạng biển số. | license plate detection, plate box, vehicle, ROI |
| [7. License Plate Recognition](<10. 10. Scenario Application/07_7. License Plate Recognition.md>) | Nhận dạng ký tự biển số sau khi phát hiện vùng plate, xuất chuỗi biển số. | license plate recognition, LPR, plate OCR, vehicle |
| [8. Target Tracking](<10. 10. Scenario Application/08_8. Target Tracking.md>) | Theo dõi mục tiêu qua các frame, dùng kết quả detection/track để cập nhật vị trí mục tiêu. | target tracking, tracker, object tracking, bbox |
| [9. Fruit classification](<10. 10. Scenario Application/09_9. Fruit classification.md>) | Phân loại ảnh trái cây bằng model AI, hiển thị class/score. | fruit classification, classifier, label, score |
| [10. Garbage classification](<10. 10. Scenario Application/10_10. Garbage classification.md>) | Phân loại rác theo nhóm bằng model AI, phù hợp demo sorting hoặc giáo dục phân loại rác. | garbage classification, waste sorting, classifier, category |
| [11. Road sign recognition](<10. 10. Scenario Application/11_11. Road sign recognition.md>) | Nhận dạng biển báo đường bằng model kmodel/config; tài liệu lưu ý model chủ yếu nhận tốt ảnh biển báo trong bộ routine, chưa chắc nhận tốt biển báo thật. | road sign recognition, traffic sign, deploy_config, AnchorBaseDet, GFLDet |

## 11. Audio and video processing

Tóm tắt chương: ghi âm, phát âm thanh, ghi video, phát video và keyword wake-up. Các bài dùng module media/audio/video, file WAV/video và với KWS thì dùng model AI âm thanh.

Từ khóa chung: audio, video, record, playback, WAV, PCM, keyword spotting, KWS, microphone, speaker, MediaManager.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1. Audio Recording](<11. 11. Audio and video processing/01_1. Audio Recording.md>) | Ghi âm từ microphone vào file âm thanh, cấu hình format/kênh/sample rate và quản lý stream. | audio recording, microphone, WAV, PCM, sample rate |
| [2. Play Audio](<11. 11. Audio and video processing/02_2. Play Audio.md>) | Phát file âm thanh qua speaker/audio output, đọc file WAV và điều khiển playback. | play audio, speaker, WAV playback, audio output |
| [3. Video Recording](<11. 11. Audio and video processing/03_3. Video Recording.md>) | Ghi video từ camera, cấu hình pipeline/media và lưu stream video ra file. | video recording, camera, encoder, media, record |
| [4. Play Video](<11. 11. Audio and video processing/04_4. Play Video.md>) | Phát video file lên màn hình/hiển thị, xử lý media playback. | play video, video playback, display, media |
| [5. Keyword wake-up](<11. 11. Audio and video processing/05_5. Keyword wake-up.md>) | Keyword spotting bằng `KWSApp(AIBase)`: đọc audio PCM, `aidemo.kws_preprocess`, reshape feature `(1, 30, 40)`, chạy model và phát âm thanh phản hồi khi wake word đạt threshold. | keyword wake-up, KWS, AIBase, kws_preprocess, PCM, threshold |

## 12. Network Basics

Tóm tắt chương: kết nối Wi-Fi/AP, TCP/UDP server-client, HTTP server-client, MQTT publisher/subscriber, RTSP streaming, gọi OpenRouter API và mở resource monitor.

Từ khóa chung: Wi-Fi, WLAN, AP hotspot, socket, TCP, UDP, HTTP, MQTT, RTSP, OpenRouter, network, server, client.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1. Wireless network connection](<12. 12. Network Basics/01_1. Wireless network connection.md>) | Kết nối K230 vào mạng Wi-Fi, cấu hình SSID/password và kiểm tra địa chỉ IP. | Wi-Fi, WLAN, SSID, password, IP address |
| [2. AP hotspot mode](<12. 12. Network Basics/02_2. AP hotspot mode.md>) | Cấu hình K230 làm AP/hotspot để thiết bị khác kết nối trực tiếp. | AP mode, hotspot, access point, SSID |
| [3. TCP-Server Example](<12. 12. Network Basics/03_3. TCP-Server Example.md>) | Tạo TCP server lắng nghe kết nối, nhận/gửi dữ liệu qua socket. | TCP server, socket, bind, listen, accept |
| [4. TCP-Client Example](<12. 12. Network Basics/04_4. TCP-Client Example.md>) | Tạo TCP client kết nối tới server và trao đổi dữ liệu. | TCP client, socket, connect, send, recv |
| [5. UDP-Server Example](<12. 12. Network Basics/05_5. UDP-Server Example.md>) | UDP server nhận datagram không kết nối, phù hợp truyền dữ liệu nhẹ. | UDP server, datagram, recvfrom, socket |
| [6. UDP-Client Example](<12. 12. Network Basics/06_6. UDP-Client Example.md>) | UDP client gửi datagram tới server/địa chỉ đích. | UDP client, sendto, datagram, socket |
| [7. HTTP-Server Example](<12. 12. Network Basics/07_7. HTTP-Server Example.md>) | Chạy HTTP server đơn giản trên K230 để trả response/web page hoặc nhận request. | HTTP server, web server, request, response |
| [8. HTTP-Client Example](<12. 12. Network Basics/08_8. HTTP-Client Example.md>) | Gửi HTTP request từ K230 tới server/API, đọc response. | HTTP client, GET, POST, request, response |
| [9. MQTT Quick Start](<12. 12. Network Basics/09_9. MQTT Quick Start.md>) | Tổng quan MQTT: broker, topic, publish/subscribe và chuẩn bị kết nối. | MQTT, broker, topic, publish, subscribe |
| [10. MQTT-Publisher](<12. 12. Network Basics/10_10. MQTT-Publisher.md>) | K230 publish message lên topic MQTT, dùng cho IoT telemetry/control. | MQTT publisher, publish, topic, IoT |
| [11. MQTT-Subscriber](<12. 12. Network Basics/11_11. MQTT-Subscriber.md>) | K230 subscribe topic MQTT và xử lý message/callback nhận được. | MQTT subscriber, subscribe, callback, message |
| [12. RTSP real-time image transmission](<12. 12. Network Basics/12_12. RTSP real-time image transmission.md>) | Truyền hình ảnh camera realtime qua RTSP để xem stream từ client. | RTSP, real-time stream, camera, video |
| [13. RTSP real-time image transmission combined with AIDemo](<12. 12. Network Basics/13_13. RTSP real-time image transmission combined with AIDemo.md>) | Kết hợp RTSP stream với AIDemo để truyền hình ảnh đã xử lý/AI overlay. | RTSP + AIDemo, AI stream, overlay, realtime |
| [14. Call OpenRouter large model aggregation service](<12. 12. Network Basics/14_14. Call OpenRouter large model aggregation service.md>) | Gọi dịch vụ OpenRouter qua network/API từ K230, gửi request và nhận phản hồi model lớn. | OpenRouter, LLM API, HTTP request, API key |
| [15. Open the Resource Monitoring Panel](<12. 12. Network Basics/15_15. Open the Resource Monitoring Panel.md>) | Mở panel giám sát tài nguyên để xem trạng thái hệ thống khi chạy ứng dụng. | resource monitor, system monitor, CPU, memory |

## 13. LVGL Graphical Interface

Tóm tắt chương: nhập môn LVGL trên K230 và tạo widget cơ bản: button, slider, image, textbox + keyboard.

Từ khóa chung: LVGL, GUI, button, slider, image widget, textbox, keyboard, event callback, screen.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1. Introduction to LVGL](<13. 13. LVGL Graphical Interface/01_1. Introduction to LVGL.md>) | Giới thiệu LVGL, khởi tạo giao diện và các khái niệm screen/object/style/event. | LVGL, GUI, screen, object, style, event |
| [2. Create a button](<13. 13. LVGL Graphical Interface/02_2. Create a button.md>) | Tạo button LVGL, đặt text/style và xử lý sự kiện click. | lv.button, button, click event, label |
| [3. Create a slider](<13. 13. LVGL Graphical Interface/03_3. Create a slider.md>) | Tạo slider để nhập giá trị số, xử lý value changed và cập nhật UI. | slider, value, event, control |
| [4. Create an Image](<13. 13. LVGL Graphical Interface/04_4. Create an Image.md>) | Hiển thị ảnh trong LVGL bằng image widget/source ảnh. | lv.image, image widget, display image |
| [5. Create a text box and keyboard](<13. 13. LVGL Graphical Interface/05_5. Create a text box and keyboard.md>) | Tạo textbox và keyboard ảo để nhập text trên màn hình cảm ứng. | textbox, keyboard, text input, touch UI |

## 14. GUI Code Tutorial & Secondary Development

Tóm tắt chương: phân tích kiến trúc GUI app/desktop của Yahboom K230, gồm engine, discovery, layout, styling, BaseApp, hello world và lifecycle/resource management.

Từ khóa chung: GUI architecture, AppManager, BaseApp, LVGL, desktop, app discovery, layout algorithm, lifecycle, resource release.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [01.GUI System Architecture](<14. 14. GUI Code Tutorial &amp; Secondary Development/01_01.GUI System Architecture.md>) | Tổng quan kiến trúc GUI: thành phần engine, desktop/app manager, ứng dụng và quan hệ với LVGL. | GUI architecture, AppManager, engine, LVGL |
| [02.Core Engine Initialization](<14. 14. GUI Code Tutorial &amp; Secondary Development/02_02.Core Engine Initialization.md>) | Phân tích quá trình khởi tạo core GUI engine, màn hình, input và tài nguyên nền. | core engine, init, display, input, resources |
| [03.Application Discovery Mechanism in GUI](<14. 14. GUI Code Tutorial &amp; Secondary Development/03_03.Application Discovery Mechanism in GUI.md>) | Cơ chế tìm/đăng ký ứng dụng GUI để hiển thị trên desktop. | app discovery, application registry, desktop icon |
| [04.Desktop Layout Algorithm](<14. 14. GUI Code Tutorial &amp; Secondary Development/04_04.Desktop Layout Algorithm.md>) | Thuật toán layout icon desktop, tính tọa độ, phân trang và xử lý vuốt chuyển page. | desktop layout, coordinates, pagination, swipe, touch |
| [05.Advanced UI Styling](<14. 14. GUI Code Tutorial &amp; Secondary Development/05_05.Advanced UI Styling.md>) | Tùy biến style UI nâng cao: màu sắc, trạng thái, visual polish cho LVGL widgets. | UI styling, LVGL style, color, state |
| [06.BaseApp Base Class Analysis](<14. 14. GUI Code Tutorial &amp; Secondary Development/06_06.BaseApp Base Class Analysis.md>) | Phân tích `BaseApp`: `__init__`, `create_icon`, `launch_with_animation`; khi phát triển app cần override `initialize(self)` và vẽ UI lên `self.screen`. | BaseApp, create_icon, launch_with_animation, initialize, self.screen |
| [07.Hello_World Practical](<14. 14. GUI Code Tutorial &amp; Secondary Development/07_07.Hello_World Practical.md>) | Bài thực hành tạo ứng dụng GUI Hello World theo framework có sẵn. | Hello World, GUI app, practical, BaseApp |
| [08.GUI Application Lifecycle and Resource Management](<14. 14. GUI Code Tutorial &amp; Secondary Development/08_08.GUI Application Lifecycle and Resource Management.md>) | Vòng đời GUI app: create/launch/running/exit; nhấn mạnh giải phóng timer, cache ảnh lớn và tài nguyên không do LVGL tự quản. | lifecycle, resource management, timer, image cache, deinit |

## 15. Train your own model

Tóm tắt chương: huấn luyện model YOLO riêng và triển khai cho K230, gồm môi trường local và nền tảng online.

Từ khóa chung: train model, YOLO, dataset, annotation, kmodel, deployment, local training, online training.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1. Local deployment of yolo training environment](<15. 15. Train your own model/01_1. Local deployment of yolo training environment.md>) | Chuẩn bị môi trường local để train YOLO: cài dependencies, dataset, annotation, training và chuyển/triển khai model cho K230. | local training, YOLO, dataset, annotation, environment, kmodel |
| [2. Use online platforms for training](<15. 15. Train your own model/02_2. Use online platforms for training.md>) | Dùng nền tảng online để train model, phù hợp khi không muốn tự cấu hình môi trường local. | online training, cloud platform, YOLO, dataset, export |

## 16. Touch Course

Tóm tắt chương: thao tác cảm ứng trên màn hình K230: đọc điểm chạm, vẽ bằng touch và chụp ảnh bằng thao tác chạm.

Từ khóa chung: touch, touchscreen, coordinate, drawing, photo capture, touch event.

| Bài | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1.Touch point detection](<16. 16.Touch Course/01_1.Touch point detection.md>) | Đọc tọa độ điểm chạm trên màn hình và hiển thị/log vị trí touch. | touch point, coordinates, touchscreen, event |
| [2.Touch Painting](<16. 16.Touch Course/02_2.Touch Painting.md>) | Dùng điểm chạm để vẽ trên màn hình, tạo ứng dụng painting đơn giản. | touch painting, draw, canvas, finger input |
| [3.Touch to take a photo](<16. 16.Touch Course/03_3.Touch to take a photo.md>) | Kết hợp camera và touch: chạm để chụp/lưu ảnh. | touch capture, camera, photo, snapshot |

## 17. Multi-master communication (purchased separately)

Tóm tắt chương: các routine giao tiếp đa chủ/ngoại vi mua riêng, nơi K230 chạy thuật toán vision/AI và truyền kết quả cho bộ điều khiển khác như micro:bit, Arduino, STM32 hoặc các biến thể K230/UART board. Nội dung lặp theo cùng 17 chức năng: màu, mã vạch, QR, AprilTag, DM, face, gaze/looking direction, face recognition, human, fall, palm, gesture, OCR, object detection, target tracking, self-learning object và license plate.

Từ khóa chung: multi-master communication, purchased separately, microbit_k230, arduino_k230, stm32_k230, UART, serial protocol, K230 result output, color recognition, barcode, QR, AprilTag, DM, face detection, gaze direction, face recognition, human body, fall detection, palm, gesture, OCR, object detection, tracking, license plate.

### Nhóm nền tảng và dải file

| Nhóm file | Nền tảng/giao tiếp | Nội dung |
| --- | --- | --- |
| [01-17](<17. 17. Multi-master communication (purchased separately)/01_1.microbit_k230 color recognition.md>) | micro:bit + K230 | 17 bài từ `microbit_k230 color recognition` đến `microbit_k230 license plate recognition`; dùng micro:bit nhận kết quả vision/AI từ K230. |
| [18-34](<17. 17. Multi-master communication (purchased separately)/18_1.arduino_k230 color recognition.md>) | Arduino + K230 | 17 bài từ `arduino_k230 color recognition` đến `arduino_k230 license plate recognition`; Arduino đọc dữ liệu nhận dạng từ K230. |
| [35-51](<17. 17. Multi-master communication (purchased separately)/35_1.k230 color recognition.md>) | K230 communication group A | 17 bài chức năng K230, gồm color/barcode/QR/AprilTag/DM/face/gaze/AI detection/tracking/license plate. |
| [52-68](<17. 17. Multi-master communication (purchased separately)/52_1.k230 color recognition.md>) | K230 communication group B | Bộ 17 bài tương tự group A, dùng cho biến thể phần cứng/giao tiếp khác trong tài liệu. |
| [69-85](<17. 17. Multi-master communication (purchased separately)/69_1.k230 color recognition.md>) | K230 communication group C | Bộ 17 bài tương tự, có đủ chức năng từ color recognition tới license plate recognition. |
| [86-102](<17. 17. Multi-master communication (purchased separately)/86_1.k230 color recognition.md>) | K230 communication group D | Bộ 17 bài tương tự, dùng tra theo số file 86-102. |
| [103-119](<17. 17. Multi-master communication (purchased separately)/103_1.k230 color recognition.md>) | K230 communication group E | Bộ 17 bài tương tự, dùng tra theo số file 103-119. |
| [120-136](<17. 17. Multi-master communication (purchased separately)/120_1.k230 color recognition.md>) | K230 communication group F | Bộ 17 bài tương tự, dùng tra theo số file 120-136. |
| [137-153](<17. 17. Multi-master communication (purchased separately)/137_1. stm32_k230 color recognition.md>) | STM32 + K230 | 17 bài từ `stm32_k230 color recognition` đến `stm32_k230 license plate recognition`; STM32 nhận kết quả vision/AI từ K230. |

### Ma trận chức năng trong mỗi bộ 17 bài

| Số bài trong mỗi bộ | Chức năng | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- | --- |
| 1 | Color recognition | Nhận dạng màu/color blob và gửi kết quả màu/vị trí cho master controller. | color recognition, LAB threshold, blob, color result |
| 2 | Barcode recognition | Quét barcode/1D code và gửi payload/giá trị nhận dạng. | barcode, payload, 1D code, scan |
| 3 | QR code recognition | Quét QR code, giải mã nội dung và truyền chuỗi kết quả. | QR code, payload, two-dimensional code |
| 4 | AprilTag code recognition | Nhận dạng AprilTag marker, gửi ID/vị trí/góc hoặc thông tin marker. | AprilTag, marker ID, pose, fiducial |
| 5 | DM code recognition | Nhận dạng Data Matrix/DM code, gửi payload và thông tin mã. | DM code, Data Matrix, industrial code |
| 6 | Face detection | Phát hiện khuôn mặt và gửi bounding box/tọa độ. | face detection, bbox, face position |
| 7 | Gaze/looking direction | Nhận dạng hướng nhìn/hướng mặt và gửi hướng. | gaze direction, looking direction, head pose |
| 8 | Face recognition | Nhận dạng danh tính khuôn mặt đã đăng ký, gửi ID/name/score. | face recognition, identity, register face |
| 9 | Human body detection | Phát hiện người, gửi vị trí body box hoặc trạng thái có người. | human detection, person, body bbox |
| 10 | Fall detection | Phát hiện té ngã và gửi trạng thái cảnh báo. | fall detection, alarm, posture |
| 11 | Palm detection | Phát hiện lòng bàn tay, gửi tọa độ/box bàn tay. | palm detection, hand, bbox |
| 12 | Gesture recognition | Nhận dạng cử chỉ tay và gửi class gesture. | gesture, hand gesture, class |
| 13 | OCR character recognition | Nhận dạng ký tự/text và gửi chuỗi OCR. | OCR, character recognition, text |
| 14 | Object detection | Phát hiện vật thể bằng model AI, gửi class/box/confidence. | object detection, YOLO, class, confidence |
| 15 | Target tracking | Theo dõi mục tiêu và gửi tọa độ tracking qua thời gian. | target tracking, tracker, object position |
| 16 | Self-learning object recognition | Nhận dạng vật thể tự học/đã đăng ký, gửi ID/nhãn. | self-learning, object recognition, feature |
| 17 | License plate recognition | Phát hiện/nhận dạng biển số xe và gửi chuỗi biển số. | license plate, LPR, plate OCR |

## 18. Extension case (purchase separately)

Tóm tắt chương: các case mở rộng mua riêng, thường là demo tích hợp K230 với robot/servo/xe/thiết bị ngoại vi. Chương gồm nhóm case cơ bản 01-07 và hai bộ case hành động/tracking lặp lại 08-21, 22-35 cho biến thể phần cứng.

Từ khóa chung: extension case, purchase separately, tracking, visual tracking, color tracking, face tracking, palm tracking, target tracking, human body tracking, QR action, machine code tracking, autonomous avoid, license plate tracking, OCR action, fruit sorting, color response, road sign recognition.

| Bài/Nhóm | Tóm tắt nhanh | Từ khóa |
| --- | --- | --- |
| [1.Moving target control and automatic tracking system](<18. 18.Extension case (purchase separately)/01_1.Moving target control and automatic tracking system.md>) | Case điều khiển mục tiêu di chuyển và tự động tracking, kết hợp vision với cơ cấu điều khiển để bám mục tiêu. | moving target, automatic tracking, control system, tracking |
| [2.Human body recognition alarm](<18. 18.Extension case (purchase separately)/02_2.Human body recognition alarm.md>) | Phát hiện người và kích hoạt cảnh báo, dùng K230 làm cảm biến an ninh/AI alarm. | human body alarm, person detection, security, alert |
| [3.Gesture Recognition](<18. 18.Extension case (purchase separately)/03_3.Gesture Recognition.md>) | Case nhận dạng cử chỉ tay để điều khiển hoặc phản hồi hành động. | gesture recognition, hand control, action |
| [4.Rock Paper Scissors](<18. 18.Extension case (purchase separately)/04_4.Rock Paper Scissors.md>) | Case game đá/kéo/bao dùng nhận dạng gesture bàn tay. | rock paper scissors, gesture game, hand |
| [5.Fruit sorting](<18. 18.Extension case (purchase separately)/05_5.Fruit sorting.md>) | Case phân loại/sắp xếp trái cây bằng model AI và cơ cấu ngoại vi. | fruit sorting, classification, actuator, sorting |
| [6.Color Tracking](<18. 18.Extension case (purchase separately)/06_6.Color Tracking.md>) | Tracking vật thể theo màu, thường điều khiển servo/xe theo tâm vùng màu. | color tracking, color blob, servo, tracking |
| [7.Face Tracking](<18. 18.Extension case (purchase separately)/07_7.Face Tracking.md>) | Tracking khuôn mặt bằng face detection và điều khiển cơ cấu bám theo mặt. | face tracking, face detection, servo tracking |
| [8/22.Visual tracking](<18. 18.Extension case (purchase separately)/08_1.Visual tracking.md>) | Hai biến thể visual tracking tổng quát: theo dõi mục tiêu trong ảnh và xuất lệnh điều khiển. | visual tracking, target, control |
| [9/23.Color tracking](<18. 18.Extension case (purchase separately)/09_2.Color tracking.md>) | Hai biến thể tracking theo màu, dùng threshold màu để bám vật thể. | color tracking, threshold, blob center |
| [10/24.Color response](<18. 18.Extension case (purchase separately)/10_3.Color response.md>) | Case phản hồi theo màu nhận dạng được, ví dụ đổi hành động theo màu. | color response, color recognition, action |
| [11/25.Road sign recognition](<18. 18.Extension case (purchase separately)/11_4.Road sign recognition.md>) | Nhận dạng biển báo đường và thực hiện phản hồi/điều khiển theo class biển báo. | road sign recognition, traffic sign, action |
| [12/26.Machine code tracking](<18. 18.Extension case (purchase separately)/12_5.Machine code tracking.md>) | Tracking theo machine code/marker, dùng mã làm mục tiêu điều hướng hoặc căn chỉnh. | machine code tracking, marker, code tracking |
| [13/27.QR code recognition action](<18. 18.Extension case (purchase separately)/13_6.QR code recognition action.md>) | Nhận dạng QR code và thực hiện hành động dựa trên payload/kết quả mã. | QR action, QR payload, code recognition |
| [14/28.Autonomous avoid](<18. 18.Extension case (purchase separately)/14_7.Autonomous avoid.md>) | Case tự động tránh vật cản, kết hợp cảm nhận môi trường và điều khiển di chuyển. | autonomous avoid, obstacle avoidance, robot |
| [15/29.License plate tracking](<18. 18.Extension case (purchase separately)/15_8.License plate tracking.md>) | Tracking biển số xe hoặc vùng license plate bằng detection/recognition. | license plate tracking, LPR, vehicle |
| [16/30.Face tracking](<18. 18.Extension case (purchase separately)/16_9.Face tracking.md>) | Tracking khuôn mặt trong bộ extension, điều khiển hướng bám theo face box. | face tracking, face bbox, servo |
| [17/31.Gaze direction tracking](<18. 18.Extension case (purchase separately)/17_10.Gaze direction tracking.md>) | Tracking/phản hồi theo hướng nhìn hoặc hướng mặt. | gaze tracking, looking direction, head pose |
| [18/32.Palm tracking](<18. 18.Extension case (purchase separately)/18_11.Palm tracking.md>) | Tracking bàn tay/lòng bàn tay, dùng palm detection làm mục tiêu. | palm tracking, hand detection, gesture target |
| [19/33.Target tracking](<18. 18.Extension case (purchase separately)/19_12.Target tracking.md>) | Tracking mục tiêu tổng quát bằng AI/tracker, xuất vị trí để điều khiển. | target tracking, object tracking, bbox |
| [20/34.Human body tracking](<18. 18.Extension case (purchase separately)/20_13.Human body tracking.md>) | Tracking người/body, dùng human detection để bám theo người. | human body tracking, person tracking, body detection |
| [21/35.OCR character recognition action](<18. 18.Extension case (purchase separately)/21_14.OCR character recognition action.md>) | Nhận dạng ký tự OCR và thực hiện hành động theo text/class nhận được. | OCR action, character recognition, text command |
