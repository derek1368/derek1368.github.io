---
title:  "스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술[1]"
excerpt: "Project 세팅법"

categories:
  - spring
tags:
  - spring
last_modified_at: 2021-07-24T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---
## 강의명
스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술  

## 프로젝트 환경설정
1. Java 11 설치 권장
2. IDE: IntelliJ or Ecrips
3. http://start.spring.io 접속 후 프로젝트 생성
4. project: Grandle Project / Java / Spring Boot: 2.3.1 / Project
5. dependencies : Spring Web / Thymeleaf 추가
6. 다운로드 후 IntelliJ를 통해 build.gradle 파일로 프로젝트 시작
7. src/main/java/HelloSpringApplication 파일의 main 함수 컴파일
8. localhost:8080 로 접속하여 errorPage 뜨면 성공! (아무 파일이 없기 때문에)

## 라이브러리 살펴보기
- build.gradle 에 설정햇던 라이브러리들이 명시되어있음
- Gradle은 의존관계가 있는 라이브러리들을 자동으로 함께 다운로드함

### 스프링 부트 라이브러리
- spring-boot-starter-web  
  - spring-boot-starter-tomcat: 톰캣(웹서버)  
  - spring-webmvc: 스프링 웹 MVC

- spring-boot-starter-thymeleaf: 타임리프 템플릿 엔진(View)
- spring-boot-starter(공통): 스프링 부트 + 스프링코어 + 로깅
  - spring-boot
   - spring-core
  - spring-boot-starter-logging
   - logback, slf4j
   
### 테스트 라이브러리
- spring-boot-starter-test
 - junit: 테스트 프레임워크
 - mockito: 목 라이브러리
 - assertj: 테스트코드를 좀 더 편하게 작성하게 도와주는 라이브러리
 - spring-test: 스프링 통합테스트 지원
 
## View 환경설정
- rsources/static/index.html 경로에 html 내용이 view의 메인을 구성

### 스프링 부트가 제공하는 welcome page 기능(정적인 웹)
- static/index.html을 올려두면 welcome page 기능을 제공함
- docs.spring.io 참조

### thymeleaf 템플릿 엔진(동적인 웹) 
- thymeleaf 공식 사이트 참조
- 스프링 공스 튜토리얼도 있음

## 빌드하고 실행하기
1. ./gradlew build
2. cd build/libs
3. java -jar hello-spring-0.0.1-SNAPSHOT.jar
4. 실행 확인
5. 빌드가 잘 안되었으면 ./gradlew clean build

