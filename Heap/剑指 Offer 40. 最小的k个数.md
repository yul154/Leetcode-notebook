# 输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。

 
```
示例 1：

输入：arr = [3,2,1], k = 2
输出：[1,2] 或者 [2,1]
示例 2：

输入：arr = [0,1,2,1], k = 1
输出：[0]
```

限制：

0 <= k <= arr.length <= 10000
0 <= arr[i] <= 10000


* Solution
```
import java.util.ArrayList;
import java.util.Arrays;
class Solution {
    public int[] getLeastNumbers(int[] input, int k) {
       int[] res = new int[k];
       if (k == 0) { // 排除 0 的情况
            return res;
        }
        //PriorityQueue<Integer>  maxHeap = new PriorityQueue<Integer>((x, y) -> Integer.compare(y, x));
        PriorityQueue<Integer>  maxHeap = new PriorityQueue<Integer>(Collections.reverseOrder());
        
        for(int i = 0; i<k; i++){
            maxHeap.offer(input[i]);
        }
        
        for (int i = k; i<input.length;i++){
            if(input[i]<maxHeap.peek()){
                maxHeap.poll();
                maxHeap.add(input[i]);
            }
        }
        
        /*for (int e : input) {
        // 当前数字小于堆顶元素才会入堆
          if (heap.isEmpty() || heap.size() < k || e < heap.peek()) {
              heap.offer(e);
          }
          if (heap.size() > k) {
              heap.poll(); // 删除堆顶最大元素
          }*/
        }


        
        for(int i = 0; i<k; i++){
            res[i]= maxHeap.poll();
        }
        return res;


    }
}
```


## How to define a max heap
> Priority queue represented as a balanced binary heap: the two children of queue[n] are queue[2*n+1] and queue[2*(n+1)]. The priority queue is ordered by comparator, or by the elements' natural ordering.

* The default PriorityQueue is implemented with Min-Heap, that is the top element is the minimum one in the heap.


```
Queue<Integer> maxHeap = new PriorityQueue<Integer>(Collections.reverseOrder());
PriorityQueue<Integer> pq =new PriorityQueue<>((x, y) -> Integer.compare(y, x));
Queue<Integer> pq = new PriorityQueue<>((v1, v2) -> v2 - v1);
PriorityQueue<Integer> maxPQ = new PriorityQueue<>((a,b) -> b.compareTo(a)); 

PriorityQueue<Integer> pq = new PriorityQueue<Integer>(new Comparator<Integer>() {
    public int compare(Integer lhs, Integer rhs) {
        if (lhs < rhs) return +1;
        if (lhs.equals(rhs)) return 0;
        return -1;
    }
});

PriorityQueue<Integer> queue = new PriorityQueue<Integer>(k,new Comparator<Integer>(){
            public int compare(Integer i1, Integer i2) {
               j-i
            }
        });

```
