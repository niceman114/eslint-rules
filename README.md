## 203가지 eslint rules 모음

[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fniceman114%2Feslint-rules&count_bg=%2379C83D&title_bg=%23555555&icon=awesomelists.svg&icon_color=%23EBFF00&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)

### 1. accessor-pairs

getter와 setter가 쌍으로 정의되어 있는지 검사합니다.
```js
/* 올바름 */
const obj = {
  get prop() { return 'value'; },
  set prop(value) { /* ... */ }
};

/* 오류 */
const obj = {
  get prop() { return 'value'; }
};
```

### 2. array-callback-return

`Array` 메서드의 콜백에서 값을 반환하도록 강제합니다.
```js
/* 올바름 */
const numbers = [1, 2, 3];
const doubled = numbers.map(number => number * 2);

/* 오류 */
const numbers = [1, 2, 3];
numbers.map(number => {
  number * 2;
});
```

### 3. arrow-body-style

화살표 함수의 본문을 일관되게 유지하도록 강제합니다.
```js
/* 올바름 */
const foo = () => 'bar';

/* 오류 */
const foo = () => { return 'bar'; };
```

### 4. block-scoped-var

변수 선언을 블록 범위 내에서만 유효하도록 합니다.
```js
/* 올바름 */
if (true) {
  let x = 1;
}

/* 오류 */
if (true) {
  var x = 1;
}
console.log(x); // x는 블록 밖에서도 접근 가능
```

### 5. camelcase

카멜 케이스로 변수명을 작성하도록 합니다.
```js
/* 올바름 */
const myVariable = 1;

/* 오류 */
const my_variable = 1;
```

### 6. capitalized-comments

주석의 첫 글자를 대문자로 작성하도록 합니다.
```js
/* 올바름 */
// This is a comment.

/* 오류 */
// this is a comment.
```

### 7. class-methods-use-this

클래스 메서드가 반드시 `this`를 사용하도록 강제합니다.
```js
/* 올바름 */
class MyClass {
  method() {
    console.log(this);
  }
}

/* 오류 */
class MyClass {
  method() {
    return 42;
  }
}
```

### 8. complexity

함수의 복잡도를 제한합니다.
```js
/* 올바름: 복잡도가 낮은 코드 */
function foo(x) {
    if (x > 2) {
        return x;
    }
}

/* 오류: 복잡도가 높은 코드 */
function foo(x) {
  if (x > 0) {
    if (x > 1) {
      if (x > 2) {
        return x;
      }
    }
  }
}
```

### 9. consistent-return

모든 함수가 일관되게 값을 반환하도록 합니다.
```js
/* 올바름 */
function foo() {
  if (true) {
    return 1;
  }
  return 2;
}

/* 오류 */
function foo() {
  if (true) {
    return 1;
  }
}
```

### 10. consistent-this

`this` 참조를 일관되게 사용할 수 있도록 강제합니다.
```js
/* 올바름 */
const self = this;

/* 오류 */
const that = this;
```

### 11. constructor-super

클래스 생성자 내에서 `super()`를 호출하도록 강제합니다.
```js
/* 올바름 */
class A extends B {
  constructor() {
    super();
  }
}

/* 오류 */
class A extends B {
  constructor() {
  }
}
```

### 12. curly

모든 제어문에 중괄호를 사용하도록 합니다.
```js
/* 올바름 */
if (foo) {
  bar();
}

/* 오류 */
if (foo) bar();
```

### 13. default-case

`switch`문에 `default` 케이스를 추가하도록 강제합니다.
```js
/* 올바름 */
switch (foo) {
    case 1:
        break;
    default:
        break;
}

/* 오류 */
switch (foo) {
    case 1:
        break;
}
```

### 14. default-case-last

`switch`문의 `default` 케이스를 마지막에 위치시키도록 강제합니다.
```js
/* 올바름 */
switch (foo) {
  case 1:
    break;
  case 2:
    break;
  default:
    break;
}

/* 오류 */
switch (foo) {
  default:
    break;
  case 1:
    break;
}
```

### 15. default-param-last

기본 매개변수를 함수 매개변수 목록의 마지막에 배치하도록 합니다.
```js
/* 올바름 */
function foo(a, b = 1) {
  // ...
}

/* 오류 */
function foo(a = 1, b) {
  // ...
}
```

### 16. dot-notation

가능한 경우 점 표기법을 사용하도록 합니다.
```js
/* 올바름 */
foo.bar = 1;

/* 오류 */
foo["bar"] = 1;
```

### 17. eqeqeq

일치 연산자(`===`, `!==`)를 사용하도록 강제합니다.
```js
/* 올바름 */
if (foo === 1) {
  // ...
}

/* 오류 */
if (foo == 1) {
  // ...
}
```

### 18. for-direction

`for` 반복문이 올바른 방향으로 진행되도록 강제합니다.
```js
/* 올바름 */
for (let i = 0; i < 10; i++) {
  // ...
}

/* 오류 */
for (let i = 10; i < 0; i++) {
  // ...
}
```

### 19. func-name-matching

함수명이 변수명과 일치하도록 강제합니다.
```js
/* 올바름 */
const foo = function foo() {
  // ...
};

/* 오류 */
const foo = function bar() {
  // ...
};
```

### 20. func-names

함수 표현식에 이름을 지정하도록 강제합니다.
```js
/* 올바름 */
const foo = function foo() {
  // ...
};

/* 오류 */
const foo = function() {
  // ...
};
```

### 21. func-style

함수 선언 스타일을 일관되게 유지하도록 강제합니다.
```js
/* 올바름 */
const foo = function() {
  // ...
};

/* 오류 */
function foo() {
  // ...
};
```

### 22. getter-return

getter 메서드가 값을 반환하도록 강제합니다.
```js
/* 올바름 */
const obj = {
  get prop() {
    return 'value';
  }
};

/* 오류 */
const obj = {
  get prop() {
    // 값 반환 없음
  }
};
```

### 23. grouped-accessor-pairs

getter와 setter를 그룹화하도록 강제합니다.
```js
/* 올바름 */
const obj = {
  get prop() {
    return 'value';
  },
  set prop(value) {
    // ...
  }
};

/* 오류 */
const obj = {
  get prop() {
    return 'value';
  },
  otherMethod() {
    // ...
  },
  set prop(value) {
    // ...
  }
};
```

### 24. guard-for-in

`for-in` 루프에서 `hasOwnProperty` 검사를 사용하도록 강제합니다.
```js
/* 올바름 */
for (const key in obj) {
  if (obj.hasOwnProperty(key)) {
    // ...
  }
}

/* 오류 */
for (const key in obj) {
  // ...
}
```

