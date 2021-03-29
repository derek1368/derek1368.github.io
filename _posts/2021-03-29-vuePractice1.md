---
title:  "Vue.js 로그인 및 게시판 만들기(1)"
excerpt: "프로젝트 환경 설정 및 구성"

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

## Vue.js 프로젝트 생성
 1. vue create 명령어를 사용하여 프로젝트를 생성함 (vue2 에서는 init 사용)
 2. vue manually select project 와 default가 있으나, 자세히 설정하기 위해서 전자를 선택함

## ESLint 무시하는 법
 - ES는 Ecma Script를 뜻하며, Lint는 에러코드에 표시를 달아놓은것을 말함  
 즉, ESLint는 JavaScript 문법 에러를 표시하는 도구
 - 아래와 같이 vue.config.js 파일 생성 후 *overlay:false* 입력  
 
 ```javascript
  // /home/vue/vue-endgame/vue-til/vue.config.js
 
 module.exports = {
    devServer: {
        overlay: false
    }
 };
```
## Prettier 란?
 -  규격이 정해져 있는 것이 아닌 여러 살람들이 indent, 변수선언 등 코드 작성에 있어 서로 약속하여 개발하는 것  
 - /home/vue/vue-endgame/vue-til/.prettierrc 파일 생성  
 - eslintc.js 에서 설정 필요  
 - prettier 설정 후에는 자동으로 코드 정리를 VS Code에서 해줌