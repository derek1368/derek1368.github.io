---
title:  "CSS Postion 속성"
excerpt: "Position 속성 종류 및 성격"

categories:
  - css
tags:
  - css
last_modified_at: 2021-05-14T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

## Position
- 태그들의 위치를 결정해주는 CSS라고 말할 수 있음.  
1. static
2. relative
3. absolute
4. fixed

### 1. static (기본값)
- position 속성의 기본 값으로 따로 명시 하지않으면 static이 적용 됨.
- static 속성상황 에서는 z-index, top, bottom, left, right이 아무런 효과를 발휘하지 못함.  
> 차례대로 왼쪽부터 오른쪽, 위에서 아래로 태그들의 위치가 쌓임  
>(HTML의 일반적인 흐름)

### 2. relative
- static 속성과 같이 일반적 흐름으로 배치 되나, z-index, top, bottom 등과 같은 속성을 사용하기 위한다면 relative(상대적인)을 사용해야됨.
> static과 같이 왼쪽부터 오른쪽, 위에서 아래로 태그들의 위치를 쌓음  
> `상대적인 위치 배정 태그를 사용하고 싶다면` relative사용!!!

### 3. absolute
- absolute는 elelment 문서의 흐름을 따르지않고, 가장 가까운 위치에 있는 조상 elelment에 대해 상대적 위치로 배치 됨.
- 조상 element가 없다면 본문(body)를 기준 삼고 페이지 스크롤에 따라 움직임.
- absolute가 되면 div여도 width는 더 이상 100%가 아님

1. 아래 코드에서  #absolute는 조상에 postion이 명시 안되있어 body가 기준.
2. #child의 경우 조상 태그에 postion:relative가 명시되어 그것이 기준.

```html
<body>
  <div>
    <div id="absolute">absolute</div>
  </div>
  <div id="parent">
    <div id="child">children</div>
  </div>
</body>

<style>
#absolute {
  background: yellow;
  position: absolute;
  right: 0;
}

#parent {
  position: relative;
  width: 100px;
  height: 100px;
  background: skyblue;
}

#child {
  position: absolute;
  right: 0;
}
</style>
```

### 4. fixed
- fixed는 뷰포트(viewPort)를 기준으로 항상 한 위치에 해당 태그가 고정이 됨
- absolute 처럼 div는 width: 100%가 아님.
- 네이게이션 메뉴 등과 같이 스크롤을 내려도 고정된 곳에 위치가 필요할때 사용
> ※ 뷰포트(viewport): 웹페이지가 사용자에게 보여지는 영역