### 25. id-denylist

금지된 식별자를 사용하지 않도록 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "id-denylist": ["data", "item"]
}

/* 오류 */
const data = {};
const item = {};
```

### 26. id-length

식별자의 길이를 제한합니다.
```js
/* 설정 예시 */
"rules": {
  "id-length": ["error", { "min": 2, "max": 20 }]
}

/* 오류 */
const x = 1;  // 너무 짧음
const thisIsAVeryLongIdentifier = 1;  // 너무 김
```

### 27. id-match

식별자가 특정 패턴과 일치하도록 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "id-match": ["error", "^_[a-z]+([A-Z][a-z]+)*$"]
}

/* 올바름 */
const _myVariable = 1;

/* 오류 */
const myVariable = 1;
```

### 28. init-declarations

변수 선언시 반드시 값을 초기화하도록 강제합니다.
```js
/* 올바름 */
let foo = 1;

/* 오류 */
let foo;
```

### 29. logical-assignment-operators

논리 할당 연산자를 사용하도록 강제합니다.
```js
/* 올바름 */
a ||= b;
a &&= b;
a ??= b;

/* 오류 */
a = a || b;
a = a && b;
a = a ?? b;
```

### 30. max-classes-per-file

파일당 클래스 수를 제한합니다.
```js
/* 설정 예시 */
"rules": {
  "max-classes-per-file": ["error", 1]
}

/* 올바름 */
class MyClass {
  // ...
}

/* 오류 */
class MyClass {
  // ...
}
class AnotherClass {
  // ...
}
```

### 31. max-depth

코드의 중첩 깊이를 제한합니다.
```js
/* 설정 예시 */
"rules": {
  "max-depth": ["error", 4]
}

/* 올바름 */
if (foo) {
  if (bar) {
    if (baz) {
      if (qux) {
        // ...
      }
    }
  }
}

/* 오류 */
if (foo) {
  if (bar) {
    if (baz) {
      if (qux) {
        if (quux) {
          // ...
        }
      }
    }
  }
}
```

### 32. max-lines

파일당 최대 코드 라인 수를 제한합니다.
```js
/* 설정 예시 */
"rules": {
  "max-lines": ["error", { "max": 300 }]
}

/* 올바름 */
// 300줄 이하의 코드

/* 오류 */
// 300줄 이상의 코드
```

### 33. max-lines-per-function

함수당 최대 코드 라인 수를 제한합니다.
```js
/* 설정 예시 */
"rules": {
  "max-lines-per-function": ["error", { "max": 50 }]
}

/* 올바름 */
function foo() {
  // 50줄 이하의 코드
}

/* 오류 */
function foo() {
  // 50줄 이상의 코드
}
```

### 34. max-nested-callbacks

중첩된 콜백 함수의 최대 깊이를 제한합니다.
```js
/* 설정 예시 */
"rules": {
  "max-nested-callbacks": ["error", 3]
}

/* 올바름 */
asyncFunction1(() => {
  asyncFunction2(() => {
    asyncFunction3(() => {
      // ...
    });
  });
});

/* 오류 */
asyncFunction1(() => {
  asyncFunction2(() => {
    asyncFunction3(() => {
      asyncFunction4(() => {
        // ...
      });
    });
  });
});
```

### 35. max-params

함수 매개변수의 최대 개수를 제한합니다.
```js
/* 설정 예시 */
"rules": {
  "max-params": ["error", 3]
}

/* 올바름 */
function foo(a, b, c) {
  // ...
}

/* 오류 */
function foo(a, b, c, d) {
  // ...
}
```

### 36. max-statements

함수 내의 최대 명령문 수를 제한합니다.
```js
/* 설정 예시 */
"rules": {
  "max-statements": ["error", 5]
}

/* 올바름 */
function foo() {
  let a = 1;
  let b = 2;
  let c = 3;
  let d = 4;
  let e = 5;
}

/* 오류 */
function foo() {
  let a = 1;
  let b = 2;
  let c = 3;
  let d = 4;
  let e = 5;
  let f = 6;
}
```

### 37. new-cap

생성자 함수 이름을 대문자로 시작하도록 강제합니다.
```js
/* 올바름 */
function MyConstructor() {
  // ...
}
const instance = new MyConstructor();

/* 오류 */
function myConstructor() {
  // ...
}
const instance = new myConstructor();
```

### 38. no-alert

`alert`, `confirm`, `prompt` 사용을 금지합니다.
```js
/* 올바름 */
// alert 사용 없음

/* 오류 */
alert('This is an alert');
```

### 39. no-array-constructor

`Array` 생성자의 사용을 금지합니다.
```js
/* 올바름 */
const arr = [];

/* 오류 */
const arr = new Array();
```

### 40. no-async-promise-executor

`Promise` 생성자 함수에서 `async` 함수를 사용하지 않도록 강제합니다.
```js
/* 올바름 */
new Promise((resolve, reject) => {
  // ...
});

/* 오류 */
new Promise(async (resolve, reject) => {
  // ...
});
```

### 41. no-await-in-loop

루프 내에서 `await` 사용을 금지합니다.
```js
/* 올바름 */
async function processItems(items) {
  for (const item of items) {
    await processItem(item);
  }
}

/* 오류 */
async function processItems(items) {
  for (const item of items) {
    await processItem(item);
  }
}
```

### 42. no-bitwise

비트 연산자의 사용을 금지합니다.
```js
/* 올바름 */
let x = 2 * 2;

/* 오류 */
let x = 2 << 1;
```

### 43. no-caller

`arguments.caller`와 `arguments.callee` 사용을 금지합니다.
```js
/* 올바름 */
function foo() {
  // ...
}

/* 오류 */
function foo(n) {
  if (n <= 0) {
    return;
  }
  arguments.callee(n - 1);
}
```

### 44. no-case-declarations

`case/default` 절에서 블록없는 변수 선언을 금지합니다.
```js
/* 올바름 */
switch (foo) {
  case 1: {
    let x = 1;
    break;
  }
  case 2: {
    const y = 2;
    break;
  }
}

/* 오류 */
switch (foo) {
  case 1:
    let x = 1;
    break;
  case 2:
    const y = 2;
    break;
}
```

### 45. no-class-assign

클래스에 대한 할당을 금지합니다.
```js
/* 올바름 */
class Foo {
  // ...
}

/* 오류 */
Foo = 'bar';
```

