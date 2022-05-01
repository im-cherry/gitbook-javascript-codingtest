# 트리

### 1. 트리

방향 그래프의 일종으로 정점을 가리키는 간선이 하나 밖에 없는 구조를 가지고 있다. (ex: 조직도, 폴더 구조)

#### 특징

- 루트 정점을 제외한 모든 정점은 반드시 하나의 부모 정점을 가진다.
- 정점이 N개인 트리는 반드시 N-1 개의 간선을 가진다.
- 루트에서 특정 점점으로 가는 경로는 유일하다.

#### 구현 방법

그래프와 마찬가지로 인접 행렬, 인접 리스트 두 가지 방식으로 표현할 수 있다.

<br>

### 2. 이진 트리

각 정점이 최대 2개의 자식을 가지는 트리를 의미한다.

#### 특징

- 정점이 N 개인 이진 트리는 최악의 경우 높이가 N이 될 수 있다.
- 정점이 N 개인 포화 또는 완전 이진 트리의 높이는 logN 이다.
- 높이가 h인 포화 이진 트리는 2^h - 1 개의 정점을 가진다.

#### 구현 방법

배열 혹은 요소에 링크가 2개 존재하는 연결 리스트로 구현할 수 있다.

<br>

### 4. 자바스크립트로 구현 - 이진 트리

#### Array

```
// Left = Index * 2
// Right = Index * 2 + 1
// Parent = floor(Index / 2)
const tree = [
  undefined,
  // 1
  9,
  // 1*2, 1*2 + 1
  3, 8,
  // 2*2, 2*2 + 1, 3*2, 3*2 + 1
  2, 5, undefined, 7,
  // 4*2, 4*2 + 1, 5*2, 5*2 + 1
  undefined, undefined, undefined, 4
]
```

#### Linked List

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class Tree {
  constructor(node) {
    this.root = node;
  }

  display() {
    const queue = new Queue();
    queue.enqueue(this.root);

    while (queue.size) {
      const currentNode = queue.dequeue();
      console.log(currentNode);

      if (currentNode.left) queue.enqueue(currenNode.left);
      if (currentNode.right) queue.enqueue(currenNode.right);
    }
  }
}

const tree = new Tree(new Node(9));
tree.root.left = new Node(3);
tree.root.right = new Node(8);
tree.root.left.left = new Node(2);
tree.root.left.right = new Node(5);
tree.root.right.right = new Node(7);
tree.root.left.right.right = new Node(4);
```

<br>
