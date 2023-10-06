### 0. 라이브러리

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

// 4. 오름차순 정렬하면 binary search 로 특정값을 찾을 수 있다.
Arrays.binarySearch(arr,2);

// 5. 배열을 ArrayList로 변환
List list = Arrays.asList(arr);

// 6. 배열의 특정 범위 자르기
int tmp[] = Arrays.copyOfRange(arr, 0, 3);
```

### 3. length / length() size()

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

// 3. size()
ArrayList<Integer> list = new ArrayList<>();
System.out.println(list.size());
```

### 4. String
```java
String str = "hello world";

// 1. 자르기
str.split(" ");
str.substring(0,5);
for(int i=0; i<str.length(); i++) str.charAt(i);

// 2. 문자열을 배열로 만들기
String str=  "12345";
String[] arr = str.split("");

// 3. 대소문자 변경
str = str.toUpperCase();
str = str.toLowerCase();

// *한번 쓴 문자열은 변경 불가함*
```

### 5. HashMap
```java
// 1. 선언
HashMap<String, Integer> hm = new HashMap<>();

// 2. key-value 넣기
hm.put("java",0);
hm.put("python",1);

// 3. 키로 값 가져오기
hm.get("java");

// 4. containsKey()로 존재유무 확인
if(!hm.containsKey("java")) hm.put("java",1);

// 5. 특정 키가 없으면 값 설정, 있으면 기존 값 가져오는 함수
hm.put("java", hm.getOrDefault("java",3));

// 6. keySet() 함수로 맵 순회
for(String key) : hm.keySet()){
    hm.get(key);
}
```

### 6. ArrayList
```java
// 1. 선언
ArrayList<String> list = new ArrayList<>();

// 2. 삽입
list.add("java");
list.add(0, "javascript"); //0번째 인덱스에 삽입

// 3. 수정
list.set(1, "c++")

// 4. 삭제
list.remove(1); //헤딩 인덱스 삭제

// 5. 값 존재 유무 확인
list.contains("java"); //false
list.indexOf("javascript"); //존재하면 인덱스 리턴, 없으면 -1 리턴

// 6. iterator 사용
Iterator it = list.iterator();

// 6-1. 인덱스 오름차순 순회
while (it.hasNext()) {
    // ...
}

// 6-2. 인덱스 내림차순 조회
while (it.hasPrevious()) {
    // ...
}

// 7. 중복없이 값을 넣고 싶을 때
if(list.indexOf(value) < 0 ){
    list.put(value);    
}

// 8. 리스트 값 하나씩 가져올 때 (int 일 경우)
for(int i=0; i<list.size(); i++){
    list.get(i).intValue();
}
```
