# Detect-traffic-sign--yolov4
Link hướng dẫn : <a href= "https://www.miai.vn/2020/05/25/yolo-series-train-yolo-v4-train-tren-colab-chi-tiet-va-day-du-a-z/?fbclid=IwAR0krYX_ocEIXkQ0BTWN8GtXMtV0OWg56sQ5nqOePVdaHh2qiLRiDIPFRGE">MÌ AI</a>

### Bước 1: Lưu Darknet (<a href="https://github.com/AlexeyAB/darknet">AlexeyAB</a>) trong Google Drive
### Bước 2: Lablel data, sau đó để hết ảnh và label chung một thư mục data trong darknet
### Bước 3: Tải file "yolov4.custom.cfg" về máy và chỉnh sửa:

- Dòng 20: `max_batches= max( 'số class' *2000, 6000)`
- Dòng 22: `step = 80%,90% của max_batches`
- Thay thế toàn bộ các dòng `classes=80` thành `classes= 'số class'` 
( Dòng 970,1058, 1146)
- Thay thế toàn bộ các dòng `filters=255` thành `filters= ('số class"+5)*3`
( Dòng 963,1051,1139)
*Nếu bị out memory, chuyển `subdivisions`( Dòng 7) thành 32 hoặc 64,hoặc chuyển size ảnh xuống còn `width=416, height=416` (Dòng 8,9)
### Bước 4: Chỉnh sửa file Makefile:
- Dòng 1 sửa thành `GPU=1`
- Dòng 2 sửa thành `CUDNN=1`
- Dòng 4 sửa thành `OPENCV=1`

### Bước 5: Copy phần code trong file "Train model use Yolov4 in GG Colab.py" sang Google Colab và chạy
Tải các file lên Google Drive sau bước 2: Makefile vào mục darknet, yolov4-custom.cfg vào mục cfg Khi chạy lại thì chỉ cần chạy bước 7,10
(Sau khi chạy được 100 batches, file weights được lưu lại trong thư mục backup, lấy
file last.weights và tiếp tục train, tiến độ được lưu trong ảnh Capture.png)
