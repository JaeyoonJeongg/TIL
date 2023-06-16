```java
import java.util.*;

public class Inf3 {
	public static void main(String[] args){
		// 최대 매출
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		
		int array[] = new int[n];
		for(int i=0; i<n; i++) {
			array[i] = sc.nextInt();
		}
		
		//Solution
		
		int sum = 0;
		int max = 0;
		
		for(int i=0; i<k; i++) {
			sum += array[i];
		}
		max = sum;
		
		for(int i=0; i<n-k; i++) {
			if(sum - array[i] + array[i+k]> max) {
				max = sum - array[i] + array[i+k];
			}
			sum = sum - array[i] + array[i+k];
		}
	    System.out.print(max);
		
	}
}
```