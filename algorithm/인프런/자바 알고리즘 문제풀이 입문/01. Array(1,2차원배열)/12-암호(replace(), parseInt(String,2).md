```java
import java.util.*;

public class Inf12 { 
	public static void main(String[] args){
		// <암호 해석 문제>
		// #*****# 를 일곱자리의 이진수
		// #은 이진수의 1로, *이진수의 0으로 변환 -> 1000001
		// 이진수를 십진수로 변환, 십진수를 아스키 코드로 변환하여 알파벳 출력
		
		//입력: 4 #****###**#####**#####**##**
		//출력: COOL
		String answer = "";
		Scanner sc = new Scanner(System.in);
		
		int n = sc.nextInt();
		String str = sc.next();
		
		str = str.replace("#", "1");
		str = str.replace("*", "0");

		ArrayList<Integer> numbers = new ArrayList();
		
		for(int i=0; i<n; i++) {
			numbers.add(Integer.parseInt(str.substring(0,7),2));
			str = str.substring(7);
			int temp = numbers.get(i);
			answer += ((char)temp);
		}
		
		System.out.println(answer);
	
	}
}
```