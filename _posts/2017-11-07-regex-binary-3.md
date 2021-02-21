---
layout: post
title: Regex for binary multiple of 3 (Java)
tags: [Algorithm, Java, Regex]
---

코드워즈의 kyu 4짜리 문제.


>In this kata, your task is to create a regular expression capable of evaluating binary strings (strings with only 1s and 0s) and determining whether the given string represents a number divisible by 3.


>Take into account that:
> - An empty string might be evaluated to true (it's not going to be tested, so you don't need to worry about it - unless you want)
> - The input should consist only of binary digits - no spaces, other digits, alphanumeric characters, etc.
> - There might be leading 0s.



뒤에다 갖다붙여도 3의 배수임을 보장하는 binary string이 들어왔는지 정규식으로 확인하도록 하는 문제이다.


```
multipleof3Regex.test('000') should be true

multipleof3Regex.test('001') should be false

multipleof3Regex.test('011') should be true

multipleof3Regex.test('110') should be true

multipleof3Regex.test(' abc ') should be false
```

![FSM](https://i.stack.imgur.com/TuwGt.png)

케케묵은 전통적인 알고리즘 문제라고 하는데 처음 봤다.




다음과 같은 유한 상태 기계를 설명할 때 자주 쓰이는 문제인데

```
A를 mod 3 = 0 (3의 배수)
B를 mod 3 = 1 (3의 배수 +1)
C를 mod 3 = 2 (3의 배수 +2)
```


라고 할때, b 비트가 뒤로 들어갔을 때 상태를 설명한다.

```
A일 때 b = 0 추가: 3n에 2를 곱하므로 3n'(A)
A일 때 b = 1 추가: 3n에 2를 곱하고 1을 더함, 3n'+1(B)
B일 때 b = 0 추가: 3n+1에 2를 곱함. 3n'+2(C)
B일 때 b = 1 추가: 3n+1에 2를 곱하고 1을 더함. 3n'(A)
C일 때 b = 0 추가: 3n+2에 2를 곱함. 3n'+1(B)
C일 때 b = 1 추가: 3n+2에 2를 곱하고 1을 더함. 3n'+2(C)
```


이렇게 서로 FSM으로 나타낼 수 있다.


정규식은 [다음과 같이 만든다.](https://stackoverflow.com/questions/867279/regular-expression-to-define-some-binary-sequence)

```
A = 1B + 0A
B = 1A + 0C
C = 1C + 0B
```

```
C = 1*0B // Eliminate recursion
B = 1A + 0(1*0B)
B = 01*0B + 1A
B = (01*0)*1A // Eliminate recursion

A = 1(01*0)*1A + 0A
A = (1(01*0)*1 + 0)A
A = (1(01*0)*1 + 0)* // Eliminate recursion
```


그래서 결과는 `/^(1(01*0)*1|0)+$/`.




[다른 방식](https://stackoverflow.com/questions/7974655/regex-for-binary-multiple-of-3)으로 풀면

```
The simplest one, using only state A, is:
0*

Including state B:
0*(11)*0*

Including state C:
0*(1(01*0)*1)*0*

And include the fact that after going back to state A, the whole process can be started again.

0*((1(01*0)*1)*0*)*

Using some basic regex rules, this simplifies to
(1(01*0)*1|0)*
```


아무튼 결론은 


```java
import java.util.regex.Pattern;

public class BinaryRegexp {
  public static Pattern multipleOf3() {

    return Pattern.compile("^(0|1(01*0)*1)*$");

  }
}
```
