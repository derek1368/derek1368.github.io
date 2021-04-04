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
