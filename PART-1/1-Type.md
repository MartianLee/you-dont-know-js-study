# 타입

강타입 언어에 익숙한 사람들은 자바스크립트에 타입이 '없다'고 이야기하는 경우가 많다. 하지만 ECMAScript 5.1(이하 ES5)에 따르면 ECMAScript 언어 타입에는 'Undefined, Null, Boolean, String, Number, Object'가 있다.

## 1.1 타입 그 실체를 이해하자

자바스크립트에서는 강제변환이 자주, 의도치 않게 일어난다. 이 책에서는 강제변환의 강력함과 유용함을 십분 활용하도록 안내할 것이다.

## 1.2 내장 타입
* null
* undefined
* boolean
* number
* string
* object
* symbol (ES6부터 추가됨)

``object를 제외한 타입을 원시 타입primitive이라 한다.``

값의 타입은 typeof 연산자를 사용해 알 수 있다.

## 1.3 값은 타입을 가진다
자바스크립트는 타입 강제를 하지 않는다.
``변수에 typeof 연산자를 대어보는 건 "이 변수의 타입이 무엇이니?"라는 질문이지만 타입이란 개념은 변수에 없으므로 정확히는 이 변수에 들어있는 값의 타입은 무엇이니? 라고 묻는 것이다.``
변수는 언제라도, 어떤 형태의 값이라도 가질 수 있다.

```javascript
let a = 42;
typeof a; // "number"
a = true;
typeof a; // "boolean"
```

### 1.3.1 값이 없는 vs 선언되지 않음.

```javascript
var a;
typeof a; // "undefiend"
```

```javascript
var a;
a; // "undefined"
b; // Uncaught ReferenceError: b is not defined
```

```javascript
var a;
typeof a; // "undefined"
typeof b; // "undefined"
```

### 1.3.2 선언되지 않은 변수

```javascript
// 이렇게 하면 에러가 난다.
if (DEBUG) {
  console.log("디버깅 시작");
}
// 안전하게 존재 여부를 체크하기
if (typeof DEBUG !== "undefined") {
  console.log("디버깅 시작");
}
```

typeof 안전 가드 없이 전역 변수를 체크하는 다른 방법은 전역 변수가 모두 전역 객체의 프로퍼라는 점을 이용하면 된다.



## 1.4 정리하기

변수는 타입이 없지만 값은 타입이 있다.
"undefined"와 "undeclared"는 전혀 다르다.
그래도 typeof를 잘 활용하면 에러를 내지 않고 값의 타입을 체크할 수 있다.

# 질문
* let도 호이스팅이 일어나나요?
  * 네. 대신 not initialized 상태여서 접근할 수 없습니다. 접근하면 에러가 납니다.
  * 관련 [링크](https://medium.com/korbit-engineering/let%EA%B3%BC-const%EB%8A%94-%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85-%EB%90%A0%EA%B9%8C-72fcf2fac365)
* undefined와 undeclared는 무엇이 다른가요?
  * undeined는 선언되었지만 할당되지 않은 것이고
  * undeclared는 접근 가능한 스코프에 해당 변수가 선언되지 않은 것이다.


# 트러블 슈팅 경험
* javascript 활용 게임의 코드 최적화 중
  * 문제 : 메모리 프로파일링 중 익명함수가 너무 많이 호출됨. -> 어떤 함수인지 찾기 힘든 현상이 생김.
  * 해결 : 번거롭지만 개발자가 함수 이름을 꼭 지어준다.
* V8 엔진 히든 클래스
  * 객체의 프로퍼티에 값을 할당하는 순서에 따라 히든 클래스 종류가 달라진다.
  * ``a.b = 1; a.c = 2;``와 ``a.c = 2; a.b = 1``의 히든 클래스는 다르다.
  * 문제 : 이런 순서를 생각하지 않고 객체를 생성하면 히든 클래스가 어마어마하게 생긴다.
* typeof로 undefined 값 처리
  * 문제 : 비동기 처리 이후 객체의 깊은 뎁스 프로퍼티를 조회할 때 undefined가 자주 발생한다.
  * 해결 : 1장에서 소개된 typeof 안전가드를 유용하게 실무에 적용하였다.
