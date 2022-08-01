# traffic-sign-detection-in-viet
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
Bộ dataset được xây dựng bằng cách thu thập những đoạn video ngắn từ camera hành trình của oto lưu thông trên đường phố Việt Nam. Với một đoạn video, tôi tách một số frame nhất định. Sau đó, sử dụng một số tiêu chí để chọn ảnh vào dataset như: mỗi ảnh phải có ít nhất 1 biển báo, biển báo trong ảnh phải có thể nhận biết bằng mắt thường từ người lựa chọn,... </br>
Sự dụng [LabelImg]

[1]: https://github.com/heartexlabs/labelImg
