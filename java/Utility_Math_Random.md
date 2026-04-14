# [Java] 유틸리티 클래스 - Math & Random

수학적 연산 기능을 제공하는 `Math` 클래스와 다양한 난수 생성을 담당하는 `Random` 클래스의 활용법을 정리함.

## 1. Math 클래스
`java.lang` 패키지에 포함되어 별도의 import가 필요 없으며, 모든 메서드가 `static`으로 선언되어 객체 생성 없이 클래스명으로 즉시 호출 가능함.

### 1-1. 주요 메서드 요약
| 메서드 | 설명 | 예시 |
| :--- | :--- | :--- |
| `Math.ceil()` | 소수점 이하 올림 처리하여 반환함. | `Math.ceil(3.14)` -> `4.0` |
| `Math.floor()` | 소수점 이하 내림 처리하여 반환함. | `Math.floor(3.14)` -> `3.0` |
| `Math.round()` | 소수점 첫째 자리에서 반올림하여 정수형으로 반환함. | `Math.round(3.5)` -> `4` |
| `Math.pow(a, b)` | a의 b제곱값을 계산함. | `Math.pow(2, 5)` -> `32.0` |
| `Math.sqrt()` | 숫자의 제곱근(루트) 값을 반환함. | `Math.sqrt(16)` -> `4.0` |
| `Math.max/min()` | 두 인자 중 최댓값 또는 최솟값을 선택함. | `Math.max(10, 20)` -> `20` |

### 1-2. 실습 예제 코드 (Standard Edition)
```java
public class MathSummary {
    public static void main(String[] args) {
        double pi = Math.PI; // 3.141592653589793
        
        System.out.println("올림: " + Math.ceil(pi));
        System.out.println("내림: " + Math.floor(pi));
        System.out.println("반올림: " + Math.round(pi));
        
        double base = 2;
        double exp = 10;
        System.out.println("2의 10승: " + Math.pow(base, exp));
        System.out.println("144의 제곱근: " + Math.sqrt(144.0));
    }
}
```

## 2. 난수(Random Number) 생성

### 2-1. Math.random() 메서드
0.0 이상 1.0 미만의 실수(`double`)를 반환함. 특정 범위의 정수를 얻기 위해 곱셈과 형변환 연산이 필요함.
- **공식**: `(int)(Math.random() * 범위내갯수) + 시작숫자`

### 2-2. Random 클래스
`java.util.Random` 패키지를 사용하며, 정수형 난수 생성이 `Math.random()`보다 직관적임.
- **주요 메서드**: `nextInt(n)` 호출 시 0부터 n-1까지의 정수를 반환함.

### 2-3. 실습 예제 코드 (Standard Edition)
```java
import java.util.Random;

public class RandomSummary {
    public static void main(String[] args) {
        // 1. Math.random()을 이용한 1~45 로또 번호 생성
        int lottoNum = (int)(Math.random() * 45) + 1;
        System.out.println("Math.random 로또: " + lottoNum);

        // 2. Random 클래스를 이용한 주사위 번호(1~6) 생성
        Random random = new Random();
        int diceNum = random.nextInt(6) + 1;
        System.out.println("Random 클래스 주사위: " + diceNum);
        
        // 3. 음수를 포함한 정수 난수 생성
        int anyInt = random.nextInt(); // int 전체 범위 중 난수 발생
        System.out.println("임의의 정수: " + anyInt);
    }
}
```

## 3. 활용 및 요약
- 단순 산술 및 절대값, 삼각함수 등의 계산에는 `Math` 클래스 활용이 필수적임.
- 로또 번호 생성, 주사위 게임 등 무작위 수치가 필요한 로직에는 `Random` 클래스의 `nextInt()` 메서드 사용이 가독성 측면에서 유리함.