### 46. no-compare-neg-zero

`-0`과의 비교를 금지합니다.
```js
/* 올바름 */
if (x === 0) {
  // ...
}

/* 오류 */
if (x === -0) {
  // ...
}
```

### 47. no-cond-assign

조건문에서 할당 연산자를 사용하지 않도록 강제합니다.
```js
/* 올바름 */
if (x === 0) {
  // ...
}

/* 오류 */
if (x = 0) {
  // ...
}
```

### 48. no-console

콘솔 사용을 금지합니다.
```js
/* 올바름 */
// console.log 사용 없음

/* 오류 */
console.log('This is a log');
```

### 49. no-const-assign

`const`로 선언된 변수에 값을 재할당하지 않도록 강제합니다.
```js
/* 올바름 */
const x = 1;

/* 오류 */
const x = 1;
x = 2;
```

### 50. no-constant-binary-expression

상수식의 이항 표현식을 금지합니다.
```js
/* 올바름 */
if (x > 0) {
  // ...
}

/* 오류 */
if (true === true) {
  // ...
}
```

### 51. no-constant-condition

조건문에서 상수 조건을 사용하지 않도록 강제합니다.
```js
/* 올바름 */
if (x > 0) {
  // ...
}

/* 오류 */
if (true) {
  // ...
}
```

### 52. no-constructor-return

생성자 함수에서 값을 반환하지 않도록 강제합니다.
```js
/* 올바름 */
class Foo {
  constructor() {
    // ...
  }
}

/* 오류 */
class Foo {
  constructor() {
    return {};
  }
}
```

### 53. no-continue

`continue`문 사용을 금지합니다.
```js
/* 올바름 */
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) {
    // ...
  }
}

/* 오류 */
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) continue;
}
```

### 54. no-control-regex

정규 표현식에서 제어 문자 사용을 금지합니다.
```js
/* 올바름 */
const regex = /foo/;

/* 오류 */
const regex = /\x1f/;
```

### 55. no-debugger

디버거 사용을 금지합니다.
```js
/* 올바름 */
// 디버거 없음

/* 오류 */
debugger;
```

### 56. no-delete-var

변수 삭제를 금지합니다.
```js
/* 올바름 */
let foo;
foo = null;

/* 오류 */
let foo;
delete foo;
```

### 57. no-div-regex

정규 표현식에서 나눗셈 연산자를 사용하는 것을 금지합니다.
```js
/* 올바름 */
const regex = /foo/;

/* 오류 */
const regex = /=/foo/;
```

### 58. no-dupe-args

함수 정의시 중복된 매개변수 이름을 사용하지 않도록 강제합니다.
```js
/* 올바름 */
function foo(a, b, c) {
  // ...
}

/* 오류 */
function foo(a, a, b) {
  // ...
}
```

### 59. no-dupe-class-members

클래스 멤버의 중복 선언을 금지합니다.
```js
/* 올바름 */
class Foo {
  bar() {
    // ...
  }
  baz() {
    // ...
  }
}

/* 오류 */
class Foo {
  bar() {
    // ...
  }
  bar() {
    // ...
  }
}
```

### 60. no-dupe-else-if

`else-if` 절에서 중복된 조건을 금지합니다.
```js
/* 올바름 */
if (x === 1) {
  // ...
} else if (x === 2) {
  // ...
} else if (x === 3) {
  // ...
}

/* 오류 */
if (x === 1) {
  // ...
} else if (x === 1) {
  // ...
}
```

### 61. no-dupe-keys

객체 리터럴에서 중복된 키를 금지합니다.
```js
/* 올바름 */
const obj = {
  a: 1,
  b: 2
};

/* 오류 */
const obj = {
  a: 1,
  a: 2
};
```

### 62. no-duplicate-case

`switch` 문에서 중복된 `case` 절을 금지합니다.
```js
/* 올바름 */
switch (foo) {
  case 1:
    // ...
    break;
  case 2:
    // ...
    break;
}

/* 오류 */
switch (foo) {
  case 1:
    // ...
    break;
  case 1:
    // ...
    break;
}
```

### 63. no-duplicate-imports

동일한 모듈로부터 여러번의 `import`를 금지합니다.
```js
/* 올바름 */
import { foo, bar } from 'module';

/* 오류 */
import { foo } from 'module';
import { bar } from 'module';
```

### 64. no-else-return

`if`문에 `return`이 있을 경우, `else` 블록을 금지합니다.
```js
/* 올바름 */
function foo() {
  if (x) {
    return y;
  }
  return z;
}

/* 오류 */
function foo() {
  if (x) {
    return y;
  } else {
    return z;
  }
}
```

### 65. no-empty

빈 블록을 금지합니다.
```js
/* 올바름 */
if (foo) {
  // 코드 작성
}

/* 오류 */
if (foo) {
  // 빈 블록
}
```

### 66. no-empty-character-class

정규 표현식에서 빈 문자 클래스를 금지합니다.
```js
/* 올바름 */
const regex = /[a-z]/;

/* 오류 */
const regex = /[]/;
```

### 67. no-empty-function

빈 함수를 금지합니다.
```js
/* 올바름 */
function foo() {
  // 코드 작성
}

/* 오류 */
function foo() {}
```

### 68. no-empty-pattern

빈 패턴을 금지합니다.
```js
/* 올바름 */
const {bar} = foo();

/* 오류 */
const {} = foo();
```

### 69. no-empty-static-block

빈 `static` 블록을 금지합니다.
```js
/* 올바름 */
class Foo {
  static {
    // 코드 작성
  }
}

/* 오류 */
class Foo {
  static {}
}
```

### 70. no-eq-null

`null`과의 비교에서 `==`와 `!=` 대신 `===`와 `!==`를 사용하도록 강제합니다.
```js
/* 올바름 */
if (foo === null) {
  // ...
}

/* 오류 */
if (foo == null) {
  // ...
}
```

### 71. no-eval

`eval` 함수 사용을 금지합니다.
```js
/* 올바름 */
// eval 사용 없음

/* 오류 */
eval("console.log('This is an eval')");
```

### 72. no-ex-assign

`catch` 절에서 예외 변수에 값을 할당하는 것을 금지합니다.
```js
/* 올바름 */
try {
  // ...
} catch (e) {
  console.error(e);
}

/* 오류 */
try {
  // ...
} catch (e) {
  e = 'new value';
}
```

### 73. no-extend-native

원시 객체의 프로토타입을 확장하는 것을 금지합니다.
```js
/* 올바름 */
// 원시 객체 프로토타입 확장 없음

/* 오류 */
Object.prototype.extra = function() {};
```

