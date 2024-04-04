# 디자인패턴

### 디자인패턴이란?
프로그램을 설계할 때 발생했던 문제점들을 객체 간의 상호 관계 등을 이용하여 해결할 수 있도록 하나의
’규약‘형태로 만들어 놓은 것을 의미

1. 싱글톤 패턴(singleton pattern)
   하나의 클래스에 오직 하나의 인스턴스만 가지는 패턴

하나의 인스턴스를 만들어 놓고 해당 인스턴스를 다른 모듈들이 공유하며 사용하기 때문에, 보통 데이터베이스 연결 모듈에 많이 사용한다.
장점 : 인스턴스 생성할 때 드는 비용이 줄어든다. 왜??????
단점 : 의존성이 높아진다.

인스턴스


* Java로 싱글톤 패턴을 구현하는 7가지 방법



2. 팩토리 패턴(factory pattern)
팩토리 패턴에는 2가지가 있다.

먼저 심플 팩토리(Simple Factory) 패턴을 알아보자.

#### 💡 심플 팩토리 패턴
객체 만드는 작업을 하나의 팩토리 클래스에 모아두는 것을 의미한다.




심플 팩토리 패턴에서 createPhone() 부분에서 Factory에서 직접 객체를 만드는 것을 Factory를 상속한 서브클래스에서 객체를 만들게끔 하는 것이 팩토리 메소드 패턴이다.

위의 코드에 팩토리 메소드 패턴을 적용해보자.



#### ① 팩토리 메소드 패턴

클래스의 인스턴스를 만드는 일을 서브클래스에게 맡기는 것이다.
심플 팩토리 패턴에서 만들었던 객체 생성하는 함수를 모아둔 클래스를 인터페이스화하여 서브클래스에서 어떤 객체를 생성할지 결정하는 것이다.

<img src="C:\Users\lsi66\Desktop\TIL-blog-post\deisgnPattern\src\image\디자인패턴1.PNG" width="400" height="400"/>

<img src="C:\Users\lsi66\Desktop\TIL-blog-post\deisgnPattern\src\image\디자인패턴2.PNG" width="400" height="400"/>



이렇게 서브 클래스를 둔다면 아이폰, 안드로이드폰의 종류가 열개로 늘어난다 해도 Phone 구현체 클래스 생성과 createPhone()의 분기처리만 하면 확장이 가능한 구조가 된다.

즉 클래스 만들 때 확장은 가능하게 하되, 한번 만들면 추후에 수정할 필요 없게 만들라는 원칙인 OCP (개방 폐쇄의 원칙 : Open Close Principle)를 따르게 된다.





#### ② 추상 팩토리 패턴

구체적인 클래스에 의존하지 않고 서로 연관되거나 의존적인 객체들의 조합을 만드는 인터페이스를 제공하는 패턴이다.

먼저 위에서 본 메소드 팩토리 패턴에서는 PhoneFactory의 구현체 IPhoneFactory, AndroidPhoneFactory가 각각 IPhone객체 AndroidPhone객체 하나씩을 생성하게끔 작성했다.

추상 팩토리 패턴은 이것을 한번더 감싸서 하나의 Factory에서 여러개의 제품군(Product)조합을 생성할 수 있게 해주는 패턴이다.


<img src="C:\Users\lsi66\Desktop\TIL-blog-post\deisgnPattern\src\image\디자인패턴3.PNG" width="400" height="400"/>
<img src="C:\Users\lsi66\Desktop\TIL-blog-post\deisgnPattern\src\image\디자인패턴4.PNG" width="400" height="400"/>





💬 코드보기

///
public interface PhoneFactoryOfFactory {
PhoneFactory requestPhone(String company);
}
public class DefaultPhoneFactoryOfFactory implements PhoneFactoryOfFactory{
@Override
public PhoneFactory requestPhone(String company) {
switch (company) {
case "IPHONE":
return new IPhoneFactory();
case "ANDROID":
return new AndroidPhoneFactory();
}
throw new IllegalArgumentException();
}
}
///

///
public interface PhoneFactory {
Phone createPhone();
OS createOS();
}
public class IPhoneFactory implements PhoneFactory{
@Override
public Phone createPhone() {
OS os = createOS();
os.installOS();
return new IPhone();
}
@Override
public OS createOS() {
return new IOS();
}
}
public class AndroidPhoneFactory implements PhoneFactory{
@Override
public Phone createPhone() {
OS os = createOS();
os.installOS();
return new AndroidPhone();
}
@Override
public OS createOS() {
return new GoogleOS();
}
}
///

///
public interface OS {
void installOS();
}
public class IOS implements OS {
@Override
public void installOS() {
System.out.println("IOS 설치");
}
}
public class GoogleOS implements OS {
@Override
public void installOS() {
System.out.println("구글OS 설치");
}
}
///

///
public interface Phone {
public void call();
public void playGame();
}
public class IPhone implements Phone{
@Override
public void call() {
System.out.println("아이폰으로 전화하다");
}

    @Override
    public void playGame() {
        System.out.println("아이폰으로 게임하다");
    }
}
public class AndroidPhone implements Phone{
@Override
public void call() {
System.out.println("안드로이드로 전화하다");
}

    @Override
    public void playGame() {
        System.out.println("안드로이드로 게임하다");
    }
}
///

public class Main {
public static void main(String[] args) {
PhoneFactoryOfFactory phoneFactoryOfFactory = new DefaultPhoneFactoryOfFactory();
PhoneFactory iphoneFactory= phoneFactoryOfFactory.requestPhone("IPHONE");   //아이폰을 산다.
Phone iphone = iphoneFactory.createPhone();
iphone.call();
iphone.playGame();

        PhoneFactory androidPhoneFactory = phoneFactoryOfFactory.requestPhone("ANDROID");   //안드로이드폰을 산다.
        Phone androidPhone = androidPhoneFactory.createPhone();
        androidPhone.call();
        androidPhone.playGame();
    }
}

//결과
IOS 설치
아이폰으로 전화하다
아이폰으로 게임하다
구글OS 설치
안드로이드로 전화하다
안드로이드로 게임하다




#### 정리!

팩토리 메소드 패턴은 객체생성하는 인스턴스를 인터페이스화하여 서브클래스에 맡기는 것이다.

추상 메소드 패턴은 추상적인 메소드(서브클래스)의 조합을 만드는 인터페이스를 제공하는 패턴이다.



즉 팩토리 메소드 패턴을 여러개 만들어 한 interface에 모아둔 것을 추상 메소드 패턴이라 한다!

<img src="C:\Users\lsi66\Desktop\TIL-blog-post\deisgnPattern\src\image\디자인패턴5.PNG" width="400" height="400"/>



#### 참고링크
[[디자인 패턴] 팩토리 패턴 종류/개념/예제](https://cjw-awdsd.tistory.com/54)

3. 전략 패턴

4. 옵저버 패턴

5. 프록시 패턴과 프록시 서버

6. 이터레이터 패턴

7. 노출모듈 패턴

8.  MVC 패턴

9. MVP 패턴

10. MVVM 패턴