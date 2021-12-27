---
categories: JAVA
tag: [java]
---

## [JAVA] ==와 equals() 차이

- ==
  - 항등 연산자(Operator)
  - 참조 비교(Reference Compariso)
  - 두 객체가 같은 메모리 공간을 가리키는지 확인합니다.
  - (비교하고자 하는 대상의 **주소값**을 비교)
  - 반환 형태: boolean
  - 같은 주소면 true, 그렇지 않으면 false
  - 모든 기본 타입(Primitive Type)에도 적용 -> Object !
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

## ==

`==`

```java
public class Test {
  public static void main(String[] args) {
    System.out.println(10 == 20);  // false
    System.out.println('a' == 'b');  // false
    System.out.println('a' == 97.0);  // true
    System.out.println(true == true);  // true
  }
}
```

- 참조 타입(Reference Type)에도 적용 가능.
- 이때, 사용하는 객체 인자의 유형간에 호환성이 있어야 가능.
- 부모-자식 관계, 동일한 클래스 그렇지 않으면 컴파일 오류가 발생.

```java
public class Test {
  public static void main(String[] args) {
    Thread t = new Thread();
    Object o = new Object();
    String s = new String("hello");

    System.out.println(t == o);  // false
    System.out.println(o == s);  // false
    System.out.println(t == s);  // 컴파일 오류
  }
}
```

## equals() 메소드 동작 원리

`equals()`

- Java에서는 대상의 내용 자체를 비교한다.
- 그렇다면 두 문자열을 비교할 때, 어떤 원리로 비교할까?
- Ex) a = "Victory", b = "Victory"

```java
public boolean equals()(Object anObject){
  if(this == anObject) return true;

  if(anObject instanceof String){
    String anotherString = (String) anObject;
    int n = value.length;
    if(n == anohterString.value.length){
      char v1[] = value;
      char v2[] = anotherString.value;

      int i = 0;
      while(n-- !=0){
        if(v1[i] != v2[i]) return false;

        i++;
      }
      return true;
    }
  }
  return false;
}
```

- 간단한 내용이지만, 회사 신입분과 이야기 할때도 나왔고,
- == 으로 코딩하여 잘못나오고 있던 데이터가 존재했다!! (경력있는 개발자가 짰던거였을텐데...)

- 먼저, 같은 객체인지 비교한다. 같은 객체라면 같은 값을 가지고 있기 때문에 true를 반환하며, 아래 문장은 수행되지 않는다.
- 다음으로 인자로 들어온 Object가 String 타입인지 확인하고 조건을 만족하면 해당 객체를 String타입으로 형 변환을 한다.
- 그리고 char[] 배열로 변환한 뒤, 문자를 앞에서부터 하나씩 비교한다. 한 개의 문자라도 다르다면 false를 반환하고 모든 문자가 동일하다면 true를 반환한다.
- true -> 동일한 내용임을 의미. false -> 다른 내용임을 의미.