### 74. no-extra-bind

불필요한 함수 바인딩을 금지합니다.
```js
/* 올바름 */
const foo = function() {
  // ...
};

/* 오류 */
const foo = function() {
  // ...
}.bind(this);
```

### 75. no-extra-boolean-cast

불필요한 `Boolean` 형변환을 금지합니다.
```js
/* 올바름 */
const isValid = Boolean(value);

/* 오류 */
const isValid = !!value;
```

### 76. no-extra-label

불필요한 레이블 사용을 금지합니다.
```js
/* 올바름 */
outerLoop: for (let i = 0; i < 10; i++) {
  for (let j = 0; j < 10; j++) {
    if (i === j) {
      break outerLoop;
    }
  }
}

/* 오류 */
outerLoop: for (let i = 0; i < 10; i++) {
  innerLoop: for (let j = 0; j < 10; j++) {
    if (i === j) {
      break innerLoop;
    }
  }
}
```

### 77. no-fallthrough

`switch`문에서 `fall through`를 금지합니다.
```js
/* 올바름 */
switch (foo) {
  case 1:
    // ...
    // fall through
  case 2:
    // ...
    break;
}

/* 오류 */
switch (foo) {
  case 1:
    // ...
  case 2:
    // ...
    break;
}
```

### 78. no-func-assign

함수 선언에 값을 할당하는 것을 금지합니다.
```js
/* 올바름 */
function foo() {
  // ...
}

/* 오류 */
function foo() {
  // ...
}
foo = bar;
```

### 79. no-global-assign

읽기 전용 전역 변수에 값을 할당하는 것을 금지합니다.
```js
/* 올바름 */
// 전역 변수 재할당 없음

/* 오류 */
window = {};
```

### 80. no-implicit-coercion

짧은 형변환을 금지합니다.
```js
/* 올바름 */
const num = Number(value);
const str = String(value);
const bool = Boolean(value);

/* 오류 */
const num = +value;
const str = '' + value;
const bool = !!value;
```

### 81. no-implicit-globals

전역 범위에서 변수 및 함수 선언을 금지합니다.
```js
/* 올바름 */
(function() {
  var foo = 1;
})();

/* 오류 */
var foo = 1;
```

### 82. no-implied-eval

암묵적 `eval` 사용을 금지합니다.
```js
/* 올바름 */
setTimeout(function() {
  doSomething();
}, 100);

/* 오류 */
setTimeout("doSomething()", 100);
```

### 83. no-import-assign

`import`된 변수에 값을 할당하지 않도록 강제합니다.
```js
/* 올바름 */
import {myVar} from 'module';

/* 오류 */
import {myVar} from 'module';
myVar = 'newValue';
```

### 84. no-inline-comments

코드 줄 중간에 주석을 사용하지 않도록 강제합니다.
```js
/* 올바름 */
// 이것은 주석입니다.
var foo = 1;

/* 오류 */
var foo = 1; // 이것은 주석입니다.
```

### 85. no-inner-declarations

블록 내에서 함수나 변수 선언을 금지합니다.
```js
/* 올바름 */
function foo() {
  bar();
}

var bar = function() {};

/* 오류 */
if (foo) {
  function bar() {}
}
```

### 86. no-invalid-regexp

정규 표현식 생성자에 잘못된 정규 표현식을 사용하지 않도록 강제합니다.
```js
/* 올바름 */
const regex = new RegExp('foo');

/* 오류 */
const regex = new RegExp('[');
```

### 87. no-invalid-this

유효하지 않은 `this` 사용을 금지합니다.
```js
/* 올바름 */
class Foo {
  constructor() {
    this.bar = 1;
  }
}

/* 오류 */
function foo() {
  this.bar = 1;
}
```

### 88. no-irregular-whitespace

불규칙한 공백 문자를 금지합니다.
```js
/* 올바름 */
let foo = "bar baz";

/* 오류 */
let foo = "bar\u00a0baz";
```

### 89. no-iterator

`__iterator__` 속성 사용을 금지합니다.
```js
/* 올바름 */
let arr = [1, 2, 3];
for (let value of arr) {
  console.log(value);
}

/* 오류 */
let arr = [1, 2, 3];
let iterator = arr.__iterator__();
```

### 90. no-label-var

변수와 동일한 이름의 레이블을 금지합니다.
```js
/* 올바름 */
let foo = 1;
outer: for (let i = 0; i < 10; i++) {
  for (let j = 0; j < 10; j++) {
    if (i === j) {
      break outer;
    }
  }
}

/* 오류 */
let foo = 1;
foo: for (let i = 0; i < 10; i++) {
  for (let j = 0; j < 10; j++) {
    if (i === j) {
      break foo;
    }
  }
}
```

### 91. no-labels

레이블문 사용을 금지합니다.
```js
/* 올바름 */
// 레이블문 없음

/* 오류 */
label:
while (foo) {
  // ...
}
```

### 92. no-lone-blocks

불필요한 블록을 금지합니다.
```js
/* 올바름 */
// 블록없음

/* 오류 */
{
  // 불필요한 블록
}
```

### 93. no-lonely-if

`else` 블록이 없는 `if`문을 금지합니다.
```js
/* 올바름 */
if (foo) {
  // ...
} else if (bar) {
  // ...
}

/* 오류 */
if (foo) {
  // ...
} else {
  if (bar) {
    // ...
  }
}
```

### 94. no-loop-func

반복문 내에서 함수 선언을 금지합니다.
```js
/* 올바름 */
for (let i = 0; i < 10; i++) {
  process(i);
}

/* 오류 */
for (let i = 0; i < 10; i++) {
  function process() {
    // ...
  }
}
```

### 95. no-loss-of-precision

숫자의 정밀도 손실을 방지합니다.
```js
/* 올바름 */
let num = 1234567890123456;

/* 오류 */
let num = 12345678901234567;
```

### 96. no-magic-numbers

매직 넘버 사용을 금지합니다.
```js
/* 설정 예시 */
"rules": {
  "no-magic-numbers": ["error", { "ignore": [0, 1] }]
}

/* 올바름 */
const secondsInMinute = 60;

/* 오류 */
const foo = 42;
```

### 97. no-misleading-character-class

오해의 소지가 있는 문자 클래스를 금지합니다.
```js
/* 올바름 */
const regex = /^[\u{61}-\u{7A}]+$/u;

/* 오류 */
const regex = /^[a-zA-Z]+$/;
```

