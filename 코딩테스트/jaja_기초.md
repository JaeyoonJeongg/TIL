0. 라이브러리

```java
import java.util.*;
import java.io.*;
```

### 1. 변수 선언

```java
String args[] = new String[5];
int[] arr2 = {1, 2, 3};
int[] arr3 = new int[5];
```

### 2. Arrays

```java
int arr[] = {10, 8, 11, 2, 3, 0}

// 1. 오름차순
Arrays.sort(arr);
// 2. 내림차순
Arrays.sort(arr, Collections.reverseOrder());
// 3. 일부만 정렬(인덱스 0-4만 정렬)
Arrays.sort(arr, 0, 4);
// 4. 오름차순 정렬하면 binary search 로 특정값을 찾을 수 있다
Arrays.binarySearch(arr,2);
// 5. 배열을 ArrayList로 변환
List list = Arrays.asList(arr);
// 6. 배열의 특정 범위 자르기
int tmp[] = Arrays.copyOfRange(arr, 0, 3);
```

### length / length() size()

- length: 배열의 길이

- length(): String 관련 object

- size(): Collections object

```java
// 1. length
int[] arr = new arr[3];
System.out.println(arr.length);

// 2. length()
String str = "java";
System.out.println(str.length());
```