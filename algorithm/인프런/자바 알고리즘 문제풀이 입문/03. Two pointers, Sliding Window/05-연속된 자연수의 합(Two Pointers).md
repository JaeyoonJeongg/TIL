```java
import java.util.*;

public class Inf5 {
	public static void main(String[] args){
		// 연속된 자연수의 합 (two pointers)
		
		Scanner sc = new Scanner(System.in);	
		int n = sc.nextInt();
		
		//solution
		int sum = 0;
		int answer = 0;
		int lt = 1;
		int rt;
		
		for(rt=1; rt<=n/2+1; rt++) {
			sum += rt;
			if(sum == n) {
				answer++;
			}
			while(sum>=n) {
				sum -= lt;
				if(sum == n) {
					answer++;
				}
				lt++;
			}
		}
		
		System.out.println(answer);
		
	    
	}
}

```