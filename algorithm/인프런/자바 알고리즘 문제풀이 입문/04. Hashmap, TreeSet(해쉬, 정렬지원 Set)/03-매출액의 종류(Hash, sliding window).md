```java
import java.util.*;

public class Inf04 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int k = sc.nextInt();
        int[] array = new int[n];
        for (int i=0; i<n; i++){
            array[i] = sc.nextInt();
        }

        // solution
        ArrayList<Integer> answer = new ArrayList<>();
        HashMap<Integer, Integer> map = new HashMap<>();
        int lt=0;
        int rt=0;

        for(int i=0; i<k; i++){
            map.put(array[i], map.getOrDefault(array[i], 0)+1);
        }
        answer.add(map.size());

        for(rt=k; rt<n; rt++){
            map.put(array[rt-k], map.get(array[rt-k])-1);
            if(map.get(array[rt-k]) == 0 ){
                map.remove(array[rt-k]);
            }
            map.put(array[rt], map.getOrDefault(array[rt], 0)+1);
            answer.add(map.size());
        }

        for(int x: answer){
            System.out.print(x+ " ");
        }

    }
}
```