---
layout: post
title: DOTA(Dataset for Object deTection in Aerial Images)
tags: [PapersWithCode, Dataset]
---

[Paperswithcode 원문](https://paperswithcode.com/dataset/dota) 

### 개요

- DOTA는 객체 탐지 기술을 위한 대용량 항공 이미지 데이터셋
- 항공 이미지의 객체 탐지를 위한 개발 및 평가에 활용
- (v1.0 기준) `2,806`개의 항공 이미지 수록
- 각각의 이미지는 `800x800` 부터 `4000x4000`의 크기를 가지며, 다양한 스케일, 방향 및 모양을 보여주는 객체를 포함
- `15개`의 객체 카테고리
- 답지는 총 `188,282`개의 인스턴스를 포함하며, `x1, y1, x2, y2, x3, y3, x4, y4`, `카테고리`, `난이도` 가 레이블링 되어있다



[홈페이지](https://captain-whu.github.io/DOTA/)

### 예시 이미지

![Image](https://paperswithcode.com/media/datasets/DOTA-0000000287-8115825a_h3m67GA.jpg)

![Image1](https://captain-whu.github.io/DOTA/images/plane1.jpg)
![Image2](https://captain-whu.github.io/DOTA/images/rotaterec.jpg)
![Image3](https://captain-whu.github.io/DOTA/images/baseball2.jpg)



### 관련 논문

[Paperswithcode](https://paperswithcode.com/paper/towards-multi-class-object-detection-in)에는 2019년 발표된 Towards Multi-class Object Detection in Unconstrained Remote Sensing Imagery만 올라와있으며, `mAP` 수치로 `68.16%`를 기록하여 글로벌 1위인 상태다. 코드는 따로 없네..

[논문 링크](https://arxiv.org/pdf/1807.02700v3.pdf)



### 참고

비슷한 데이터셋으로 [xView](https://paperswithcode.com/dataset/xview)가 있다.

[공식 홈페이지](http://xviewdataset.org/#dataset) 등록해야 다운로드 받을 수 있는 모양

![xView](https://paperswithcode.com/media/datasets/example6.jpg)