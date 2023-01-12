---
layout: post
title:  "substring, slice 알아보기"
date:   2023-01-12 22:10:03 +0900
categories: javascript substring slice
---
Javascript에서 substring(), slice() 함수는 모두 문자열을 잘라주는 역할을 한다.
substring에 대해 알아본다.

오늘 코드테스트 예문을 푸는데 내가 했던 방식 말고 ,substring를 써서
쉽게 답이 나왔던 코드가 있었는데, substring를 몰라 쏟아부은 시간이 꽤나있어서,
substring를 기억하고서 다음에 써먹으면 유용할 것 같아 글을 남긴다.

## substring() 메소드는 string 객체의 시작 인덱스로 부터 종료 인덱스 전 까지 문자열의 부분 문자열을 반환합니다.

말이 좀 어려운데, 

```javascript
const str = 'Mozilla';
console.log(str.substring(1, 3)); // "oz"
console.log(str.substring(2)); // "zilla"
//  추가 예시

var anyString = 'Mozilla';

// Displays 'M'
console.log(anyString.substring(0, 1));
console.log(anyString.substring(1, 0));

// Displays 'Mozill'
console.log(anyString.substring(0, 6));

// Displays 'lla'
console.log(anyString.substring(4));
console.log(anyString.substring(4, 7));
console.log(anyString.substring(7, 4));

// Displays 'Mozilla'
console.log(anyString.substring(0, 7));
console.log(anyString.substring(0, 10));

```
요정도로 이해하면 될 것같다.

이제 slice

slice() 함수는 substring() 함수와 사용법이 같고, 

substring() 함수와 마찬가지로 파라미터로 자를 문자열의 start index와 end index를 전달한다.
이거도 예시를 보면 이해에 도움이 될 것 같다.

```javascript
let str = "안녕하세요?"
let first_char = str.slice(0, 1); // 안
let second_char = str.slice(1, 2); // 녕
let last_char = str.slice(str.length-1, str.length); // ?
```

근데 의문점.. 두개가 쓰는게 똑같아 보인다.
차이점은 뭘까? 

## 파라미터로 전달되는 start > end 일 경우 두 함수의 처리가 다르다!
substring() : start 값과 end 값을 바꾸어서 처리.
slice() : 그냥 비어있는 string, 즉 ""을 리턴.

다른 상황

start 또는 end 값이 음수인 경우

slice() : string의 가장 뒤에서 음수의 절대값만큼 내려온 index로 취급
substring() : start값이 음수인 경우, start값은 0으로 취급, end값이 음수인 경우에도, start값과 마찬가지로 end값은 0으로 취급

유 용 하네. 언제한번 써먹어 봐야겠다!