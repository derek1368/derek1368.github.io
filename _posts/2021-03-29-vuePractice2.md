---
title:  "Vue.js 로그인 및 게시판 만들기(2)"
excerpt: "라우터&컴포넌트 설계"

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

## 화면 구성
화면은 아래와같이 구성 될 것이며, 라우터를 통해 각 화면(컴퍼넌트) 간에 관계를 연결 해야됨.  
 - 로그인 화면
 - 회원가입 화면
 - 게시판 메인화면  
 - 게시판 추가/수정/삭제 화면  

## 라우터(Router)설치 및 조정
 - 라우터(Router) : Vue에서 화면간 이동을 지원하는 공식 라이브러리를 말함  
 
  ```javascript
 <router-link to="URL값"> : 페이지 이동 태그, 화면에선 <a> 태그로 치환됨  
 <router-view> : 페이지 표시 태그 , 변경된 URL에 따라 해당 컴포넌트를 뿌려주는 영역
```
 
 - npm i vue-router를 이용하여 라우터를 vue.js 프로젝트에 설지
 - /src/folder에 routes 폴터 생성 후 index.js 작성하여 라우터를 별도로 관리해줌

 ```javascript
// /home/vue/vue-endgame/vue-til/src/folder/routes/index.js
import Vue from 'vue';
import VueRouter from 'vue-router';
import LoginPage from  '@/views/LoginPage.vue';
import SignupPage from '@/views/SignupPage.vue';

Vue.use(VueRouter);

export default new VueRouter({
    routes: [
        {
            path: '/login',
            component: LoginPage,
        },
        {
            path: '/signup',
            component: SignupPage,
        }
    ],
});

```
- main.js에 router 설정 필요

```jsx
import Vue from "vue";
import App from "./App.vue";
import router from '@/routes/index.js';

Vue.config.productionTip = false;

new Vue({
  render: h => h(App),
  router,
}).$mount("#app");
```

## Code Splitting 없는 페이지 라우터 처리 (History)
- Code Splitting: Javascript File을 필요할때 마다 그때그때 불러오는 것을 말함 (Dynamic import 기능)
- History: URL의 # 부분 없애줌, (단, 배포할 때, 서버마다 조정이 필요 vue공식사이트 참고)
- 없는페이지 라우터처리 : *를 붙여 진행

```jsx
import Vue from 'vue';
import VueRouter from 'vue-router';
//import LoginPage from '@/views/LoginPage.vue';
//import SignupPage from '@/views/SignupPage.vue';

Vue.use(VueRouter);

export default new VueRouter({
  mode: 'history',
  routes: [
    {
      path: '/',
      redirect: '/login',
    },
    {
      path: '/login',
      component: () => import('@/views/LoginPage.vue'), //Code Splitting
      //component: LoginPage,
    },
    {
      path: '/signup',
      component: () => import('@/views/SignupPage.vue'), //Code Splitting
      //component: SignupPage,
    },
    {
      path: '*',
      component: () => import('@/views/NotFoundPage.vue'), // Non Found Page 
    },
  ],
});
```