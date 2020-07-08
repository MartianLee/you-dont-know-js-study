# 값

## 2.1 배열
```javascript
var a = [];
a[0] = 1;
a[2] = [3];
a[1]; // undefined
a.length; // 3
a["foobar"] = 2;
a.length; // 3
a.foobar; // 2
```

## 2.5 값 vs 레퍼런스
* 자바스크립트는 포인터라는 개념 자체가 없다.
* null, undefined, string, number, boolean, symbol은 언제나 값-복사 방식으로 할당/전달된다.

# 질문
* 배열의 숫자 인덱스 중 가장 마지막 값이 배열의 길이다.
* 자바스크립트는 왜 포인터라는 개념이 없나요?
* NaN !== NaN
  * ``var a = 2 / "foo"; // NaN``
  * window.isNaN(NaN) === true
  * window.isNaN("foo") === true // 문제가 있음.
  * ES6의 Number.isNan()을 사용해야 한다.
  * 자매품 : 0 / -3 === -0
  * -0 === 0
  * Number("-0") === -0
  * JSON.parse("-0") === -0
  * JSON.stringify(-0)
  * -> 인터프리터가 고의로 거짓말을 한다.
* 자바스크립트 문자열은 문자 배열과 다르다.
  ```javascript
  var a  = "foo";
  var b = ["f","o","o"];
  ```
  * 문자열은 불변값이다.

# 트러블 슈팅 경험
* 
