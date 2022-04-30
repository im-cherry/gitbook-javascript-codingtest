# 스택

### 1. 스택

Last In First Out 이라는 개념을 가진 선형 자료 구조다.

<br/>

### 2. 자바스크립트로 구현

#### Array 로 구현

```javascript
const stack = [];

// Push
stack.push(1);
stack.push(5);
stack.push(3);
console.log(stack); // [1, 5, 3]

// Pop
stack.pop();
console.log(stack); // [1, 5]

// Get Top
console.log(stack[stack.length - 1]); // 5
```

#### Linked List 로 구현

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class Stack {
  constructor() {
    this.top = null;
    this.size = 0;
  }

  push(value) {
    const node = new Node(value);
    node.next = this.top;
    this.top = node;
    this.size += 1;
  }

  pop() {
    const value = this.top.value;
    this.top = this.top.next;
    this.size -= 1;
    return value;
  }

  size() {
    return this.size;
  }
}

const stack = new Stack();

// Push
stack.push(2);
stack.push(5);
stack.push(1);
console.log(stack); // [1, 2, 3]

// Pop
console.log(stack.pop()); // 3
console.log(stack); // [1, 2]

// Get Top
console.log(stack.size); // 2
```

<br/>

### 3. 문제 풀기 - 올바른 괄호

괄호가 올바르게 짝지어졌다는 것은 "(" 문자로 열렸으면 반드시 ")" 문자로 닫혀야 한다는 뜻입니다.  
"(" 또는 ")" 로만 이루어진 문자열 s가 주어졌을 때,  
문자열 s가 올바른 괄호이면 true 를 return 하고,  
올바르지 않은 괄호이면 false 를 return 하는 solution 함수를 완성해 주세요.

```javascript
function solution(s) {
  const stack = [];

  for (const c of s) {
    if (c === "(") {
      stack.push(c);
    } else {
      if (stack.length === 0) {
        return false;
      }
      stack.pop();
    }
  }

  return stack.length === 0;
}
```

```javascript
function solution(s) {
  let count = 0;

  for (const c of s) {
    if (c === "(") {
      count += 1;
    } else {
      if (count === 0) {
        return false;
      }
      count -= 1;
    }
  }

  return count === 0;
}
```

<br />
