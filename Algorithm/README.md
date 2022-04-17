# Algorithm
### Stack
- 순차적으로 데이터 접근
- **중복 허용**
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
- **중복 허용 X**
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
- **중복 허용 X**
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
- **중복 허용**
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
### 그래프
- 정점(Node)과 그 정점을 연결하는 간선(edge)으로 이루어진 자료구조의 일종.
- 그래프를 탐색한다는 것은 하나의 정점으로부터 시작하여 차례대로 모든 정점들을 한 번씩 방문하는 것.
- 그래프 중에서 **방향성이 있는 비순환 그래프**를 **트리**라고 한다.
---
### DFS(깊이 우선 탐색)
- 최대한 깊이 내려간 뒤, 더이상 깊이 갈 곳이 없을 경우 옆으로 이동
- 개념 : 루트 노드에서 시작해서 다음 분기로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 방식.
- 모든 노드를 방문, BFS보다 좀 더 간단하지만 속도는 느림.
- 스택 또는 재귀함수로 구현
```java
/* DFS에 의해 사용되는 함수 */ 
void DFSUtil(int v, boolean visited[]) { 
  // 현재 노드를 방문한 것으로 표시하고 값을 출력 
  visited[v] = true; 
  System.out.print(v + " "); 
  
  // 방문한 노드와 인접한 모든 노드를 가져온다. 
  Iterator<Integer> it = adj[v].listIterator(); 
  while (it.hasNext()) { 
    int n = it.next(); 
    // 방문하지 않은 노드면 해당 노드를 시작 노드로 다시 DFSUtil 호출 
    if (!visited[n]) DFSUtil(n, visited); 
  }
}
```
---
### BFS(너비 우선 탐색)
- 최대한 넓게 이동한 다음, 더 이상 갈 수 없을 때 아래로 이동
- 개넘 : 루트 노드에서 시작해서 인접한 노드를 먼저 탐색하는 방식.
- 주로 두 노드 사이의 최단 경로를 찾을 때.
- 큐를 이용해서 구현
```java
/* BFS */ 
void BFS(int s) { 
  boolean visited[] = new boolean[V]; 
  //방문여부 확인용 변수 
  LinkedList<Integer> queue = new LinkedList<Integer>(); 
  //연결리스트 생성 
  visited[s] = true; 
  queue.add(s); 
  while (queue.size() != 0) { 
    // 방문한 노드를 큐에서 추출(dequeue)하고 값을 출력 
    s = queue.poll(); 
    System.out.print(s + " "); 
    // 방문한 노드와 인접한 모든 노드를 가져온다. 
    Iterator<Integer> i = adj[s].listIterator();
    while (i.hasNext()) { 
      int n = i.next(); 
      // 방문하지 않은 노드면 방문한 것으로 표시하고 큐에 삽입(enqueue) 
      if (!visited[n]) { 
        visited[n] = true; 
        queue.add(n); 
      } 
    } 
  }
}
```
---
### DFS, BFS를 활용한 문제 유형/응용
- 모든 정점 방문 : DFS, BFS
- 경로의 특징 저장(a에서 b까지 가는 경로를 구하는 데 경로에 같은 숫자가 있으면 안 된다는 문제) : DFS
- 최단거리 : BFS
- 검색 대상 그래프가 크다 : DFS
---
### Divide and Conquer(분할 정복)
- 그대로 해결할 수 없는 문제를 작은 문제로 분할하여 문제를 해결하는 방법
- 주로 Quick Sort나 Merge Sort로 대표되는 정렬 알고리즘
```
1. 문제 사례를 하나 이상의 작은 사례로 분할(Divide)한다.  
2. 작은 사례들을 각각 정복(Conquer)한다. 작은 사례가 충분히 작지 않는 이상 재귀를 사용한다.
3. 필요하다면, 작은 사례에 대한 해답을 통한(Combine)하여 원래 사례의 해답을 구한다.
```
**장점**
- 문제를 나눔으로써 어려운 문제를 해결.
**단점**
함수를 재귀적으로 호출 -> 오버헤드, 스택에 다양한 데이터 보관 -> 스택 오버플로우, 과도한 메모리 사용.
ex)
```java
int consecutive_sum(start, end){
	if(start == end) return start;
  
    mid = (start + end) / 2;
    
    return consecutive_sum(start, mid) + consecutive_sum(mid + 1, end);
}
# 출력
System.out.println(consecutive_sum(1, 100))
# 결과 값
5050
```
---
### DP(Dynamic Programming)(동적 프로그래밍)
- 큰 문제를 작은 문제로 나누어 푸는 문제.('다이나믹'이라는 단어는 아무런 관련이 없다?!)
- Divide and Conquer(분할정복)과 다른 점 : 작은 문제가 중복이 일어나는지 안일어나는지 차이.
- DP는 겹치는 문제가 발생하기 때문에 메모이제이션 등이 필요하다.
- 조건 : 작은 문제가 반복이 일어나는 경우, 같은 문제는 구할 때마다 정답이 같다.
- 그리디 알고리즘과 비교 : 시간이 오래 걸리지만 항상 최적의 해를 구할 수 있다.
- **Memoization을 이용한 피보나치 수열 알고리즘**
```java
public class Fibonacci{
	static int[] dp = new int[1000];      //dp[] 배열에 값을 저장해서 또 그 값이 나온다면 바로 리턴.
	static int fibonacci(int n){
    	if(n == 0) return 0;
        if(n == 1) return 1;
        if(dp[n] != 0) return dp[n];
        dp[n] = fibonacci(n - 2) + fibonacci(n - 1);
        return dp[n];
    }
    
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        System.out.println(fibonacci(N));
    }
}
```
