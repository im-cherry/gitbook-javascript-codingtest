# 연결 리스트

### 1. 연결 리스트

연결 리스트는 각 요소를 포인터로 연결하여 관리하는 선형 자료 구조다.  
각 요소는 노드라고 부르며, 데이터 영역과 포인터 영역으로 구성된다.

#### 특징

- 메모리가 허용하는 요소를 제한없이 추가할 수 있다.
- 탐색은 O(n) 이 소요된다.
- 요소를 추가하거나 제거할 때는 O(1)이 소요된다. 그러므로 추가와 삭제가 반복되는 로직에 유리하다.
- 단일 연결 리스트, 이중 연결 리스트, 환형 연결 리스트가 존재한다.

#### 배열과 차이점

- 메모리 차이
- 요소 추가 및 삭제

<br />

### 2. 단일 연결 리스트

Head 에서 Tail 까지 단방향으로 이어지는 가장 단순한 형태인 연결 리스트이다.

<br />

### 3. 이중 연결 리스트

양방향으로 이어지는 연결 리스트로, 단일 연결 리스트 보다 자료구조의 크기가 조금 더 크다.

<br />

### 4. 환형 연결 리스트

단일 혹은 이중 연결 리스트에서 Tail 이 Head 로 연결되는 연결 리스트로, 메모리를 아껴쓸 수 있다.

<br />

### 5. 단일 연결 리스트 자바스크립트 구현

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class SinglyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
  }

  find(value) {
    let currNode = this.head;
    while (currNode.value !== value) {
      currNode = currNode.next;
    }
    return currNode;
  }

  append(newValue) {
    const newVale = new Node(newValue);
    if (this.head == null) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      this.tail.next = newNode;
      this.tail = newNode;
    }
  }

  insert(node, newValue) {
    const newNode = new Node(newValue);
    newNode.next = node.next;
    node.next = newNode;
  }

  remove(value) {
    let preNode = this.head;
    while (preNode.next.value !== value) {
      preNode = preNode.next;
    }

    if (preNode.next !== null) {
      preNode.next = preNode.next.next;
    }
  }

  display() {
    let currNode = this.head;
    let displayString = "[";
    while (currNode !== null) {
      displayString += `${currNode.value}, `;
      currNode = currNode.next;
    }
    displayString = displayString.substr(0, displayString.length - 2);
    displayString += "]";
    console.log(displayString);
  }
}

const linkedList = new SinglyLinkedList();
linkedList.append(1);
linkedList.append(2);
linkedList.append(3);
linkedList.append(5);
linkedList.display(); // [1, 2, 3, 5, ]

console.log(linkedList.find(3)); // Node { value: 3, next Node { value: 5, next: null } }

linkedList.remove(3);
linkedList.display(); // [1, 2, 5, ]

linkedList.insert(linkedList(2), 10);
linkedList.display(); // [1, 2, 10, 5, ]
```

<br />
