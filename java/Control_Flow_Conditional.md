# [Java] 제어문 - 조건문 (if, switch)

프로그램의 실행 흐름을 조건에 따라 제어하는 **조건문**의 핵심 개념과 효율적인 사용법을 정리함.

## 1. if 문
가장 기본이 되는 조건문으로, 불리언(boolean) 결과값에 따라 실행 여부를 결정함.

### 1-1. 구조 및 특징
- **if-else**: 두 가지 상황 중 하나를 선택할 때 사용함.
- **if-else if-else**: 여러 단계의 조건을 순차적으로 검사함. 상위 조건이 충족되면 하위 조건은 검사하지 않으므로 효율적임.

> **💡 기술 면접 포인트**: 단순 `if`문을 여러 번 나열하는 것과 `else if`를 사용하는 것의 차이는?
> - 단순 `if` 나열: 모든 조건을 각각 확인하므로 불필요한 연산이 발생함.
> - `else if`: 앞선 조건이 참이면 뒤의 조건은 무시하므로 성능상 유리함.

### 1-2. 실습 예제 코드 (Standard Edition)
```
public class GradeSummary {
    public static void main(String[] args) {
        int score = 85;

        if (score >= 90) {
            System.out.println("결과: A등급");
        } else if (score >= 80) {
            System.out.println("결과: B등급"); // 85점이므로 여기서 실행 후 종료
        } else if (score >= 70) {
            System.out.println("결과: C등급");
        } else {
            System.out.println("결과: F등급");
        }
    }
}
```

## 2. switch 문
특정 변수의 값에 따라 분기할 때 사용하며, `if`문보다 구조가 정형화되어 있어 가독성이 좋음.

### 2-1. 사용 가능 타입과 제약
- **허용**: `byte`, `short`, `char`, `int`, `String`(Java 7+), `Enum`
- **불가**: `long`, `float`, `double`
- **이유**: `switch`는 내부적으로 정수 기반의 점프 테이블을 사용함. 부동 소수점 오차가 있는 실수형이나 범위가 너무 큰 `long`은 효율적인 테이블 생성이 어려움.

### 2-2. Modern Java (Switch Expressions)
Java 12 이상에서 도입된 간결한 문법으로, `->` 연산자와 `yield`를 활용함.

### 2-3. 실습 예제 코드 (Standard Edition)
```
public class SwitchModern {
    public static void main(String[] args) {
        char grade = 'B';

        // 1. 화살표 연산자를 이용한 간결한 처리 (Java 12+)
        switch (grade) {
            case 'A', 'a' -> System.out.println("우수 등급임");
            case 'B', 'b' -> System.out.println("일반 등급임");
            default -> System.out.println("기타 등급임");
        }

        // 2. 값을 반환하는 스위치 표현식 (Java 13+)
        int point = switch (grade) {
            case 'A' -> 100;
            case 'B' -> {
                int base = 50;
                int bonus = 20;
                yield base + bonus; // yield를 사용하여 최종 결과값 반환
            }
            default -> 0;
        };
        System.out.println("획득 포인트: " + point);
    }
}
```