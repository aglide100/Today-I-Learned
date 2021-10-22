# SingleTone(싱글톤)

싱글톤이란 전체 시스템에서 하나의 인스턴스만 존재하도록 보장하는 객체 생성패턴을 의미한다.

이러한 방법은 가장 간단하게 객체를 이용하여 구현이 가능하다.

```javascript
    const a = {1,2};
    const b = {3,4}
```

일때 a, b는 각각 단 하나의 객체만이 존재하게 되는 것이다.

여기서 객체 리터럴이란 객체를 생성자(`new`)을 사용해서 생하는 것이 아닌 `{}`을 이용하는 것이다.

하지만 이러한 객체 리터럴로 객체를 생성하는 방식은 비공개 상태 및 함수를 정의하기가 힘들어진다.

이에 따라 대부분의 라이브러리에서 외부에서 접근가능한 비공개 맴버를 가지고 있다.

자바스크립트에서는 이러한 접근가능한 비공개 맴버를 위해서면 클로저를 이용하여야 한다.

대표적인 es6에서 추가된 클래스를 이용한 싱글톤 패턴은 이용한 예제는 아래와 같다.

```javascript
    class Person{
        private static instance: Person;
        private static name: String

        constructor() {}

        public static getInstance(): Person {
            if (!Person.instance) {
                Person.instance = new Person();
            }

            return Person.instance;
        }

        public getName():String {
            return Person.name;
        }

        public setName(name:String) {
            Person.name = name;
        }
    }
```

```javascript
var person = Person.getInstance();
var name = person.getName();
```

위에서는 `getInstance()`를 통해 Person클래스의 인스턴트를 가져온다.

이러한 `instance`을 통해 해당되는 클래스의 클로저를 가지고 접근자를 통해 객체의 공개된 함수나 변수를 사용이 가능해진다.

## 참고 자료:

---

> https://velog.io/@recordboy/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%8B%B1%EA%B8%80%ED%86%A4-%ED%8C%A8%ED%84%B4

> https://webclub.tistory.com/150
