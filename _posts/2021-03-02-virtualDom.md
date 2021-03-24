---
title:  "DOM VS Virtual DOM"
excerpt: "DOM(Document Object Model)과 Virtual DOM의 정의 및 차이"

categories:
  - vue.js
tags:
  - vue.js
last_modified_at: 2021-03-02T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

## DOM(Document Object Model) 정의
 - DOM은 웹 페이지(HTML,XML, etc)에 접근하기 위한 일종의 인터페이스로 정의 됨
 - 여러 페이지의 콘텐츠 및 구조, 스타일을 읽고 조작 할 수 있도록 API를 제공함
 - DOM은 노드 트리로 표현 됨

## 웹 페이지가 만들어지는 과정
 1. 브라우저는 읽어들이 문서를 파싱하여 최종적으로 어떤 내용을 페이지에 렌더링할 지 결정 -> "렌더트리 생성"
 2. 브라우저는 해당 렌더링을 수행

※ 렌더트리 : DOM - HTML 요소의 구조화된 표현 / CSSOM(Cascading Style Sheets Object Model) - 스타일 정보의 구조화된 표현

## DOM의 한계
 - 대용량 앱플리케이션(FaceBook, etc) 등장으로 DOM에 접근하여 변경된 다량의 데이터를 변화를 주는데 성능상 이슈 발생
 - Repaint 하는데 시간이 허비되어 느려진다고 볼 수 있음

## Virthal DOM 정의
 - DOM을 추상화한 가상의 객체, 다시말해 실제 DOM에 접근하여 조작하는 대신 이를 추상화하여 자바스크립트 객체를 구성하여 사용(실제 DOM의 가벼운 사본) 
 - Vue.js, React가 일종의 Virtual DOM의 역할을 함 

## Virtual DOM 필요성
 - DOM의 상태를 메모리에 저장하고 변경 전과 변경 후를 비교한 뒤 변경 된 내용만 반영 => 성능을 향상 시켜줌

[Virtual DOM 참고영상](https://www.youtube.com/watch?v=BYbgopx44vo)



