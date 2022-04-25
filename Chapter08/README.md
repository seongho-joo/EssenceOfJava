> 자바의 정석을 읽고 내용 정리

<details>
<summary>ToC</summary>

- [예외처리(Exception handling)](#예외처리exception-handling)
  - [예외 클래스의 계층구조](#예외-클래스의-계층구조)
  - [예외처리하기 - try-catch 문](#예외처리하기---try-catch-문)
  - [예외 발생시키기](#예외-발생시키기)
  - [메서드에 예외 선언하기](#메서드에-예외-선언하기)
  - [finally 블럭](#finally-블럭)
- [사용자정의 예외 만들기](#사용자정의-예외-만들기)
- [예외 되던지기(exception re-throwing)](#예외-되던지기exception-re-throwing)

</details>

***

## 예외처리(Exception handling)
- 프로그램이 실행 중 어떤 원인에 의해서 오작동을 하거나 비정상적으로 종료되는 경우가 있다. 이러한 결과를 초래하는 원인을 프로그램 에러 또는 오류라고 한다.
- 컴파일 에러(compile-time error)
  - 컴파일 시에 발생하는 에러
- 런타임 에러(runtime error)
  - 실행 시에 발생하는 에러
- 논리적 에러(logical error)
  - 실행은 되지만, 의도와 다르게 동작하는 것

- 런타임 에러를 방지하기 위해서는 프로그램의 실행도중 발생할 수 있는 모든 경우의 수를 고려하여 이에 대한 대비를 하는 것이 필요하다. 자바에서는 runtime 시 발생할 수 있는 프로그램 오류를 'error'와 'exception', 두 가지로 구분하였다.
  - error
    - 메모리 부족(OutOfMemoryError)나 스택오버플로우(StackOverFlowError)와 같이 발생하면 복구할 수 없는 심각한 오류
    - 프로그램의 비정상적인 종료를 막을 길이 없음
  - exception
    - 발생하더라고 수습될 수 있는 비교적 덜 심각한 오류
    - 프로그래머가 이에 대한 적절한 코드를 미리 작성해 놓음으로써 프로그램의 비정상적인 종료를 막을 수 있음

### 예외 클래스의 계층구조
```
Exception
├── IOException
├── ClassNotFoundException
├── ...
└── RunTimeException 
    ├── ArithmeticException
    ├── ClassCastException
    ├── NullPointerException
    ├── ...
    └── IndexOutOfBoundsException
```
- 모든 예외의 최고 조상은 **Exception** 클래스이며, 상속계층도를 Exception 클래스로부터 도식화하면 위와 같다.
- Exception 클래스: 사용자의 실수와 같은 외적인 요인에 의해 발생하는 예외
- RuntimeException 클래스: 프로그래머의 실수로 발생하는 예외

### 예외처리하기 - try-catch 문
- 예외처리(exception handling)란, **프로그램 실행 시 발생할 수 있는 예기치 못한 예외의 발생에 대비한 코드를 작성하는 것**이며, 예외처리의 목적은 **예외의 발생으로 인한 실행 중인 프로그램의 갑작스런 비정상 종료를 막고, 정상적인 실행상태를 유지할 수 있도록 하는 것**이다.
- 예외를 처리하기 위해서는 try-catch 문을 사용한다.

```java
try {
    // 에외가 발생할 가능성이 있는 문장
} catch (Exception e) {
    // Exception이 발생했을 경우, 이를 처리하기 위한 문장
}
```

try-catch 문 흐름
- try 블럭 내에서 예외가 발생한 경우
  - 발생한 예외와 일치하는 catch 블럭이 있는지 확인
  - 일치하는 catch 블럭을 찾게 되면, 그 catch 블럭 내의 문장들을 수행하고 전체 try-catch 문을 빠져나가서 그 다음 문장을 계속해서 수행, 만일 일치하는 catch 블럭을 찾지 못하면, 예외는 처리되지 못함
- try 블럭 내에서 예외가 발생하지 않는 경우
  - catch 블럭을 거치지 않고 전체 try-catch 문을 빠져나가서 수행을 계속함

- 예외가 발생했을 때 생성되는 예외 클래스의 인스턴스에는 발생한 예외에 대한 정보가 담겨있으며, `getMessage()`와 `printStackTrace()`를 통해서 정보들을 얻을 수 있다.
  - **printStackTrace()**: 에외발생 당시의 호출스택(Call stack)에 있었던 메서드의 정보와 예외 메시지를 출력
  - **getMessage()**: 발생한 예외클래스의 인스턴스에 저장된 메시지를 얻을 수 있음

- JDK1.7부터 여러 catch블럭을 `|`기호를 이용해서, 하나의 catch 블럭으로 합칠 수 있게 되었으며, 이를 **멀티 catch 블럭**이라 한다.

### 예외 발생시키기
- 키워드 `throw`를 사용해서 프로그래머가 고의로 예외를 발생시킬 수 있다.

```java
// 먼저, 연산자 new를 이용해서 발생시키려는 예외 클래스의 객체를 만듦
Exception e = new Exception("고의로 발생시킴");
// 키워드 throw를 이용해서 예외 발생
throw e;
// 한 줄로 사용가능함
throw new Exception("고의로 발생시킴");
```

### 메서드에 예외 선언하기
- 메서드 선언부에 키워드 `throws`를 사용한다.
- 메서드 선번부에 예외를 선언함으로써 메서드를 사용하려는 사람이 메서드의 선언부를 보았을 때, 이 메서드를 사용하기 위해서는 어떠한 예외들이 처리되어져야 하는지 쉽게 알 수 있다.

### finally 블럭
- `finally` 블럭은 예외의 발생여부에 상관없이 실행되어야할 코드를 포함시킬 목적으로 사용된다.

```java
try {
  ...
} catch (Exception e) {
  ...
} finally {
  ...
}
```

## 사용자정의 예외 만들기
- 기존의 정의된 예외 클래스 외에 필요에 따라 프로그래머가 새로운 예외 클래스를 정의하여 사용할 수 있다.

```java
class MyException extends Exception {
  MyException(String msg) {
    super(msg);
  }
}
```

## 예외 되던지기(exception re-throwing)
- 단 하나의 예외에 대해서도 예외가 발생한 메서드와 호출한 메서드, 양쪽에서 처리하도록 할 수 있다.
- 이것은 예외를 처리한 후에 인위적으로 다시 발생시키는 방법을 통해서 가능한데, 이것을 **예외 되던지기**(exception re-throwing)라고 한다.
- 반환값이 있는 경우, 예외가 발생 했을경우에도 값을 반환해야하기 때문에 catch 블럭에서도 `return`이 있어야 한다.

```java
public class ExceptionRethrowing { 

    public static void main(String[] args) {
        try {
            method1();
        } catch (Exception e) {
            System.out.println("main 메서드에서 예외가 처리되었습니다.");
        }
    }

    private static void method1() throws Exception {
        try {
            throw new Exception();
        } catch (Exception e) {
            System.out.println("method1 메서드에서 예외가 처리되었습니다.");
            throw e;
        }
    }
}
/** 출력 결과
 * method1 메서드에서 예외가 처리되었습니다.
 * main 메서드에서 예외가 처리되었습니다.
 */
```
