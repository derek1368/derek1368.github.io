---
title:  "스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술[4]"
excerpt: "스프링 빈과 의존관계"

categories:
  - spring
tags:
  - spring
last_modified_at: 2021-08-1T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---
## 강의명
스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술  

## 스프링 빈을 등록하는 방법 2가지
 1. Component 스캔과 자동 의존관계 설정
 2. 자바코드로 직접 스프링 빈 등록

## 1. Component 스캔과 자동 의존관계 설정
- `@Component` 어노테이션이 있으면 스프링 빈으로 자동 등록됨
- `@Controller` 컨트롤러가 스프링 빈으로 자동 등록된 이유는 컴포넌트 스캔 때문 
- `@AutoWired`가 있으면 스프링이 스프링컨테이너와 연결해줌  

- `@Component`를 포함하는 다음 애노테이션도 스프링 빈으로 자동 등록됨 
   (@Controller, @Service, @Repository)  
![](/assets/images/JavaSpring/scriptController.png){: .align-center} 
![](/assets/images/JavaSpring/springContainer.png){: .align-center} 

![](/assets/images/JavaSpring/springBeanRegister.png){: .align-center} 


## 2. 자바코드로 직접 스프링 빈 등록
- SpringConfig 파일에 @Configuration을 직접 작성함
- @Bean을 활용하여 Servie와 Repository를 입력
- @Controller의 경우 위의 Component 스캔의 경우와 같이 직접 입력 필요
![](/assets/images/JavaSpring/springRegManually.png){: .align-center} 



