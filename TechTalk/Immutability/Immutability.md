# 불변성 (Immutability)

**JS에서 Memory Heap 과 Call Stack 이 어떻게 변하는지에 따라 알아보고자함.**

## 원시타입 vs 참조타입

![image](https://github.com/wltnthss/Skils/assets/60785586/92ca9347-ecc9-41f1-b8c5-ed7107b3c91e)

* 원시 타입은 불변하고 참조 타입 객체는 변한다고 말할 수 있음

> 이는 원시타입과 참조타입의 데이터 저장방식이 다르기 때문에 불변성이 생긴다고 볼 수 있음.

```javascript
let a = 10;
let b = [1,2,3]
let c = { name : "son", course: "FE"}
```

* a = 10 는 원시타입으로 Call Stack 값 10이 저장됨.
* b, c 는 참조타입으로 Memory Heap 영역에 실제 값이 담김.


**원시타입 변수 재할당**

```javascript
let a = 10;
let b = 20;

a = 20;
b = 30;
```

* a,b 의 메모리 힙 영역의 값은 변경되지 않음 == 불변함.

**참조타입 변수 재할당**

```javascript
const c = [1, 2, 3];
let d = [4, 5, 6];

c.push(100);
d.push(100);
```

* c, d 의 메모리 힙 영역의 값이 변경되었음. == 불변하지 않음.

**얕은 비교 vs 깊은 비교**

![image](https://github.com/wltnthss/Skils/assets/60785586/5b64a8cf-5cba-45da-9f19-a24636aeb661)

```javascript
const obj1 = { a: 1, b: 2 };
const obj2 = { a: 1, b: 2 };

console.log(obj1 === obj2);  // false
console.log(JSON.stringify(obj1) === JSON.stringify(obj2));  // true
```

* Call Stack 값을 비교하는 것을 얕은 비교, Memory Heap 영역에 값을 비교하는 것을 깊은 비교라고함.

**React 내에서 불변성을 지켜야하는 이유**

* React에서 setState 를 하는 경우 얕은 비교를 통해 계산리소스를 덜어줌.(CallStack 값만 비교함)
* CallStack 값이 다르다면 재렌더링을 통해 상태를 업데이트함.
* React에서 참조타입을 쓸 때는 콜스택의 값을 다르게 생성한 후에 넣어줘야함.

**React에서 참조타입을 쓸 때 불변성을 지키는 방법**

* ES5, ES6, ES2023 중 ES2023 을 사용하는 것이 불변성을 지키는데 용이함.
  
```javascript
const twoDepth = [
    [1, 1, 1],
    [2, 2, 2],
    [3, 3, 3],
]

const copiedArray = [...twoDepth];

console.log(twoDepth === copiedArray);              // false
console.log(twoDepth[0] === copiedArray[0]);        // true

const twoDepth2 = [
    [1, 1, 1],
    [2, 2, 2],
    [3, 3, 3],
]

const structedArray = structuredClone(twoDepth2);

console.log(twoDepth2 === structedArray);           // false
console.log(twoDepth2[0] === structedArray[0]);     // false
```

* 깊은 복사에 새로운 콜스택의 값이 할당되었으므로 false
* 즉, 리액트는 얕은 비교를 통해 생태를 업데이트 하는데 참조타입의 setState 시에는 새로운 배열이나 객체를 생성해서 set 해야함.
