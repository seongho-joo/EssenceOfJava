# 객체지향 프로그래밍 Ⅱ

- [객체지향 프로그래밍 Ⅱ](#객체지향-프로그래밍-ⅱ)
  - [상속 (Inheritance)](#상속-inheritance)
    - [클래스간의 관계 - 포함관계](#클래스간의-관계---포함관계)
    - [클래스간의 관계 결정하기](#클래스간의-관계-결정하기)
    - [단일 상속(single inheritance)](#단일-상속single-inheritance)
    - [Object 클래스 - 모든 클래스의 조상](#object-클래스---모든-클래스의-조상)
  - [오버라이딩 (overriding)](#오버라이딩-overriding)
    - [오버로딩 vs 오버라이딩](#오버로딩-vs-오버라이딩)
    - [super](#super)
    - [패키지 (package)](#패키지-package)
    - [import](#import)
  - [제어자(modifier)](#제어자modifier)
    - [`static` - 클래스의, 공통적인](#static---클래스의-공통적인)
    - [`final` - 마지막의, 변경될 수 없는](#final---마지막의-변경될-수-없는)
    - [`abstract` - 추상의, 미완성의](#abstract---추상의-미완성의)
    - [접근 제어자](#접근-제어자)
    - [제어자(modifier)의 조합](#제어자modifier의-조합)
  - [다형성(Polymorphism)](#다형성polymorphism)
    - [참조변수의 형변환](#참조변수의-형변환)
    - [`instanceof` 연산자](#instanceof-연산자)
    - [참조변수와 인스턴스의 연결](#참조변수와-인스턴스의-연결)
  - [추상 클래스(abstract class)](#추상-클래스abstract-class)
    - [추상 메서드(abstract method)](#추상-메서드abstract-method)
  - [인터페이스(interface)](#인터페이스interface)
    - [`default` 메서드와 `static` 메서드](#default-메서드와-static-메서드)
  - [내부 클래스(inner class)](#내부-클래스inner-class)
    - [익명 클래스 (anonymous class)](#익명-클래스-anonymous-class)
***

## 상속 (Inheritance)
- 상속이란, 기존의 클래스를 재사용하여 새로운 클래스를 작성하는 것이다.
- 상속의 장점
  - 코드를 공통적으로 관리할 수 있기 때문에 코드의 추가 및 변경이 매우 용이
  - 코드의 재사용성을 높이고 코드의 중복을 제거하여 프로그램의 생산성과 유지보수에 크게 기여
- 클래스의 이름 뒤에 상속받고자 하는 클래스의 이름을 `extends` 키워드와 함께 써준다.
```java
 class Child extends Parent {
   ...
 }
```
- 조상 클래스
  - 부모(parent) 클래스, 상위(super) 클래스, 기반(base) 클래스
- 자손 클래스
  - 자식(child) 클래스, 하위(sub) 클래스, 파생된(derived) 클래스
- 생성자와 초기화 블럭은 상속되지 않는다. 멤버만 상속된다.
- 자손 클래스의 멤버 개수는 조상 클래스보다 항상 같거나 많다.
- 자손 클래스의 인스턴스를 생성하면 조상 클래스의 멤버와 자손 클래스의 멤버가 합쳐진 하나의 인스턴스로 생성된다.

### 클래스간의 관계 - 포함관계
- 하나의 거대한 작정하는 것보다 단위별로 여러 개의 클래스를 작성한 다음, 이 단위 클래스들을 포함관계로 재사용하면 보다 간결하고 손쉽게 클래스를 작성할 수 있다.
```java
class Point {
  int y;
  int x;
}

class Circle {
  Point point = new Point();
  int r;
}
```

### 클래스간의 관계 결정하기
- 상속 관계 : '~ is a ~'
- 포홤 관계 : '~ has a ~'
```java
class Shape { ... }

class Point { ... }

class Circle extends Shape {
  Point point = new Point();
  ...
}
```

### 단일 상속(single inheritance)
- C++는 다중 상속을 허용하지만 자바는 **단일 상속만 허용한다.**

### Object 클래스 - 모든 클래스의 조상
- 모든 클래스 상속계층도의 최상위에 있는 조상 클래스다.
- Object 클래스에 `toString()`, `equals()`등을 정의됐기 때문에 따로 정의하지 않고도 사용할 수 있었다.

## 오버라이딩 (overriding)
- 조상 클래스로부터 상속받은 메서드의 내용을 변경하는 것을 말한다.
- 오버라딩의 조건
  - 조상 클래스의 선언부와 일치해야 사용할 수 있다.
  - 접근 제어자를 조상 클래스의 메서드보다 좁은 범위로 변경할 수 없다.
  - 예외는 조상 클래스의 메서드보다 많이 선언할 수 없다.
  - 인스턴스 메서드를 static 메서드로 또는 그 반대로 변경할 수 없다.
```java
class Point {
  int x;
  int y;

  String getLocation() {
    return "x : " + x + ", y : " + y;
  }
}

class Point3D extends Point {
  int z;

  String getLocation() {
    return "x : " + x + ", y : " + y + ", z : " + z;
  }
}
```

### 오버로딩 vs 오버라이딩
- 오버로딩(overloading)
  - 기존에 없는 새로운 메서드를 정의하는 것(new)
- 오버라이딩(overriding)
  - 상속받은 메서드의 내용을 변경하는 것(change, modify)

### super
- `super`는 자손 클래스에서 조상 클래스로부터 상속받은 멤버를 참조하는데 사용되는 참조 변수다.
- `super()`
  - 조상 클래스의 생성자를 호출하는데 사용된다.
  - Object 클래스를 제외한 모든 클래스의 생성자 첫 줄에 생성자를 호출해야 됨. 그렇지 않으면 컴파일러가 자동적으로 `super();`를 생성자의 첫줄에 삽입한다.

```java
class PointTest {
  public static void main(String[] args) {
    Point3D = p3 = new Point3D();
  }
}

class Point {
  int x;
  int y;

  Point (int x, int y) {
    this.x = x;
    this.y = y;
  }
}

class Point3D extends Point {
  int z;

  Point3D() {
    this(100, 200, 300);
  }

  Point3D(int x, int y, int z) {
    super(x, y);
    this.z = z;
  }
}
```
호출 순서
1. Point3D()
2. Point3D(int x, int y, int z)
3. Point(int x, int y)

### 패키지 (package)
```java
package 패키지명;
```
- 클래스의 묶음
- 하나의 소스파일에는 첫 번째 문장으로 단 한 번의 패키지 선언만을 허용한다.
- 모든 클래스는 반드시 하나의 패키지에 속해야 한다.
- 패키지에는 클래스 또는 인터페이스를 포함시킬 수 있으며, 서로 관련된 클래스들끼리 그룹 단위로 묶어 놓음으로써 클래스를 효울적으로 관리 할 수 있다.
- 패키지는 `.`을 구분자로 하여 계층 구조로 구성할 수 있다.
- 클래스가 물리적으로 하나의 클래스파일(.class)인 것과 같이 패키지는 물리적으로 하나의 디렉터리이다.

### import
```java
import 패키지명.클래스명;
  또는
import 패키지명.*;
```
- import 문의 역할은 컴파일러에게 소스파일에 사용된 클래스의 패키지에 대한 정보를 제공하는 것이다.
- import 문은 프로그램의 성능에 전혀 영향을 미치지 않고 컴파일 시간이 아주 조금 더 소요된다.

📍 **static import 문**
- static import 문을 사용하면 static멤버를 호출할 때 클래스 이름 생략 가능
```java
import static java.lang.System.out;

class StaticImport {
  public static void main(String[] args) {
    out.println("Hello World!");
  }
}
```

## 제어자(modifier)
- 제어자는 클래스 변수 또는 메서드의 선언부에 함께 사용되어 부가적인 의미를 부여
- 제어자의 종류
  - 접근 제어자 :  `public`, `protected`, `default`, `private`
  - 그 외 : `static`, `final`, `abstract`, `native`, `transient`, `synchronized`, `volatile`, `strictfp`

### `static` - 클래스의, 공통적인
- `static`멤버 변수는 하나의 변수를 모든 인스턴스가 공유하기 때문에 인스턴스에 관계없이 같은 값을 갖는다.
- `static`은 멤버 변수, 메서드, 초기화 블럭에서 사용될 수 있다.

### `final` - 마지막의, 변경될 수 없는
- 변수에 사용되면 상수, 메서드에 사용되면 오버라이딩 불가능하고, 클래스에 사용되면 상속이 불가능하다.
- `final`은 클래스, 메서드, 멤버 변수, 지역 변수에서 사용될 수 있다.

**생성자를 이용한 `final`멤버 변수의 초기화**
- 인스턴스 변수의 경우 생성자에서 초기화가 가능
- 이 기능을 활용하여 각 인스턴스마다 `final`멤버 변수가 다른 값을 갖도록 하는 것이 가능

### `abstract` - 추상의, 미완성의
- 메서드의 선언부만 작성하고 실제 수행내용은 구현하지 않은 추상 메서드를 선언하는데 사용
- `abstract`는 클래스, 메서드에서 사용될 수 있다.

### 접근 제어자
- 멤버 또는 클래스에 사용되어, 해당하는 멤버 또는 클래스를 외부에서 접근하지 못하도록 제한하는 역할
- 접근 제어자가 사용될 수 있는 곳 - 클래스, 멤버 변수, 메서드, 생성자
  - `private` : 같은 클래스 내에서만 접근 가능
  - `default` : 같은 패키지 내에서만 접근 가능
  - `protected` : 같은 패키지 내에서, 그리고 다른 패키지의 자손 클래스에서 접근 가능
  - `public` : 접근 제한 x

**접근 범위**
```java
public > protected > (default) > private
```

**접근 제어자를 이용한 캡슐화**
- 클래스의 내부에 선언된 데이터를 보호하기 위해서 클래스나, 멤버에 접근 제어자를 사용
- 외부로부터의 접근을 제한하는 것을 데이터 감추기(data hiding)라고 하며, 객체지향개념의 캡슐화(encapsulation)에 해당하는 내용이다.

**접근 제어자를 사용하는 이유**
- 외부로부터 데이터를 보호하기 위해서
- 외부에는 불필요한, 내부적으로만 사용되는, 부분을 감추기 위해서

**생성자의 접근 제어자**
- 생성자에 접근 제어자를 사용함으로써 인스턴의 생성을 제한할 수 있음
- 생성자의 접근 제어자를 `private`로 지정하면,외부에서 생성자에 접근할 수 없으므로 클래스 내부에서 인스턴스를 생성해 반환해주는 `public` 메서드를 제공함으로써 외부에서 인스턴스를 사용할 수 있게 할 수 있음
- 생성자가 `private`인 클래스는 자손클래스에서 조상클래스 생성자 호출이 불가능하기 때문에 다른 클래스의 조상이 될 수 없음

### 제어자(modifier)의 조합
제어자를 조합해서 사용할 때 주의해야 할 사항
- 메서드에 `static`과 `abstract`를 함께 사용할 수 없다.
  - `static` 메서드는 몸통이 있는 메서드에만 사용할 수 있기 때문이다.
- 클래스에 `abstract`와 `final`을 동시에 사용할 수 없다.
  - 클래스에 사용되는 `final`은 클래스를 확장할 수 없다는 의미이고 `abstract`는 상속을 통해서 완성되어야 한다는 의미이므로 서로 모순되기 때문이다.
- `abstract` 메서드의 접근 제어자가 `private`일 수 없다.
  - `abstract` 메서드는 자손클래스에서 구현해주어야 하는데 접근 제어자가 `private`이면, 자손클래스에서 접근할 수 없기 때문이다.
- 메스드에 `private`과 `final`을 같이 사용할 필요는 없다.
  - 접근 제어자가 `private`인 메서드는 오버라이딩될 수 없기 때문이다.

## 다형성(Polymorphism)
객체지향개념에서 다형성이란 '여러 가지 형태를 가질 수 있는 능력'을 의미하며, 자바에서는 한 타입의 참조변수로 여러 타입의 객체를 참조할 수 있도록 함으로써 다형성을 프로그램적으로 구현하였다.
- **조상클래스 타입의 참조변수로 자손클래스의 인스턴스를 참조할 수 있도록 하였다.**

```java
class Tv {
  ...
}

class CationTv extends Tv {
  ...
}

Tv t = new CationTv();
CationTv c = new CationTv();
```
실제 인스턴스가 CationTv타입이라 할지라도, 참조 변수 t로는 CationTv인스턴스의 모든 멤버를 사용할 수 없다. **둘 다 같은 타입의 인스턴스지만 참조변수의 타입에 따라 사용할 수 있는 멤버의 개수가 달라진다.**

`CationTv c = new Tv();` 와 같은 코드는 컴파일 에러가 발생한다. 그 이유는 실제 인스턴스인 Tv의 멤버 개수보다 참조변수 c가 사용할 수 있는 멤버 개수가 더 많기 때문이다.    
**참조변수가 사용할 수 있는 멤버의 개수는 인스턴스의 멤버 개수보다 같거나 적어야 한다.**

### 참조변수의 형변환
서로 상속관계에 있는 클래스사이에서만 가능하기 때문에 자손타입의 참조변수를 조상타입의 참조변수로, 조상타입의 참조변수를 자손타입의 참조변수로의 형변환만 가능하다.
```
자손타입 -> 조상타입(Up-casting) : 형변환 생력가능
자손타입 <- 조상타입(Down-casting) : 형변환 생략불가
```
**형변환은 참조변수의 타입을 변환하는 것이지 인스턴스를 변환하는 것은 아니기 때문에 참조변수의 형변환은 인스턴스에 아무런 영향을 미치지 않는다. 단지 참조변수의 형변환을 통해서, 참조하고 있는 인스턴스에서 사용할 수 있는 멤버의 범위를 조절하는 것뿐이다.**

서로 상속관계에 있는 타입의 형변환은 양방향으로 자유롭게 수행될 수 있으나, **참조변수가 가리키는 인스턴스의 자손타입으로 형변환은 허용되지 않는다. 따라서 참조변수가 가리키는 인스턴스의 타입이 무엇인지 확인하는 것이 중요하다.**

### `instanceof` 연산자
참조변수가 참조하고 있는 인스턴스의 실제 타입을 알아보기 위해 `istanceof` 연산자를 사용한다.   
**어떤 타입에 대한 `instanceof` 연산의 결과가 true 라는 것은 검사한 타입으로 형변환이 가능하다는 것을 뜻한다.**

### 참조변수와 인스턴스의 연결
멤버변수가 조상 클래스의 자손 클래스에 중복으로 정의된 경우, 조상타입의 참조변수를 사용했을 때는 자손 클래스에 선언된 멤버변수가 사용된다. 하지만 중복 정의되지 않는 경우, 조상타입의 참조변수를 사용했을 때와 자손타입의 참조변수를 사용했을 때의 차이는 없다.

## 추상 클래스(abstract class)
추상 클래스는 클래스로서의 역할을 다 못하지만, 새로운 클래스를 작성하는데 있어서 바탕이 되는 조상 클래스로서 중요한 의미를 갖는다. 추상 클래스는 키워드 `abstract` 를 붙인다.   

추상 클래스는 추상 메서드를 포함하고 있다는 것을 제외하고는 일반 클래스와 전혀 다르지 않다.

**추상화**
- 클래스간의 공통점을 찾아내서 공통의 조상을 만드는 작업

**구체화**
- 상속을 통해 클래스를 구현, 확장하는 작업

### 추상 메서드(abstract method)
추상 메서드란 선언부만 작성하고 구현부는 작성하지 않은 채로 남겨 둔 것이다.

추상 클래스로부터 상속받는 자손 클래스는 오버라이딩을 통해 조상인 추상 클래스의 추상 메서드를 모두 구현해주어야 한다. 만일 조상으로부터 상속받은 추상 메서드 중 하나라도 구현하지 않는다면, 자손 클래스 역시 추상 클래스로 지정해 주어야 한다.

## 인터페이스(interface)
- 인터페이스는 일종의 추상 클래스
- 인터페이스는 추상 메서드와 상수만을 멤버로 가질 수 있음
- 모든 멤버변수는 `public static final` 이어야 하며, 생략 가능
- 모든 메서드는 `public abstract` 이어야 하며, 생략 가능

```java
interface InterfaceName {
  (public static final) 타입 상수이름 = 값;
  (public static) 메서드이름(args);
}
```

**인터페이스의 상속**
- 클래스와 달리 다중 상속, 즉 여러 개의 인터페이스로부터 상속을 받는 것이 가능

**인터페이스의 구현**
- 인터페이스는 구현 클래스를 구현한다는 의미의 키워드 `implements` 를 사용
- 구현 클래스의 메서드 중 일부만 구현한다면, `abstract` 를 붙임

**리턴 타입이 인터페이스라는 것은 메서드가 해당 인터페이스를 구현한 클래스의 인스턴스를 반환한다는 것을 의미한다.**

**인터페이스의 장점**
- 개발시간을 단축시킬 수 있음
- 표준화 가능
- 서로 관계없는 클래스들에게 관계를 맺어 줄 수 있음
- 독립적인 프로그래밍 가능

### `default` 메서드와 `static` 메서드
JDK1.8부터 인터페이스에 default 메서드와 static 메서드를 추가할 수 있게 됐다.

가장 대표적인 예: `java.util.Collecltions`

**default 메서드**
인터페이스가 확장된다는 것은 추상 메서드를 추가한다는 것이고, 이 인터페이스를 구현한 기존의 모든 클래스들이 새로 추가된 메서드를 구현해야 한다. 이를 방지하기 위해 `default method` 가 나오게 되었다.   
default 메서드는 추상 메서드의 기본적인 구현을 제공하는 메서드로, 추상 메서드가 아니기 때문에 default 메서드가 새로 추가되어도 해당 인터페이스를 구현한 클래스를 변경하지 않아도 된다.
```java
public interface MyInterface {
  void method();
  default void newMethod();
}
```
위와 같이 default 메서드를 추가하면, 기존의 `MyInterface` 를 구현한 클래스를 변경하지 않아도 된다. 즉, 조상 클래스에 새로운 메서드를 추가한 것과 동일해 지는 것이다.

> **새로 추가된 default 메서드가 기존의 메서드의 이름이 중복되어 충돌하는 경우 해결하는 규칙**
> - 여러 인터페이스의 default 메서드 간의 충돌
>   - 인터페이스를 구현한 클래스에서 default 메서드를 오버라이딩해야 한다.
> - default 메서드와 조상 클래스의 메서드 간의 충돌
>   - 조상 클래스의 메서드가 상속되고, default 메서드는 무시된다.

## 내부 클래스(inner class)
내부 클래스란 클래스 내에 선언되는 클래스를 뜻한다.
```java
public class Outer {
  class InstanceInner { }
  static class StaticInnter { }
}
```

> 내부 클래스의 장점
> - 내부 클래스에서 외부 클래스의 멤버들을 쉽게 접근 가능
> - 코드의 복잡성을 줄일 수 있음 ➡️ 캡슐화

**내부 클래스의 종류**
내부 클래스 | 특징 
-- | --
인스턴스 클래스<br>(instance class) | 외부 클래스의 멤버변수 선언위치에 선언하며, 외부 클래스의 인스턴스멤버 처럼 다루어진다. 주로 외부 클래스의 인스턴스 멤버들과 관련된 작업에 사용될 목적으로 선언된다.
스태틱 클래스<br>(static class) | 외부 클래스의 멤버변수 선언 위치에 선언하며, 외부 클래스의 static 멤버처럼 다루어진다. 주로 외부 클래스의 static 멤버, 특히 static 메서드에서 사용될 목적으로 선언된다.
지역 클래스<br>(local class) | 외부 클래스의 메서드나 초기화 블럭 안에 선언하며, 선언된 영역 내부에서만 사용될 수 있다.
익명 클래스<br>(anonymous class) | 클래스의 선언과 객체의 생성을 동시에 하는 이름없는 클래스(일회용)

### 익명 클래스 (anonymous class)
익명클래스는 클래스의 선언과 객체의 생성을 동시에 하기 때문에 단 한번만 사용될 수 있고 오직 하나의 객체만을 생성할 수 있는 일회용 클래스이다.
```java
class AnonymousClass {
  Object object = new Object() { ... }
}
```