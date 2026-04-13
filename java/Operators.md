## 연산자(Operators)

### 1. 증감 연산자 (Prefix vs Postfix)
- **전치(Prefix)**: 모든 연산에 앞서 값이 먼저 변경됨 (`++a`)
- **후치(Postfix)**: 현재 라인의 연산이 모두 끝난 후 값이 변경됨 (`a++`)

> **⚠️ 주의**: 다른 연산과 복합적으로 사용될 때 실행 순서가 달라지므로 주의가 필요함.

### 2. 논리 연산자와 단락 회로 (Short-Circuit Logic)
- **비트 논리 (`&`, `|`)**: 좌항과 우항을 **모두 검사**함.
- **Short-Circuit (`&&`, `||`)**: 효율적인 연산을 위해 불필요한 검사를 생략함.
    - `||`: 좌항이 `true`면 우항은 보지도 않고 전체를 `true`로 판단.
    - `&&`: 좌항이 `false`면 우항은 보지도 않고 전체를 `false`로 판단.

### 3. 삼항 연산자 (Conditional Operator)
- 조건식의 결과에 따라 다른 값을 반환하는 간결한 제어문.
- 형식: `조건식 ? 참일_때_값 : 거짓일_때_값`
- 중첩해서 사용하여 다중 조건 처리도 가능하지만, 가독성을 위해 적절히 사용해야 함.

### 4. 실습 예제 코드 (Standard Edition)
```java
public class OperatorSummary {
    public static void main(String[] args) {
        // 1. 증감 연산
        int a = 10;
        int b = a++; // b에 10 대입 후 a는 11
        int c = ++a; // a가 12가 된 후 c에 12 대입

        // 2. Short-Circuit Logic
        // 좌항이 true이므로 우항의 0으로 나누기 연산은 실행되지 않아 에러가 나지 않음
        if (true || (10 / 0 == 0)) {
            System.out.println("Safe Execution!");
        }

        // 3. 삼항 연산자
        int score = 85;
        String grade = (score >= 90) ? "A" : (score >= 80 ? "B" : "C");
        System.out.println("Grade: " + grade);
    }
}