---
title:  "JS 변수 Scope"
excerpt: "Js 변수에 대한 정의 및 스코프(var, let, const)"

categories:
  - front-end
tags:
  - front-end
last_modified_at: 2021-03-24T08:06:00-05:00
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---
## JS Scope란?
 - ES6 전에는 var 변수 키워드만 사용 가능, 그 후로 const, let 변수 키워드가 추가됨.  

## var, let, const 차이점
 - var: 함수레벨의 스코프, let/const: 블록레벨의 스코프
 - var로 선언한 변수는 선언 전에 사용해도 애러 나지 않지만, let/const의 경우에는 애러가 발생  

```javascript
function a() {
    console.log(num1); // undefined
    console.log(num2); // Uncaught ReferenceError: num2 is not defined
    console.log(num3); // Uncaught ReferenceError: num3 is not defined

    var num1 = 1;
    const num2 = 1;
    let num3 = 1;
}
```
 - var은 이미 선언된 이름과 같은 이름으로 변수를 재선언 해도 애러 나지않음, but let/const의 경우 같은 이름의 변수를 재선언 할시 애러 발생
 - var/let은 선언시 초긱값을 주지 않아도 되지만, const는 반드시 초기값 할당 필요
 - var/let은 값을 다시 할당 가능 하지만, const는 한번 할당 되면 변경 불가

 ```javascript
 // let
let a = 'test'
let a = 'test2' // Uncaught SyntaxError: Identifier 'a' has already been declared
a = 'test3'     // 가능

// const
const b = 'test'
const b = 'test2' // Uncaught SyntaxError: Identifier 'a' has already been declared
b = 'test3'    // Uncaught TypeError:Assignment to constant variable.
 ```
  ※ var는 function scope으로 hoisting이 일어남, let/const는 block scope으로 hoisting이 일어나지만 TDZ(Temporal Dead Zone)으로 인해 ReferenceError가 발생할 수 있음

## var 대신 let/const 사용해야 되는 이유
 - 함수레벨 스코프이기 때문에, 전역 변수를 남발할 가능성을 높임
 - 변수 중복 선언 허용하기 때문에 의도하지 않은 변수의 값의 변경이 일어날 가능성 큼
 - 변수 호이스팅(hoisting)이 일어나기때문에 변수를 선언하기 전에 참조 가능해짐
 - var키워드 생략을 허용하기 때문에, 암묵적 전역 변수를 양산할 가능성이 큼  

  ※ 대부분의 문제는 전역변수로 인해 발생  
    (복잡한 애플리케이션의 경우 유효범위가 넓어 어디까지 사용될 것인지 파악이 힘듬)   
  ※  값을 재할당 한다면 let, 재할당 안한다면 const를 사용하자!
