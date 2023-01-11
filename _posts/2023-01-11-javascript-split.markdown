---
layout: post
title:  "split(), indexOf() 정확하게 알기"
date:   2023-01-11 21:35:36 +0900
categories: javascript split indexOf
---
javascript 그 중에서도 split, indexOf 제대로 알기

코딩테스트 연습을 쭉해오다 보니 꽤나 자주 사용되는 것 중 하나인 split, indexOf

## string.split(separator, limit)
split() 함수는 문자열을 'separator'로 잘라서, 'limit' 크기 이하의 배열에 잘라진 문자열을 저장하여 리턴한다.
- separator = 문자열을 잘라 줄 구분자 (문자열 또는 정규식)
- limit = 최대 분할 갯수
```javascript
const str = "apple banana orange";
const arr = str.split();
console.log(arr) //은 ['apple banana orange']로
// 파라미터로 아무것도 전달하지 않으면 문자열 전체를 length 1인 배열에 담아서 리턴

const arr = str.split(" ");
console.log(arr) //은 
[
    'a', 'p', 'p', 'l', 'e',
    ' ', 'b', 'a', 'n', 'a',
    'n', 'a', ' ', 'o', 'r',
    'a', 'n', 'g', 'e'
] // 이렇게 문자열을 조각 내서 나온다.

const str = "apple,banana,orange";
const arr = str.split(",");
console.log(arr) //은 ["apple", "banana", "orange"]
//separator(여기서는 ',')를 지정하여, 문자열을 separator로 잘라서 만들어진 조각들을 배열에 담아서 리턴.

const str = "apple,banana,orange";
const arr = str.split(",", 2);
console.log(arr) //	[ 'apple', 'banana' ]

// 두번째 파라미터인 limit 값을 지정
// 문자열을 ','로 자르면 총 3개의 배열이 나오는데, limit이 2여서 2개 배열만 나옴.
```

## string.indexOf(searchvalue, position)
문자열(string)에서 특정 문자열(searchvalue)을 찾고, 검색된 문자열이 '첫번째'로 나타나는 위치 index를 리턴합니다.
- 찾는 문자열이 없으면 -1 리턴
- 대소문자 구분하니 주의 필요.

```javascript
const str = "abcd";
console.log(str.indexOf("b")) // 1 이 나옴

const str = "abcdabcd";
console.log(str.indexOf("c",3)) // 6이 나옴, 문자열 3부터 찾으라고했으니, 인덱스 2에 있어도 안찾음
```

개념정리 한 번 해봤음. 다른거도 해야징