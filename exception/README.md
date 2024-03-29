# 예외처리

* [블로그 게시글 보러가기](https://sesam-dev.tistory.com/manage/newpost/151?type=post&returnURL=https%3A%2F%2Fsesam-dev.tistory.com%2F151)

## 프로그램 오류
### 1. 컴파일 에러
   컴파일 시에 발생하는 에러

📌 자바 컴파일러
1. 구문체크
2. 번역
3. 최저화
4. 생략된 구문 추가(ex. extens Object)


### 2. 런타임 에러
   실행 시에 발생하는 에러
   <br/>
<img src="C:\Users\lsi66\Desktop\TIL-blog_post\exception\src\image\예외처리1.PNG" width="400" height="400"/>

<br/>
<br/>
💡 Exception클래스들
: Exception클래스 + 자식 클래스
사용자의 실수와 같은 외적인 요인에 의해 발생하는 예외

💡 RuntimeException클래스들
:RuntimeException클래스 + 자식 클래스
프로그래머의 실수로 발생하는 예외


💡 체크드예외/언체크드예외
- 컴파일러로 체크된다.

● 체크드예외(checked)
try-catch 필수

● 언체크드예외(unchecked)
try-catch 선택
❓ 왜 언체크드예외는 try-catch가 선택인가?
개발자의 실수로 발생할 수 있는 오류까지 모두 try-catch로 잡으면 코드가 너무 길어진다.





### 3. 논리적 에러
   실행은 되지만, 의도와 다르게 동작하는 것

ex. 재고가 -(마이너스)처리 되는 등


<br/><br/><br/>


## 참고 링크

* [예외처리 (throwable, exception, error, throws)](https://sjh836.tistory.com/122)
* [자바 이론# 예외 처리](https://velog.io/@codepark_kr/%EC%9E%90%EB%B0%94-%EC%9D%B4%EB%A1%A0-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC)
