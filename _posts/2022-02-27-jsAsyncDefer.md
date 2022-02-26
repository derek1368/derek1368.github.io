---
title:  "Async VS Defer"
excerpt: "js 개념정리"

categories:
  - javascript
tags:
  - javascript
last_modified_at: 2022-02-27T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---
## HTML 안에서 JS 효율적으로 배치방식
### 1. head 안에 위치 
 - js file이 크고 인터넷이 느리다면 브라우저의 과부하가옴 

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="main.js"></script>
</head>
<body>
    
</body>
</html>
```

### 2. body 맨 끝에 위치
 - html이 parsing(그려지는것을 의미)하고 서버로부터 js file을 받아와 속도가 빨라짐
 - 단점은 해당 페이지가 js에 의존적인 페이지라면, 사용자가 정상적인 페이지를 받아올수 없음

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div></div>
    <script src="main.js"></script>
</body>
</html>
```

### 3. head + async
 - 병렬로 main.js를 받기 다운받는 속도가 빠름, but DOM요소를 컨트롤할때 HTML이 완료되지않으면 문제가 생길 위험 있음 

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script async src="main.js"></script>
</head>
<body>
    
</body>
</html>

```
### 4. head + defer (가장 좋은 방법)
 - 병렬로 main.js를 받고 실행은 HTML이 전부 Parsing되었을때 실행됨

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script defer src="main.js"></script>
</head>
<body>
    
</body>
</html>
```
※ 'use strict'; 를 JS를 작성할떄 맨 위에 명시해주면 좋음  
(JS는 Flexible하기 때문에 떄로 이해할 수 없는상황이 일어날수 있음, 이를 방지하기 위함임)