### 98. no-mixed-operators

다른 연산자와의 혼합 사용을 금지합니다.
```js
/* 설정 예시 */
"rules": {
  "no-mixed-operators": ["error", { "groups": [["+", "-", "*", "/", "%", "**"]] }]
}

/* 올바름 */
const foo = a + b - c;

/* 오류 */
const foo = (a + b) * c;
```

### 99. no-mixed-requires

`require`문을 여러 유형으로 혼합 사용하지 않도록 강제합니다.
```js
/* 올바름 */
const fs = require('fs');
const path = require('path');

/* 오류 */
const fs = require('fs'),
      _ = require('lodash');
```

### 100. no-multi-assign

변수에 여러번 할당을 금지합니다.
```js
/* 올바름 */
let a = 1;
let b = 2;
let c = 3;
/* 오류 */
let a = b = c = 1;
```

### 101. no-multi-str

멀티 라인 문자열을 금지합니다.
```js
/* 올바름 */
const str = "This is a \n multiline string.";

/* 오류 */
const str = "This is a \
multiline string.";
```

### 102. no-negated-condition

부정 조건을 금지합니다.
```js
/* 올바름 */
if (isReady) {
  // ...
} else {
  // ...
}

/* 오류 */
if (!isReady) {
  // ...
} else {
  // ...
}
```

### 103. no-nested-ternary

중첩 삼항 연산자를 금지합니다.
```js
/* 올바름 */
const result = condition1 ? value1 : value2;

/* 오류 */
const result = condition1 ? (condition2 ? value1 : value2) : value3;
```

### 104. no-new

생성자 호출이 아닌 `new` 연산자를 금지합니다.
```js
/* 올바름 */
const myObject = new MyObject();

/* 오류 */
new MyObject();
```

### 105. no-new-func

`Function` 생성자 사용을 금지합니다.
```js
/* 올바름 */
function sum(a, b) {
  return a + b;
}

/* 오류 */
const sum = new Function('a', 'b', 'return a + b');
```

### 106. no-new-native-nonconstructor

네이티브 전역함수를 `new`와 함께 사용하는 것을 금지합니다.
```js
/* 올바름 */
const foo = Symbol('foo');

/* 오류 */
const foo = new Symbol('foo');
```

### 107. no-new-wrappers

기본형 래퍼 타입을 `new`와 함께 사용하는 것을 금지합니다.
```js
/* 올바름 */
const str = String(123);

/* 오류 */
const str = new String(123);
```

### 108. no-nonoctal-decimal-escape

비 8진수 이스케이프 시퀀스를 금지합니다.
```js
/* 올바름 */
const str = "\u{1F4A9}";

/* 오류 */
const str = "\089";
```

### 109. no-obj-calls

`Math`, `JSON`, `Reflect` 등 객체를 함수로 호출하는 것을 금지합니다.
```js
/* 올바름 */
const mathResult = Math.max(1, 2);

/* 오류 */
const mathResult = Math(1, 2);
```

### 110. no-object-constructor

`Object` 생성자 사용을 금지합니다.
```js
/* 올바름 */
const obj = {};

/* 오류 */
const obj = new Object();
```

### 111. no-octal

8진수 리터럴을 금지합니다.
```js
/* 올바름 */
const num = 10;

/* 오류 */
const num = 012;
```

### 112. no-octal-escape

8진수 이스케이프 문자를 금지합니다.
```js
/* 올바름 */
const str = "\u0030";

/* 오류 */
const str = "\043";
```

### 113. no-param-reassign

함수 매개변수에 값을 재할당하는 것을 금지합니다.
```js
/* 올바름 */
function foo(bar) {
  let baz = bar;
  baz = 'new value';
}

/* 오류 */
function foo(bar) {
  bar = 'new value';
}
```

### 114. no-plusplus

증감 연산자(`++`, `--`) 사용을 금지합니다.
```js
/* 올바름 */
let i = 0;
i += 1;

/* 오류 */
let i = 0;
i++;
```

### 115. no-promise-executor-return

`Promise` 생성자 함수에서 값을 반환하는 것을 금지합니다.
```js
/* 올바름 */
new Promise((resolve, reject) => {
  resolve('done');
});

/* 오류 */
new Promise((resolve, reject) => {
  return 'done';
});
```

### 116. no-proto

`__proto__` 속성 사용을 금지합니다.
```js
/* 올바름 */
Object.getPrototypeOf(obj);

/* 오류 */
obj.__proto__;
```

### 117. no-prototype-builtins

객체의 `prototype` 속성에 직접 접근하는 것을 금지합니다.
```js
/* 올바름 */
Object.prototype.hasOwnProperty.call(obj, 'prop');

/* 오류 */
obj.hasOwnProperty('prop');
```

### 118. no-redeclare

변수의 재선언을 금지합니다.
```js
/* 올바름 */
let foo = 1;
foo = 2;

/* 오류 */
let foo = 1;
let foo = 2;
```

### 119. no-regex-spaces

정규 표현식 리터럴에서 여러 개의 공백을 사용하지 않도록 금지합니다.
```js
/* 올바름 */
const regex = /foo {3}bar/;

/* 오류 */
const regex = /foo   bar/;
```

### 120. no-restricted-exports

특정 이름으로의 모듈 내보내기를 금지합니다.
```js
/* 설정 예시 */
"rules": {
  "no-restricted-exports": ["error", { "restrictedNamedExports": ["default", "then"] }]
}

/* 올바름 */
export const foo = 1;

/* 오류 */
export default foo;
```

### 121. no-restricted-globals

사용을 제한할 전역 변수들을 정의합니다.
```js
/* 설정 예시 */
"rules": {
  "no-restricted-globals": ["event"]
}

/* 올바름 */
const customEvent = new CustomEvent('build');

/* 오류 */
const event = new Event('build');
```

### 122. no-restricted-imports

사용을 제한할 `import` 모듈을 정의합니다.
```js
/* 설정 예시 */
"rules": {
  "no-restricted-imports": ["fs"]
}

/* 올바름 */
import path from 'path';

/* 오류 */
import fs from 'fs';
```

### 123. no-restricted-modules

사용을 제한할 `require` 모듈을 정의합니다.
```js
/* 설정 예시 */
"rules": {
  "no-restricted-modules": ["fs"]
}

/* 올바름 */
const path = require('path');

/* 오류 */
const fs = require('fs');
```

### 124. no-restricted-properties

