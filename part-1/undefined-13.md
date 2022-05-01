# 트라이

### 1. 트라이

문자열을 저장하고 효율적으로 탐색하기 위한 트리 형태의 자료구조

#### 특징

- 검색어 자동완성, 사전 찾기 등에 응용될 수 있다.
- 문자열을 탐색할 때, 단순하게 비교하는 것보다 효율적으로 찾을 수 있다.
- L 이 문자열의 길이일 때, 삽입은 O(L) 만큼 걸린다.
- 각 정점이 자식에 대한 링크를 모두 가지고 있기에 저장공간을 많이 사용한다.

#### 구조

- 루트는 비어있다.
- 각 간선(링크)는 추가될 문자를 키로 가진다.
- 각 정점은 이전 정점의 값 + 간선의 키를 값으로 가진다.
- 해시 테이블과 연결 리스트를 이용하여 구현할 수 있다.

<br>

### 2. 자바스크립트로 구현

```javascript
class Node {
  constructor(value = "") {
    this.value = value;
    this.children = new Map();
  }
}

class Trie {
  constructor() {
    this.root = new Node();
  }

  insert(string) {
    let currentNode = this.root;

    for (const char of string) {
      if (!currentNode.children.has(char)) {
        currentNode.children.set(char, new Node(currentNode.value + char));
      }
      currentNode = currentNod.children.get(char);
    }
  }

  has(string) {
    let currentNode = this.root;

    for (const char of string) {
      if (!currentNode.children.has(char)) {
        return false;
      }
      currentNode = currentNode.children.get(char);
    }

    return true;
  }
}

const trie = new Trie();
```

<br>

### 3. 문제 풀기 - 검색 자동 완성

<br>
