# OpenCV Basics C++

* Read an image
```c++ 
cv::Mat img=cv::imread("path/to/image.jpg",0); 
```
* Read an PNG image
```c++
cv::Mat img=cv::imread("path/to/image.png",-1); 
```
* Show Image
```c++ 
cv::imshow("windowname",img);
```
* Write Image
```c++
cv::imwrite("path/to/store/image.jpg",img);
```
* Split Image
```c++ 
cv::Mat img_channels[3];
cv::split(img,img_channels);

cv::imshow("Blue",img_channels[0]);
cv::imshow("Green",img_channels[1]);
cv::imshow("Red",img_channels[2]);
```
* Merge into an Image and get Mask channel
```c++
cv::Mat channels[4];
cv::Mat mask;
cv::Mat image_without_background;
cv::split(png_img,channels);

cv::merge(channels,3,image_without_background);
mask= channels[3];
```
* Image size
```c++
img.size()
```
* Modify Pixel in 3 channels at same time
```c++
img.at<uchar>(0,0)=200;
```
* Modify Pixel by channel 
```c++ 
img.at<cv::Vec3b>(0,0)= cv::Vec3b(0,255,255);
```
* Modify a group of pixels (from row 6 to 9 and from column 0 to 3 set in white color)
```c++
img(cv::Range(6,9),cv::Range(0,3)).setTo(cv::Vec3b(255,255,255));
```
