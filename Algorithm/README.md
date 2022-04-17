# Algorithm
### Stack
- 순차적으로 데이터 접근
- 중복 허용
```java
Stack<Integer> stack = new Stack<>();
if(stack.empty()){
  stack.push(1);
}
int n = stack.peek();
if(stack.search(n)==-1) sout("3 is poped");
```
---
### Map
- 입력된 데이터들을 Key와 Value로 저장하고 싶을 때, 탐색이 O(1)이기 때문에 특정한 값을 바로 읽어와야 할 때 사용. 
- 중복 허용 X
- Key를 사용하고 정렬 가능
```java
HashMap<String, Integer> hm = new HashMap<>();
hm.put("key1", 1);
if(hm.containsKey("key1") && hm.containsValue(1)) sout("YES");
hm.put("key1", hm.getOrDefault(("key1"), 0) + 10);  //key가 존재하면 value를 반환, 존재하지 않으면 지정한 Default값 반환
List<String> keyList = new ArrayList<>(hm.keySet());
Collections.sort(keyList, new Comparator<String>(){
  public int compare(String s1, String s2){
    int v1 = hm.get(s1);
    int v2 = hm.get(s2);
    return Integer.compare(v1, v2);
  }
});
for(String s : KeyList){
  sout(hm.get(s));
}
sout(hm.size());
```