사용을 제한할 속성을 정의합니다.
```js
/* 설정 예시 */
"rules": {
  "no-restricted-properties": [
    {
      "object": "disallowedObject",
      "property": "disallowedProperty"
    }
  ]
}

/* 올바름 */
allowedObject.allowedProperty();

/* 오류 */
disallowedObject.disallowedProperty();
```

### 125. no-restricted-syntax

사용을 제한할 특정 구문을 정의합니다.
```js
/* 설정 예시 */
"rules": {
  "no-restricted-syntax": ["ForInStatement"]
}

/* 올바름 */
for (let i = 0; i < array.length; i++) {
  // ...
}

/* 오류 */
for (const key in object) {
  // ...
}
```

### 126. no-return-assign

`return`문에서 할당 연산자를 사용하지 않도록 강제합니다.
```js
/* 올바름 */
function foo() {
  let x = 1;
  return x;
}

/* 오류 */
function foo() {
  return x = 1;
}
```

### 127. no-script-url

JavaScript URL 사용을 금지합니다.
```js
/* 올바름 */
<a href="https://example.com">Click here</a>;

/* 오류 */
<a href="javascript:void(0)">Click here</a>;
```

### 128. no-self-assign

자기 할당을 금지합니다.
```js
/* 올바름 */
foo = bar;

/* 오류 */
foo = foo;
```

### 129. no-self-compare

자기 비교를 금지합니다.
```js
/* 올바름 */
if (foo === bar) {
  // ...
}

/* 오류 */
if (foo === foo) {
  // ...
}
```

### 130. no-sequences

쉼표 연산자의 사용을 금지합니다.
```js
/* 올바름 */
foo();
bar();

/* 오류 */
(foo(), bar());
```

### 131. no-setter-return

setter 메서드가 값을 반환하지 않도록 강제합니다.
```js
/* 올바름 */
const obj = {
  set prop(value) {
    this._prop = value;
  }
};

/* 오류 */
const obj = {
  set prop(value) {
    this._prop = value;
    return value;
  }
};
```

### 132. no-shadow

상위 범위 변수의 이름을 재사용하지 않도록 강제합니다.
```js
/* 올바름 */
let foo = 1;
function bar() {
  let baz = 2;
}

/* 오류 */
let foo = 1;
function bar() {
  let foo = 2;
}
```

### 133. no-shadow-restricted-names

제한된 이름을 변수로 사용하는 것을 금지합니다.
```js
/* 올바름 */
let myVariable = 1;

/* 오류 */
let undefined = 1;
```

### 134. no-sparse-arrays

드문 배열의 사용을 금지합니다.
```js
/* 올바름 */
let arr = [1, 2, 3];

/* 오류 */
let arr = [1, , 3];
```

### 135. no-tabs

탭 문자의 사용을 금지합니다.
```js
/* 올바름 */
let myVar = 1; // 공백 사용
let yourVar = 2; // 공백 사용

/* 오류 */
let myVar   = 12345; // 탭 사용
let yourVar = 2;     // 탭 사용
```

### 136. no-template-curly-in-string

템플릿 리터럴의 중괄호를 문자열에서 사용하지 않도록 강제합니다.
```js
/* 올바름 */
let str = `Hello, ${name}`;

/* 오류 */
let str = "Hello, ${name}";
```

### 137. no-ternary

삼항 연산자의 사용을 금지합니다.
```js
/* 올바름 */
if (condition) {
  value = trueValue;
} else {
  value = falseValue;
}

/* 오류 */
value = condition ? trueValue : falseValue;
```

### 138. no-this-before-super

`super()` 호출 전에 `this`를 사용하지 않도록 강제합니다.
```js
/* 올바름 */
class Child extends Parent {
  constructor() {
    super();
    this.foo = 1;
  }
}

/* 오류 */
class Child extends Parent {
  constructor() {
    this.foo = 1;
    super();
  }
}
```

### 139. no-throw-literal

오브젝트가 아닌 리터럴을 `throw` 하지 않도록 강제합니다.
```js
/* 올바름 */
throw new Error('Error message');

/* 오류 */
throw 'Error message';
```

### 140. no-undef

정의되지 않은 변수를 사용하지 않도록 강제합니다.
```js
/* 올바름 */
let foo = 1;
console.log(foo);

/* 오류 */
console.log(foo);
```

### 141. no-undef-init

변수를 `undefined`로 초기화하는 것을 금지합니다.
```js
/* 올바름 */
let foo;

/* 오류 */
let foo = undefined;
```

### 142. no-undefined

`undefined` 변수 사용을 금지합니다.
```js
/* 올바름 */
let foo = void 0;
if (typeof foo === 'undefined') {
  // ...
}

/* 오류 */
let foo = undefined;
if (foo === undefined) {
  // ...
}
```

### 143. no-underscore-dangle

식별자의 시작이나 끝에 밑줄(`_`) 사용을 금지합니다.
```js
/* 올바름 */
let foo;

/* 오류 */
let _foo;
```

### 144. no-unexpected-multiline

예상치 못한 여러 줄 표현을 금지합니다.
```js
/* 올바름 */
let foo = bar + (baz * qux);

/* 오류 */
let foo = bar
+ (baz * qux);
```

### 145. no-unmodified-loop-condition

루프 조건을 수정하지 않는 것을 금지합니다.
```js
/* 올바름 */
let i = 0;
while (i < 10) {
  i++;
}

/* 오류 */
let i = 0;
while (i < 10) {
  // ...
}
```

### 146. no-unneeded-ternary

불필요한 삼항 연산자를 금지합니다.
```js
/* 올바름 */
let foo = bar ? bar : baz;

/* 오류 */
let foo = bar ? true : false;
```

### 147. no-unreachable

도달할 수 없는 코드를 금지합니다.
```js
/* 올바름 */
function foo() {
  return bar;
}

/* 오류 */
function foo() {
  return bar;
  baz();
}
```

### 148. no-unreachable-loop

도달할 수 없는 반복문을 금지합니다.
```js
/* 올바름 */
for (let i = 0; i < 10; i++) {
  console.log(i);
}

/* 오류 */
return;
for (let i = 0; i < 10; i++) {
  console.log(i);
}
```

### 149. no-unsafe-finally

`finally` 블록에서 제어문을 사용하는 것을 금지합니다.
```js
/* 올바름 */
try {
  // ...
} catch (e) {
  // ...
} finally {
  // ...
}

/* 오류 */
try {
  // ...
} catch (e) {
  // ...
} finally {
  return;
}
```

### 150. no-unsafe-negation

