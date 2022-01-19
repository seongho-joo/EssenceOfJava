<h1>자바를 시작하기 전에</h1>
<h2>목차</h2>

- [자바란](#자바란)
- [자바의 특징](#자바의-특징)
- [JVM(Java Virtual Machine)](#jvmjava-virtual-machine)
- [JDK](#jdk)
- [자바 실행과정](#자바-실행과정)

## 자바란
1996년 썬마이크로시스템즈에서 개발하고 발표한 객체지향 프로그래밍 언어이다.

운영체제에 독립적이라 운영체제의 종류에 관계없이 실행이 가능하다. 즉 이식성이 높다.

## 자바의 특징
1. 운영체제의 독립적
2. 객체지향 언어
3. 비교적 배우기 쉬움
4. 자동 메모리 관리(Garbage Collection)
5. 네트워크와 분산처리를 지원
6. 멀티쓰레드 지원
7. 동적 로딩(Dynamic Loading) 지원

## JVM(Java Virtual Machine)
JVM을 직역하면 '자바를 실행하기 위한 가상 기계'라 할 수 있다.

<img width="450" alt="image" src="https://user-images.githubusercontent.com/45463495/150100776-e544cf3b-3f0f-4181-86ef-8a4044689927.png">

일반적인 프로그램은 OS만 거치고 실행되는데 자바 애플리케이션은 JVM을 한 번 더 거쳐서 실행된다.   
자바 애플리케이션은 JVM하고만 상호작용을 하기 때문에 다른 OS에서도 프로그램의 변경없이 실행이 가능하다. 단 JVM은 OS 종속적이다.

## JDK
자바는 프로그래밍을 하기위해서는 JDK(Java Development Kit)를 설치해야 한다.   
JDK의 bin 디렉토리내에 있는 주요 실행파일
- javac 
  - 자바 컴파일러, 자바소스크도르르 바이트코드로 컴파일
- .java
  - 자바 인터프리터, 컴파일러가 생성한 바이트코드를 해석하고 실행
- .class
  - 역어셈블러, 컴파일된 클래스파일을 원래의 소스로 변환

## 자바 실행과정
자바 컴파일러(javac)가 소스파일(.java)를 읽어들여 클래스파일(.class)로 변환시킨다.

내부적인 진행순서
1. 프로그램의 실행에 필요한 클래스(*.class) 로드
2. 클래스파일 검사(파일형식, 악성코드 체크)
3. 지정된 클래스에서 main 호출