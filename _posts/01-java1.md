---
categories: JAVA
tag: [java]
---

## [JAVA] ==와 equals() 차이

- ==
  - 비교를 위한 연산자.
  - 비교하고자 하는 대상의 **주소값**을 비교한다. -> Object !
- equals()
  - 메소드이며, 객체끼리 내용을 비교할 수 있다.
  - 비교하고자 하는 **대상의 내용 자체**를 비교한다. -> String !

∴가르키는 것이 다름

[Code]

```java
String a = "a";
String b = a;
String c = new String("a"); // 새로운 객체 생성. 주소가 다름.

// 주소값을 비교.
a == b; // true
a == c; // false

// 내용(값)을 비교.
a.equals(b); // true
a.equals(c); // true
```

- 간단한 내용이지만, 회사 신입분과 이야기 할때도 나왔고,
- == 으로 코딩하여 잘못나오고 있던 데이터가 존재했다!! (경력있는 개발자가 짰던거였을텐데...)