관계 연산자의 왼쪽에 부정연산자 사용을 금지합니다.
```js
/* 올바름 */
if (foo !== bar) {
  // ...
}

/* 오류 */
if (!foo === bar) {
  // ...
}
```

### 151. no-unsafe-optional-chaining

안전하지 않은 선택적 체이닝을 금지합니다.
```js
/* 올바름 */
foo?.bar?.();

/* 오류 */
(foo?.bar)();
```

### 152. no-unused-expressions

사용되지 않는 표현식을 금지합니다.
```js
/* 올바름 */
if (foo) {
  bar();
}

/* 오류 */
foo && bar();
```

### 153. no-unused-labels

사용되지 않는 레이블을 금지합니다.
```js
/* 올바름 */
outer: while (foo) {
  break outer;
}

/* 오류 */
outer: while (foo) {
  bar();
}
```

### 154. no-unused-private-class-members

사용되지 않는 비공개 클래스 멤버를 금지합니다.
```js
/* 올바름 */
class MyClass {
  #privateField;
  method() {
    this.#privateField = 1;
  }
}

/* 오류 */
class MyClass {
  #privateField;
}
```

### 155. no-unused-vars

사용되지 않는 변수를 금지합니다.
```js
/* 올바름 */
let foo = 1;
console.log(foo);

/* 오류 */
let foo = 1;
```

### 156. no-use-before-define

정의되기 전에 변수를 사용하는 것을 금지합니다.
```js
/* 올바름 */
let foo = 1;
console.log(foo);

/* 오류 */
console.log(foo);
let foo = 1;
```

### 157. no-useless-assignment

불필요한 할당을 금지합니다.
```js
/* 올바름 */
let foo = 1;
foo += 1;

/* 오류 */
let foo = 1;
foo = 1;
```

### 158. no-useless-backreference

정규 표현식에서 불필요한 역참조를 금지합니다.
```js
/* 올바름 */
const regex = /(a)\1/;

/* 오류 */
const regex = /a\1/;
```

### 159. no-useless-call

불필요한 함수 호출을 금지합니다.
```js
/* 올바름 */
foo.call(bar);

/* 오류 */
foo.call(foo);
```

### 160. no-useless-catch

불필요한 `catch`문을 금지합니다.
```js
/* 올바름 */
try {
  doSomething();
} catch (error) {
  handleError(error);
}

/* 오류 */
try {
  doSomething();
} catch (error) {
  throw error;
}
```

### 161. no-useless-computed-key

불필요한 계산된 속성 이름을 금지합니다.
```js
/* 올바름 */
const obj = { foo: 'bar' };

/* 오류 */
const obj = { ['foo']: 'bar' };
```

### 162. no-useless-concat

불필요한 문자열 연결을 금지합니다.
```js
/* 올바름 */
const str = 'Hello, ' + 'world!';

/* 오류 */
const str = 'Hello, '.concat('world!');
```

### 163. no-useless-constructor

불필요한 생성자를 금지합니다.
```js
/* 올바름 */
class MyClass {
  constructor() {}
}

/* 오류 */
class MyClass {}
```

### 164. no-useless-escape

불필요한 이스케이프 문자를 금지합니다.
```js
/* 올바름 */
const str = "Hello, world!";

/* 오류 */
const str = "Hello, world\!";
```

### 165. no-useless-rename

불필요한 식별자 이름 바꾸기를 금지합니다.
```js
/* 올바름 */
const { foo: foo } = obj;

/* 오류 */
const { foo: bar } = obj;
```

### 166. no-useless-return

불필요한 `return`문을 금지합니다.
```js
/* 올바름 */
function foo() {
  return bar();
}

/* 오류 */
function foo() {
  return bar();
  return;
}
```

### 167. no-var

`var` 선언을 금지하고 `let` 또는 `const`를 사용합니다.
```js
/* 올바름 */
let foo = 1;
const bar = 2;

/* 오류 */
var foo = 1;
```

### 168. no-void

`void` 연산자의 사용을 금지합니다.
```js
/* 올바름 */
if (foo !== undefined) {
  // ...
}

/* 오류 */
void foo;
```

### 169. no-warning-comments

경고 주석을 사용하지 않도록 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "no-warning-comments": ["error", { "terms": ["todo", "fixme"], "location": "start" }]
}

/* 올바름 */
// 참고: 이 부분을 수정해야 합니다.

/* 오류 */
// TODO: 이 부분을 수정해야 합니다.
```

### 170. no-with

`with`문 사용을 금지합니다.
```js
/* 올바름 */
let foo = { bar: 'baz' };
console.log(foo.bar);

/* 오류 */
with (foo) {
  console.log(bar);
}
```

### 171. object-shorthand

객체 리터럴에서 축약 표현을 사용하도록 강제합니다.
```js
/* 올바름 */
const obj = { foo, bar };

/* 오류 */
const obj = { foo: foo, bar: bar };
```

### 172. one-var

하나의 선언문으로 여러 변수를 선언하는 것을 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "one-var": ["error", "always"]
}

/* 올바름 */
let foo = 1, bar = 2;

/* 오류 */
let foo = 1;
let bar = 2;
```

### 173. operator-assignment

할당 연산자를 사용하도록 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "operator-assignment": ["error", "always"]
}

/* 올바름 */
foo += 1;

/* 오류 */
foo = foo + 1;
```

### 174. prefer-arrow-callback

익명 함수 대신 화살표 함수를 사용하도록 강제합니다.
```js
/* 올바름 */
array.map(item => item * 2);

/* 오류 */
array.map(function(item) {
  return item * 2;
});
```

### 175. prefer-const

재할당하지 않는 변수를 `const`로 선언하도록 강제합니다.
```js
/* 올바름 */
const foo = 1;

/* 오류 */
let foo = 1;
```

### 176. prefer-destructuring

할당시 구조 분해를 사용하도록 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "prefer-destructuring": ["error", { "object": true, "array": true }]
}

/* 올바름 */
const { foo, bar } = obj;

/* 오류 */
const foo = obj.foo;
const bar = obj.bar;
```

### 177. prefer-exponentiation-operator

`Math.pow()` 대신 지수 연산자를 사용하도록 강제합니다.
```js
/* 올바름 */
const result = a ** b;

/* 오류 */
const result = Math.pow(a, b);
```

### 178. prefer-named-capture-group

정규 표현식에서 이름 있는 캡처 그룹을 사용하도록 강제합니다.
```js
/* 올바름 */
const regex = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/;

/* 오류 */
const regex = /(\d{4})-(\d{2})-(\d{2})/;
```

### 179. prefer-numeric-literals

