## 벡터(Vector)
: 동적으로 요소를 할당할 수 있는 동적 배열

### <span style="color:indianred">Vector vs ArrayList</span>
: 먼저, Vector와 ArrayList는 동일한 내부 구조를 가지고 있다.

```java
public class Vector<E> extends AbstractList<E> 
		implements List<E>, RandomAccess, Cloneable, Serializable {
}

public class ArrayList<E> extends AbstractList<E> 
		implements List<E>, RandomAccess, Cloneable, Serializable {
}
```

위와 같이 같은 Class나 Interface를 상속받는 것을 볼 수 있다.

#### 차이점 ?

- **동기화**
 1. Vector는 한번에 하나의 스레드에서만 접근이 가능
 2. ArrayList는 동시에 여러 스레드에서 작업이 가능하다 (때문에 ArrayList를 사용할 때는 명시적으로 동기화가 필요하다.)
 
- 크기
1. Vector는 기존 용량의 100% (2의 N+1승 만큼 증가)
2. ArrayList 기존 용량의 50%
 
- 성능
: 동기화 되지 않는 ArrayList가 성능이 좋다

#### Vector를 사용하지 않는 이유 ?
 
- 완전한 동기화
: ArrayList와의 차이점이 동기화가 된다는 것인데, 사실 Vector는 완전한 동기화가 되지 않는다. 작업간의 동기화는 가능하지만 전체적으로 동기화 하지 않는다. 그러므로 성능이 좋은 ArrayList를 사용.


#### 그렇다면 왜 Vector는 없어지지 않는 것일까 ?
: Vector는 JDK1.0 부터 사용해 오던 Class 이다. 그래서 Vector를 상속 받는 Class들이 많아 호환성을 위해 아직 존재하고 있다.
