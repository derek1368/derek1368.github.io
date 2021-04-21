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
- 식별자 정보(선언)를 끌어올리다라는 뜻을 내포
- 함수 안에 있는 선언들을 모두 끌어올려서 해당 함수 유효범위의 최상단에 선언 되어짐

#### 1. Function Declaration (함수선언문)
- 일반적인 프로그래밍 언어에서의 함수선언과 비슷한 형식  

```javascript
function functionDeclaration() {
  return '함수선언식';
}
functionDeclaration();
```

#### 2. Function Expression (함수표현식)
- 유연한 자바스크립트 언어의 특징을 활용 

```javascript
var funcExpression = function () {
    return '함수표현식';
}
funcExpression(); 
```

#### 3. 함수 선언문과 표현식 차이
- 함수 선언문 호이스팅 영향 받음, but 표현식은 호이스팅 영향 안받음 

```javascript
// 실행 전
logMessage();
sumNumbers();

function logMessage() {
  return 'worked';
}

var sumNumbers = function () {
  return 10 + 20;
};
```
- Hoisting 영향으로 아래와 같이 코드가 변경됨  

```javascript
// 실행 시
function logMessage() {
  return 'worked';
}

var sumNumbers;

logMessage(); // 'worked'
sumNumbers(); // Uncaught TypeError: sumNumbers is not a function

sumNumbers = function () {
  return 10 + 20;
};
```
> `함수표현식이 호이스팅에 영향을 받지 않는다`는 특징 외에도 함수 선언식 보다 유용하게 쓰임  
> `클로저사용, 콜백으로 사용(다른 함수의 인자로 넘김 가능)`

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
