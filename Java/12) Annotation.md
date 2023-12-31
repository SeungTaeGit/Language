# 목표
자바의 애노테이션에 대해 학습하세요.
<br>

## 학습할 것
- 애노테이션 정의하는 방법
- @Retention
- @Target
- @documented
- 애노테이션 프로세서
<br>


### 애노테이션 정의하는 방법
---
  #### Annotation
  - 해석 그대로의 뜻으로 `주석`.
  - `java.lang.annotation.Annotation`클래스를 조상으로 보유.
  - **약속된 형식의 정보**를 제공.
<br>

  #### Annotation 정의
  - Annotation의 정의는 `인터페이스`정의 방법과 유사.
  - 인터페이스의 정의에서 `interface` 키워드 앞에 `@`표시를 함께 명시한다.

  **유형**
  ```java
  @interface 어노테이션명 {
    // 타입 요소
  }
  ```
<br>


### @Retention
---
  - 어노테이션을 어디까지 가지고 사용할 것인지 정의하는 어노테이션.
  - `어노테이션이 유지되는 기간을 지정`.
<br>


### @Target
---
  - `어노테이션을 적용할 수 있는 위치`를 의미하는 어노테이션.
<br>


### @documented
---
  - `어노테이션의 스펙을 자바 문서화`시키는 어노테이션.
  - `주석`부분을 문서화.
  - `javadoc`파일에 추가할지 여부 결정.
<br>


### 애노테이션 프로세서
---
  #### Meta Annotation
  - 커스텀 어노테이션 제작을 위해 제공된 어노테이션.
> **Built-in Annotation** : Java 에서 기본적으로 제공하는 어노테이션.
<br>


___
___
#### REFERENCE
>
>
