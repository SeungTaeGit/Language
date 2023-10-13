# 목표
자바 소스 파일(.java)을 JVM으로 실행하는 과정 이해하기

## 학습할 것
* JVM이란 무엇인가
* 컴파일 하는 방법
* 실행하는 방법
* 바이트코드란 무엇인가
* JIT 컴파일러란 무엇이며 어떻게 동작하는지
* JVM 구성 요소
* JDK와 JRE의 차이
<br>


### 1. JVM이란 무엇인가
---
  - JVM(Java Virtual Machine) 자바 가상 머신을 줄여 부르는 용어이다.
  - OS와 JAVA Application 사이에서 중재자 역할을 한다.
  - 자바 컴파일러에 의해 바이트 코드로 변환된 자바 소스 파일을 클래스 로더를 통해 읽어 자바 API와 함께 실행한다.
<br>

> **- Why use?** <br><br>
>   모든 프로그래밍 언어는 application(source) -> compilered source -> OS -> Hardware 의 구조를 가진다.<br>
>   위 구조의 경우 사용하는 OS에 따라 코드해석을 달리 해야한다.<br>
>    -> java의 경우 JVM을 사용, 자바 바이트코드(.class)파일을 실제 사용중인 OS에 맞는 특화된 코드로 변환하여 실행한다.
<br>


### 2. 컴파일 및 실행하는 방법
---
  - Compile : 사람이 읽기 쉬운 소스 코드를 컴퓨터가 읽기 쉽게 변환해주는 개념.
  - Java 컴파일의 경우 사람이 작성한 프로그래밍 코드를 JVM이 이해할 수 있는 수준으로 변환하는 작업.
<br>
  <p align="center"><img src="https://github.com/SeungTaeGit/ComputerScience/assets/129585999/6e724309-1a75-446d-a980-2b14f225b067"></p>
  
  #### Java 컴파일 및 실행 과정
    1) 개발자가 자바 소스코드(.java)를 작성.   (.java 파일 생성)
    2) 자바 컴파일러가 자바 소스코드(.java)파일을 읽어 바이트코드(.class)코드로 컴파일.  (.java -> .class 파일 생성)
      -> 이 단계에서 생성된 .class파일은 OS가 아직 이해하지 못하는 코드로 구성.
    3) 컴파일된 바이트코드(.class)를 JVM으로 전달.
<br><br>


### 3. 바이트코드란 무엇인가
---
  - JAVA 컴파일 과정에서 생성되는 .class 파일.
  - 자바 가상머신(JVM)이 실행하는 명령어의 형태.

> 명령어의 크기가 1byte라서 바이트 코드라고 불리며, 자바 가상 머신에 의해 실행되는 바이너리 코드(binary code)로 CPU에 의해 직접 실행되지 않고, 자바 가상 머신에 의해 인터프리터 방식으로 실행.
<br>


### 4. JIT(Just In Time) 컴파일러란 무엇이며 어떻게 동작하는지
---
**- Java는 인터프리터 방식과 컴파일 방식 2가지를 모두 사용하는 언어다.** <br>
 * Java의 인터프리터 방식 : 바이트코드를 인터프리터. (이 부분에서 JIT 컴파일러 사용)<br>
 * Java의 컴파일 방식 : 바이트코드로 컴파일. (Java 컴파일러 사용)<br>

> 인터프리터 방식 : 소스코드를 빌드시에 암것도 하지 않다가, 런타임시에 한줄 한줄 읽어가며 변환.<br>
> 컴파일 방식 : 소스코드를 한꺼번에 컴퓨터가 읽을 수 있는 native machine (기계)어로 변환.<br>

