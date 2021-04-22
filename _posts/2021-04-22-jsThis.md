---
title:  "JS This"
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

## thisBinding
- 실행컨텍스트가 활성화 되는 순간에 this가 binding
- 함수가 실행 될때 this가 바인딩 됨

## this가 Binding 되는 시점
1. 전역공간에서
2. 함수 호출시
3. 메소드 호출시
4. callback 호출시
5. 생성자함수 호출시

### 1. 전역공간에서
- `this는 전역객체 (window/global)`

### 2. 함수 호출시
- `this는 전역객체 (window/global)`

### 3. 매소드 호출시
- `this는 매소드 호출 주체 (메소드명 앞)`  

```javascript
var a = {
  b: function() {
    console.log(this);    // this -> a
  }
}
a.b();
```

### 4. callback 호출시
- `this는 기본적으로 함수의 this와 같다 (전역객체)`
- 제어권을 가진 함수가 callback의 this를 명시한 경우엔 그것을 따름
- 개발자가 this를 바인딩한채로 callback을 넘기면 그것을 따름

### 5. 생성자함수 호출시
- `this는 인스턴스`  

```javascript
function person(n,a) {
  this.name = n ;
  this.age = a;
}

var sun = new person ('태양', 30);
console.log(sun);
```

