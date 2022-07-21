# GoogleNet~7.20 UPLOADING 

Going deeper with Convolutions
======

-2014년 Image Net 우승 Model

-inception layer 추가

Google Net 전체적인구조
=======================

![image](https://user-images.githubusercontent.com/104436260/179454596-ab4a46d9-baf7-4289-8b7c-7b9405fc3aea.png)

-1.input data size(color images) 224x224x3

-2.Convolution(output channels=64,filter size=7, stride=2,padding=3), output=112x112x64

-3.Maxpooling(3x3,stride=2), output=56x56x64->이미지 절반으로 줄어듬

-4.Convolution(output channel=192, filter size=3, stride=1, padding=1), output=56x56x192

-5.Maxpooling(3x3,stride=2), output=28x28x192->이미지 절반으로 줄어듬

inception Module
====================

inception Module이란 1x1, 3x3, 5x5, maxpooling을 병렬적으로 처리하여 연산량을 줄이고(계산되는 양) Feature Map을 추출해주는 층. 앞에 Convolution에 이어서 진행

![image](https://user-images.githubusercontent.com/104436260/179454452-ef6b51e1-d645-4053-83a1-ce208fc79e36.png)

Google Net에서는 Inception Module with dimension reductions 사용

-Inception(3a) input: 28x28x192, #1x1 Conv: 64 channels, #3x3 Conv reduce: 96 channels, 3x3 Conv: 128 channels, #5x5 reduce: 16 channels, 5x5: 32 channels, pooling: 32 channels, output=28x28x256

-Inception(3b) input: 28x28x256, #1x1 Conv: 128 channels, #3x3 Conv reduce: 128 channels, 3x3 Conv: 192 channels, #5x5 reduce: 32 channels, 5x5: 96 channels, pooling: 64 channels, output=28x28x480

-Maxpooling 3x3, stride=2-> out put: 14x14x480

-Inception(4a) input: 14x14x480, #1x1 Conv: 192 channels, #3x3 Conv reduce: 96 channels, 3x3 Conv: 208 channels, #5x5 reduce: 16 channels, 5x5: 48 channels, pooling: 64 channels, output=14x14x512

-Inception(4b) input: 14x14x512, , #1x1 Conv: 160 channels, #3x3 Conv reduce: 112 channels, 3x3 Conv: 224 channels, #5x5 reduce: 24 channels, 5x5: 64 channels, pooling: 64 channels, output=512

-Inception(4c) input: 14x14x512, , #1x1 Conv: 128 channels, #3x3 Conv reduce: 128 channels, 3x3 Conv: 256 channels, #5x5 reduce: 24 channels, 5x5: 64 channels, pooling: 64 channels, output=512

-Inception(4d) input: 14x14x528, , #1x1 Conv: 112 channels, #3x3 Conv reduce: 144 channels, 3x3 Conv: 288 channels, #5x5 reduce: 32 channels, 5x5: 64 channels, pooling: 64 channels, output=528

-Inception(4e) input: 14x14x528, #1x1 Conv: 256 channels, #3x3 Conv reduce: 160 channels, 3x3 Conv: 320 channels, #5x5 reduce: 32 channels, 5x5: 128 channels, pooling: 128 channels, output=832

-MaxPooling 3x3, stride=2

-Inception(5a) input=7x7x832, #1x1 Conv: 256 channels, #3x3 Conv reduce: 160 channels, 3x3 Conv: 320 channels, #5x5 reduce: 32 channels, 5x5: 128 channels, pooling: 128 channels, output=832

-Inception(5b) input=7x7x832, #1x1 Conv: 384 channels, #3x3 Conv reduce: 192 channels, 3x3 Conv: 384 channels, #5x5 reduce: 48 channels, 5x5: 128 channels, pooling: 128 channels, output=1024

-Avg Pool 7x7, stride=1 output=1x1x1024

-drop out(0.4)->linear->softmax

Pytorch에서 Google Net 구현하기
======
Dataset: STL-10 dataset, image size=96x96x3->Google net에 맞게 Resize필요 224x224x3 size로

분석환경: Jupyter lab

분석 Flow

-Transform 객체 생성

-Dataset Load

-Dataset EDA

-Built Model

-Train Model

-Test Model


Transform 객체 생성& Dataset Load & Dataset EDA
=====

![image](https://user-images.githubusercontent.com/104436260/180103614-3a0fc17d-7e17-4bea-b0bf-8b5586b7f269.png)

![image](https://user-images.githubusercontent.com/104436260/180103690-e6f28a6e-5d41-48bf-9251-d41e5cd95b01.png)

Built Model & Train Model 
======

1.Convolution 정의



2.Inception Block 정의(Convolution Module사용)



