---
title:  "스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술[2]"
excerpt: "스프링 웹개발 기초"

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

## 정적 컨텐츠
- src/main/resources/static 경로에 정적컨텐츠가 존재함
- 원하는 파일을 넣으면 웹브라우저에서 확인 가능  
![](/assets/images/JavaSpring/staticImage.png){: .align-center}  
> `※ 1번의 스프링 컨테이너에 컨트롤러가 없기 때문에 2번의 resources 경로를 찾아 정적 컨텐츠를 보여줌`

## MVC와 템플릿 엔진 (JSP / PHP)
- MVC : Model, View, Controller
- Model : 디비와같은 리소스를 주로 담당
- View: 화면을 그려주는것을 담당
- Controller: 비지니스로직을 담당

### Controller
- src/main/java/contorller/ 경로에 컨트롤러 내용을 넣을 수 있음
- src/main/resources/templetes/ 경로에 동적 View 내용을 넣을 수 있음
![](/assets/images/JavaSpring/MVCImage.png){: .align-center} 
  
## API (Vue.js / React)
- String 뿐만아니라 객체를 반환해줌
- HttpMessageConverter를 통해서 Jason 방식으로 반환해줌
- View 화면 없이 HttpResponse에 값을 넣어 반환해줌
- JAVA bean 표준방식 : getter, setter (property 접근방식)
![](/assets/images/JavaSpring/APIImage.png){: .align-center} 
