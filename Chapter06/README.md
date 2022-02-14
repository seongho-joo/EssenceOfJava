# 객체지향 프로그래밍 Ⅰ
> 객체지향이론의 기본 개념은 '실제 세계는 사물(객체)러 이루어져 있으며, 발생하는 모든 사건들을 사물간의 상호작용이다.'라는 것이다.
- [객체지향 프로그래밍 Ⅰ](#객체지향-프로그래밍-ⅰ)
  - [객체지향 언어](#객체지향-언어)
  - [클래스와 객체](#클래스와-객체)
  - [객체와 인스턴스](#객체와-인스턴스)
  - [객체의 구성요소 - 속성과 기능](#객체의-구성요소---속성과-기능)
  - [인스턴스의 생성과 사용](#인스턴스의-생성과-사용)
  - [클래스의 또 다른 정의](#클래스의-또-다른-정의)
  - [선언위치에 따른 변수의 종류](#선언위치에-따른-변수의-종류)
    - [1. 인스턴스 변수](#1-인스턴스-변수)
    - [2. 클래스 변수](#2-클래스-변수)
    - [3. 지역 변수](#3-지역-변수)
  - [클래스 변수와 인스턴스 변수](#클래스-변수와-인스턴스-변수)
  - [메서드](#메서드)
  - [JVM의 메모리 구조](#jvm의-메모리-구조)
  - [기본형 매개변수와 참조형 매개변수](#기본형-매개변수와-참조형-매개변수)
  - [클래스 메서드와 인스턴스 메서드](#클래스-메서드와-인스턴스-메서드)
  - [클래스 멤버와 인스턴스 멤버간의 참조와 호출](#클래스-멤버와-인스턴스-멤버간의-참조와-호출)
  - [오버로딩(Overloading)](#오버로딩overloading)
    - [오버로딩의 조건](#오버로딩의-조건)
    - [오버로딩의 장점](#오버로딩의-장점)
    - [가변인자와 오버로딩](#가변인자와-오버로딩)
  - [생성자(Constructor)](#생성자constructor)
    - [기본 생성자(default constructor)](#기본-생성자default-constructor)
    - [매개변수가 있는 생성자](#매개변수가-있는-생성자)
    - [생성자에서 다른 생성자 호출하기 - this(), this](#생성자에서-다른-생성자-호출하기---this-this)
    - [생성자를 이용한 인스턴스의 복사](#생성자를-이용한-인스턴스의-복사)
  - [변수의 초기화](#변수의-초기화)
    - [명시적 초기화 (explicit intialization)](#명시적-초기화-explicit-intialization)
    - [초기화 블럭 (initialization block)](#초기화-블럭-initialization-block)
    - [멤버 변수의 초기화 시기와 순서](#멤버-변수의-초기화-시기와-순서)
***

## 객체지향 언어
객체지향 언어의 주요 특징
- 코드의 재사용성이 높다.
   - 새로운 코드를 작성할 때 기존의 코드를 이용하여 쉽게 작성할 수 있다. 
- 코드의 관리가 용이하다.
  - 코드간의 관계를 이용해서 적은 노력으로 쉽게 코드를 변경할 수 있다.
- 신뢰성이 높은 프로그래밍을 가능하게 한다.
  - 제어자와 메서드를 이용해서 데이터를 보호하고 올바른 값을 유지하도록 하며, 코드의 중복을 제거하여 코드의 불일치로 인한 오동작을 방지할 수 있다.

> 너무 객체지향개념에 얽매여서 고민하기 보다는 일단 프로그램을 기능적으로 완성한 다음 어떻게 하면 보다 객체지향적으로 코드를 개선할 수 있을지를 고민하여 점차 개선하는 것이 좋다.

## 클래스와 객체
클래스의 정의와 용도
- 클래스란 객체를 정의해 놓은 것이다.
- 클래스는 객체를 생성하는데 사용된다.

객체의 정의와 용도
- 실제로 존재하는 것, 사물 또는 개념
- 객체가 가지고 있는 기능과 속성에 따라 다름

유형의 객체
- 책상, 의자, 자동차, TV와 같은 사물

무형의 객체
- 수학 공식, 프로그램 에러와 같은 논리나 개념
  
프로그래밍에서의 객체는 클래스에 정의된 내용대로 메모리에 생성된 것을 뜻한다.

🔍 클래스와 객체의 예
클래스|객체
--|--
제품 설계도|제품
TV 설계도|TV
붕어빵 기계|붕어빵

## 객체와 인스턴스
인스턴스화 
- 클래스로부터 객체를 만드는 과정

인스턴스
- 어떤 클래스로부터 만들어진 객체

객체와 인스턴스는 같은 의미이지만, 객체는 모든 인스턴스를 대표하는 포괄적인 의미를 갖고있으며, 인스턴스는 어떤 클래스로부터 만들어진 것인지를 강조하는 보다 구체적인 의미를 갖고있다.

예를들면, '책상은 인스턴스다.'라고 하기 보단 '책상은 객체다.'라는 쪽이, '책상은 책상 클래스의 객체이다.'라고 하기 보단 '책상은 책상 클래스의 인스턴스다.'라고 하는 것이 자연스럽다.

## 객체의 구성요소 - 속성과 기능
객체는 속성과 기능의 집합이라고 할 수 있다. 그리고 객체가 가지고 있는 속성과 기능을 그 객체의 멤버라 한다.

속성(property)
- 멤버 변수(member variable), 특성(attribute), 필드(field), 상태(state)

기능(function)
- 메서드(method), 함수(function), 행위(behavior)

## 인스턴스의 생성과 사용
```java
class Tv {
  String color;
  boolean power;
  int channel;

  void power() { power != power; }
  void channelUp() { channel += 1; }
  void channelDown() { channel -= 1; }
}

class Tvtest {
  public static void main(String args[]) {
    Tv t; // Tv 클래스 타입의 참조변수 t 선언
    t = new Tv(); // Tv클래스의 인스턴스가 메모리의 빈 공간에 생성됨
    t.channel = 7; // 인스턴스의 멤버 변수 channel에 7을 저장
    t.channelDown(); // Tv인스턴스의 channelDown 메서드 호출
    System.out.println("현재 채널은 " + t.channel + " 입니다");
  }
}
```
인스턴스는 참조변수를 통해서만 다룰 수 있으며, 참조변수의 타입은 인스턴스의 타입과 일치해야한다.

## 클래스의 또 다른 정의
1. 클래스 - 데이터와 함수의 결합
> 1. 변수&nbsp;&nbsp;&nbsp;&nbsp;하나의 데이터를 저장할 수 있는 공간
> 2. 배열&nbsp;&nbsp;&nbsp;&nbsp;같은 종류의 여러 데이터를 하나의 집합으로 저장할 수 있는 공간
> 3. 구조체 서로 관련된 여러 데이터를 종류에 관계없이 하나의 집합으로 저장할 수 있는 공간
> 4. 클래스 데이터와 함수의 결합

2. 클래스 - 사용자정의 타입(user-defined type)   
프로그래밍언어에서 제공하는 자료형외에 프로그래머가 서로 관련된 변수들을 묶어서 하나의 타입으로 새로 추가하는 것을 사용자정의 타입이라고 한다.

## 선언위치에 따른 변수의 종류
변수는 클래스 변수, 인스턴스 변수, 지역변수 등 세 종류가 있다.
변수의 종류|선언위치|생성시기
:--:|:--:|--
클래스 변수<br>(class variable)|클래스 영역|클래스가 메모리에 올라갈 때
인스턴스 변수<br>(instance variable)|클래스 영역|인스턴스가 생성되었을 때
지역 변수<br>(local variable)|클래스 영역 이외의 영역|변수 선언문이 수행되었을 때

### 1. 인스턴스 변수
- 클래스 영역에 선언
- 클래스의 인스턴스를 생성할 때 만들어짐
- 독립적인 저장공간을 가지므로 서로 다른 값을 가질 수 있음
- 인스턴스마다 고유한 상태를 유지해야하는 속성의 경우, 인스턴스 변수로 선언

### 2. 클래스 변수
- 인스턴스 변수 앞에 `static`을 붙임
- 모든 인스턴스가 공통된 저장공간을 공유
- 인스턴스를 생성하지 않고도 바로 사용할 수 있음
- 클래스가 메모리에 loading될 때 생성되어 프로그램이 종료될 때 까지 유지됨

### 3. 지역 변수
- 메서드 내에 선언되어 메서드 내에서만 사용 가능
- 메서드가 종료되면 소멸되어 사용할 수 없음

## 클래스 변수와 인스턴스 변수
인스턴스 변수는 인스턴스가 생성될 때 마다 생성되므로 인스턴스마다 각기 다른 값을 유지할 수 있지만, 클래스 변수는 모든 인스턴스가 하나의 저장공간을 공유하므로, 항상 공통된 값을 갖는다.

## 메서드
메서드(method)는 특정 작업을 수행하는 일련의 문장들을 하나로 묶인 것이다.

메서드를 사용하는 이유
1. 높은 재사용성(reusability)
2. 중복된 코드의 제거
3. 프로그램의 구조화

메서드의 선언과 구현
```java
반환 타입 메서드 이름 (타입 변수명, ...) {
  // 수행될 코드
}

int add(int a, int b) {
  return a + b;
}
```
메서드 호출
```java
메서드이름(arg1, arg2, ...);

int res = add(1, 3);
```

## JVM의 메모리 구조
JVM은 시스템으로부터 프로그램을 수행하는데 필요한 메모리를 할당받고 JVM은 이 메모리를 용도에 따라 여려 영역으로 나누어 관리한다.

1. 메서드 영역(method area)
   - 프로그램 실행 중 어떤 클래스가 사용되면, JVM은 해당 클래스의 클래스 파일을 읽어서 분석하여 클래스에  대한 정보를 이곳에 저장한다. 이 때, 그 클래스의 클래스 변수도 이 역역에 생성된다.
2. 힙(heap)
   - 인스턴스가 생성되는 공간
3. 호출스택(call stack or excution stack)
   - 메서드의 작업에 필요한 메모리 공간을 제공 

## 기본형 매개변수와 참조형 매개변수
기본형 매개변수
- 기본형 값 복사
- 변수의 값을 읽기만 가능

참조형 매개변수
- 인스턴스의 주소 복사
- 변수의 값을 읽고 변경 가능

## 클래스 메서드와 인스턴스 메서드
변수와 마찬가지로 `static`이 붙어 있으면 클래스 메서드, 붙어 있지 않으면 인스턴스 메서드다.   
인스턴스 메서드는 인스턴스 변수와 관련된 작업을하는, 즉 메서드의 작업을 수행하는데 인스턴스 변수를 필요로 하는 메서드이다. 반면에 인스턴스와 관계없는 메서드를 클래스 메서드로 정의한다.

📌 정리
1. 클래스를 설계할 때, 멤버 변수 중 모든 인스턴스에 공통으로 사용하는 것에 `static`을 붙인다.
2. 클래스 변수는 인스턴스를 생성하지 않아도 사용할 수 있다.
3. 클래스 메서드는 인스턴스 변수를 사용할 수 없다.
4. 메서드 내에서 인스턴스 변수를 사용하지 않는다면, `static`을 붙이는 것을 고려한다.

```java
class Math {
  long a, b;
  public Math(int a, int b) {
    this.a = a;
    this.b = b;
  }
  // 인스턴스 메서드
  long add() { return a + b; }
  long substract() { return a - b; }
  long multiply() { return a * b; }
  double devide() { return a / b; }
  // 클래스 메서드
  static long add(int a, int b) { return a + b; }
  static long substract(int a, int b) { return a - b; }
  static long multiply(int a, int b) { return a * b; }
  static double devide(int a, int b) { return a / b; }
}

class MathTest {
  public static void main(String[] args)  {
    // 클래스 메서드는 인스턴스 생성없이 호출 가능
    Math.add(200, 100);
    Math.substract(200, 100);
    Math.multiply(200, 100);
    Math.devide(200, 100);

    Math math = new Math(200, 100);
    // 인스턴스 메서드는 인스턴스 생성 후 호출 가능
    math.add();
    math.substract();
    math.multiply();
    math.devide();
  }
}
```

## 클래스 멤버와 인스턴스 멤버간의 참조와 호출
같은 클래스에 속한 멤버들 간에는 별도의 인스턴스를 생성하지 않고도 서로 참조 또는 호출이 가능하다. 단, 클래스 멤버가 인스턴스 멤버를 참조 또는 호출하고자 하는 경우에는 인스턴스를 생성해야 한다. 그 이유는 클래스 멤버가 존재하는 시점에 인스턴스 멤버가 존재하지 않을 수도 있기 때문이다.
```java
class Test {
  int iv;
  static int cv;
  void instanceMethod() { }
  static void staticMethod() { }

  void instanceMethod2() {
    instanceMethod();
    staticMethod();
  }

  static void staticMethod2() {
    // int a = iv; // Error
    int a = new Test().iv;
    int b = cv;
    // instanceMethod(); // Error
    new Test().instanceMethod();
    staticMethod();
  }
}
```

## 오버로딩(Overloading)
한 클래스 내에 같은 이름의 메서드를 여러 개 정의하는 것을 '메서드 오버로딩' 또는 '오버로딩'이라 한다.

### 오버로딩의 조건
오버 로딩이 성립하기 위해서는 다음과 같은 조건을 만족해야 한다.
1. 메서드 이름이 같아야 한다.
2. 매개변수 개수 또는 타입이 달라야 한다.

반환 타입은 오버로딩을 구현하는데 아무런 영향을 주지 못한다.

오버로딩의 몇가지 예
- 보기 1
```java
// 매개변수만 다를 경우
int add(int a, int b) {
  return a + b;
}
int add(int x, int y) {
  return x + y;
}
```
위 코드는 오버로딩이 성립하지 않는다.
- 보기 2
```java
// 반환 타입만 다를 경우
int add(int a, int b) {
  return a + b;
}
long add(int a, int b) {
  return a + b;
}
```
위 코드도 오버로딩이 성립하지 않는다.
- 보기 3
```java
// 매개변수 타입의 순서가 다른 경우
long add(int a, long b) {
  return a + b;
}
long add(long a, int b) {
  return a + b;
}
```
위 코드는 오버로딩으로 간주한다. 하지만 `add(3, 3)`과 같이 호출한다면 두 메서드 중 어느 메서드 호출된 것인지 알 수 없기 때문에 컴파일 에러가 발생한다.
- 보기 4
```java
int add(int a, int b) {
  return a + b;
}
long add(int a, long b) {
  return a + b;
}
long add(int[] a) {
  int ret = 0;
  for (int i : a) {
    ret += i;
  }
  return ret;
}
```
위 코드는 바르게 오버로딩되어 있다.

### 오버로딩의 장점
- 오버로딩을 통해 여러 메서드들이 하나의 이름으로 정의할 수 있다.
- 메서드의 이름을 절약할 수 있다.

### 가변인자와 오버로딩
가변인자는 `타입... 변수명`과 같은 형식으로 선언하며, `PrintStream`클래스의 `printf()`가 대표적인 예이다.
```java
public PrintStream printf(String format, Object... args) { ... }
```

## 생성자(Constructor)
생성자는 인스턴스가 생성될 때 호출되는 '인스턴스 초기화 메서드'다.

생성자의 조건
- 생성자의 이름은 클래스의 이름과 같아야 한다.
- 생성자는 리턴 값이 없다.

```java
class Class_name {
  Class_name() {
    ...
  }
  Class_name(String k, int num) {
    ...
  }
}
```
참고❗️   
- **연산자 `new`가 인스턴스를 생성하는 것이지 생성자가 인스턴스를 생성하는 것이 아니다.**

### 기본 생성자(default constructor)
모든 클래스에는 반드시 하나 이상의 생성자가 정의되어 있어야 하지만 컴파일러에서 `기본 생성자`를 제공하기 때문에 생성자를 정의하지 않아도 인스턴스를 생성할 수 있었다.
> 기본 생성자가 컴파일러에 추가되는 경우는 클래스에 정의된 생성자가 하나도 없을 때 뿐이다.

### 매개변수가 있는 생성자
생성자에 매개변수를 선언하여 인스턴스의 초기화 작업에 사용할 수 있다.
```java
class Math {
  long a, b;
  Math(long a, long b) {
    this.a = a;
    this.b = b;
  }

  public static void main(String[] args) {
    Math math = new Math(1, 2);
  }
}
```

### 생성자에서 다른 생성자 호출하기 - this(), this
- 생성자의 이름으로 클래스 이름 대신 this를 사용한다.
- 한 생성자에서 다른 생성자를 호출할 때는 반드시 첫 줄에서만 호출이 가능하다.

```java
class Math {
  long a, b;

  Math() {
    this(-1, -1);
  }

  Math(long a, long b) {
    this.a = a;
    this.b = b;
  }

  public static void main(String[] args) {
    Math dMath = new Math(); // -1, -1로 초기화
    Math math = new Math(1, 2); // 1, 2로 초기화
  }
}
```
`this`는 참조변수로 인스턴스 자신을 가리킨다. 그리고 인스턴스 멤버만 사용할 수 있으며, `static`메서드에서는 사용할 수 없다.

> `this`  인스턴스 자신을 가리키는 참조변수, 인스턴스의 주소가 저장되어 있다.
> 모든 인스턴스 메서드에 지역변수로 숨겨진 채로 존재한다.   
> `this(), this(arguments)` 생성자, 같은 클래스의 다른 생성자를 호출할 때 사용한다.

### 생성자를 이용한 인스턴스의 복사
현재 사용하고 있는 인스턴스의 같은 상태를 갖는 인스턴스를 하나더 만들고자 할 때 생성자를 이용할 수 있다.
```java
class Math {
  long a, b;

  Math() {
    this(-1, -1);
  }

  Math(long a, long b) {
    this.a = a;
    this.b = b;
  }

  Math(Math m) {
    this(c.a, c.b);
  }
}
```
인스턴스를 생성할 때는 다음의 2가지 사항을 결정해야 한다.
* 클래스 - 어떤 클래스의 인스턴스를 생성할 것인가?
* 생성자 - 선택한 클래스의 어떤 생성자로 인스턴스를 생성할 것인가?

## 변수의 초기화
**멤버 변수와 배열의 초기화는 선택적이지만, 지역변수의 초기화는 필수적이다.**

📍 각 타입의 기본값
자료형 | 기본값
:--:|:--:
boolean | false
char | '\u000'
byte, short, int | 0
long | 0L
float | 0.0f
double | 0.0d or 0.0
참조형 변수 | null

📍 멤버 변수의 초기화 방법
- 명시적 초기화 (explicit intialization)
- 생성자 (Constructor)
- 초기화 블럭 (initialization block)
  - 인스턴스 초기화 블럭 : 인스턴스 변수를 초기화 하는데 사용
  - 클래스 초기화 블럭 : 클래스 변수를 초기화 하는데 사용

### 명시적 초기화 (explicit intialization)
변수를 선언과 동시에 초기화하는 것을 명시적 초기화라고 한다.

### 초기화 블럭 (initialization block)
- 클래스 초기화 블럭
  - 클래스 변수의 복잡한 초기화에 사용
  - 클래스가 메모리에 처음 로딩될 때 한번만 수행
- 인스턴스 초기화 블럭
  - 인스턴스 변수의 복잡한 초기화에 사용
  - 생성자와 같이 인스턴스를 생성할 때 마다 수행
  - 생성자보다 먼저 수행됨
  - 공통으로 수행돼야 하는 코드를 넣는데 사용

```java
class InitBlock {
  static { ... } // 클래스 초기화 블럭
  { ... } // 인스턴스 초기화 블럭
}
```
```java
Car() {
  count++;
  serialNo = count;
  ...
}

Car(String color, String gearType) {
  count++;
  serialNo = count;
  ...
}
```
위 코드를 아래와 같이 바꾸면 코드가 보다 간결해진다.
```java
{
  count++;
  serialNo = count;
}

Car () {
  ...
}
Car (String color, String gearType) {
  ...
}
```
코드의 중복을 제거하는 것은 코드의 신뢰성을 높여 주고, 오류의 발생가능성을 줄여준다. 즉, 재사용성을 높이고 중복을 제거하는 것이 객체지향 프로그래밍이 추구하는 궁극적인 목표다.
```java
class BlockTest {
  static {
    System.out.println("static { }");
  }

  { 
    System.out.println("{ }");
  }

  BlockTest() {
    System.out.println("생성자");
  }

  public static void main(String[] args) {
    System.out.println("BlockTest bt = new BlockTest()");
    BlockTest bt = new BlockTest;
  }
  /* 출력 결과
    static { } 
    BlockTest bt = new BlockTset()
    { }
    생성자
  */
}
```

### 멤버 변수의 초기화 시기와 순서
- 클래스 변수
  - 초기화 시점
    - 클래스가 처음 로딩될 때 단 한번 초기화된다.
  - 초기화 순서
    - 기본값 -> 명시적 초기화 -> 클래스 초기화 블럭
- 인스턴스 변수
  - 초기화 시점
    - 인스턴스가 생성될 때 마다 각 인스턴스별로 초기화가 이루어진다.
  - 초기화 순서
    - 기본값 -> 명시적 초기화 -> 인스턴스 초기화 블럭 -> 생성자