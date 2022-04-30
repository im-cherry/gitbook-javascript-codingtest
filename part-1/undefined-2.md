# 시간 복잡도

### 1. 빅오 표기법

알고리즘의 시간 복잡도를 나타내는 표기법

- O(n)

```javascript
for(let i=0; i<n; i++){
    ...
}
```

- O(logn)

```javascript
for(let i=0; i<n; i*=2){
    ...
}
```

- O(nlogn)

```javascript
for(let i=0; i<n; i++){
    for(let j=0; j<n; j*=2){
        ...
    }
}
```

- O(n^2)

```javascript
for(let i=0; i<n; i++){
    for(let j=0; j<n; j++){
        ...
    }
}
```

<br/>

### 2. 빅오 표기법에서 중요한 법칙

- 상수항은 무시한다.

```javascript
// O(n+m)
for(let i=0; i<n*6; i++){
    ...
}
for(let i=0; i<m*3; i++){
    ...
}
```

- 가장 큰 항외에는 전부 무시한다.

```javascript
// O(n^2)
for(let i=0; i<n; i++){
    for(let j=0; j<n; j++){
        ...
    }
}
for(let i=0; i<n; i++){
    ...
}
```

<br/>

### 3. 성능 측정 방법

```javascript
const start = new Date().getTime();

/*
알고리즘 구현
*/

const end = new Date().getTime();

console.log(end - start); // ms
```

<br/>
