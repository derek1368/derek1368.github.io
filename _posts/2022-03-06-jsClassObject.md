---
title:  "Class VS Object"
excerpt: "js 클래스와 오브잭트의 차이점"

categories:
  - javascript
tags:
  - javascript
last_modified_at: 2022-03-06T08:06:00-05:00
toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---
## Class 및 Object 차이점
### Class (붕어빵의 틀)
 - 일종의 틀(template)과 같은 청사진을 class라 부름
 - 정의는 한번만 선언됨
 - 데이터는 포함하고 있지않음

### Object (붕어빵)
 - 한개의 class의 예시
 - 여러번 선언이 됨
 - 데이터를 포함

## 개체지향에 대한 개념

### 1. Class 선언 및 Object 생성

```js
//Class 선언
Person {
    //constructor
    constructor(name, age) { // 생성자
        //fields
        this.name = name;
        this.age =age;
    }

    //methods
    speak() {
        console.log(`${this.name}: hello!`);
    }
}
// Object 생성
const derek = new Person('derek', 30);
console.log(derek.name);
console.log(derek.age);
derek.speak();
```

### 2. Getter/Setter
- 내부 변수명에 _ 추가해야함 (eg. this._age)  

```js
class User {
    constructor(firstName, lastName, age) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
    get age() {    // 값 리턴
        return this._age;     
    }

    set age(value) {    //  값 설정
        this._age = value < 0 ? 0: value;
    }
}
const user1= new User('Steve', 'job', -1);
console.log(user1.age);
```

### 상속 & 다형성
 - 'extends'를 포함하여 부모 Class의 내용을 상속 받을수 있음  
 - 부모 Class에서 상속 받은 내용을 특정하게 변경 가능, 이를 'overriding' 이라고함  
 - 'super'를 함수나 변수에 붙여 부모clss 내용을 overriding 하더라도 공통으로 받을 수 있음

```js
class Shape {
   constructor(width, height, color) {
       this.width = width;
       this.height = height;
       this.color = color;
   } 

   draw() {
       console.log(`drawing ${this.color} color of `);
   }
   getArea() {
       return this.width * this.height;
   }
}

class Reteangle extends Shape {}
class Triangle extends Shape {
    draw() {
        super.draw();     //부모 draw의 값을 받기위해서 super 사용
        console.log('🛑');
    }
    getArea() {
        return this.width*this.height/2   //overriding
    }
}
const rectangle = new Reteangle(20,20,'blue');
rectangle.draw();
console.log(rectangle.getArea());
const triangle = new Triangle(20, 20, 'red');
triangle.draw();
console.log(triangle.getArea());
```
### instanceof
- 부모와 자식 class가 맞는지 체킹할 수 있음  

```js
console.log(rectangle instanceof Reteangle); //True
console.log(triangle instanceof Reteangle);  //Flase
console.log(triangle instanceof Triangle);//True
console.log(rectangle instanceof Shape);//True
console.log(rectangle instanceof Object);//True
```