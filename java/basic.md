## java 기본 문법

```java
public class Main { // 파일명과 클래스명이 동일해야 함
    public static void main(String[] args) { // 프로그램의 시작점
        System.out.println("Hello, Java!"); // 콘솔 출력 후 줄바꿈
    }
}
```


## 기본 출력 (Output)
자바에서는 세 가지 방식의 출력 메서드를 주로 사용함

**System.out.print()**  
내용 출력 (줄바꿈 없음)

**System.out.println()**  
내용 출력 후 줄바꿈(Enter) 포함

**System.out.printf()**
서식(Format) 지정 출력

%d: 정수, %f: 실수, %s: 문자열, %c: 문자

\n: 줄바꿈, \t: 탭 간격

```java
package ch_variable;

public class PrintTest {

	public static void main(String[] args) {
		// 1. 제어 문자 (Escape Sequence) 테스트
		System.out.print("Hi\t");      // \t: 탭(Tab) 만큼 간격을 띕니다. (보통 4~8칸)
		System.out.print("Hello\n");   // \n: 줄 바꿈(New Line)을 수행합니다.
		System.out.print("Hoe are you"); // 줄 바꿈 없이 이어서 출력합니다.
		System.out.println();          // 아무것도 출력하지 않고 다음 줄로 넘어갑니다. (print 완료 후 line new)

		// 2. printf (Formatted Print) 기본 사용법
		// %s: 문자열(String), %d: 정수(Decimal), %f: 실수(Floating-point)
		System.out.printf("%s이 %s에게 %d만원을 년이자 %f에 빌렸다.\n", "홍길동", "XX은행", 300, 3.14);

		// 3. 숫자 자릿수 및 정렬 설정
		System.out.printf("%5d\n", 200);   // %5d: 전체 5칸을 확보하고 오른쪽 정렬하여 200 출력
		System.out.printf("%-5d\n", 200);  // %-5d: 전체 5칸을 확보하고 왼쪽 정렬(-)하여 200 출력
		System.out.printf("%05d\n", 200);  // %05d: 전체 5칸 중 빈자리를 0으로 채워서 200 출력

		// 4. 실수의 소수점 자릿수 정밀도 설정
		// %10.3f: 전체 10칸(소수점 포함) 확보, 소수점 아래 3자리까지만 표시
		System.out.printf("%s이 %s에게 %d만원을 년이자 %10.3f에 빌렸다.\n", "홍길동", "XX은행", 300, 3.14);
	} //main

}
```