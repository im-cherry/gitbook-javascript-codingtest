# 자바스크립트 코드 트릭

### 1. 구조 분해 할당을 이용한 변수 swap

```javascript
let a = 5;
let b = 10;

[a, b] = [b, a];

console.log(a, b); // 10 5
```

<br/>

### 2. 배열 생성으로 루프 제거하기

```javascript
const sum = Array.from(new Array(10), (_, k) => k + 1).reduce(
  (acc, cur) => acc + cur,
  0
);

console.log(sum); // 55
```

<br/>

### 3. 배열 내 같은 요소 제거하기

```javascript
const names = ["Lee", "Kim", "Park", "Lee", "Kim"];
const uniqueNames = [...new Set(names)];

console.log(uniqueNames); // ['Lee', 'Kim', 'Park']
```

<br/>

### 4. Spread 연산자를 이용한 객체 병합

```javascript
const person = {
  name: "im cherry",
  familyName: "im",
  givenName: "cherry",
};

const company = {
  name: "SSAFY",
  address: "Daejeon",
};

const cherry = { ...person, ...company };
console.log(cherry); // {name: 'SSAFY', familyName: 'im', givenName: 'cherry', address: 'Daejeon'}
```

<br/>

### 5. %% 와 || 활용

```javascript
// 기본 값을 넣어주고 싶을때 사용할 수 있습니다.
// participantName 이 0, undefined, 빈 문자열, null 일 경우 "Guest" 로 할당됩니다.
const name = participantName || "Guest";

// flag 가 true일 경우에만 실행됩니다.
flag && func();

// 객체 병합에도 이용할 수 있습니다.
const makeCompany = (showAddress) => {
  return {
    name: "SSAFY",
    ...(showAddress && { address: "Daejeon" }),
  };
};
console.log(makeCompany(true)); // {name: 'SSAFY', address: 'Daejeon'}
console.log(makeCompany(false)); // {name: 'SSAFY'}
```

<br/>

### 6. 구조 분해 할당 사용하기

```javascript
const person = {
  name: "im cherry",
  familyName: "im",
  givenName: "cherry",
  company: "SSAFY",
  address: "Daejeon",
};

const { name, company } = person;
console.log(name); // im cherry
console.log(company); // SSAFY
```

```javascript
const name = "im cherry";
const company = "SSAFY";

const person = {
  name,
  company,
};
console.log(person); // {name: 'im cherry', company: 'SSAFY'}
```

<br/>

### 7. 비구조화 할당 사용하기

```javascript
const makeCompany = ({ name, address, serviceName }) => {
  return {
    name,
    address,
    serviceName,
  };
};

const SSAFY = makeCompany({
  name: "SSAFY",
  address: "Daejeon",
  serviceName: "education",
});
console.log(SSAFY); // {name: 'SSAFY', address: 'Daejeon', serviceName: 'education'}
```

<br/>

### 8. 동적 속성 이름

```javascript
const nameKey = "name";
const emailKey = "email";

const person = {
  [nameKey]: "im cherry",
  [emailKey]: "collcr@kakao.com",
};
console.log(person); // {name: 'im cherry', email: 'collcr@kakao.com'}
```

<br/>

### 9. !! 연산자를 사용하여 Boolean 값으로 바꾸기

```javascript
function check(variable) {
  if (!!variable) {
    console.log(variable);
  } else {
    console.log("잘못된 값입니다.");
  }
}

check(null); // 잘못된 값입니다.
check(undefined); // 잘못된 값입니다.
check(0); // 잘못된 값입니다.
check(""); // 잘못된 값입니다.
check(NaN); // 잘못된 값입니다.

check(5); // 5
check(3.14); // 3.14
check("Good"); // Good
```

<br/>
