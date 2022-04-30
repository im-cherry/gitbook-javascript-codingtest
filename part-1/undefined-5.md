# 자바스크립트 배열과 객체

### 1. 배열

배열은 연관된 데이터를 연속적인 형태로 저장하는 구조로,  
배열에 포함된 원소는 순서대로 번호(index) 가 붙는다.

#### 배열 생성

```javascript
const arr1 = new Array();
const arr2 = [];
const arr3 = [0, 1, 2, 3, 4];
const arr4 = new Array(5);
const arr5 = new Array(5).fill(0);
const arr6 = Array.from(Array(5), (value, index) => index);
```

#### 배열에서 사용하는 유용한 프로퍼티 및 함수

```javascript
const arr1 = [0, 1, 2, 3, 4];

console.log(arr1.length); // 5
console.log(arr1.join("-")); // 0-1-2-3-4
console.log(arr1.reverse()); // [4, 3, 2, 1, 0] : 배열 자체가 바뀜

const arr2 = [0, 1, 2];
const arr3 = [3, 4, 5];
console.log(arr2.concat(arr3)); // [0, 1, 2, 3, 4, 5]
```

#### 배열 요소의 추가와 삭제

```javascript
const arr = [0, 1, 2, 3, 4];

// push, pop
arr.push(5); //  [0, 1, 2, 3, 4, 5]
arr.push(6, 7); //  [0, 1, 2, 3, 4, 5, 6, 7]
arr.pop(); // 7
arr.pop(); // 6
arr.pop(); // 5
console.log(arr); //  [0, 1, 2, 3, 4]

// unshift, shift
arr.shift(); // 0
arr.shift(); // 1
arr.unshift(-2); // [-2, 2, 3, 4]
console.log(arr); // [-2, 2, 3, 4]
```

#### 배열 자르기

```javascript
const arr = [0, 1, 2, 3, 4];
console.log(arr.slice(2, 4)); //  [2, 3]
```

#### 중간 요소 삭제하기

```javascript
const arr = [0, 1, 2, 3, 4];
arr.splice(2, 2);
console.log(arr); // [0, 1, 4]
```

#### 배열 순회

```javascript
const arr = [0, 1, 2, 3, 4];

for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}

for (const item of arr) {
  console.log(item);
}
```

<br />

### 2. 객체

여러 값을 키-값 형태로 결합시켜 저장하는 구조이다.

#### 객체 생성

```javascript
const obj1 = new Object();
const obj2 = {};
const obj3 = { name: "im cherry" };
```

#### 객체 생성

```javascript
const obj = { name: "im cherry" };

// 추가
obj["email"] = "collcr@kakao.com";
obj.phone = "01012345678";

// 삭제
delete obj.phone;

// 객체의 키 존재 확인
console.log("email" in obj); // true
console.log("phone" in obj); // false
```

#### 객체의 키와 값 집합

```javascript
const obj = {
  name: "im cherry",
  email: "collcr@kakao.com",
  phone: "01012345678",
};

console.log(Object.keys(obj)); // ["name", "email", "phone"]
console.log(Object.values(obj)); // ["im cherry", "collcr@kakao.com", "01012345678"]
```

#### 객체 순회

```javascript
const obj = {
  name: "im cherry",
  email: "collcr@kakao.com",
  phone: "01012345678",
};

for (const key in obj) {
  console.log(key, obj[key]);
}
```

<br />
