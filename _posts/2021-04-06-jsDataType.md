---
title:  "JS 데이터 타입(DataType)"
excerpt: "PrimitiveType, ReferenceType"

categories:
  - javascript
tags:
  - javascript
last_modified_at: 2021-04-06T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

## 데이터 타입
### 기본형(Primitive Type)
객체가 아닌 데이터 유형을 말함  
- Number
- String
- Boolean
- null
- undefined
- Symbol(ES6에서 추가)
> `말 그대로 기본 데이터 값을 그대로 할당 한다라는 뜻을 가지고 있음.`  
> 메모리에 기본형 데이터 값 자체를 보관하여 불변적임  
> 같은 데이터는 하나의 메모리사용(재사용)  

![기본형이미지](/assets/images/js/primitiveType.jpg){: .align-right}    

- 위의 이미지와 같이 기본형에서는 메모리에 직접 데이터 값을 할당함
- a -> @313, b-> @314, c-> @315
- c경우 c=b; 로 인해 @315를 b의 false 값에 매핑
- c는 이후 20으로 재 선언 하여 @315에 20으로 변경 됨


### 참조형(Reference Type)
참조형은 변수에 직접 할당하지 않고 데이터의 주소를 지정함
- Object (Array, Function, RegExp)
- Array
- Function
- RegExp(문자열에 나타나는 특정문자조합과 대응 시키는 패턴)
- Map,set,WeakMap ...(ES6에서 추가)
> `참조형 데이터는 값 자체를 보관하는게 아닌, 지정된 주소값을 할당(참조)함`   
> 기본형 데이터의 집합이라고 말 할 수 있음  

![참조형이미지](/assets/images/js/referenceType.jpg){: .align-right}  

- 값이 지정된 주소값을 할당함
- @1185 데이터 공간확보, 그후 객체 속 프로퍼티에 대한 공간 재 확보
- 객체의 프로퍼티 명과 주소를 매칭하고, 1184에 데이터를 할당 함