<p align="center"><img src="https://github.com/SeungTaeGit/ComputerScience/assets/129585999/e96c215c-cf24-4e52-b2b8-711b22a1d6d6"></p>

  ### JIT Compiler
  - **프로그램을 실제 실행하는 시점에 (실시간에) 기계어로 번역하는 컴파일 기법.**
  - JIT 컴파일러는 바이트코드를 인터프리터 방식으로 컴파일하다 적절한 시점에 바이트코드 전체를 네이티브 코드로 변경. <br>
    (이때 네이티브 코드는 캐시에 저장)
  - 변경된 네이티브 코드는 캐시에 저장하기 때문에 한 번 컴파일된 코드를 재사용할 경우 빠른 명령 수행이 가능.

<br><br>


### 5. JVM 구성 요소
---
  **OS 및 JVM 동작 방식**
  1) 자바 프로그램을 실행하면 JVM은 OS로부터 메모리를 할당받는다.
  2) 자바 컴파일러(javac)가 자바 소스코드(.java)를 자바 바이트 코드(.class)로 컴파일 한다.
  3) Class Loader는 동적 로딩을 통해 필요한 클래스들을 로딩 및 링크 하여 Runtime Data Area(실질적인 메모리를 할당 받아 관리하는 영역)에 올린다.
  4) Runtime Data Area에 로딩 된 바이트 코드는 Execution Engine을 통해 해석된다.
  5) 이 과정에서 Execution Engine에 의해 Garbage Collector의 작동과 Thread 동기화가 이루어진다.
<br>

  **JVM(Java Virtual Machine) 구조**<br>
  JVM 동작 과정 중 Class Loader ↔ Execution Engine ↔ Runtime Data Area 부분을 상세히 표현한 그림.
  <p align="center"><img src="https://github.com/SeungTaeGit/ComputerScience/assets/129585999/b157e002-c26b-467e-a655-0373e0f70652"></p>
<br>

  보기와 같이 **JVM(Java Virtual Machine) 구성**은
  * 클래스 로더(Class Loader)
  * 실행 엔진(Execution Engine)
      * JIT 컴파일러(JIT Compiler)
      * 인터프리터(Interpreter)
      * 가비지 콜렉터(Garbage collector)
  * 런타임 데이터 영역(Runtime Data Area)
      * 메소드 영역(Method Area)
      * 힙 영역(Heap)
      * PC Register
      * JVM 스택(JVM Stack)
      * 네이티브 메소드(Native Method Stack)
  * 네이티브 메소드 인터페이스 (Native Medthod Interface)
  * 네이티브 메소드 라이브러리 (Native Method Library)로 이루어진다.
<br>

  #### Class Loader
    - JVM 내로 클래스 파일(*.class)을 동적으로 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈.
    - 클래스 파일의 로딩 순서는 Loading(로드) → Linking(링크) → Initialization(초기화) 3단계로 구성.
  <p align="center"><img src="https://github.com/SeungTaeGit/ComputerScience/assets/129585999/3713ed10-662a-46a7-ba1f-803ee31b53f4"></p>
  
>  **Loading(로드)** : .class 파일을 읽어들여 JVM의 메모리에 로드.<br><br>
>  **Link(링크)** : 로드한 .class 파일을 검증.<br>
>  * Verify(검증) : .class 파일의 유효성 체크<br>
>  * Prepare(준비) : 클래스 변수와 기본값에 필요한 메모리 할당<br>
>  * Resolve(분석) : 클래스의 상수 풀 내 모든 심볼릭 레퍼런스를 다이렉트 레퍼런스로 변경<br>
>
>  **Initialization(초기화)** : 클래스 내의 변수들을 적절한 값으로 초기화.
<br>
  
  #### Execution Engine
    - 클래스 로더를 통해 런타임 데이터 영역에 배치된 바이트 코드를 명령어 단위로 읽어서 실행.
    - 바이트 코드를 운영체제에 맞게 해석해주는 역할 수행.
