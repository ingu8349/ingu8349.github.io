---
layout: post
title:  "JAVASCRIPT의 시작"
date:   2023-02-05 18:35:03 +0900
categories: Javascript
---

Javascript의 시작

html의 기초는 있으니 바로 시작,

```javascript

<h1> //태그가 있다고 가정해봤을 때

<h1 id="hello">안녕하세요<h1>
//의 innerHTML을 바꾸는 방법은 script안에 document.getElementById("hello") = "안녕"
// 이라고 쓰면 되는데 쉬게 .을 ~의 라고 생각하면 좋다.

document의 id로 선택한 element의~ html을 안녕을 바꿔라 라고 이해하면 되겠다.
```

## 여기서 = 등호는 같다! 가 아닌 오른쪽 거를 왼쪽에 넣어주세요 라고 알아야한다.

document.getElementById,? = ? 여기서 ?에 어떤걸 넣느냐에 따라 활용법이 무궁무진하다.

- document.getElementById('hello').style.color = "red" 로 색을 바꾼다던가
- 이미지의 경우 document.getElementById('hello').src = 로 이미지 주소를 바꿀 수 도 있다.

```javascript
//onClick 매서드 안에도 
<button onclick="document.getElementById('hello').style.color = 'red';"></button>
```
이런식으로 활용할 수 있다.


그런데 코드마다 저렇게 길~게 써서 해버리면, 코드 읽기도 어려워지고, 코드도 길어지고, 여간 어려운게 아니다.

그래서 써야하는게 바로 function 함수이다
```javascript
document.getElementById('hello').style.color = 'red'; 
//이런 긴 글을
function name(){
document.getElementById('hello').style.color = 'red';
}
//으로 써준다면 onclick='name()'
//이런식으로 짧고 재사용하기 쉽게 function을 활용할 수 있다.
```

이젠 parameter에 대해 알아본다.

function name(parameter){} 자리는 이렇다.
여기에 변수를 넣어서 사용하는건데 간단하게 예시로 써보자면 위에 쓴 걸 토대로
```javascript
function name(){
    document.getElementById('hello').style.color = 'red';
}
name()
// 이렇게 써도 문제는 없지만, 위에 처럼 다 똑같은데 속성만 다른 저런경우 parameter을 이용하면 훨씬 간단하다.

function name(parameter){
    document.getElementById('hello').style.color = parameter;
}
// 이런식으로 parameter가 들어갈 자리를 정해주고
name(red)
// 이렇게 쓴다면 위와 같은 기능이 실행된다.
```
또한 
```javascript
function a(p){
    1 + p
}
// 이런식으로 연산도 쓸 수 있다.

//또한 parameter은 여러개를 쓸수도 있다. 순서대로 쓰면 된다.
```
앞에서 뺴먹었는데 id의 경우는 중복을 허용하지 않아서 상관이 없는데 , class의 경우 중복을 허용하기때문에, 
document.getElementsByClassName의 경우는  뒤에 인덱싱을 해줘야한다. 
ex/ getElementsByClassName()[0] 이런식으로 쓰이는 곳 인덱스번호


## 이젠 addEventListener에 대해 알아보자
위에처럼 onclick으로 통해서 해도 되지만 더 보기 좋은 방법인 addEventListener

addEventListener는 
```javascript
document.getElementById('hello').addEventListener("click", function (){})
//의 형태로 쓰며 action, 그리고 콜백함수 순으로 쓴다.
```

끝