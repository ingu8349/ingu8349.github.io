---
layout: post
title:  "React 시작"
date:   2023-01-04 20:55:36 +0900
categories: React JSX Component
---
<h1>React 문서보기 시작</h1>

<div>
    <div>React는 별도의 파일에 마크업과 로직을 넣어 기술을 인위적으로 분리하는 대신, 둘 다 포함하는 “컴포넌트”라고 부르는 느슨하게 연결된 유닛으로 관심사를 분리합니다</div><br/>
    <div>JSX의 중괄호 안에는 유효한 모든 JavaScript 표현식을 넣을 수 있습니다. 예를 들어 2 + 2, user.firstName 또는 formatName(user) 등은 모두 유효한 JavaScript 표현식입니다.</div>
    <br/>
</div>

```javascript
const element = <h1>Hello, world!</h1>;
//위에 희한한 태그 문법은 문자열도, HTML도 아니고 JSX라고 이해하면 되겠다.
```
<br/>
<div style="font-weight: bold; font-size: 16px;">JSX도 표현식이라고 한다.</div>
<br/>
<div>
    <div>-----------------------------------------------------------------------------------------------------</div>
    <div>* 하다보니 용어가 어려운게 너무 많다. 갑자기 생각나서 몇 개 짚고 넘어가기 ( 내 블로그라 갑자기 딴길로 셀 수 있다. )</div>
    <br/><div style="font-weight: bold; font-size: 26px;">그 놈의 콜백함수가 뭐냐</div>
    <br/><div>함수에 파라미터로 들어가는 함수이며, 뭔가 순차적으로 실행하고 싶을 때 쓴다.</div>
</div>

```javascript
// 예시
document.querySelector(".button").addEventListener("click", function (()=>{
    alert("짠")
})
// 이런식으로 addEventListener도 함수인데, click옆에 argument자리에, 파라미터자리에 함수가 들어갔다. 
// '순차적'!! 1.버튼을 누른다 => 2. 경고창이 뜬다.    요것이 콜백함수
```

<div>특징은 function 저기에 다른곳에 const 뭐뭐해서 만든 함수가 들어올 수 있고,</div>
<div>아무데나 쓰는게 아니고 위에 addEventListener처럼 쓰여야 하는 곳에만 넣을 수 있다.</div>

```javascript
function callback(a) {
    alert(a)
}
//근데 
const fun = async function c(){
    console.log('aaa')
    return 'end'
}

fun().then(callback)

// async를 붙히면 뒤에 promise로 then을 쓸 수 있다.
```

<div>이정도면 콜백함수 얼추 이해를 했고, 실무에서 딥하게 더 배워봐야겠다.</div>
<br />

<div>순서는 없다. 다음 글은 react 위에 하던거 이어서 보기 및 맨날 몰랐던 useMemo, useCallback 알아봐야지.</div>