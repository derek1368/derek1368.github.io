---
title:  "JS Callback Function"
excerpt: "환경에 따라 다른 This 알아보기"

categories:
  - javascript
tags:
  - javascript
last_modified_at: 2021-04-22T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

## CallbackFunction
- 이벤트가 발생하거나 특정 시점에 도달했을때 시스템에서 호출 하는 함수
- 제어권을 넘기는 경우 3가지
1. 실행 시점 : setInterval
2. 인자 : forEach
3. this 

## CallbackFunction 특징 
- 다른함수(A)의 인자로 콜백함수(B)를 전달하면, A가 B의 제어권을 갖게 됨.
- A에 미리 정해놓은 방식에 따라 B를 호출
- 미리 정해좋은 방식이란 어떤 시점에 콜백을 호출할지, 인자에는 어떤 값을 지정할지, this에 무엇을 바인딩할지 등이다.