>  **JIT Compiler** : 자주 실행되는 바이트 코드 영역을 런타임 중에 기계어로 컴파일하여 사용.<br><br>
>  **Interpreter** : 바이트 코드를 읽고(read), 운영체제가 실행할 수 있도록 기계어로 변경하는 역할 수행.<br><br>
>  **Garbage collector** : Runtime Data Area의 Heap 메모리 영역에서 더는 사용하지 않는 메모리를 자동으로 회수.<br>
<br>

  #### Runtime Data Area
    - JVM의 메모리 영역.
    - 자바 애플리케이션을 실행할 때 사용되는 데이터들을 적재하는 영역.
  <p align="center"><img src="https://github.com/SeungTaeGit/ComputerScience/assets/129585999/7f336c42-c5a2-4a59-bd8d-2fd32aee00ff"></p>
  
>  **Method Area** : 클래스 멤버 변수의 이름, 데이터 타입, 접근 제어자 정보와 같은 각종 필드 정보들과 메서드 정보, 데이터 Type 정보, Constant Pool, static변수, final class 등이 생성되는 영역.<br><br>
>  **Heap** : new 키워드로 생성된 객체와 배열이 생성되는 영역. 주기적으로 GC가 제거하는 영역.<br><br>
>  **PC Register** : Thread가 생성될 때마다 생성되는 영역으로 프로그램 카운터, 즉 현재 스레드가 실행되는 부분의 주소와 명령을 저장하고 있는 영역.<br><br>
>  **JVM Stack** : 지역변수, 파라미터, 리턴 값, 연산에 사용되는 임시 값 등이 생성되는 영역.<br><br>
>  **Native Method Stack** : 자바 외 언어로 작성된 네이티브 코드를 위한 메모리 영역.<br>
<br>

  #### Native Medthod Interface
    - 자바가 다른 언어로 만들어진 어플리케이션과 상호 작용할 수 있는 인터페이스 제공하는 프로그램.
    - JVM이 Native Method를 적재하고 수행할수 있도록 도움.
  #### Native Method Library
    - C, C++로 작성된 라이브러리.
    - 헤더가 필요하면 JNI는 이 라이브러리를 로딩해 실행.
  
<br><br>


### 6. JDK와 JRE의 차이
---
  #### JRE
    - Java Runtime Environment. 자바 실행 환경.
    - JVM 뿐만 아니라 Java binaries, Java 클래스 라이브러리 등을 포함.
  #### JDK
    - Java Development Kit. 자바 개발 키트.
    - 자바 애플리케이션을 개발하기 위한 환경 지원.
    - JRE를 포함할 뿐만 아니라 컴파일러(javac), javadoc, jar 등 개발에 유용한 도구들을 포함.
    
<p align="center"><img src="https://github.com/SeungTaeGit/ComputerScience/assets/129585999/0899f808-a74a-4831-91b9-a3ec09f0bafe"></p>


___
___
#### REFERENCE
> + Tistory - JVM 내부 구조 & 메모리 영역 💯 총정리 : https://inpa.tistory.com/entry/JAVA-%E2%98%95-JVM-%EB%82%B4%EB%B6%80-%EA%B5%AC%EC%A1%B0-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%98%81%EC%97%AD-%EC%8B%AC%ED%99%94%ED%8E%B8
> + [1주차] JVM은 무엇이며 자바 코드는 어떻게 실행하는 것인가. : https://catsbi.oopy.io/df0df290-9188-45c1-b056-b8fe032d88ca
> + Velog - [1주차] JVM은 무엇이며 자바 코드는 어떻게 실행하는 것인가 : https://velog.io/@roro/1%EC%A3%BC%EC%B0%A8-JVM%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B4%EB%A9%B0-%EC%9E%90%EB%B0%94-%EC%BD%94%EB%93%9C%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%8B%A4%ED%96%89%ED%95%98%EB%8A%94-%EA%B2%83%EC%9D%B8%EA%B0%80
> + Tistory - [Java-3] JVM과 JIT 컴파일러란? : https://catch-me-java.tistory.com/11
