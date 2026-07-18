# JavaScript Prerequisites for This Project

## JavaScript

### Functions

Normal functions in JavaScript are written like this:

```javascript
function square(n) {
  return n * n;
}
```

### Arrow Functions

Arrow functions are written in the following format.

There are **two types of return**:

#### 1. Implicit Return

* No curly braces `{}` are used.
* No `return` keyword is needed.

```javascript
const square = n => n * n;
```

#### 2. Explicit Return

* Curly braces `{}` are used.
* The `return` keyword **must** be written; otherwise, the function returns `undefined`.

```javascript
const square = n => {
  return n * n;
};
```

---

### Callback Functions

* Callback functions

---

### Promises
* `async` / `await`

* Learn Promises first to understand **why `await` exists**.

---

### Destructuring & Template Literals

* Used when we are trying to pull data out of objects or arrays.
* Template literals help us create dynamic strings more cleanly.
