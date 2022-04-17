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
---
### Set
- 중복 허용 X
- TreeSet은 정렬되어서 저장, HashSet은 정렬 보장 X
```java
TreeSet<String> ts = new TreeSet<>();
ts.add("apple");
ts.add("core");
for(String s : ts) sout(s)    //정렬된 순서로 출력

HashSet<String> hs = new HashSet<>(ts);
for(String s: hs) sout(s)     //정렬되지 않은 채 출력

Iterator<String> iterator = hs.iterator();
while(iterator.hasNext()){
  String element = iteraot.next();
  if(element.length() % 2 == 0) iterator.remove();
}
```
---
### Heap(Priority Queue)
- 데이터의 추가 및 삭제를 해도 항상 정렬 상태를 유지
- Priority Queue의 생성자를 통해서, Heap Tree(Min, Max) 외 다양한 형태 구현 가능
- 중복 허용
```java
public static class Item{
  int val1, val2;
  Item(int val1, int val2){
    this.val1 = val1;
    this.val2 = val2;
  }
}
public static void main (String[] args) throws java.lang.Exception
{
  // 생성 및 정렬
  PriorityQueue<Item> queue = new PriorityQueue<>(new Comparator<Item>(){
    public int compare(Item i1, Item i2){
      if(i1.val1 == i2.val1){
        return Integer.compare(i1.val2, i2.val2);
      }else
        return Integer.compare(i1.val1, i2.val1);
    }
  });
        
  queue.add(new Item(4, 3));
  queue.add(new Item(3, 6));
  queue.add(new Item(4, 8));
  queue.add(new Item(1, 1));
        
  // Poll & Peek
  if(queue.size() != 0)
    queue.poll();
            
  queue.add(new Item(7, 3));
  queue.add(new Item(2, 6));
        
  // 단순 출력(정렬되어 있어도, 단순 출력은 정렬형태가 아님)
  for(Item item : queue){
    System.out.println(item.val1 + " : " + item.val2);
  }
        
        
  // Sort 확인
  while(queue.size() != 0){
    Item item = queue.poll();
    System.out.println(item.val1 + " : " + item.val2);
  }
}
```
---
