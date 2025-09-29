
## Number 객체 (생성자 함수)

정확히 말하면, 자바스크립트에서 `Number`는:

> 👉 **생성자 함수이자 객체이며,  
> 내장 표준 라이브러리의 일부인 "기본형 래퍼 객체"**야.

---

## 🔍 조금 더 자세히 설명하자면:

### 1. `Number`는 함수 (생성자 함수)

```js
typeof Number; // 'function'
```

`Number`는 숫자 값을 감싸는 **래퍼 객체**를 생성할 수 있는 생성자 함수.

---

### 2. 숫자는 원시 타입, `Number`는 객체

```js
let x = 123;               // 원시 숫자
let y = new Number(123);   // 객체로 래핑된 숫자

console.log(typeof x); // 'number'
console.log(typeof y); // 'object'
```

⚠️ 주의: `new Number(...)`로 생성한 객체는 진짜 숫자가 아님

```js
123 === new Number(123); // false ❌
123 == new Number(123);  // true ✅ (암묵적 형변환)
```

---

### 3. 숫자 리터럴도 메서드처럼 쓸 수 있음

```js
(123).toFixed(2); // '123.00'
```
- 여기서 `(123)`은 원시 숫자지만
- 자바스크립트는 내부적으로 다음처럼 처리해:

```js
new Number(123).toFixed(2);
```
→ 그래서 `Number.prototype`의 메서드를 쓸 수 있는 거야

---

### ✅ 4. `Number`는 내장 표준 객체

- `Number`, `String`, `Boolean`, `Array`, `Function`, `Date` 등과 같이
- ECMAScript에서 제공하는 **전역 내장 객체 (Standard Built-in Object)**

---

## 📌 요약 비교: `Number` vs `number`

|구분|설명|
|---|---|
|`number`|원시 타입 (primitive)|
|`Number`|생성자 함수이자 객체|
|`new Number()`|객체 (`typeof === "object"`)|
|리터럴 메서드 사용|내부적으로 `Number` 객체로 래핑되어 사용됨|

---

## 🎯 결론

> `Number`는 `String`과 같은 부류의  
> 👉 **내장 생성자 함수(객체)**이고,  
> 👉 원시 타입을 래핑하는 **기본형 래퍼(wrapper)** 객체야.

둘은 자바스크립트의 타입 시스템과 객체 모델을 이해할 때  
아주 중요한 **쌍둥이 개념**이야.

ChatGPT에게 묻기