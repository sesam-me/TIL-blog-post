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




## 참고링크
[[Java] 자바 - Object클래스와 메소드, equals(), toString(), getClass()](https://kadosholy.tistory.com/107)
[Java의 Object Class 에 대해 알아보자!](https://velog.io/@tsi0521/Java%EC%9D%98-Object-Class-%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)