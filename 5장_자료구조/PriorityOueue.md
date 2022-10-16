## 5.3.4 우선순위 큐(Priority Queue)
: 우선순위 큐는 우선순위 대기열이라고도 하며, 대기열에서 우선순위가 높은 요가가 우선 순위가 낮은 요소보다 먼저 제공되는 자료 구조. (힙을 기반으로 구현된다.) - 시간 복잡도 O(logN)


### 구현 방법
- 트리 구조를 배열을 통해서 구현 한다.
- 왼쪽 자식 노드 인덱스 = 부모 노드 인덱스 × 2 

- 오른쪽 자식 노드 인덱스 = 부모 노드 인덱스 × 2 + 1

- 부모 노드 인덱스 = 자식 노드 인덱스 / 2

**배열을 이용하는 이유**
: 연결리스트로도 구현이 가능하긴 하지만, 문제는 특정 노드의 '검색', '이동' 과정이 조금 더 번거롭기 때문이다. 배열의 경우는 특정 인덱스에 바로 접근할 수가 있기 때문에 좀 더 효율적이기도 하다.

### 실제 구조
![](https://velog.velcdn.com/images/pwolong/post/dc3be51b-b730-44c4-909f-0325623f7b53/image.png)

### 구현 내용

```kotlin
class PriorityQueue {

//    1. 왼쪽 자식 노드 인덱스 = 부모 노드 인덱스 × 2
//    2. 오른쪽 자식 노드 인덱스 = 부모 노드 인덱스 × 2 + 1
//    3. 부모 노드 인덱스 = 자식 노드 인덱스 / 2
    companion object{
        var priorityQueue = ArrayList<Int>()
        fun getInstance() : ArrayList<Int> {
            return priorityQueue
        }
    }
    
    init {
        priorityQueue.add(0)
    }

    fun offer(element: Int) {
        priorityQueue.add(element)
        offerExplore(priorityQueue.size - 1)
    }

    fun poll(): Int {
        val result = priorityQueue[1]
        priorityQueue[1] = priorityQueue[priorityQueue.size - 1]
        priorityQueue.removeLast()
        pollExplore(1)
        return result
    }

    fun switch(positionFrom: Int, positionTo: Int) {
        val temp = priorityQueue[positionFrom]
        priorityQueue[positionFrom] = priorityQueue[positionTo]
        priorityQueue[positionTo] = temp
    }

    fun offerExplore(position: Int) {
        if (position == 1) {
            return
        }
        val parentIdx = position / 2
        if (priorityQueue[parentIdx] > priorityQueue[position]) {
            switch(position, parentIdx)
            offerExplore(parentIdx)
        } else {
            return
        }
    }

    fun pollExplore(position: Int) {
        if(position*2 >= priorityQueue.size) return
        val leftIdx = position * 2
        val rightIdx = position * 2 + 1
        var resultIdx = 0

        resultIdx = if (priorityQueue[leftIdx] >= priorityQueue[rightIdx]) {
            rightIdx
        } else {
            leftIdx
        }

        if(priorityQueue[position] > priorityQueue[resultIdx]){
            switch(position, resultIdx)
            pollExplore(resultIdx)
        } else {
            return
        }

    }
}

```

### 결과 

```kotlin
fun main(){
    var priorityQueue = PriorityQueue()

    priorityQueue.offer(30)
    priorityQueue.offer(60)
    priorityQueue.offer(20)
    priorityQueue.offer(1)
    priorityQueue.offer(15)
    priorityQueue.offer(11)
    priorityQueue.offer(88)
    priorityQueue.offer(5)
    priorityQueue.offer(23)
    priorityQueue.offer(65)
    priorityQueue.offer(33)
    priorityQueue.offer(8)
    printing()

    println(priorityQueue.poll())
    printing()
    println(priorityQueue.poll())
    printing()
    println(priorityQueue.poll())
    printing()
    println(priorityQueue.poll())

    printing()

}

fun printing(){
    val list = PriorityQueue.getInstance()
    list.forEach {
        print("[$it] ")
    }
    println()
}
```

![](https://velog.velcdn.com/images/pwolong/post/fa7eb422-2cb0-4499-85aa-c474bbe72144/image.png)



