---
layout: post
title:  "React 이어서 useMemo, useCallback"
date:   2023-01-05 21:55:36 +0900
categories: React useMemo useCallback
---
## 몰랐던 useMemo, useCallback 그리고 React 이어서

<div>
    <div><b>useMemo먼저</b></div><br/>
    <div>이해한대로 쓰면 불필요하게 계속 반복적으로 쓰이는 낭비를 줄이기 위해 useMemo로 저장해놓고서<br/>
    저장해놓은 데이터를 쓴다~ 이런 내용이다.</div>
    <br/>
    <div>매번 렌더링이 왜이렇게 많이되나 했는데, </div>
</div>

```javascript
//내가 맨날 보는
function A(){
    const[a, setA]=useState(1)
    const[b, setB]=useState(1)
    const plus = (a) => {
        return a + 1
    }
    const minus = (b) => {
        return b - 1
    }
    return ( 
    <div>
        <input type="number" value="a" onchange={(e)=>{setA(e.target.value)}} />
        <span>+ 1 = {a}</span>
        <input type="number" value="a" onchange={(e)=>{setB(e.target.value)}} />
        <span>+ 1 = {a}</span>
    </div>
    )
    // 뭐 대충 이런게 있을때 a,b를 바꿔서 state가 바뀔 때 제일 위에 
    // A()는 함수이기 때문에 결국에 input이 바뀔때마다 렌더링이 되어 
    // plus함수랑 minus 함수 모두 초기화를 시키는데,
    // 그러면 minus만 실행해도 plus도 초기화 되어 불필요한 소비를 하게되는데
    
    const plus = useMemo(()=>{
        return a + 1
    },[a])
    // 이런식으로 하게되면 영향을 받지않는다는 말이다. 생각보다 이해가 잘갔다.
}

//한가지더 

const c = 나
const d = 나 //라고 하면 a===b 이지만

const c = {who: "나"}
const d = {who: "나"} //는 같아보여도 다른거라고 한다. !!기억하기
// 이런거를 useMemo를 사용해서 하는게 낭비를 줄이는 길이다.

```
<div>useMemo와 마찬가지로 useCallback의 사용도 같은 거 같다.</div>

<div>둘이 차이는 useMemo는 값을 반환하고 useCallback은 함수를 반환한다.</div>
<br/>

<div>계산 비용이 많이 들고, 사용자의 입력 값이 map과 filter을 사용했을 때와 같이 이후 렌더링 이후로도 참조적으로 동일할 가능성이 높은 경우, useMemo를 사용하는 것이 좋다.</div>
<br/>
<div>참조한 글</div>
<div>https://velog.io/@hang_kem_0531/useMemo%EC%99%80-useCallback%EC%9D%98-%EC%B0%A8%EC%9D%B4</div>
