ROV_Tracking-v1
Autonomous Underwater Vehicle (AUV) system integrated with Computer Vision for real-time object detection and tracking.

1. System Architecture
The system employs a distributed control architecture between two processing units:
High-level Control (Nvidia Jetson Nano): Executes Python-based scripts, running the YOLOv8 model for object detection and managing the Graphical User Interface (GUI).
Low-level Control (ESP32): Programmed in C, responsible for sensor data acquisition, PID control loops, and motor PWM signal generation.
Communication Protocol: UART (Jetson Nano <-> ESP32).

2. Hardware Specifications
Thruster Configuration: 06 Thrusters (04 vertical thrusters for depth and stability control, 02 horizontal thrusters for surge and yaw).
Integrated Sensors:
Pressure Sensor: MS5837 (High resolution, utilized for depth hold).
IMU: MPU9250 (9-axis, utilized for Heading Hold and attitude stabilization).
Imaging: USB/CSI Camera interfaced with Jetson Nano.

3. Operating Modes
Manual Mode:
Direct control of surge (forward/backward) and yaw (rotation) at constant velocity.
Automatic Heading Hold: The system maintains the current orientation once control input is released.

Auto Mode (AI Tracking):
Detection Model: YOLOv8 trained on a custom dataset (optimized for blue and orange bottles).
Tracking Logic: Calculates the centroid offset of the target relative to the frame center to command ROV movement, ensuring the target remains centered.
Safety Logic: Automated Station Keeping (hovering) upon loss of target visibility.

5. Tech Stack
Firmware: C (ESP32).
Software: Python (GUI, AI Inference).
AI Framework: Ultralytics YOLOv8.
Communication: I2C (Sensors), UART (Inter-board).

Hệ thống tàu lặn tự hành (ROV) tích hợp thị giác máy tính để nhận diện và bám mục tiêu theo thời gian thực.

1. Kiến trúc hệ thống (System Architecture)
Hệ thống sử dụng cấu trúc điều khiển phân tán giữa hai khối xử lý:
High-level Control (Jetson Nano): Chạy Python, thực thi mô hình YOLOv8 để phát hiện vật thể và quản lý giao diện người dùng (GUI).
Low-level Control (ESP32): Lập trình bằng ngôn ngữ C, chịu trách nhiệm đọc dữ liệu cảm biến, tính toán PID và xuất tín hiệu điều khiển động cơ.
Giao thức truyền thông: UART (Jetson Nano <-> ESP32).

2. Thông số phần cứng (Hardware Specifications)
Cấu hình động cơ: 06 Thrusters (04 động cơ đặt đứng điều khiển cao độ/cân bằng, 02 động cơ đặt ngang điều khiển hướng di chuyển).
Cảm biến tích hợp:
Áp suất: MS5837 (Độ phân giải cao, dùng để giữ độ sâu ổn định).
IMU: MPU9250 (9-axis, dùng để duy trì góc hướng - Heading Hold).
Xử lý hình ảnh: Camera kết nối Jetson Nano.

3. Chế độ vận hành (Operating Modes)
Manual Mode:
Điều khiển di chuyển tiến/lùi, xoay trái/phải với vận tốc không đổi.
Hệ thống tự động duy trì góc hướng (Heading) tại vị trí cuối cùng khi ngừng điều khiển.

Auto Mode (AI Tracking):
Mô hình nhận diện: YOLOv8 được huấn luyện với dataset tùy chỉnh (chai nước màu xanh và màu cam).
Logic bám mục tiêu: Tính toán sai lệch tọa độ tâm vật thể trên khung hình để điều khiển ROV di chuyển sao cho vật thể luôn nằm ở tâm màn hình.
Safety logic: Tự động dừng tại chỗ (Station Keeping) khi mất dấu mục tiêu.

4. Công nghệ sử dụng (Tech Stack)
Firmware: C (ESP32).
Software: Python (GUI, AI Processing).
AI Framework: Ultralytics YOLOv8.
Sensors Library: MS5837, MPU9250 (I2C communication).
