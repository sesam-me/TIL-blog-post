## Object 클래스
Obejct클래스에 속한 메소드는 총 11가지이며 메소드의 이름과 내용은 아래와 같습니다.

int  hashCode() :  현재 객체의 해쉬코드 값을 반환합니다. <br/>
String  toString() :  현재 객체의 문자열로된 표현값을 반환합니다.<br/>
boolean  equals (Object obj) :  obj객체와 현재객체가 같은지 비교하여 결과를 반환합니다. (같으면 true, 다르면 false)<br/>
final Class<?>  getClass( ) :  현재 객체의 클래스 정보를 담은 Class타입의 객체를 반환합니다.<br/>
protected Object  clone( ) :  현재 객체의 복사본을 생성후 반환합니다. (Cloneable 인터페이스를 구현한 클래스만 복사 가능함)<br/>
final void  notify() :  현재 객체를 사용하기 위해 대기하고 있는 쓰레드 하나를 깨웁니다.<br/>
final void  notifyAll() :  현재 객체를 사용하기 위해 대기하고 있는 모든 쓰레드를 깨웁니다.<br/>
final void  wait() :  다른 쓰레드가 깨울때까지 현재 쓰레드를 대기시킵니다.<br/>
final void  wait(long timeoutMillis) :  다른  쓰레드가 깨우거나 정해진 시간만큼 현재 쓰레드를 대기시킵니다.<br/>
final void  wait(long timeoutMillis, int nanos) :  다른  쓰레드가 깨우거나 정해진 시간만큼 현재 쓰레드를 대기시킵니다.<br/>
protected void  finalize( ) :  객체가 소멸되기 전 자동으로 호출되는 메소드로, 현재는 Deprecated 되어 사용하지 않습니다. (삭제예정)<br/>

모든 클래스는 Object에서 상속받고, Object 클래스의 메서드 중 일부는 재정의해서 사용할 수 있다.
그렇가면 재정의 가능한 Object 클래스의 메서드 일부를 알아 보겠다!

### 💁 toString()

대표적인 Object 클래스의 메서드는 'toString()' 메서드가 있다.

객체의 정보를 String으로 바꾸어서 사용할 때 쓰이는 메서드이며,

아마 이 글을 보는 대부분의 분들께서는 @Override toString을 통해 toString()' 메서드를 재정의 하여 사용해보았을 것이다!

여기서 @Override를 사용할 수 있는 이유가 해당 클래스가 이미 Object 클래스를 상속 받았음을 알 수 있다.

### 💁 equals()

다음으로 이 역시 널리 알려진, 메서드이다.

'equals()' 메서드는, 두 인스턴스의 주소 값을 비교하여 true/false를 반환한다!

여기서 주소 값이라 하면, heap 영역의 물리적 주소를 말한다!
하지만 'equals()' 메서드는, 사용자가 재정의 하여 두 인스턴스가 논리적으로 동일함의 여부를 구현할 수 있다

즉 인스턴스가 다르더라도 논리적으로 동일한 경우 true를 반환하도록 재정의 할 수 있음

예를 들어 다른 인스턴스라도 (같은 학번, 같은 사번, 같은 아이디의 회원...)이면 같은 인스턴스라고 취급해야 한다.

### 💁 hashCode()

hashCode()는 인스턴스의 저장 주소를 반환하도록 Object Class에 정의 되어있다!

힙메모리에 인스턴스가 저장되는 방식이 hash 방식이기에 위와 같은 이름으로 메서드가 정의된 것이다.

즉, 자료의 특정 값(키 값)에 대한 저장 위치를 반환해주는 해시 함수를 사용한다.

해시함수(hash function)란 데이터의 효율적 관리를 목적으로 임의의 길이의 데이터를 고정된 길이의 데이터로 매핑하는 함수입니다. 이 때 매핑 전 원래 데이터의 값을 키(key), 매핑 후 데이터의 값을 해시값(hash value), 매핑하는 과정 자체를 해싱(hashing)라고 합니다. ex) 검색 및 정보저장에 많이 사용되는 자료구조이다.

그렇다면 두 인스턴스가 같다는 것은 무엇을 의미하는가?

두 인스턴스에 대한 equals()의 반환 값이 true
동일한 hashCode() 값을 반환
논리적으로 동일함을 위해 equals() 메서드를 재정의 하였다면 hashCode()메서드도 재정의 하여 동일한 hashCode 값이 반환되도록 한다

![image](https://github.com/sesam-me/TIL-blog_post/assets/122416681/806466bb-1edf-44aa-9c88-92d2342abcb8)

<br/>
<br/>
<br/>

## 참고링크
[[Java] 자바 - Object클래스와 메소드, equals(), toString(), getClass()](https://kadosholy.tistory.com/107) <br/>
[Java의 Object Class 에 대해 알아보자!](https://velog.io/@tsi0521/Java%EC%9D%98-Object-Class-%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)
