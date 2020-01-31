# OpenCV Basics C++

* Read an image
```c++ 
cv::Mat img=cv::imread("path/to/image.jpg",0); 
```
* Read a PNG image
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
* Image size
```c++
img.size()
```
### Basic Image Operations

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

* create a black image 100 x 200 / 3 Channel
```c++
cv::Mat img= cv::Mat(100,200,CV_8UC3,cv::Scalar(0,0,0));
```

* create an image from other image
```c++
cv::Mat gray_img= cv::Mat(other_img.size(),other_img.type(), cv::Scalar(100,100,100));
```

* Cropping image
```c++
cropped_img=img(cv::Range(40,300),cv::Range(180,320))
```

* Copy Image
```c++ 
cv::Mat clone= img.clone();
```
* Copy/insert One Image into another Image (in left-top corner)
```c++ 
int Height= image_to_inset.size().height;
int Width= image_to_inset.size().width;
image_to_inset.copyTo(image_receiver(cv::Range(0,Height),cv::Range(0,Width)));
```

* resize down Image to 300 x 200 
```c++
/**
* INTER_NEAREST: nearest neighbor interpolation  / less expensive, no good result
* INTER_LINEAR:  bilinear interpolation  / more expensive, better result
* INTER_CUBIC:   bicubic interpolation
* 
*/
int resize_down_width = 300;
int resize_down_height = 200;
cv::Mat scaled_down;
cv::resize(source_image,scaled_down,cv::Size(resize_down_width,resize_down_height),0,0,cv::INTER_LINEAR);
```

* resize up Image 
```c++
cv::Mat scaled_up;
double scale_up_x = 1.5;
double scale_up_y = 1.5;
cv::resize(source_img,scaled_up,cv::Size(),scale_up_x,scale_up_y,cv::INTER_LINEAR);
```