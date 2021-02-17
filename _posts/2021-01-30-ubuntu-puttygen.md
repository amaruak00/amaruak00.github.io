---
layout: post
title: Ubuntu 20.04에서 Puttygen 사용하기
tags: [Ubuntu, Putty]
---

Amazon EC2 서비스를 이용할 때 private key 파일을 사용한다.

putty을 이용해서 SSH로 접속하기 위해서는 `*.pem` 파일을 `*.ppk` 파일로  Convert 해야 한다.



 1. 터미널로 접속해서 putty를 설치한다.   
(우분투 소프트웨어 센터에서 putty를 설치할 수도 있다.)
```
$ apt-get install putty-tools
```

 2. `*.pem` 파일이 있는 디렉토리로 이동해서 아래 명령을 실행한다.
```
$ puttygen *.pem -o *.ppk
```

 3. 명령 실행 후 *.pem 파일이 있는 디렉토리에 *.ppk 파일이 생성된다.