---
layout: post
title:  "첫번째 포스팅"
date:   2023-01-03 22:55:36 +0900
categories: Diary Start First
---
<h1>시작</h1>

<h4>기대된다. 앞으로 채워나갈 나의 개발 포스팅들<br/></h4>

<div>
    <div>일단 오늘은 Switch, case에 대해 써봤다.</div>
    <div>아는 내용이지만, 써먹지 않으면 모르는거나 다름 없었다.</div>
    <div>클린하게 코드를 쓰는게 중요하다는 걸 다시금 깨우침</div>
</div>

```javascript
// 내가 짠 코드 
const maxDate = reservationLimitType == "DAY" ? addDays(new Date(), reservationLimitType === "UNLIMTED" ? null : reservationLimit) :
        reservationLimitType == "WEEK" ? addWeeks(new Date(), reservationLimitType === "UNLIMTED" ? null : reservationLimit) :
            reservationLimitType == "MONTH" ? addMonths(new Date(), reservationLimitType === "UNLIMTED" ? null : reservationLimit) :
                reservationLimitType == "YEAR" ? addYears(new Date(), reservationLimitType === "UNLIMTED" ? null : reservationLimit) : ""

// 위에서 언급한 Switch와 Case를 이용한 경우
function getReservationLimit(reservationLimitType: ReservationLimitType, reservationLimit: number) {
    const now = new Date();
    switch (reservationLimitType) {
        case "YEAR":
            return addDays(now, reservationLimit)
        case "MONTH":
            return addMonths(now, reservationLimit)
        case "WEEK":
            return addWeeks(now, reservationLimit)
        case "DAY":
            return addDays(now, reservationLimit)
        case "UNLIMITED":
            return null
    }
}
const maxDate = getReservationLimit(reservationLimitType, reservationLimit)
```

<br/>
<div>
    <div style="font-weight: bold; font-size: 16px;">Vue 맛보기 시작 </div>
</div>
<br/>
<div>...제대로 된 정보 포스팅은 두번째부터, 오늘 이걸로 생략한다.</div>