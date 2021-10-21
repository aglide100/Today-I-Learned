# Closure(클로저)

MDN에서는 클로저는 함수의 함수가 선언된 어휘적 환경의 조합이라고 설명한다.

이러한 클로저의 이해를 위해서라면 변수의 어휘적 범위 지정(Lexical scoping)에 대한 이해가 필요하다.

## 어휘적 범위 지정(Lexical scoping)이란?

어휘적 범위 지정(Lexical scoping)이란 간단하게 얘기하자면 변수가 어디에서 선언되고 사용되는지, 이 범위가 내부인지 외부인지에 대한 범위이다.

아래는 MDN에서 소개한 예시이다.

```javascript
function init() {
  var name = "Mike";
  function displayName() {
    alert(name);
  }
  displayName();
}
init();
```

예시 코드에서 `alert(name)`은 부모 영역에서 선언된 지역 변수인 `name`을 호출했음을 짐작할 수 있다.

이때 `displayName()`은 `init()`안에 정의된 내부 함수이며 함수 내부에서 외부 함수의 변수에 접근을 할 수 있다는 것을 알 수 있다.

만약 `displayName()`에서 동일한 name이라는 지역변수를 가지고 있었다면 `this.name`을 사용하였을 것이다.

여기서 파서가 변수를 어떻게 처리하는 짐작할 수 있다.

내부함수인 `displayName()`에서 부모의 영역에서 `name`이라는 것을 호출할 수 있는 것을 보아 중첩된 함수는 외부 범위(scope)에서 선언한 변수에도 접근할 수 있다.

---

예시를 좀더 살펴보자면

```javascript
function makeFunc() {
  var name = "Mike";
  function displayName() {
    alert(name);
  }
  return displayName();
}

var myFunc = makeFunc();
myFunc();
```

위의 코드에서 일반적으로 `makeFunc()`에서 지역변수인 `name`은 실행이 끝났으니 리턴 된후 사라질 것(접근이 안될것)이라고 생각할 수 있지만 자바스크립트의 경우는 조금 다르다.

그 이유는 자바스크립트는 일급객체가 존재하는 언어이며 이때 생성되는 함수는 함수를 리턴하고, 리턴하는 함수가 클로저를 형성하기 때문이다. 클로저는 함수와 함수가 선언된 어휘적 환경의 조합이다. 이 환경은 클로저가 생성된 시점의 유효 범위 내에 있는 모든 지역 변수로 구성된다.

위의 코드에서 `myFunc`는 `makeFunc`이 실행될 때 생성된 함수의 인스턴스에 대한 참조이다.

이러한 상황은 `displayName`의 인스턴스는 변수 `name`이 있는 어휘적 환경에 대한 참조를 유지한다고 볼 수 있다.

이러한 이유로 `myFunc`가 호출될 때 `myFunc`은 `makeFunc`에 대한 인스턴스를 가지고 있게된다, 즉 `displaName`의 인스턴스는 변수 `name`에 대한 어휘적 환경에 대한 참조를 유지한다고 할 수 있다.

정리하자면 `myFunc`가 호출될 때 `name`에 대한 어휘적 환경에 대한 참조는 유지되어 `name`이 사용할 수 있는 상태로 남게 되는것이다.

이를 클로저라고 부르는 것이다.

## 다른 예

```javascript
function add(a, b, callback) {
  var result = a + b;
  callback(result);
  var count = 0;
  var history = function () {
    count++;
    return count + " : " + a + " + " + b + " = " + result;
  };
  return history;
}

var add_history = add(10, 10, function (result) {
  console.log("add two argument : " + result);
});

console.log("add two argument : " + add_history());
console.log("add two argument : " + add_history());
console.log("add two argument : " + add_history());
```

실행결과

```
add two argument : 1 : 10 + 10 = 20
add two argument : 2 : 10 + 10 = 20
add two argument : 3 : 10 + 10 = 20
```

---

참고자료:https://developer.mozilla.org/ko/docs/Web/JavaScript/Closures
