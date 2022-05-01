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

### 3. 문제 풀기 - 자동 완성

포털 다음에서 검색어 자동완성 기능을 넣고 싶은 라이언은 한 번 입력된 문자열을 학습해서 다음 입력 때 활용하고 싶어졌다.  
예를 들어, `go` 가 한번 입력되었다면, 다음 사용자는 `g` 만 입력해도 `go` 를 추천해주므로 `o` 를 입력할 필요가 없어진다!  
단, 학습에 사용된 단어들 중 앞부분이 같은 경우에는 어쩔 수 없이 다른 문자가 나올 때까지 입력을 해야한다.  
효과가 얼마나 좋을지 알고 싶은 라이언은 학습된 단어들을 찾을 때 몇 글자를 입력해야 하는지 궁금해졌다.  
예를 들어, 학습된 단어들이 `go`, `gone`, `guild` 일 때, `go`를 찾을때 `go`를 모두 입력해야 합니다.  
`gone`을 찾을 때 `gon`까지 입력해야 합니다. `guild` 를 찾을 때는 `gu` 까지만 입력하면 `guild` 가 완성됩니다.  
이 경우 총 입력해야 할 문자의 수는 `7` 입니다.  
라이언을 도와 문자열이 입력으로 주어지면 학습을 시킨 후, 학습된 단어들을 순서대로 찾ㅇ르 때 몇 개의 문자를 입력하면 되는지 계산하는 프로그램을 만들어 보자.

```javascript
function makeTrie(words) {
  const root = {}; // 먼저 루트 노드를 설정할 변수를 만든다.

  for (const word of words) {
    // Tire를 구성하기 위한 루프 돌리기
    let current = root; // 루프부터 시작
    for (const letter of word) {
      // 단어의 글자를 하나씩 추출한 후
      if (!current[letter]) {
        // 리스트의 첫 번째 값은 학습된 단어가 몇 개인지를 카운팅하고 두 번째 값은 트리 구조로 이용할 노드 값으로 사용한다.
        current[letter] = [0, {}]; // 값 넣기
      }
      current[letter][0] = 1 + (current[letter][0] || 0); // 카운팅을 위해 1을 더해준다.
      current = current[letter][1]; // current 는 letter에 해당되는 노드로 이동한다.
    }
  }

  return root;
}

function solution(words) {
  let answer = 0;
  const trie = makeTrie(words); // Trie 자료구조를 만들어준다.

  // 입력 받은 수 만큼 루프
  for (const word of words) {
    let count = 0; // 카운팅을 위한 변수
    let current = tri; // 루트부터 시작

    for (const [index, letter] of [...word].entries()) {
      count += 1;

      // 단어가 하나 이하로 남을 경우 종료
      if (current[letter][0] <= 1) {
        break;
      }

      current = current[letter][1]; // 다음 노드 이동
    }
    answer += count; // 카운팅 더하기
  }

  return answer;
}
```

<br>
