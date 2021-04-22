---
title:  "JS Closure"
excerpt: "Closure"

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

## Closure 정의
- 함수와 그함수가 선언될 당시의 Lecxical Environemnt의 결합

### LexicalEnvironment(어휘적인/사전적 환경)
- EnvironmentRecord(현재 문맥의 식별자 정보) : Hoisting
- OuterEnveironmentReference(현재 문맥에 관련있는 외부 식별자 정보) : Scope Chain

> 즉, `실행컨택스트 A`에서 선언한 `변수`를 `내부함수B`가 `접근`할 경우에만 발생하는 특수한 현상  
> 클로저는 OuterEnvironmentRefernce(ScopeChain)의 영향을 받는다.  
  
```javascript
var outer = function () {
  var a = 1;
  var inner = function(){
    return ++a;
  };
  return inner;
}
var outer2 = outer();
console.log(outer2());  // 2
console.log(outer2());  // 3
```  
  
>`컨텍스트 A`에서 선언한 `변수 a`를 참조하는 `내부함수B`를 `A의 외부로 전달`할 경우,`A가 종료된 이후`에도 `a가 사라지지않는` 현상
> 즉, 지역변수가 함수 종류 후에도 사라지지 않는 지역변수를 만들 수 있다.