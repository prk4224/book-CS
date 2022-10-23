## 객체 지향 이란 ?
: 객체들이 집합으로 프로그램의 상호작용을 표현하며 데이터를 객체로 취급하여 객체 내부에 선언된 메서드를 활용하는 방식

### 객체(Object) 란 ?

#### <span style="color:indianred">타입의 인스턴스</span>
어떤 대상이 타입으로 분류될 때 그 대상을 타입의 인스턴스(Instance) 라고 부른다. 일반적으로 타입의 인스턴스를 객체 라고 부른다.

**(객체의 퍼블릭 인터페이스가 객체의 타입을 결정한다.)**

(출처: Object 437p)

- 어떤 객체들이 동일한 상태를 가지고 있더라도 퍼블릭 인터페이스가 다르다면 ?

- 어떤 객체들이 내부 상태는 다르지만 동일한 퍼블릭 인터페이스를 공유한다면 ?


### 특징

- 추상화
: 복잡한 시스템으로부터 핵심적인 개념 또는 기능을 간추려내는 것

- 캡슐화
: 객체가 내부적으로 기능을 어떻게 구현하는지를 감추는 것이다. 이를 통해 내부의 기능 구현이 변경되더라도 그 기능을 사용하는 코드는 영향을 받지 않도록 만들어 준다. 즉 내부 구현의 유연함을 주는 기법

- 상속성
: 상위 클래스의 특성을 하위 클래서가 이어받아서 재사용하거나 추가, 확장하는 것

- 다형성
: 하나의 메서드나 클래스가 다양한 방법으로 동작하는 것을 말한다. (오버로딩, 오버라이딩)



### SOLID 원칙

#### 1.<span style="color:indianred"> 단일 책임 원칙 </span> (SRP - Single Responsibility Principle)
- A class should have one, and **only one, reason to change**

: **클래스는 단 한개의 책임을 가져야 한다** 클래스가 여러 책임을 갖게 되면 그 클래스는 각 책임 마다 변경되는 이유가 발생하기 때문에, 클래스가 한개의 이유로만 변경이 되려면 클래스는 한 개의 책임만을 가져야 한다.

-  위반한 코드

![](https://velog.velcdn.com/images/pwolong/post/64b6fdd8-1663-495c-b677-df4af76080b1/image.png)

```kotlin
 val token = EncryptionPreferences.getToken() 
 val response = repository.getUserInfo(token) 
 if (response.isSuccessful) {
...
```
#### 2.<span style="color:indianred"> 개방 폐쇄 원칙 </span> (Open-Closed Principle)

- You should be able to extend a classes behavior, without modifying it.

: 소프트웨어 개체(클래스, 모듈, 함수 등)는 확장에 대해 열려 있어야 하고, 수정에 대해서는 닫혀 있어야 한다.

적용 X
![](https://velog.velcdn.com/images/pwolong/post/4b6b5932-cfdb-4e07-97f2-1c6cd8d26e2a/image.png)

적용 O
![](https://velog.velcdn.com/images/pwolong/post/d1308c93-8fe7-4323-9c59-ad34a31989f5/image.png)




 


#### 3.<span style="color:indianred"> 리스코프 치환 원칙 </span> (Liskov Substitution Principle)
- Derived classes must be substitutable for their base classes.

: 상위 타입의 객체를 하위 타입의 객체로 치환해도 상위 타입을 사용하는 프로그램은 정상적으로 동작해야한다.

위반 사례 :  Stack과 Vector

- 기능적으로는 위배되지 않지만 원칙적으로 위배된다.

#### 4.<span style="color:indianred"> 인터페이스 분리 원칙 </span> (Interface Segregation Principle)
- Make fine grained interfaces that are client specific.
 
: 인터페이스는 그 인터페이스를 사용하는 클라이언트를 기준으로 분리해야한다.

적용 X
![](https://velog.velcdn.com/images/pwolong/post/8faa65e1-911a-4c05-8961-ffe8d5445efd/image.png)

적용 O
![](https://velog.velcdn.com/images/pwolong/post/b773385c-3e13-4be7-9e38-c192d583258f/image.png)


#### 5.<span style="color:indianred"> 의존 역전 원칙 </span> (Dependency Inversion Principle)

- 고수준 모듈은 저수준 모듈의 구현에 의존해서는 안된다. 저수준 모듈이 고수준 모듈에서 정의한 추상 타입에 의존해야 한다.

- **고수준 모듈 ?**
: 더 추상화된 모듈

즉, 상대적으로 더 추상화된 모듈은 덜 추상화된 모듈의 구현에 의존해서는 안된다.

#### ❗ 이 개념은 상대적이기 때문에 언제든 의존의 역전이 일어날 수 있다.


### SOLID 원칙을 사용하는 이유 ? 

**가독성 ? 유지보수 ? **

- 단일 책임 원칙과 인터페이스 분리 원칙은 객체가 커지지 않도록 막아줘서 코드의 가독성이 좋아진다.
가독성 뿐만 아니라 객체가 많은 기능을 가지게 되면, 객체가 가진 기능은 변경여파가 그 객체의 다른 기능에 까지 번지게 되고 이는 다시 다른 기능을 사용하는 클라이언트에게까지 영향을 준다. 그래서 객체가 단일 책임을 갖게하고 클라이언트마다 다른 인터페이스를 사용하게 함으로써 한 기능의 변경이 다른 곳에 까지 미치는 영향을 최소화할 수 있고, 이는 결국 기능 변경을 보다 쉽게 할 수 있도록 만들어 준다. 

- 리스코프 치환 원칙과 의존 역전 원칙은 개방 폐쇄 원칙을 지원한다. 
: 개방 폐쇄 원칙은 변화되는 부분을 추상화하고 다형성을 이용함으로써 기능 확장을 하면서도 기존 코드를 수정하지 않도록 만들어줌으로써 유지보수가 보다 쉬워진다. 여기서, 변화되는 부분을 추상화할 수 있도록 도와주는 원칙이 바로 의존 역전 원칙이고, 다형성을 도와주는 원칙이 리스코르 치환 원칙이다.

즉, 한마디로 정의하면 변화에 유연하게 대처할 수 있는 설계원칙이다.













