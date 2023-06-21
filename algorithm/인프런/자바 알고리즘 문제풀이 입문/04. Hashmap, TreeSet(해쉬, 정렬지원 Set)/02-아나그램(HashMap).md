```java
import java.util.*;

public class Inf2 {
	public static void main(String[] args){
		// 아나그램(해쉬) 
		// 아나그램 : 어느 한 단어를 재배열 하면 상대편 단어가 될 수 있는것
		
		Scanner sc = new Scanner(System.in);
		String str1 = sc.next();
		String str2 = sc.next();
		
		// solution
		boolean anagram = true;
		HashMap<Character, Integer> map = new HashMap<>();
		
		for(char x: str1.toCharArray()) {
			map.put(x, map.getOrDefault(x, 0)+1);
		}
		for(char x: str2.toCharArray()) {
			map.replace(x, map.getOrDefault(x, 0)-1);
		}
		
		for(char key: map.keySet()) {
			if(map.get(key)!=0)
				anagram = false;
		}
		
		if(anagram) 
			System.out.println("YES");
		else
			System.out.println("NO");
	}
}
```