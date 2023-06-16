```java
import java.util.*;

public class Inf08 { 
	// 유효한 팰린드롬 : 앞에서 읽을때와 뒤에서 읽을 때나 같다.
	//입력 : found7,time:study;Yduts;emit,7Dnuof 결과: YES || NO
	public static void main(String[] args){
	    Scanner sc = new Scanner(System.in);
	    
	    String str = sc.nextLine().replaceAll("[^a-zA-Z]", "").toUpperCase();
	    String reverse = new StringBuilder(str).reverse().toString();
	    String answer = "";
	   
	    if(str.equals(reverse)) {
	    	answer = "YES";
	    }
	    else
	    	answer = "NO";
	    
	    System.out.println(answer);
	    
	}
}
```