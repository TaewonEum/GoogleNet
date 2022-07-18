# GoogleNet

Going deeper with Convolutions
======

-2014년 Image Net 우승 Model

-inception layer 추가

Google Net 전체적인구조
=======================

-1.input data size(color images) 224x224x3

-2.Convolution(output channels=64,filter size=7, stride=2,padding=3), output=112x112x64

-3.Maxpooling(3x3,stride=2), output=56x56x64->이미지 절반으로 줄어듬

-4.Convolution(output channel=192, filter size=3, stride=1, padding=1), output=56x56x192

-5.Maxpooling(3x3,stride=2), output=28x28x192->이미지 절반으로 줄어듬

inception Module
====================

inception Module이란 1x1, 3x3, 5x5, maxpooling을 병렬적으로 처리하여 연산량을 줄이고 Feature Map을 추출해주는 층. 앞에 Convolution에 이어서 진행
