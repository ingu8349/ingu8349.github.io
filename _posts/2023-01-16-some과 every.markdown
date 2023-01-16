---
layout: post
title:  "some과 every"
date:   2023-01-15 22:00:03 +0900
categories: javascript  some every 
---

some과 every에 대해 알아보자

굉장히 생소했지만, 오늘 일하는 도중 보게 된 some 때문에 궁금증이 생겨서 찾아봤고,
이렇게 기록해두면 또 써먹을 일이 있을 것같아 포스팅한다. 내용이 길지는 않을 것 같다.

참고로 둘다 배열에서 쓴다. 알아두자

먼저 
## every함수

- every()는 배열의 각 엘리먼트에 대해서 테스트 함수의 반환 값이 모두 true인지 확인합니다. 
- 알기 쉽게 어떤조건을 걸었을 때 다 true일때만 true를 반환하고 하나라도 아닐떈 false를 반환하는 얄짤 없는 함수다.

```javascript
var objArr = [{name: 'a', age: 10}, {name: 'b', age: 100}, {name: 'c', age: 5}]

console.log(objArr.every((item)=> item.age>5)); //false, C때매 false다
console.log(objArr.every((item)=> item.age>1)); //true
```

이해하기 쉽다.

두번째로 
## some함수 
오늘따라 내꺼인듯 내꺼아닌. 미안하다 다시 공부로

- some()은 배열의 각 엘리먼트에 대해서 테스트 함수의 반환 값이 하나라도 true가 있는지 확인한다.
- 그래서 하나라도 있으면 true 진짜 하나도 없으면 false를 반환한다. 
- every는 얄짤없는 놈 some은 느슨한 놈으로 이해하면 될거같다.

```javascript
var objArr = [{name: 'a', age: 10}, {name: 'b', age: 100}, {name: 'c', age: 5}]

console.log(objArr.some((item)=> item.age>5)); //true
console.log(objArr.some((item)=> item.age<1)); //false
```

흠..동기 비동기하다가 이거보니 안구가 정화된다.

내일 실제 코드에 써져있는거 왜썻는지 봐야징 안녕