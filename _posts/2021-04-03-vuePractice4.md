---
title:  "Vue.js 로그인 및 게시판 만들기(4)"
excerpt: "회원가입 및 로그인/로그아웃 화면 개발 (vuex, token)"

categories:
  - vue.js
tags:
  - vue.js
last_modified_at: 2021-04-03T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

## Vuex의 정의
- vuex는 상태관리 라이브러리  
- 여러 컴포넌트들 간에 데이터를 관리 하기 위한 상태 관리 패턴이자 라이브러리  


## Vuex 구성
- state: 컴포넌트 간에 공유하는 데이터
- getters: computed와 같은 기능을 가지고 있으며, 가독성을 높힘  
- mutations: state로직을 변경시키며, method에 등록(동기적 로직)
- actions: mutations를 실행시키는 역할(비동기적 로직)  

## Vuex 등록 방법
- npm i vuex로 설치함  
- src/store/index.js에서 관리함  

```jsx
import Vue from 'vue';
import Vuex from 'vuex';

Vue.use(Vuex);

export default new Vuex.Store({
    state: {
        username : '',
    }
});
```  
- main.js에 vuex import 및 선언   

```jsx
import Vue from 'vue';
import App from './App.vue';
import router from '@/routes/index';
import store from '@/store/index';   //vuex 선언

Vue.config.productionTip = false;

new Vue({
  render: h => h(App),
  store,                       //vuex 선언
  router,
}).$mount('#app');
``` 

## Token을 이용한 API 인증처리

### JWT(Jason WEB Token) : API Key
- JSON으로 전자 서명을 하여 URL-safe 문ㄴ자열로 표현 한 것  
- 로그인-> 토큰값 받음 -> 받은 토큰값(Authorization) 확인 버튼 눌러 인증 -> 이후 쿼리 날림
- Axios 처리시, 고유 hearder의 authorization 활용 가능

```jsx
import axios from 'axios';
import store from '../store';     //store import

const instance = axios.create({
  baseURL: process.env.VUE_APP_API_URL,
  headers: {
    Authorization: store.state.token,   //store에 있는 Token 사용
  },
});

``` 
- 고유 토큰을 Axios에 넘기기 위해 vuex 활용  
```jsx
export default new Vuex.Store({
  state: {
    token: '',
  },
  mutations: {
    setToken(state, token) {
      state.token = token;
    },
  }
``` 

- 받은 토큰을 Vuex로 보내는 법
```jsx
async submitForm() {
      try {
        // 비즈니스 로직
        const userData = {
          username: this.username,
          password: this.password,
        };
        const { data } = await loginUser(userData);
        console.log(data.token);
        this.$store.commit('setToken', data.token); // token을 mutation으로 보냄
        this.$store.commit('setUsername', data.user.username);
        this.$router.push('/main');
``` 

## InterCeptors((https://github.com/axios/axios#interceptors))
- 요청과 응답을 컴포넌트 단에 처리하기 전에 추가 로직을 추가 할 수 있는 것

```jsx
// Add a request interceptor
axios.interceptors.request.use(function (config) {
    // Do something before request is sent
    return config;
  }, function (error) {
    // Do something with request error
    return Promise.reject(error);
  });

// Add a response interceptor
axios.interceptors.response.use(function (response) {
    // Any status code that lie within the range of 2xx cause this function to trigger
    // Do something with response data
    return response;
  }, function (error) {
    // Any status codes that falls outside the range of 2xx cause this function to trigger
    // Do something with response error
    return Promise.reject(error);
  });
``` 
