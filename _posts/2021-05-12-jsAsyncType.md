---
title:  "JS 비동기처리 이해와 종류"
excerpt: "비동기 처리 이해(callBack, Promise, Async&Await)"

categories:
  - javascript
tags:
  - javascript
last_modified_at: 2021-05-12T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

## 비동기처리란?
- 비동기처리란 순서에 상관없이 코드의 연산이 실행되는 것을 말한다.
- 동기처리의 경우 순차적으로 코드의 연산이 진행되며, 이전에 연산이 끝나지 않았으면 다음 연산이 이전 연산이 끝날때까지 기다렸다가 실행됨.

## 비동기처리 종류

### 1. jQuery의 Ajax(Asynchronous JavaScript and XML) 통신
```javascript
function getData() {
  var sampleData;
  $.get('https://example.com/account/c3', function(response){
    sampleData = response;
  });
  return sampleData;
}

console.log(getData());    //undefined

```
$.get은 Ajax를 말하며, 'https://exmpale.com/account/c3' 에다 HTTP get 요청을 날리며, 이때 응답받은 데이터는 response에 담아 SampleData에 전달해줌.  
그럼 밑에 찍혀있는 console.log에 해당 값이 나와야 하지만 undefined가 나옴. 그 이유는 비동기 처리이기 때문에 ajax 활동을 기다려주지 않고 초기 아무것도 없는  
sampleData 값이 출력 되기 때문이다.

> 특정 로직의 연산이 끝날때까지 기다려주지 않고 바로 이후에 명시되어있는 코드를 먼저 처리하는 것을 `비동기처리`라고 말함 


### 2. setTimeout()
```javascript
console.log('first');

setTimeout(function(){
  console.log('second');
}, 5000);

cosole.log('third');

```
위의 코드에서 first, second, third 라고 나올거라 예상하지만, second가 5초후에 실행되게 되면서 아래와 같은 순서로 로그가 찍힘.  
`first, third, second`

## 콜백함수(CallbackFunction) 사용하여 비동기처리 방식 해결
- 이벤트가 발생하거나 특정 시점에 도달했을때 시스템에서 호출 하는 함수
- 제어권을 넘기는 경우 3가지
1. 실행 시점 : setInterval
2. 인자 : forEach
3. this 
- ajax 통신 코드를 콜백으로 개선한 코드  

```javascript
function getData(callbackFunc) {
	$.get('https://example.com/account/c3', function(response) {
		callbackFunc(response); // 서버에서 받은 데이터 response를 callbackFunc() 함수에 넘겨줌
	});
}

getData(function(sampleData) {
	console.log(sampleData); // $.get()의 response 값이 sampleData에 전달됨
});
```

## Promise 정의 및 필요이유
- 자바스크립트 비동기 처리에 사용되는 객체
>필요이유: http API 사용하여 서버에 데이터를 요청하게 되는데, 이때 데이터가 넘어오기도 전에 데이터를 다 받은것 처럼 화면에 표시하면 빈화면이 뜸. 이런 현상을 방지하고자 Promise 사용
- 위의 callback함수를 promise로 바꾸면 아래와 같이 변경됨

```javascript
function getData(callback) {
  // new Promise() 추가
  return new Promise(function(resolve, reject) {
    $.get('https://example.com/account/c3', function(response) {
      // 데이터를 받으면 resolve() 호출
      resolve(response);
    });
  });
}

// getData()의 실행이 끝나면 호출되는 then()
getData().then(function(smpleData) {
  // resolve()의 결과 값이 여기로 전달됨
  console.log(sampleData); // $.get()의 reponse 값이 sampleData에 전달됨
});
```

## ※ Promise 3가지 상태(state)  
- pending(대기) : 비동기 처리 로직이 아직 완료되지 않은 상태
- Fullfiled(이행) : 비동기 처리가 완료되어 프로미스가 결과 값을 반환해준 상태
- Rejected(실패) : 비동기 처리가 실패하거나 오류가 발생한 상태

### 1. Pending(대기)
- `new Promise()` 메서드를 호출하면 대기상태가 됨
- 이때 콜백함수를 선언할 수 있고, 콜백함수의 인자는 reslove, reject 임

### 2. Fullfiled(이행)
- 여기서 콜백함수 인자 reslove를 실행하면 이행 상태가 됨
- 그리고 then()을 이용하여 처리 결과값을 받을 수 있음

### 3. Rejected(실패)
- 콜백함수 reject를 호출하면 실패 상태가 됨
- 그리고 실패 이유를 catch()로 받을 수 있음

## Promise 예제
```javascript
// Promise 예제
function getData() {
  return new Promise(function(resolve, reject) {
    $.get('url 주소/products/1', function(response) {
      if (response) {
        resolve(response);
      }
      reject(new Error("Request is failed"));
    });
  });
}

// 위 $.get() 호출 결과에 따라 'response' 또는 'Error' 출력
getData().then(function(data) {
  console.log(data); // response 값 출력
}).catch(function(err) {
  console.error(err); // Error 출력
});
```
## Promise Chaining
- 여러개의 프로미스를 연결하여 사용 가능함  
```javascript
new Promise(function(resolve, reject){
  setTimeout(function() {
    resolve(1);
  }, 2000);
})
.then(function(result) {
  console.log(result); // 1
  return result + 10;
})
.then(function(result) {
  console.log(result); // 11
  return result + 20;
})
.then(function(result) {
  console.log(result); // 31
});
```
## Async & Await???
- 자바스크립트 비동기처리 패턴 중 가장 최그 나온 문법임
- 비동기 처리방식인 콜백 함수와 프로미스 단점을 보완하고 가독성 높은 코드 작성을 도와줌
