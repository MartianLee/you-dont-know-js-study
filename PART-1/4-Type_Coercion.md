# 4장 강제변환

## 4.1 

## 4.2

## 4.3 명시적 강제변환

## 4.4 암시적 변환

trade off : ``가독성 향상 vs 매직박스``



## 질문 & 중요

* 95p : Falsy 값
  * undefined
  * null
  * false
  * +0, -0, NaN
  * ""
* 116p
  ```javascript
  var a = [1,2];
  var b = [3,4];
  a + b; // "1, 23, 4"
  ```
* 119p
  ```javascript
  var a = true;
  var b = false;
  sum = 0;
  arguments = [a, b, b, b];
  /// for ... 
  sum += arguments[i]; // 암시적 강제변환
  sum += Number(!!arguments[i]); // 명시적 강제변환
  
  ```

* 
