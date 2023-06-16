```java
import java.util.*;

public class Inf2 {
	public static void main(String[] args){
		// 공통 원소 구하기
		Scanner sc = new Scanner(System.in);
		
		int n = sc.nextInt();
		int a[] = new int[n];
		for(int i=0; i<n; i++) {
			a[i] = sc.nextInt();
		}
		
		int m = sc.nextInt();
		int b[] = new int[m];
		for(int i=0; i<n; i++) {
			b[i] = sc.nextInt();
		}
		
		Arrays.sort(a);
		Arrays.sort(b);
		
		int p1 = 0;
		int p2 = 0;
		
		ArrayList<Integer> answer = new ArrayList<>();
		
		while(p1<n && p2<m) {
			if(a[p1]==b[p2]) {
				answer.add(a[p1]);
				p1++;
				p2++;
			}
			else if(a[p1] < b[p2]) {
				p1++;
			}
			else if(a[p1] > b[p2]) {
				p2++;
			}
		}
		
		for(int x: answer) {
			System.out.print(x+ " ");
		}
	    
	}
}

```