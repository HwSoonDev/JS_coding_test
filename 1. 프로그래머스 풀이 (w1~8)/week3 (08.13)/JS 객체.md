# 객체 (Object)

객체는 JavaScript라는 언어만이 가지고 있는 특징의 기초를 이루는 자료형으로, **많은 기능**을 내장하고 있습니다.

객체는 한꺼번에 여러 값을 담을 수 있는 **통(container)**[1](https://helloworldjavascript.net/pages/180-object.html#fn-1)과 같은 **자료구조(data structure)**입니다. 

자료구조 이면서
메소드를 가지면서
자가 복제도 하는 ...

하지만 클래스는 쓰지 않는(?)
## 1. 객체 리터럴 (Object Literal)

객체 안에는 **이름-값 쌍(name-value pair)**이 저장되는데, 이를 객체의 **속성(property)**이라고 합니다.

아래와 같이 객체 리터럴(object literal)을 이용해서 객체를 생성할 수 있습니다. 중괄호 안에 직접 이름-값 쌍을 적어주면 됩니다.

```JS
const person = { 
name: '윤아준', // 속성 이름 - 'name', 속성 값 - '윤아준' 
age: 19, // 속성 이름 - 'age', 속성 값 - 19 
'languages': ['Korean', 'English'], // 속성 이름 - 'languages', 속성 값 - 배열 
'한국 나이': 20 // 속성 이름 - '한국 나이', 속성 값 - 20 
};
```

#### 속성 식별자 

일반 표기:
문자열 표기: 띄어쓰기 등 식별자에 허용되지 않는 문자 사용시 필수 

위에서 `person` 변수에 할당된 객체에는 네 개의 속성이 저장되었습니다. `'languages'`와 `'한국 나이'`와 같이 속성 이름 부분에 문자열을 써도 상관없습니다만, `'한국 나이'`에 들어간 공백과 같이 **식별자에 허용되지 않는 문자가 들어간 속성 이름**을 정의할 때는 **반드시 문자열 표기를 사용**해야 합니다.

#### 속성 접근자 

**점표기법 :** 
obj.index

**괄호표기법 :**
obj['index'] 


## 2. 메소드 (Method)

객체의 속성값으로 **함수**를 지정할 수도 있습니다.

```JS
const person = { 
	greet: function() { 
		return 'hello'; 
	} 
}; 
person.greet(); // 'hello';
```

위와 같이 **어떤 객체의 속성으로 접근해서 사용하는 함수**를 **메소드(method)** 라고 부릅니다.

## 3. this

다른 함수들과 달리 '메소드'라는 특별한 이름을 사용하는 이유는, 메소드가 다른 함수들과는 다르게 특별히 취급되기 때문입니다. `this` 키워드를 사용하면, 메소드 호출 시에 해당 메소드를 갖고 있는 객체에 접근할 수 있습니다.

## 4. 프로토타입 (Prototype)

우리가 쓰는 대부분의 프로그램들은 아주 많은 수의 비슷한 객체를 만들어냅니다.

- 스프레트시트의 **셀**
- 슈팅 게임에서의 **총알**
- DOM API의 **[HTMLElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement)**

이 객체들은 아마도 **각각 다른 속성**을 가지고 있을 것입니다.

- 셀 안에 들어있는 **데이터**
- 총알의 **현재 위치**
- HTMLElement의 **[인라인 스타일](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style)**

그렇지만, 그 수가 아무리 많더라도 **공통으로 사용하는 속성과 메소드**들이 있을 것입니다.

- 셀의 내용을 **편집하는 메소드**
- 총알의 **모양**
- 특정 HTMLElement에 키보드 포커스를 맞추는 메소드인 focus

```JS
// 사람을 나타내는 객체를 생성하는 팩토리 함수

function personFactory(name) {
  return {
    name,
    introduce: function() {
      return `안녕하세요, 제 이름은 ${this.name}입니다.`;
    }
  };
}

const people = [];

for (let i = 0; i < 1000; i++) {
  people.push(personFactory('윤아준'))
}

people[0].introduce === people[1].introduce // false
```

JS에서 객체는 클래스가 만들지 않는다.
클래스는 쓰지 않지만 객체는 있는 신기한 자바스크립트

### 프로토타입 상속 - Object.create()

JavaScript에서는 이렇게 객체 간에 공유되어야 하는 속성과 메소드를, 프로토타입(prototype)이라는 기능을 이용해서 효율적으로 저장할 수 있습니다. 어떤 객체에 프로토타입을 지정하면, 프로토타입의 속성을 해당 객체에서 **재사용**할 수 있습니다. 객체의 프로토타입을 지정하는 방법에는 여러 가지가 있는데, 가장 쉬운 방법은 `Object.create` 함수를 이용하는 것입니다.

```JS
const personPrototype = {
  introduce: function() {
    return `안녕하세요, 제 이름은 ${this.name}입니다.`;
  }
};

const person1 = Object.create(personPrototype); // 새 객체를 생성하고 프로토타입을 지정함
person1.name = '윤아준';

const person2 = Object.create(personPrototype);
person2.name = '신하경';

person1.introduce(); // 안녕하세요, 제 이름은 윤아준입니다.
person2.introduce(); // 안녕하세요, 제 이름은 신하경입니다.

person1.introduce === person2.introduce; // true
```

이렇게 프로토타입 기능을 이용해 한 객체에서 다른 객체의 기능을 가져와 사용하는 것을 **프로토타입 상속(prototype inheritance)** 
이라고 합니다. 위와 같은 경우는 **"`personPrototype`은 `person1`의 프로토타입이다."**, **"`person1` 객체는 `personPrototype` 객체를 상속받았다"** 고 표현합니다. 프로토타입 상속은 다른 언어에서는 흔히 찾아볼 수 없는 JavaScript의 특징적인 기능입니다.

### 프로토 타입 체인

더 자세한 내용은...
https://helloworldjavascript.net/pages/180-object.html#%EC%83%9D%EC%84%B1%EC%9E%90-constructor