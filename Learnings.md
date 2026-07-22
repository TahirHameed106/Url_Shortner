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
### Clousers
* leetCode Easy 

---
 2620-COUNTER : Given an integer n, return a counter function. This counter function initially returns n and then returns 1 more than the previous value every subsequent time it is called (n, n + 1, n + 2, etc).

---
mine solution :
 ```javascript

   function cerateCounter(n){  
      var init = n;
 
        function counter() { 
               return init++;
        }
     return counter;
}
```

 The code inside of the Chiled function    retain the value in the memory . bug not the parent function in the nested function in clousers.
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
---
* Your task:

Create const book = { title: "1984", author: "Orwell" };
Destructure title and author out of it in one line.
Write a function describeBook that takes { title, author } as a destructured parameter, and logs a sentence using a template literal — something like "1984 was written by Orwell".
Call describeBook(book) and confirm the output.

---

* Answer:
```javascript
const books = {title :"1982",author : "Orwell"};

const describeBook =({title , author}) => {
 console.log(`${title} was written by the ${author}`); 
};
describeBook(books);

```
