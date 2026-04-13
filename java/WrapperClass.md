## 래퍼 클래스(Wrapper Class)

### 1. Wrapper Class란?
- 기본 자료형(Primitive Type)을 객체(Object)로 다루기 위해 사용하는 클래스.
- 자바의 제네릭이나 객체 지향 API를 사용할 때 필수적임.

| 기본 타입 | 래퍼 클래스 |
| :--- | :--- |
| int | **Integer** |
| char | **Character** |
| double | Double |
| boolean | Boolean |

### 2. 주요 기능 및 메서드
- **문자열 변환 (Parsing)**: 문자열 데이터를 숫자형으로 바꿀 때 가장 많이 사용됨.
    - `Integer.parseInt("123")`
    - `Double.parseDouble("3.14")`
- **값 생성**: `new Integer()`는 권장되지 않음(Deprecated). 대신 `Integer.valueOf()`를 사용함.
- **형 변환**: 래퍼 객체에서 다른 타입의 기본형 값을 바로 추출 가능 (`intValue()`, `doubleValue()` 등).

### 3. 실습 예제 코드 (Standard Edition)
```java
public class WrapperSummary {
    public static void main(String[] args) {
        // 1. 문자열 -> 숫자 변환 (핵심)
        String strNum = "2026";
        int convertedNum = Integer.parseInt(strNum);
        
        // 2. 객체 생성 및 활용
        Integer wrappedInt = Integer.valueOf(500);
        double convertedDouble = wrappedInt.doubleValue();

        System.out.println("Converted: " + convertedNum);
        System.out.println("As Double: " + convertedDouble);
    }
}