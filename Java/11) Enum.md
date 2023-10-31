# 목표
자바의 열거형에 대해 학습하세요.
<br>

## 학습할 것
- enum 정의하는 방법
- enum이 제공하는 메소드 (values()와 valueOf())
- java.lang.Enum
- EnumMap
- EnumSet
<br>


### enum 정의하는 방법
---
  #### Enum
  - Enumeration (열거체).
  - 관련 있는 상수 집합의 정의. (관련 상수를 편리학 정의 및 사용을 위함.)
  - 정의된 값 이외의 값은 허용하지 않는다.
  - 클래스 정의와 비슷한 방법으로 정의한다.
  - 클래스 정의의 `class` 대신 `enum` 키워드 사용하여 열거체 정의.

  **유형**
  ```java
  접근제어자 enum Enum클래스명 {
    // 상수 집합
  }
  ```

  **For example**
  ```java
  public enum RobotEnum {
    GIPSY DANGER, STRIKER EUREKA, CHERNO ALPHA, CRIMSON TYPHOON
  ]
  ```
<br>

  #### Enum 의 특징
  - **class**와 동일하게 `클래스 내부`, `클래스 외부`, `별도의 java파일`로 선언 가능.

  **class 내부**
  ```java
  package EnumOfRobot;

  public class Robot {
    public enum RobotEnum {
      GIPSY DANGER, STRIKER EUREKA, CHERNO ALPHA, CRIMSON TYPHOON
    }    
  }
  ```

  **class 외부**
  ```java
  package EnumOfRobot;

  public class Robot {
    private int Size;
  }

  public enum RobotEnum {
    GIPSY DANGER, STRIKER EUREKA, CHERNO ALPHA, CRIMSON TYPHOON
  }   
  ```

  **별도의 java파일**
  ```java
  package EnumOfRobot;

  public enum RobotEnum {
    GIPSY DANGER, STRIKER EUREKA, CHERNO ALPHA, CRIMSON TYPHOON
  }   
  ```

  - 열거형으로 선언된 순서에 따라 `0`부터 인덱스 값을 가진다. (배열과 동일)
  - Enum 열거형으로 선언된 상수들은 모두 `대문자`로 입력한다.
  - 열거형 변수 선언 후 `세미콜론(;)`을 입력하지 않는다. (예외 존재)
<br>


### enum이 제공하는 메소드 (values()와 valueOf())
---
  #### values()
  - enum의 요소들을 순서대로 `enum타입의 배열로 리턴`.

  **For example**
  ```java
  package EnumOfRobot;

  public class PrintRobot {
    public static void main(String[] args) {
      for (RobotEnum Robot1 : RobotEnum.values()) {    // values() 사용.
        System.out.println(Robot1);
      }
    }
  }

  enum RobotEnum {
    GIPSY DANGER, STRIKER EUREKA, CHERNO ALPHA, CRIMSON TYPHOON
  }
  ```
  ```
  GIPSY DANGER
  STRIKER EUREKA
  CHERNO ALPHA
  CRIMSON TYPHOON
  ```
<br>

  #### valueOf()
  - String 값을 enum에서 가져옴. 값이 없으면 `IllegalArgumentException` 예외 발생.

  **For example**
  ```java
  package EnumOfRobot;

  public class PrintRobot {
    private String Name;

    public static void main(String[] args) {
      RobotEnum Robot1 = RobotEnum.valueOf("STRIKER EUREKA")
      System.out.println(Robot1);
    }
  }

  enum RobotEnum {
    GIPSY DANGER, STRIKER EUREKA, CHERNO ALPHA, CRIMSON TYPHOON
  }
  ```
  ```
  STRIKER EUREKA
  ```
<br>


### java.lang.Enum
---
  - 모든 자바 열거체의 공통된 조상 클래스.
  - 열거체 조작을 위한 다양한 메소드 포함. (values(), valueOf() ordinal() 등)
  - 모든 Enum 클래스는 `java.lang.Enum`클래스를 상속받는다.
> `다중 상속` 불가.
<br>


### EnumMap
---
  #### HashMap

  #### EnumMap 사용
<br>


### EnumSet
---
<br>


___
___
#### REFERENCE
>
