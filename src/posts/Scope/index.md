---
title: Intersection Observer API
date: 2021-03-02
description: Intersection Observer API에 대해서 알아보자
tags: ["JS"]
published: true
featuredImage: './thumbnail.png'
---

안녕하세요 Marcus입니다.
오늘은 자바스크립트에서 중요한 스코프(scope)에 대해서 소개해드리겠습니다.

#### 스코프란?
자바스크립트에서 스코프란 어떤 변수들에 접근할 수 있는지를 정의합니다.
스코프엔 두 가지 종류가 있습니다. 전역 스코프와 지역 스코프로 나뉩니다.

그럼 먼저 전역 스코프에 대해서 알아봅시다.
#### 전역 스코프
전역 스코프는 변수가 함수 바깥이나 `{}`바깥에서 선언되었다면, 전역 스코프에 정의 됩니다.

```javascript
const globalVariable = 'variable'
```
위와같이 전역 변수를 선언한다면 코드 모든곳에서 ```globalVariable```이라는 변수를 사용할 수 있습니다.

심지어 함수에서도 사용이 가능하죠
아래 예제를 보시죠

```javascript
const hello = 'Hello Marcus'
function marcusHello () {
  console.log(hello)
}
console.log(hello) // 'Hello Marcus!'
sayHello() // 'Hello Marcus!'
```
비록 위와같이 전역 스코프를 이용하여 변수를 선언할 수 있지만 그렇지 않는게 좋습니다.
왜냐하면, 두 개 이상의 변수의 이름이 충돌하는 경우가 생길 수도 있기 때문이죠

실제로 초기 프로그래밍 언어는 이 대응표를 프로그램 전체에서 하나로 관리했는데, 여기에는 이름 충돌의 문제가 있었습니다.
```javascript
// 잘못된 예시
let thing = 'Marcus'
let thing = 'Marcus else' // 이미 같은 이름의 변수가 존재합니다.
```
만약 var를 이용하여 변수를 선언했다면, 두 번째 변수가 첫 번째 변수를 덮어쓰게됩니다.
``` javascript
// var는 되도록이면 사용하지 않도록 한다.
var thing = 'Marcus'
var thing = 'Marcus else' // 위에 thing = 'Marcus' -> 'Marcus else'
console.log(thing) // ‘Marcus else’
```

위와같이 변수를 선언한다면 나중에 코드양이 많아졌을 때 디버깅을 하기 어려움을 겪기때문에 되도록이면 var는 사용하지 않습니다.

#### 지역 스코프
지역 스코프는 코드에서 특정 부분에서만 사용이 가능한 변수입니다.
자바스크립트에서는 크게 두 가지의 지역 스코프가 존재합니다. 함수 스코프와 지역 스코프
먼저 함수 스코프를 소개해드리겠습니다.
#### 함수 스코프
여러분이 만약 함수 내부에서 변수를 선언한다면, 그 변수는 선언한 함수 내부에서만 사용이 가능합니다.

아래 예제를 살펴보면 변수 hello는 marcusHello 스코프 내에 존재한다는 것을 알 수 있습니다
```javascript
function marcusHello () {
  const hello = 'Hello Marcus!'
  console.log(hello)
}
marcusHello() // 'Hello Marcus!!'
console.log(hello) // Error, hello is not defined
```
#### 블록 스코프
블록 스코프는 여러분이 중괄호 `{}`내부에서 `const` 또는 `let`으로 변수를 선언하면,
그 변수들은 중괄호 블록 내부에서만 사용이 가능합니다.

아래 예제를 살펴봅시다
```javascript
{
  const hello = 'Hello Marcus!'
  console.log(hello) // 'Hello Marcus!'
}
console.log(hello) // Error, hello is not defined
```

제가 소개해드릴 내용은 여기가 끝입니다.
스코프에 대한 내용에 틀린점이 있거나 내용이 도움이 됬다면 댓글로 공유해주세요!
자바스크립트를 공부하는 사람끼리 서로 좋은 공부가 될거같습니다:D