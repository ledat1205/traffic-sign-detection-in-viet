# traffic-sign-detection-in-viet

### Tổng quan </br>

Trong project này, với mục tiêu nhận diện 5 loại biển báo ở đường phố Việt Nam bao gồm: 
<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Vietnam_road_sign_P102.svg/180px-Vietnam_road_sign_P102.svg.png" width="50" title="No entry">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/22/Vietnam_road_sign_P131a.svg/180px-Vietnam_road_sign_P131a.svg.png" width="50" title="No parking">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/Vietnam_road_sign_I423a.svg/180px-Vietnam_road_sign_I423a.svg.png" width="50" title="Pedestrian crossing">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Vietnam_road_sign_R302a.svg/900px-Vietnam_road_sign_R302a.svg.png" width="50" title="No parking">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Vietnam_road_sign_W207b.svg/180px-Vietnam_road_sign_W207b.svg.png" width="50" title="No parking">  
</p>
Các biển báo không thuộc 5 lớp biển trên sẽ được xét vào lớp biển khác.</br>
Tôi áp dụng transfer learning trên 2 mô hình pre-train là RetinaNet và Yolov5 trên bộ dataset tự xây dựng.</br>

### Xây dựng dataset

Bộ dataset được xây dựng bằng cách thu thập những đoạn video ngắn từ camera hành trình của oto lưu thông trên đường phố Việt Nam. Với một đoạn video, tôi tách một số frame nhất định. Sau đó, sử dụng một số tiêu chí để chọn ảnh vào dataset như: mỗi ảnh phải có ít nhất 1 biển báo, biển báo trong ảnh phải có thể nhận biết bằng mắt thường từ người lựa chọn,... 
</br>

Sử dụng [LabelImg][1] để gán nhãn cho ảnh theo chuẩn yolo sau đó thông kê ta có chi tiêt số lượng cho mỗi class:
Cấm đi ngược chiều: 1716 </br>
Hướng đi phải vòng sang phải: 1069 </br>
Giao nhau với đường không ưu tiên: 362 </br>
Người đi bộ: 593 </br>
Cấm đỗ xe: 678 </br>
Biển khác: 2183 </br>

Mội vài ảnh minh họa dataset: 
<p align="center">
   <img src="https://user-images.githubusercontent.com/58855136/182258171-7a5a30ae-2f36-4f3f-98d5-673d3a14f399.jpg" width="450">
   <img src="https://user-images.githubusercontent.com/58855136/182258455-da4c404c-0afb-4846-8702-9bf5f5f28921.jpg" width="450">
</p>

### Quá trình training và test
Áp dụng transfer learning 2 mô hình pre-train [yolov5][2] và [RetinaNet][3]. Chi tiết về cách train trên custom dataset đều được hướng dẫn trong repo chính của 2 model. Với mỗi mô hình luôn train thử trên 3 epoch, sau đó mới thực hiện quá trình training. Quá trình train sẽ được dừng loại dựa trên các số liệu của tập val như:
loss, mAP.
#### RetinaNet

<p align="center">
   <img src="https://user-images.githubusercontent.com/58855136/182259855-25283471-4c7f-4d4e-8a8e-bed9aceb00b9.png" width="650">
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/58855136/182259877-f1ef471a-3309-4507-bb25-72852b45c2a6.png" width="250">
</p>

#### Yolov5
<p align="center">
   <img src="https://user-images.githubusercontent.com/58855136/182260077-77446382-ea5b-4f75-872d-05e1124eff5a.png" width="800">
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/58855136/182260084-7cc0ba12-46fc-4343-b95e-41e4c452c06a.png" width="400">
</p>


### Kết quả 
|           | mAP @.5 | mAP @.5:.95 |
|-----------|---------|-------------|
| RetinaNet | 0.619   | 0.444       |
| Yolov5    | 0.968   | 0.679       |




[1]: https://github.com/heartexlabs/labelImg
[2]: https://github.com/ultralytics/yolov5
[3]: https://github.com/kadirtereci/Keras-retinanet-Training-on-custom-datasets-for-Object-Detection--
