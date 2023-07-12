# JavaScript Essentials
1. 프로젝트 생성
- npm init -y
- npm i parcel-bundler -D
- npm i parcel

2. 데이터 타입 확인
- main.js
```javascript
import getType from'./getType'

console.log(typeof 'Hello world!') //string
console.log(typeof 123) //number
console.log(typeof undefined) //boolean
console.log(typeof null) //undefined
console.log(typeof {}) //object
console.log(typeof []) //object

console.log(getType(123)) // Number
console.log(getType(false)) // Boolean
console.log(getType(null)) // Null
console.log(getType({})) // Object
console.log(getType([])) // Array
```
- getType.js
```javascript
export default function getType(data) {
    return Object.prototype.toString.call(data).slice(8,-1)
}
```

3. 비교연산자
```javascript
const a = 1
const b = 3
console.log(a === b) //3개 사용
console.log(a !== b) 
```

3. 삼항연산자
```javascript
console.log(a ? '참' : '거짓') 
```

4. 동등연산자
```javascript
const a = 1
const b = '1'
console.log(a==b) //true
```
5. 화살표 함수
```javascript
const double = function(x) {
    return x * 2
}
//화살표 함수
const doubleArrow = x => x * 2
```

6. 즉시 실행 함수
```javascript
//IIFE, Immediately-Invoked Function Expression
const a = 7
//일반 함수
function double() {
    console.log(a*2)
}
double();
//즉시 실행 함수
(function () {
    console.log(a * 2)
})();
```

7. 호이스팅(Hoisting)
- 함수 선언부가 유효범위 최상단으로 끌어올려지는 현상
```javascript
const a = 7
double() //아래쪽에 있는 함수를 호출 

function double() {
    console.log(a * 2)
}
```

8. 타이머 함수
- setTimeout(함수, 시간): 일정 시간 후 함수 실행
- setInterval(함수, 시간): 시간 간격마다 함수 실행
- clearTimeout(): 설정된 Timeout 함수를 종료
- clearInterval(): 설정된 Interval 함수를 종료 
```javascript
setTimeout(function() {
    console.log('Heropy!')
}, 3000)
```

```javascript
setTimeout(() => {
    console.log('Heropy!')
}, 3000)
```

```javascript
//3초 전 h1태그 안의 글자를 클릭하면 타이머가 종료되어 콘솔출력이 안됨
const timer = setTimeout(() => {
    console.log('Heropy')
}, 3000)
const h1El = document.querySelector('h1')
h1El.addEventListener('click', () => {
    clearTimeout(timer)
})
```

```javascript
//함수 반복 실행
const timer = setInterval(() => {
    console.log('Heropy')
}, 3000)
const h1El = document.querySelector('h1')
h1El.addEventListener('click', () => {
    clearTimeout(timer)
})
```
