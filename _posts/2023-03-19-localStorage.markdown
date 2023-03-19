---
layout: post
title:  "Javascript localstorage"
date:   2023-03-19 18:35:03 +0900
categories: Javascript localstorage 
---

localstorage에 대하여

장바구니 기능을 만드는데 있어서 서버로 보내서 DB 이런데 저장하는게 좋겠지만 서버같은게 없기 때문에 브라우저 저장공간을 이용해본다.

브라우저 내에
- Local Storage / Session Storage 는 문자, 숫자만 key : value 형태로 저장가능
- 5MB까지만 저장가능
- Local Storage는 브라우저 재접속해도 영구적으로 남아있다 
- Session Storage는 브라우저 끄면 날아갑니다.

### 유저가 브라우저 청소하지 않는 이상 반영구적으로 데이터저장이 가능 

### 로컬 스토리지 사용법

```javascript
localStorage.setItem('이름', 'kim') //자료저장하는법
localStorage.getItem('이름') //자료꺼내는법
localStorage.removeItem('이름') //자료삭제하는법
```
localstorage 저부분을 sessionStorage로 바꾸면 Session Storage에 저장가능

## 위에서 말했듯이 문자, 숫자만 저장이 가능해서 array/object를 로컬스토리지에 저장하면 강제로 문자로 바꿔서 저장된다.

그래서 array/object를 JSON으로 바꾸면 문자취급을 받기 때문에 안전하게 로컬스토리지에 저장할 수 있다.

```javascript
var arr = [1,2,3];
var newArr = JSON.stringify(arr);
localStorage.setItem('num', newArr)
```

storage잘 이용해보면 꽤나 유익할 듯

array/object -> JSON 변환하고 싶으면 JSON.stringify()
JSON -> array/object 변환하고 싶으면 JSON.parse()

```javascript
var arr = [1,2,3];
var newArr = JSON.stringify(arr);

localStorage.setItem('num', newArr);

//꺼내서 쓸 땐
var 꺼낸거 = localStorage.getItem('num');
꺼낸거 = JSON.parse(꺼낸거);
console.log(꺼낸거);
```