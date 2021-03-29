---
title:  "Vue.js 로그인 및 게시판 만들기(3)"
excerpt: "회원가입 및 로그인/로그아웃 화면 개발 (Axios, Error처리, 로그인유효성, Vuex, Token값)"

categories:
  - vue.js
tags:
  - vue.js
last_modified_at: 2021-03-29T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

## 회원가입 페이지

### 비동기 처리(Axios)
- 회원가입을 위해 서버로 데이터 송수신이 필요, 이때 axios를 사용함 
- Jquery에서는 주로 ajax기법을 이용하여 주로 비동기 처리를 해왔음
- axios는 ajax 라이브러리 중 하나의 기법으로, 웹 브라우저에서 데이터를 조회할 때 화면 전체를 새로고침 하고 싶지 않아 사용함.
- axios를 사용하기 위해서는 npm i axios를 입력하여, 먼저 설치 필요
- 보통은 api/index.js에 공통 axios 서비스를 작성하여 코드 중복을 막음.

```jsx
// src/api/index.js 에 공통 Axios 작성

const instance = axios.create({
  baseURL: process.env.VUE_APP_API_URL,
});

function registerUser(userData) {
  return instance.post('signup', userData);
}
export { registerUser };
```
- 이후, 아래와 같이 axios 서비스를 쓰고자하는 커포넌트 파일에 impot 시킨 후 사용 하면됨

```jsx
// Axios 쓰는 js파일에 선헌 후 이용

import { registerUser } from '@/api/index';
export default {
  data() {
    return {
      username: '',
      password: '',
      nickname: '',
      logMessage: '',
    };
  },
  methods: {
    async submitForm() {    
      console.log('clicked');
      const userData = {
        username: this.username,
        password: this.password,
        nickname: this.nickname,
      };
      const { data } = await registerUser(userData);  //axios 서비스가 포함된 registerUser 함수를 불러옴 
      console.log(data.username);
      this.logMessage = `${data.username}님이 가입됨`;
      this.initForm();
    },
``` 

### Error 처리
- Aysnc Await 경우 Try Catch 로 애러 처리함
- 옳바른 로직과 애러가 공통으로 어떤 함수 쓸 시, finally 사용

```jsx
async submitForm() {
      try {   //옳바른 비지니스 로직
        const userData = {
          username: this.username,
          password: this.password,
        };
        const { data } = await loginUser(userData);
        console.log(data.user.username);
        this.logMessage = `${data.user.username} 님 환영합니다.`;
      } catch (error) {  //애러 처리
        console.log(error.response.data);
        this.logMessage = error.response.data;
      } finally {   //공통 함수 사용
        this.initForm();
      }
    },
```
### Login Validation(유효성 검사)
 - 공통으로 쓰는 Formatter와 같은 내용들은 utils에 따로 작성 하면 관리하기 쉬움  
 -  validation 내용도 공통으로 많이 쓰일 수 있으므로, src/utils/index.js에 작성

```jsx
// 이메일 유효성 함수

function validateEmail(email) {
  const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
  return re.test(String(email).toLowerCase());
}

export { validateEmail };
```

- 유효성 함수를 쓰고자 하는 컴포넌트에 import 시킴
- 대체로, 유효성 검사와 같이 데이터에 대해 즉각적으로 변화가 필요한 경우, computed 속성을 이용

```jsx
<template>
  <form @submit.prevent="submitForm">
    <div>
      <label for="username">id : </label>
      <input id="username" type="text" v-model="username" />
    </div>
    <div>
      <label for="password">pw : </label>
      <input id="password" type="text" v-model="password" />
    </div>
    <button :disabled="!isUsernameValid || !password" type="submit"> //button disable check
      Login
    </button>
    <p>{{ logMessage }}</p>
  </form>
</template>

<script>
import { loginUser } from '@/api/index';
import { validateEmail } from '@/utils/validation';
export default {
  data() {
    return {
      username: '',
      password: '',
      logMessage: '',
    };
  },
  computed: {
    isUsernameValid() {
      return validateEmail(this.username); //computed로 True, false 유효성검사
    },
  },

```