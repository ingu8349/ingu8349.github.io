---
layout: post
title:  "React useEffect와 변수 선언"
date:   2023-01-07 18:45:36 +0900
categories: React useEffect var let const
---
## React useEffect

용어 정리
마운트 - 화면에 첫 렌더링 <br/>
업데이트 - 다시 렌더링 <br/>
언마운트 - 화면에서 사라짐 으로 이해하면 좋을 것 같다.

** useEffect의 3가지 형태
```javascript
useEffect(()=>{
    // 작업
    }
)
// 렌더링 될 때 마다 실행된다.
useEffect(()=>{
        // 작업
    }
,[]) 
// 처음 렌더링 될 때만 실행
useEffect(()=>{
        // 작업
    }
    ,[value])
// 렌더링 될 때 마다 실행된다.
// value값이 바뀔 떄 실행
```

이정도 기초를 기반으로 쓰면 될것 같다.
덧붙혀서

```javascript
useEffect(()=>{
    어쩌구저저구  // 마운트될떄 발생
    return (
        어쩌구저쩌구 // 언마운트 될때 실행 
    )
},[])
```
알아두면 좋을 것같다..

매번 const 를 쓰고, var, let도 써왓지만, 이번 참에 정리 한번 제대로 하고 넘어간다.

var let = 변수 선언, const = 상수 선언 할 때 쓴다.

var는 왜 사용하면 안되고, let, const는 왜 쓸수있을까?
## var와 let의 차이 3가지
1. 스코프
 - 범위 : function, block, global 스코프가 있다. (함수범위, 블록 범위, 전역범위)
 - var은 function scope, let은 block scope
 - function scope는 변수가 선언된 함수 내부에서만 사용가능하다.
2. 중복선언 
 - let은 중복선언을 허용하지 않는다.
3. 호이스팅 -> 실행될때 미리 맨위로 끌어 올려지는것.
    
```javascript
    function main(){
    var x = "hi";
    console.log(x)
    // 이러면 당연히 hi가 뜬다.
}
    //그런데
    function main(){
        if(true){
        var x = "hi";
    }
        console.log(x)
        // 이렇게 해도 에러가 안뜨고 hi가 뜬다. 왜냐하면 함수범위는 x가 선언된 함수라면 어디든 쓸수있기 때문이다.
}
// 하지만 위에 var 을 let으로 바꾸면 에러가난다. 왜냐하면 선언된 블록 내부에서만 적용되기 때문이다.
```

이제 문제가 되는 상황을 봐보자
```javascript
function main(){
    let a = "hello"
    if(true){
        let a = "hi"
    }
    console.log(a)
    // 이렇게 되면 let의 경우 hello가 뜨지만, 
    // let 을 var 로바꾼다면 hi가 뜬다. 그렇게 되면 두개가 같은 범위 안에서 중복 선언이 허용 되기 떄문에 위에껄 아래가 덮어 씌워버리게된다.
}   
```
또한 var 키워드를 전역변수로 하면 window의 객체로 등록되지만,
let은 등록되지 않는다. window는 우리가 사용하고 있는 코드, 라이브러리의 전역객체인데, 여기에 var는 영향을 주기 때문에 위험하다.

위에 언급한 호이스팅 관련
```javascript
console.log(a)
var a = "hi"
//이러면 호이스팅되서 초기화 시킨다.
var a 
console.log(a)
a= "hi" //이런식으로 되서 console값은 에러가 안나고 undefined가 나버린다.

// let으로 하면 에러가 난다. let도 호이스팅해서 맨위로 올리긴 하지만, 초기화되진않는다.
```

const 는 블록범위 이며, let과 차이는 상수라는 것이다. 변경할 수 없다. 그리고 const는 선언만 하는 것도 안된다.
왜냐하면 상수는 할당 연산자를 통해서 값을 할당 할수 없기떄문에 const a; 이런건 안된다!'

하 지 만
```javascript
const a = 1;
a=3 //이런건 안되는데
const b = { a: 3} 
b.a =5 //이런건 된다. 객체 내부의 속성 값은 변경 할 수 있다.

const a = object.freeze({ a:3})  // 오브젝트 프리즈를 이용하면 절대 못바꾸게도 할 수 있다.
```

이제 드디어 왜 const를 써야하는 지 명 확 하게 알겠다. 끝