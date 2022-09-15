---
layout: post
title: Find Angle MBC | Hackerrank
tags: [Algorithm, Python]
author: amaruak00
excerpt_separator: <!--more-->
---

![triangle](https://s3.amazonaws.com/hr-challenge-images/9668/1440151155-10b2b748ee-rsz_1438840048-2cf71ed69d-findangle.png)

쎄타 구하는 문제

```python

import math 

#빗변 외 입력 받음
AB, BC = int(input()), int(input())

#빗변 구하기
AC = math.hypot(AB, BC)

#역코사인 함수로 쎄타값 구하기(∠MBC = ∠ACB)
dACB = math.acos(BC/AC)
dACB = round(math.degrees(dACB)) #각도값으로 환산


print(f'{dACB}{chr(176)}')

```
