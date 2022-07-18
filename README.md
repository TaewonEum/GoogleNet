# GoogleNet

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

-inception(3a) input: 28x28x192, #1x1 Conv: 64 channels, #3x3 Conv reduce: 96 channels, 3x3 Conv: 128 channels, #5x5 reduce: 16 channels, 5x5: 32 channels, pooling: 32 channel
