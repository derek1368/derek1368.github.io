---
title:  "스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술[3]"
excerpt: "회원관리 예제"

categories:
  - Back-end
tags:
  - Back-end
last_modified_at: 2021-07-25T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---
## 강의명
스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술  

## 비지니스 요구사항 정리

### 일반적인 웹 애플리케이션 계층 구조
![](/assets/images/JavaSpring/springSturcture.png){: .align-center} 

### 클래스 의존 관계
![](/assets/images/JavaSpring/springClass.png){: .align-center} 

## 회원 도메인과 리포지토리 만들기
## 회원 리포지토리 테스트 케이스 작성
- 개발한 기능을 실행해서 테스트 할 때 자바의 main 메서드를 통해 실행하거나, 웹 애플리케이션의 컨트롤를 통해서 해당 기능을 실행
- 이러한 방법은 준비하고 실행하는데 오래 걸리고, 반복 실행하기 어렵고 여러 테스트를 한번에 실행하기 어려운 단점 가지고 있음
- JUnit이라는 프레임워크로 테스트를 실행해서 이런 문제 해결 가능
- 테스트 주도개발: 테스트케이스를 만들고 구현케이스를 만드는 법
- 테스트는 given, when, then 의 패턴으로 하면 편함

## 회원 서비스 개발


