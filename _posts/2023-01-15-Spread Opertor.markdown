---
layout: post
title:  "Spread Opertor"
date:   2023-01-15 21:10:03 +0900
categories: javascript ES6 Spread Opertor 
---

간략하게 Spread Opertor 알아보기

## 스프레드 연산자를 사용하면 배열, 문자열, 객체 등 반복 가능한 객체 (Iterable Object)를 개별 요소로 분리할 수 있다.

요새 자주 보이는 ... 이런걸 스프레드 연산자라고 하는데,
꽤나 자주 접하는 부분이라 이렇게 한 파트로 지정했다. 짧겠지만 유용한 글이 될거다. 

쭉 보니 예시를 통해 이해하는게 좋을 것 같다.
```javascript
// Array
var arr1 = [1, 2, 3, 4, 5]; 
var arr2 = [...arr1, 6, 7, 8, 9];
console.log(arr2); // [ 1, 2, 3, 4, 5, 6, 7, 8, 9 ]

// String
var str1 = 'friend';
var str2 = [...str1];
console.log(str2); // [ "f","r","i","e","n","d"]
```

감이온다.

1. 배열에서의 Spread Operator
   ES6에서는 spread 연산자를 이용하여 배열 병합이 가능 ( = concat과 같다.)
```javascript
var arr1 = [1, 2, 3, 4];
var arr2 = [5, 6];
var arr = arr1.concat(arr2); // [1,2,3,4,5,6]
// 이것처럼
var arr = [...arr1, ...arr2]; // [1,2,3,4,5,6]

var arr1 = [1,2,3];
var arr2 = [4,5,6];
arr1.push(...arr2) // [1,2,3,4,5,6]
```

2. 배열 복사
```javascript
var arr1 = ['1','2']; 
var arr2 = [...arr1];
arr2.push('3');
console.log(arr2); // [ "1", "2", "3" ]
// 원본 배열은 변경되지 않는다.
console.log(arr1); // [ "1", "2" ]

//만약에
var arr1 = ['1','2'];
var arr2 = arr1;
arr2.push('3');
console.log(arr2); // [ "1", "2", "3" ]
// 이렇게 arr2는 위와 같지만 arr1 또한 영향을 받아서 [1,2,3]이 나오기 때문에 조심해야 된다.
```

3. 객체 복사
```javascript
var currentState = { name: '길동', species: 'human'};
currentState = { ...currentState, age: 10};

console.log(currentState)// {name: "길동", species: "human", age: 10}
```
단박에 이해가 간다.

4. 함수에서의 Spread Operator
   함수를 호출할 때 함수의 매개변수(parameter)를 spread operator로 작성한 형태를 Rest parameter라고 부르고,
   Rest 파라미터를 사용하면 함수의 파라미터로 오는 값들을 모아서 "배열"에 집어넣는다!
```javascript
function add(...restParameter) {
  let sum = 0;
  for (let item of restParameter) {
    sum += item;
  }
  return sum;
}
console.log( add(1) ); // 1
console.log( add(1, 2) ); // 3
console.log( add(1, 2, 4) ); // 7
```

아주 유용하게 써먹을거같다.