# 이진 탐색

### 선형 탐색

- 순서대로 하나씩 찾는 탐색 알고리즘
- O(n) 시간 복잡도가 걸린다.

<br>

### 이진 탐색

- 정렬 되어 있는 요소들을 반씩 제외하면서 찾는 알고리즘
- O(logN) 의 시간 복잡도가 걸린다.

#### 특징

- 반드시 정렬이 되어있어야 사용할 수 있다.
- 배열 혹은 이진 트리를 이용하여 구현할 수 있다.
- O(logN) 시간 복잡도인 만큼 상당히 빠르다.

<br>

### 이진 탐색 트리

이진 탐색을 위한 이진 트리로 왼쪽 서브 트리는 루트보다 작은 값이 모여있고, 오른쪽 서브 트리는 루트보다 큰 값이 모여있다.

#### 문제점

- 최악의 경우 한쪽으로 편향된 트리가 될 수 있다.
- 그런 경우 순차 탐색과 동일한 시간 복잡도를 가진다.
- 이를 해결하기 위해 AVL 트리, 레드-블랙 트리 같은 자료 구조를 이용할 수 있다.

<br>

### 자바스크립트로 구현

- Array

```javascript
const array = [1, 1, 5, 124, 400, 599, 1004, 2876, 8712];

function binarySearch(array, findValue) {
  let left = 0;
  let right = array.length - 1;
  let mid = Math.floor((left + right) / 2);

  while (left < right) {
    if (array[mid] === findValue) {
      return mid;
    }

    if (array[mid] < findValue) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }

    let mid = Math.floor((left + right) / 2);
  }

  return -1;
}

console.log(binarySearch(array, 2876)); // 7
console.log(binarySearch(array, 1)); // 0
console.log(binarySearch(array, 500)); // -1
```

- Binary Search Tree

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class BinarySearchTree {
  constructor() {
    this.root = null;
  }

  insert(value) {
    const newNode = new Node(value);
    if (this.root === null) {
      this.root = newNode;
      return;
    }

    let currentNode = this.root;
    while (currentNode !== null) {
      if (currentNode.value < value) {
        if (currentNode.right === null) {
          currentNode.right = newNode;
          break;
        }
        currentNode = currentNode.right;
      } else {
        if (currentNode.left === null) {
          currentNode.left = newNode;
          break;
        }
        currentNode = currentNode.left;
      }
    }
  }

  has(value) {
    let currentNode = this.root;

    while (currentNode !== null) {
      if (currentNode.value === value) {
        return true;
      }

      if (currentNode.value < value) {
        currentNode = currentNode.right;
      } else {
        currentNode = currentNode.left;
      }
    }
    return false;
  }
}

const tree = new BinarySearchTree();
tree.insert(5);
tree.insert(4);
tree.insert(7);
tree.insert(8);
tree.insert(5);
tree.insert(6);
tree.insert(2);

console.log(tree.has(8)); // true
console.log(tree.has(1)); // false
```

<br>
