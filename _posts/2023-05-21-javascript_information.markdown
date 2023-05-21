---
layout: post
title:  "자바스크립트 자료형"
date:   2023-05-21 14:05:03 +0900
categories: 자료형 자바스크립트 map set 
---

자바스크립트 자료형 정리를 해보려고 한다.

자료형에 대해 다 알고 있는줄 알았는데,, ES6나온 새로운 자료형에 대해 들어보기만하고
정확한 데이터가 없었던것같아 한번 총 정리? 를 해보려고 한다.

자바스크립트에는 하단의 
기본 자료형이 있다. ( 숙지가 되어있던 부분 )

1. 숫자형
- 숫자형(number type) 은 정수 및 부동소수점 숫자(floating point number)를 나타낸다.
- 숫자형엔 일반적인 숫자 외에 Infinity, -Infinity, NaN같은 '특수 숫자 값(special numeric value)'이 포함된다.
  - Infinity는 어떤 숫자보다 더 큰 특수 값, 무한대(∞)를 나타낸다. 이부분은 숙지가 필요하다.
```javascript
alert( 1 / 0 ); // 무한대 예시
alert( infinity ); // 무한대 예시
```

2. 문자형
- 자바스크립트에선 문자열(string)을 따옴표로 묶는다.
  - 따옴표는 세 종류가 있습니다.
    - 큰따옴표: "Hello"
    - 작은따옴표: 'Hello'
    - 역 따옴표(백틱, backtick): `Hello`
  - 큰따옴표와 작은따옴표는 ‘기본적인’ 따옴표로, 자바스크립트에서는 이 둘에 차이를 두지 않고, 백틱의 경우 역 따옴표로 변수나 표현식을 감싼 후 ${…}안에 넣어주면 문자열 중간에서 쓸 수 있다.

3. 불린형
- 불린형(논리 타입)은 true와 false 두 가지 값밖에 없는 자료형이다.

4. ‘null’ 값
- null 값은 지금까지 소개한 자료형 중 어느 자료형에도 속하지 않는 값이다.
- ‘존재하지 않는(nothing)’ 값, ‘비어 있는(empty)’ 값, ‘알 수 없는(unknown)’ 값을 나타낸다.
- null 값은 오로지 null 값만 포함하는 별도의 자료형을 만든다.
```javascript
let age = null;은 나이(age)를 알 수 없거나 그 값이 비어있음을 보여준다.
```
5. ‘undefined’ 값
- undefined 값도 null 값처럼 자신만의 자료형을 형성한다.
- undefined는 '값이 할당되지 않은 상태’를 나타낼 때 사용한다.
- 변수는 선언했지만, 값을 할당하지 않았다면 해당 변수에 undefined가 자동으로 할당한다.

##  변수가 ‘비어있거나’ ‘알 수 없는’ 상태라는 걸 나타내려면 null을 사용하는 걸 권장한다.

6. 객체 오브젝트형
- 객체(object)형은 특수한 자료형이다.
- 데이터 컬렉션이나 복잡한 개체(entity)를 표현할 수 있다.

7. 심볼형
- 심볼(symbol)'은 유일한 식별자(unique identifier)를 만들고 싶을 때 사용한다.
```javascript
// id는 새로운 심볼이 된다.
let id = Symbol();
```
- 심볼을 만들 때 심볼 이름이라 불리는 설명을 붙일 수도 있다.
```javascript
// 심볼 id에는 "id"라는 설명이 붙는다.
let id = Symbol("id");
```
### 객체의 속성키를 심볼값으로해서 해당 속성을 고유하게 관리하고 싶을 때 사용한다!

### 이제부터 ES6 에서 추가된 map과 set을 알아본다.
- map, set은 ES6에서 새로 도입한 자료구조이다.

## SET
- Set은 중복을 허용하지 않는 데이터 집합
- Set을 사용하면 데이터에 빠르게 엑세스 할 수 있다.
- 1와 '1'은 다른것으로 간주 즉, 중복을 확인하기 위해 강제적으로 자료형을 변형하지 않는다.
- forEach(callback(value,key,set)[, thisArg]), for of 로 값에 접근가능하다.

```javascript
const mySet = new Set(); // 이렇게 사용하는게 기본이다.
mySet.add(1); // 객체에 추가하는 방법
mySet.size; //2, 갯수 구하는 방법
mySet.delete(1); //객체 안에 있는거 지우는 방법
mySet.has(2); //true
mySet.has(1); //false
myset.clear(); // {} 전부 비우기

let arr = [...mySet]; //Spread 연산자를 이용해 array로 만들 수 있다.
```

## Map
- Object자료형과 똑같이 key, value 형태로 자료를 저장할 수 있는 자료형
- Set과 마찬가지로 key는 자료형을 구분한다.
- Set처럼 배열을 넣어서 초기화 시킬 수 도 있다.
- 
```javascript
let myMap = new Map(); // 기본 형태이다.
myMap.set(1, 'hello'); //{1=>'hello'}
myMap.set('1', 'hello'); //{1=>'hello', '1'=>'hello'}
myMap.set(1, 'world'); //{1=>'world', '1'=>'hello'}
myMap.get(1); //'world'
myMap.has(1); //true
myMap.delete(1); // {'1' => 'hello'}
//clear, size 는 Set과 같다.

let myMap = new Map(['name', 'kyle'], ['city', 'seoul']); //{"name" => "kyle", "city" => "seoul"}
```

근데! 출력해보면 위에처럼 object랑 다르게 화살표로 나온다. 
### Map 자료형은 자료의 연관성을 표현하기 위해 쓰기 때문이다.

## 자료들 간의 연관성을 표현하기 위해 쓰는 자료형이 바로 Map
예시
```javascript
var person = new Map();
person.set([1,2,3], 'Kim'); // [1,2,3] => 'Kim'
person.set('age', 20); // ["age" => 20]
// 자료의 이름으로 array도 되고 object도 된다는 걸 볼 수 있다.
```


## Map 과 Object 차이
- Object의 key type은 string,symbols,integer 밖에 안된다.
- Map의 key type은 어떤 것이든 되고 서로 구분된다. (array,object...)
- Map은 데이터의 순서를 보존하는 반면 Object는 그렇지 않다.
- Map은 Object의 인스턴스이지만 Object는 그렇지 않다. 


출처 
- https://eboong.tistory.com/254
- https://control-time.com/entry/Javascript-%EC%9E%90%EB%A3%8C%ED%98%95%EC%97%90%EB%8A%94-%EC%96%B4%EB%96%A4-%EA%B2%83%EC%9D%B4-%EC%9E%88%EC%9D%84%EA%B9%8C?category=904089