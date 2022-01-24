<h1>조건문과 반복문</h1>
<h1>목차</h1>

- [조건문](#조건문)
  - [if 문](#if-문)
  - [if-else 문](#if-else-문)
  - [switch 문](#switch-문)
- [반복문](#반복문)
  - [for 문](#for-문)
  - [향상된 for 문](#향상된-for-문)
  - [while 문](#while-문)
  - [do-while 문](#do-while-문)
  - [break 문](#break-문)
  - [continue 문](#continue-문)

## 조건문
조건문은 조건식과 문장을 포함하는 블럭으로 구성되어 있으며, 조건식의 연산결과에 따라 실행할 문장이 달라져서 프로그램의 실행흐름을 변경할 수 있다.

### if 문
if 문은 가장 기본적인 조건문이다.
```java
if (조건식) {
  // 조건식이 true일 때 수행될 문장
}
```
블럭 내의 문장이 하나뿐 일 때는 괄호를 생략할 수 있지만 가능하면 생략하지않고 사용하는 것이 바람직하다.

### if-else 문
else블럭은 조건식이 결과가 참이 아닐 때 else블럭의 문장을 수행하라는 뜻이다.
```java
if (조건식) {
  // 조건식이 true일 때 수행될 문장
} else {
  // 조건식이 false일 때 수행횔 문장
}
```
처리해야할 경우의 수가 셋 이상인 경우에는 if-else if 문을 사용한다.
```java
if (조건식 1) {
  // 조건식1이 true일 때 수행될 문장
} else if (조건식 2) {
  // 조건식 2이 true일 때 수행될 문장
} else {
  // 조건식 모두 false일 때 수행횔 문장
}
```

### switch 문
조건식이 많으면 else-if 문을 계속 추가해야하므로 복잡해지고 처리시간도 많이 걸리기 때문에 이 경우에는 swith 문을 사용한다.   
switch 문은 단 하나의 조건식으로 많은 경우의 수를 처리할 수 있고, 표현도 간결하므로 알아보기 쉽다.   
switch 문의 과정
1. 조건식 계산
2. 조건식의 결과와 일치하는 case 문으로 이동
3. 이후의 문장들을 수행
4. break 문이나 switch 문의 끝을 만나면 switch 문 전체를 빠져나감

```java
switch (조건식) {
  case 값1 : 
    // 조건식의 결과가 값1과 같을 경우 수행될 문장
    break;
  case 값2 : 
    // 조건식의 결과가 값2와 같을 경우 수행될 문장
    break;
  ...
  default : 
    // 조건식의 결과와 일치하는 case 문이 없을 떄 수행될 문장
}
```
switch 문의 제약조건
- switch 문의 조건식 결과는 정수 또는 문자열이어야 한다.
- case 문의 값은 정수 상수만 가능하며, 중복되지 않아야 한다.

## 반복문
반복문은 어떤 작업이 반복적으로 수행되도록 할 때 사용된다.   
반복문의 종류로는 for 문, while 문, do-while 문이 있다.

### for 문
반복 횟수를 알고 있을 때 적합하고, 직관적이라 이해하기 쉽다.
```java
for (초기화; 조건식; 증감식) {
  // 수행될 문장
}
```
- 초기화
  - 반복문에 사용될 변수를 초기화하는 부분
  - 처음 한번만 수행된다
- 조건식
  - 조건식의 값이 참이면 반복을 계속하고, 거짓이면 반복을 중단하고 for 문을 벗어난다.
- 증감식
  - 반복문을 제어하는 변수의 값을 증가 또는 감소시키는 식

### 향상된 for 문
배열과 컬렉션에 저장된 요소에 접근할 때 기존보다 편리한 방법으로 처리할 수 있도록 for 문의 새로운 문법
```java
for (타입 변수명 : 배열 또는 컬렉션) {
  // 반복할 문장
}
```

### while 문
조건식이 거짓일 될 때까지 블록 내의 문장을 반복한다.
```java
while (조건식) {
  // 조건식이 참인 동안, 반복될 문장
}
```

### do-while 문
기본적인 구조는 while 문과 같으나 블럭을 먼저 수행한 후에 조건식을 평가한다.
```java
do {
  // 수행될 문장
} while (조건식);
```

### break 문
자신이 포함된 가장 가까운 반복문을 벗어난다.

### continue 문
반복문 내에서만 사용될 수 있으며, 반복이 진행되는 도중 continue 문을 만나면 반복문의 끝으로 이동하여 다음 반복으러 넘어간다.