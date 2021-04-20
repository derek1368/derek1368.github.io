---
title:  "JS Execution Context"
excerpt: "실행 맥락/환경/상황"

categories:
  - javascript
tags:
  - javascript
last_modified_at: 2021-04-20T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

## Execution Context(실행 환경/문맥/맥락)
- 건축적 사전정의: 역사적, 문화적, 지리적인 배경이 되는 조건등을 가리킴
- 프로그래밍적 의미: Execution(실행)에 필요한 코드 흐름상의 배경이 되는 조건/환경

> Execution: 동일한 조건/환경을 지니는 코드뭉치를 -> 함수 or 전역공간
> Context: 실행할 때 필요한 조건/환경정보  
>`즉, 함수를 실행할 때 필요한 환경정보를 담은 객체`  

### Execution Context 구조
- Variable Environment
- Lexical Environment 
- this

### LexicalEnvironment(어휘적인/사전적 환경)
- EnvironmentRecord(현재 문맥의 식별자 정보) : Hoisting
- OuterEnveironmentReference(현재 문맥에 관련있는 외부 식별자 정보) : Scope Chain

### Hoisting
- 식별자 정보를 끌어올리다
- 함수선언문의 경우 함수 전체를 끓어올림

### Execution Context 예시
- Call Stack : 현재 어떤 함수가 동작하고 있는지, 다음에 어떤함수가 호출되어야하는지 등을 제어하는 자료구조  
- 전역 컨텍스트 -> Outer -> Inner -> Inner제거 -> Outer제거 -> 전역컨텍스트

```javascript
var a = 1;
function outer() {
  console.log(a);     //1 -> 1
 
  function inner() {
    console.log(a);  // 2 -> undefined
    var a = 3 ;
  }

  inner();

  console.log(a);    // 3  -> 1
}

outer();
console.log(a);     // 4 -> 1
```

- Call Stack : 현재 어떤 함수가 동작하고 있는지, 다음에 어떤함수가 호출되어야하는지 등을 제어하는 자료구조
- 전역 컨텍스트 -> Outer -> Inner -> Inner제거 -> Outer제거 -> 전역컨텍스트
