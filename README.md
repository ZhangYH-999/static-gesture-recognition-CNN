# Gesture-Recognition Lightweight CNN
CNN for static gesture recognition base on Computer Vision



## Dataset

Dataset from Ankara Ayranci Anadolu, Turkey, and 10 types of gestures in total.

<img src="README.assets/image-20220929122701663.png" alt="image-20220929122701663" style="zoom: 67%;" />



## Data Processing

### Skin colour detection

A wide variety of skin colour detection algorithms, including elliptical skin colour detection models, Cr component of YCrCb colour space + Otsu threshold segmentation, YCrCb colour space based Cr, Cb range filtering method, HSV colour space based H, S, V range filtering method, etc. After testing, YCrCb + Otus has better result,  so YCrCb + Otus will be used in the following models.

<img src="README.assets/image-20220929130355897.png" alt="image-20220929130355897" style="zoom: 50%;" />

<img src="README.assets/image-20220929123244972.png" alt="image-20220929123244972" style="zoom:80%;" />



### Edge detection

Comparison of the effects of seven different edge detection operators (Roberts, Sobel, Prewitt, Laplace, Scharr, Canny, LoG) after Otsu thresholding segmentation of the Cr component of YCrCb. In the following models, Canny will be used.

<img src="README.assets/image-20220929130440673.png" alt="image-20220929130440673" style="zoom:67%;" />

### Other image Processing

including image morphology adjustment, image smoothing, noise reduction etc.



## Lightweight CNN models

Based on LetNet-5, our lightweight CNN model has the following structure, it mainly contains 2 Convolutional layers and Max pooling layers, followed by 3 Dense layers. The Dropout layer is added to prevent overfitting of the model.

![image-20220929130332044](README.assets/image-20220929130332044.png)



Part of result of different edge detection methods base on this CNN model:

|        methods         | traning set | testing set |
| :--------------------: | :---------: | :---------: |
| YCrCb + Otus & Roberts |   99.94%    |   93.22%    |
|  YCrCb + Otus & Sobel  |   99.62%    |   93.70%    |
| YCrCb + Otus & Prewitt |   99.54%    |   93.71%    |
|  YCrCb + Otus & Canny  |   99.27%    |   94.18%    |



<img src="README.assets/image-20220929133704444.png" alt="image-20220929133704444" style="zoom: 67%;" /><img src="README.assets/image-20220929133804556.png" alt="image-20220929133804556" style="zoom: 67%;" />

After hyper-parameterisation, the final test set is accurate to **95.15%**.



​                                                   <img src="README.assets/image-20220929134724798.png" alt="image-20220929134724798" style="zoom: 25%;" /><img src="README.assets/image-20220929134827867.png" alt="image-20220929134827867" style="zoom: 25%;" /><img src="README.assets/image-20220929134917173.png" alt="image-20220929134917173" style="zoom:25%;" />



## Document Intro

`capture_video.py`: run the program in real-time recognition  with `gesture_model.h5`

`run_model.py`: train the CNN model

