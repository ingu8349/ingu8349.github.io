---
layout: post
title:  "Javascript es6 arrow-function event listener constructor"
date:   2023-04-01 18:35:03 +0900
categories: Javascript es6  event listener와 constructor arrow-function 
---

Javascript event listener와 constructor 그리고 arrow function

## this는 이전 포스트에 이어 3번째로  constructor 안에서 쓰면 constructor로 새로생성되는 오브젝트를 뜻한다.

```javascript
var something = {}

function machine (){
    this.name = "Kim" 
    //  새로 생성되는 오브젝트, 인스턴스 instance라고 한다.
}

var object = new machine();
console.log(object) // 는 machine {name:"kim"} 이 뜬다
```
## Eventlistener 안에서 쓰면 this는 e.currentTarget이라는 의미다.

```javascript
document.getElementById('버튼').addEventListener('click', function(e){
  console.log(this)
});
```
this를 소환하면 이것은 바로 e.currentTarget이라는 뜻과 똑같은 의미다.
e.currentTarget은 지금 이벤트가 동작하는 곳을 뜻합니다. 

그리고 2번째 주제 

## arrow-function
자주 혼나는 분야인데, 공부하다 강의 주제가 Arrow function은 function을 대체하는 신문법이 아님 이라는 말이
너무 와닿았다.

정리해보면 

### Arrow function 문법 

기존 
```javascript
function a(){
  //어쩌구
}
```
라는게 기존의 알던 우리가 함수를 쓰던 방법인데,

ES6 문법 이후부터는 자바스크립트에서 함수를 만들 수 있는 문법이 새롭게 하나 등장한게 arrow function이다.

```javascript
var a = () => {
  //어쩌구
}
``` 
형태는 이러하다.

그렇다면 왜쓰나?

1. 함수 본연의 기능을 아주 잘 표현하는 문법
   arrow function을 사용하면 함수 본연의 입출력기능을 아주 직관적으로 잘 표현해준다.
2. 소괄호 생략이 가능  
   파라미터가 하나라면 소괄호를 생략가능합니다.
```javascript
var double = x => { return x * 2 }
```
3. 중괄호 생략이 가능. 
   중괄호 안에 return 한줄 뿐이라면 중괄호와 return도 생략가능
```javascript
var double = x => x * 2 ;
```

### arrow function을 쓰면 내부에서 this값을 쓸 때 밖에 있던 this값을 그대로 사용
- arrow function은 어디서 쓰든간에 내부의 this 값을 변화시키지 않는다.

예시
```javascript
var 오브젝트1 = {
  함수 : function(){ console.log(this) }
}

오브젝트1.함수()
```
이러면 console은 오브젝트1을 찍는데,

arrow function을 쓰면
```javascript
var 오브젝트1 = {
  함수 : () => { console.log(this) }
}

오브젝트1.함수()
```
window라는게 출력

### this값은 함수를 만나면 항상 변하는데 arrow function 안에서는 변하지 않고 밖에 있던 this를 그대로 쓰기 때문에

## 일반 function과 용도가 완전 같지 않기 때문에 일반 function을 항상 대체할 수 있는 문법이 아니기 때문에 그것만 주의합시다!!