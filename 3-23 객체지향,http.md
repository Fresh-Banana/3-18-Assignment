# http란?
* `정의:`클라이언트와 서버가 데이터를 교환하기 위해 사용되는 프로토콜입니다

# http Method
* `정의:`서버가 수행해야 할 동작을 명시하여 요청을 보내는 방법
* `get:`특정 데이터를 갖고올때 사용함
    * ex) 블로그 글 보기
    * 단순 조회만
* `HEAD:`데이터 존재여부 확인
    * 파일 크기/날짜/타입 정보등
* `post:`새로운 게시글을 작성할때 사용
    * 회원가입등
* `put:` 기존 데이터를 전체 수정할때 사용
* `patch:`일부 필드만 수정할때 사용
* `delete:`데이터를 삭제할때 사용
  
  # http Status code란?
* `정의:`서버가 클라이언트의 요청을 어떻게 처리했는지 알려주는 숫자 코드
  ## 상태 코드의 종류
* `1xx code:`요청은 받았지만 처리중인 상태
* `2xx code:` 정상적으로 처리하여 성공
* `3xx code:`리다이렉션 다른주소로 이동 필요
* `4xx code:`클라이언트 오류로 요청의 문제가 있음
* `5xx code:`서버오류로 서버쪽 문제로 처리 실패
 ## 상태 코드들의 대표적인 예
* `200:`요청 성공 새로운 리소스 생성
* `204:`요청성공,응답 데이터 없음
* `301:`주소 영구 이동
* `302:`다른 주소로 이동
*  `400:`요청 자체가 잘못됨
*  `401:`인증 필요
*  `403:`접근 권한이 없음
*  `404:`해당 주소의 페이지 없음
*  `500:`서버 내부 오류
*  `502:`게이트웨이 또는 프록시 서버 오류
* `503:`서버 과부하 또는 서버 점검중
  
  ## HTTP 무상태성
* `정의:`서버가 클라이언트의 요청이 끝나면 정보를 삭제함
## 정보의 저장위치
* 쿠키->클라이언트
* 세션->서버
* 토큰->클라이언트에 저장
  
  # 추상화
* `정의:`각 사물의 공통적인 개념을 하나의 메소드로 묶는것
```java
  abstract class Shape {
    abstract void draw();   // 구현 없음
}

class Circle extends Shape {
    void draw() {
        System.out.println("원을 그린다");
    }
}

public class Main {
    public static void main(String[] args) {
        Shape s = new Circle();
        s.draw();
    }
}
```
  # 캡슐화
* `정의:`외부에서 어떤 데이터를 바꾸지 못하게한다
    * ex) private써서 의존도를 낮추고 결합성을 낮춤
```java
  class Account {
    private int balance;   // 외부 접근 불가

    public void deposit(int money) {
        balance += money;
    }

    public int getBalance() {
        return balance;
    }
}

public class Main {
    public static void main(String[] args) {
        Account a = new Account();
        a.deposit(1000);
        System.out.println(a.getBalance());
    }
}
```
# 상속성
* `정의:` 기존의것을 재사용하고 확장하는것임
```java
class Animal {
    void sound() {
        System.out.println("동물이 소리를 낸다");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("멍멍");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.sound();  // 부모 기능 사용
        d.bark();
    }
}
```
# 다형성
* `정의:`하나의 요청을 각각 다르게 행동을 하게 함
```java
  class Animal {
    void sound() {
        System.out.println("동물 소리");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("야옹");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("멍멍");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a1 = new Cat();
        Animal a2 = new Dog();

        a1.sound();
        a2.sound();
    }
}
```