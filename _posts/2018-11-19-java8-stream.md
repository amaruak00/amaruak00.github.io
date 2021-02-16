---
layout: post
title: Java8 Stream - 각종 int Array 를 다루는 Stream 기법들
tags: [Java, Java8]
author: amaruak00
excerpt_separator: <!--more-->
---

```java
static void countApplesAndOranges(int s, int t, int a, int b, int[] apples, int[] oranges){
    System.out.println(IntStream.range(0, apples.length).map(i -> apples[i]+a).filter(i -> s <= i && i <= t).count());
    System.out.println(IntStream.range(0, oranges.length).map(i -> oranges[i]+b).filter(i -> s <= i && i <= t).count());
}//end of function
```
IntStream으로 int array를 다시 만들어준 후, filter로 거른 후 count해줌(long 반환)

```java
int min = (int)Arrays.stream(a).max().getAsInt();
int max = (int)Arrays.stream(b).min().getAsInt();
```
max/min 값 추출

```java
aliceScoreList.stream().mapToInt(i->i).toArray();
```
List<Integer> 를 int[]로 바꾸기

```java 
int[] array = IntStream.of(scores).distinct().toArray();
```
int[] 배열에서 중복을 제거하고 다시  int[] 배열로 전환