`Number` 생성자 대신 숫자 리터럴을 사용하도록 강제합니다.
```js
/* 올바름 */
const num = 0b111110111;

/* 오류 */
const num = Number("0b111110111");
```

### 180. prefer-object-has-own

`Object.prototype.hasOwnProperty.call` 대신 `Object.hasOwn`을 사용하도록 강제합니다.
```js
/* 올바름 */
if (Object.hasOwn(obj, "prop")) {
  // ...
}

/* 오류 */
if (Object.prototype.hasOwnProperty.call(obj, "prop")) {
  // ...
}
```

### 181. prefer-object-spread

`Object.assign()` 대신 객체 스프레드 문법을 사용하도록 강제합니다.
```js
/* 올바름 */
const obj = { ...foo };

/* 오류 */
const obj = Object.assign({}, foo);
```

### 182. prefer-promise-reject-errors

`Promise rejection`시 `Error` 객체를 사용하도록 강제합니다.
```js
/* 올바름 */
Promise.reject(new Error('Something went wrong'));

/* 오류 */
Promise.reject('Something went wrong');
```

### 183. prefer-reflect

`Reflect` 메서드 사용을 선호하도록 강제합니다.
```js
/* 올바름 */
Reflect.apply(func, thisArg, args);

/* 오류 */
Function.prototype.apply.call(func, thisArg, args);
```

### 184. prefer-regex-literals

`RegExp` 생성자 대신 정규 표현식 리터럴을 사용하도록 강제합니다.
```js
/* 올바름 */
const regex = /abc/u;

/* 오류 */
const regex = new RegExp('abc', 'u');
```

### 185. prefer-rest-params

`arguments` 객체 대신 나머지 매개변수를 사용하도록 강제합니다.
```js
/* 올바름 */
function foo(...args) {
  return args;
}

/* 오류 */
function foo() {
  return arguments;
}
```

### 186. prefer-spread

`apply()` 대신 스프레드 연산자를 사용하도록 강제합니다.
```js
/* 올바름 */
foo(...args);

/* 오류 */
foo.apply(null, args);
```

### 187. prefer-template

문자열 연결 대신 템플릿 리터럴을 사용하도록 강제합니다.
```js
/* 올바름 */
const message = `Hello, ${name}`;

/* 오류 */
const message = 'Hello, ' + name;
```

### 188. radix

`parseInt` 함수 사용시 두번째 매개변수로 기수를 명시하도록 강제합니다.
```js
/* 올바름 */
const num = parseInt('10', 10);

/* 오류 */
const num = parseInt('10');
```

### 189. require-atomic-updates

변경 가능한 변수를 안전하게 업데이트하도록 강제합니다.
```js
/* 올바름 */
let foo = 0;
foo = bar + 1;

/* 오류 */
foo += bar;
```

### 190. require-await

비동기 함수에서 반드시 `await`를 사용하도록 강제합니다.
```js
/* 올바름 */
async function foo() {
  await bar();
}

/* 오류 */
async function foo() {
  bar();
}
```

### 191. require-unicode-regexp

정규 표현식에서 유니코드 플래그를 사용하도록 강제합니다.
```js
/* 올바름 */
const regex = /\p{Letter}/u;

/* 오류 */
const regex = /\p{Letter}/;
```

### 192. require-yield

생성기 함수 내에서 반드시 `yield`를 사용하도록 강제합니다.
```js
/* 올바름 */
function* generator() {
  yield 1;
}

/* 오류 */
function* generator() {
  return 1;
}
```

### 193. sort-imports

`import`문을 정렬하도록 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "sort-imports": ["error", {
    "ignoreCase": false,
    "ignoreDeclarationSort": false,
    "ignoreMemberSort": false,
    "memberSyntaxSortOrder": ["none", "all", "multiple", "single"]
  }]
}

/* 올바름 */
import a from 'a';
import b from 'b';

/* 오류 */
import b from 'b';
import a from 'a';
```

### 194. sort-keys

객체 리터럴의 키를 정렬하도록 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "sort-keys": ["error", "asc", { "caseSensitive": false, "natural": true }]
}

/* 올바름 */
const obj = { a: 1, b: 2 };

/* 오류 */
const obj = { b: 2, a: 1 };
```

### 195. sort-vars

변수 선언을 정렬하도록 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "sort-vars": ["error"]
}

/* 올바름 */
let a = 1;
let b = 2;

/* 오류 */
let b = 2;
let a = 1;
```

### 196. strict

`strict` 모드를 사용하도록 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "strict": ["error", "global"]
}

/* 올바름 */
'use strict';

/* 오류 */
// 엄격 모드 없음
```

### 197. symbol-description

`Symbol` 객체에 설명을 추가하도록 강제합니다.
```js
/* 올바름 */
const sym = Symbol('description');

/* 오류 */
const sym = Symbol();
```

### 198. unicode-bom

`BOM(Byte Order Mark)`을 사용하거나 사용하지 않도록 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "unicode-bom": ["error", "never"]
}

/* 올바름 */
// BOM 없음

/* 오류 */
// BOM 있음
```

### 199. use-isnan

`NaN`과 비교할 때는 반드시 `isNaN()`을 사용하도록 강제합니다.
```js
/* 올바름 */
if (isNaN(value)) {
  // ...
}

/* 오류 */
if (value === NaN) {
  // ...
}
```

### 200. valid-typeof

`typeof` 연산자 사용시 유효한 문자열을 사용하도록 강제합니다.
```js
/* 올바름 */
if (typeof value === 'string') {
  // ...
}

/* 오류 */
if (typeof value === 'strnig') {
  // ...
}
```

### 201. vars-on-top

모든 변수 선언을 함수의 맨 위에 두도록 강제합니다.
```js
/* 올바름 */
function foo() {
  var bar = 1;
  var baz = 2;
  // ...
}

/* 오류 */
function foo() {
  var bar = 1;
  // ...
  var baz = 2;
}
```

### 202. yield-star-spacing

`yield*` 표현식의 별 주위에 공백을 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "yield-star-spacing": ["error", "both"]
}

/* 올바름 */
function* foo() {
  yield * other();
}

/* 오류 */
function* foo() {
  yield*other();
}
```

### 203. yoda

`Yoda` 조건문 스타일을 사용하도록 강제합니다.
```js
/* 설정 예시 */
"rules": {
  "yoda": ["error", "always"]
}

/* 올바름 */
if ("red" === color) {
  // ...
}

/* 오류 */
if (color === "red") {
  // ...
}
```
