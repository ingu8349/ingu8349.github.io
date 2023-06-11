---
layout: post
title:  "세션과 JWT"
date:   2023-06-11 14:05:03 +0900
categories: session Login jwt token 
---

세션과 JWT

## Authentication vs Authorization

Authentication은 인증이고, Authorization은 권한 부여인데 로그인 시스템에서 중요한 역할을 한다. 웹사이트에서 로그인하는 것을 Authentication이라고 한다. 한번 로그인을 한 후에는 로그인 상태가 유지되어야 한다. 이 역할을 하는 것이 Authorization이다.

### 쉽게 로그인을 하는 것 , 인증 authenticaion, 그리고 로그인 한 상태로 인가를 받은 것 authorization으로 생각하며 된다.

##  세션(Session)

- 세션은 브라우저와 웹 서버가 연결되어 브라우저가 종료될 때까지의 시점이다. 
- 브라우저를 통해 서버에 접속할 때 서버는 세션 id를 쿠키에 담아 되돌려주고, 사용자는 세션 id를 담은 쿠키인 세션 쿠키를 이 후 요청부터 계속해서 함께 전달함으로 서버가 클라이언트를 식별할 수 있게 하는 기술이 세션 기반 인증 방식인데 보통 세션이라고 한다.

### 쿠키 vs 세션

- 가장 중요한 점은 쿠키의 유형에는 영구 쿠키와 세션 쿠키가 있어 만료시기가 각각 다르지만 세션은 대부분의 경우 브라우저 종료 시 만료된다.
- 두번쨰는 쿠키와 세션의 가장 큰 차이는 저장 위치이다.쿠키는 클라이언트에 저장되고, 세션은 서버에 저장된다.

## JWT 

- JWT는 'JSON Web Token'의 약자로 이상한 형태의 문자열이다.
프로젝트에서 포스트맨에서 로그인을 할 떄 access 토큰을 자주 사용했는데, 이번에 정리를 해본다..

- .을 기준으로 3부분으로 구분되어 heaer, payload, signature로 구성 되어 있다
   - header: typ와 alg라는 정보가 존재하는데 typ의 값은 JWT이고 alg signature를 해싱하기위한 알고리즘이다.
     {
     "alg": "HS256",
     "typ": JWT
     }
   - payload: 토큰에서 사용할 조각들인 클레임이 존재한다. 토큰의 목적에 따라 클레임이 달라진다. registered claim에는 토큰 만료시간, 토큰 발급 날짜 등을 작성할 수 있다.
   - signature: 토큰을 인코딩하거나 유효성 검사를 할 때 필요한 암호화 코드이다.

###  JWT는 일종의 확인서이다
    1. 어떤 웹사이트에 로그인을 해서 성공적으로 Authentication이 이루어지면 서버는 사인된 확인서(JWT)를 우리에게 제공한다.   
    2. 요청 때마다 JWT를 서버에게 같이 보여주면서 권한을 확인받는다.
    3. 서버는 JWT만 확인해 Authorization하기 때문에 세션 DB에 저장할 필요가 없다.

## 세션 vs JWT
1. 세션방식에서 서버는 로그인 된 유저의 정보를 모두 저장하고 있어서 유저들의 통제가 JWT보다 비교적 쉽다
   _ 예를 들어 웹에서 로그인되있는걸, 핸드폰에서 동시접속을 할 때 웹 로그인을 로그아웃 시킨다던가,
2. JWT를 서버가 발급하고나면 JWT를 관리하지 않는다. 오직 JWT를 받았을 때 JWT가 유효한 것인지만 확인하기 때문에 서버 자원과 비용을 절감할 수 있다.

### JWT 는 access token & refresh token 방식 2가지가 있다. access token은 유효기간이 짧은 토큰이고, refresh token은 access token보다 유효기간이 긴 토큰이다.

1. 사용자가 로그인을 하면 서버로부터 access token, refresh token 2개의 토큰을 받는다. 이때 서버는 refresh token을 안전한 저장소에 저장한다.
2. 서버로부터 받은 access token의 유효 기간이 지나지 않은 경우 사용자가 어떤 요청을 보낼 때 access token을 함께 보내고 서버는 유효한 지 확인 후 응답을 보낸다.
3. 서버로부터 받은 access token의 유효 기간이 지난 경우 사용자는 refresh token과 함께 요청을 보내고, 저장소에 저장되어 있던 refresh token과 비교한 후에 유효하다면 새로운 access token과 응답을 함께 보낸다.

출처
https://velog.io/@gotaek/%EC%84%B8%EC%85%98Session%EA%B3%BC-JWT
그리고 유튜브 얄팍한 코딩사전 영상