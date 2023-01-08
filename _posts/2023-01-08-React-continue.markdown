---
layout: post
title:  "React continue"
date:   2023-01-08 18:45:36 +0900
categories: React JSX Component
---
React 하던 것이어서..

JSX 개념잡기 

태그가 비어있다면 XML처럼 /> 를 이용해 바로 닫아주어야 합니다.

```javascript
const element = <img src={user.avatarUrl} />;
```
매번 오류가 뜨는 부분이라 확인체크가 필수다.

**기본적으로 React DOM은 JSX에 삽입된 모든 값을 렌더링하기 전에 이스케이프 하므로, 애플리케이션에서 명시적으로 작성되지 않은 내용은 주입되지 않습니다. 

## **JSX는 객체를 표현합니다.**

Babel은 JSX를 React.createElement() 호출로 컴파일합니다.
```javascript
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
const element = React.createElement(
    'h1',
    {className: 'greeting'},
    'Hello, world!'
);

// 이 두가지는 같은 내용이다. 참고
```
용어 정리 : <br/>
-'엘리먼트'는 React 앱의 가장 작은 단위입니다. <br/>
-또한 엘리먼트는 컴포넌트의 “구성 요소”이다. <br/>
-React 엘리먼트는 불변객체이다.

===>UI를 업데이트하는 유일한 방법은 새로운 엘리먼트를 생성하고 이를 root.render()로 전달하는 것

**"전체 UI를 다시 그리도록 엘리먼트를 만들었지만 React DOM은 내용이 변경된 텍스트 노드만 업데이트한다."
=> 리엑트의 핵심내용**

## 주의: 컴포넌트의 이름은 항상 대문자로 시작합니다.
 
props 관련 내용 

**개념적으로 컴포넌트는 JavaScript 함수와 유사합니다. “props”라고 하는 임의의 입력을 받은 후, 화면에 어떻게 표시되는지를 기술하는 React 엘리먼트를 반환합니다. <br/><br/>
**React가 사용자 정의 컴포넌트로 작성한 엘리먼트를 발견하면 JSX 어트리뷰트와 자식을 해당 컴포넌트에 단일 객체로 전달합니다. 이 객체를 “props”라고 합니다.

## props는 읽기 전용입니다.
## 모든 React 컴포넌트는 자신의 props를 다룰 때 반드시 순수 함수처럼 동작해야 합니다.