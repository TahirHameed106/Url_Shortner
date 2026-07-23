# My C# Learning Log

A running journal of what I've actually learned, broken, fixed, and understood
so far — not a polished checklist, the real messy version.

---

## Where this started

Originally I was building the URL shortener project in Node.js/Express (MERN).
Switched to C# / .NET because I couldn't find MERN jobs and .NET has stronger
demand where I'm looking. The project idea stayed the same — only the language
changed.

---

## Session 1 — Arrow functions and async (the JS chapter, before the switch)

Before switching, I got stuck on arrow function syntax — didn't know the
difference between:

```js
const square = n => n * n;        // implicit return, no braces
const square = n => { return n * n; }; // explicit return, with braces
```

My actual mistake was mixing the two forms — dropping the braces but keeping
`return`. Once I saw that braces + `return` are a package deal (both or
neither), it clicked.

Also learned `const` can't be reassigned — tried declaring the same variable
name twice and got `Identifier has already been declared`.

This is where I decided to pivot to .NET, so this chapter mostly stopped here.

---

## Session 2 — First real C# confusion: get / set

Started with fields vs. properties. Genuinely didn't get what `get` and `set`
were doing at first — thought I had to call them like normal methods.

The thing that made it click: **`get` runs when you read the property,
`set` runs when you write to it — you never call either by name yourself.**
`value` inside `set` is a special keyword that means "whatever was just
assigned."

Before this clicked, my mental model was completely wrong — I thought fields
and properties were basically the same thing with extra typing. Now I get
that a property is a checkpoint, a field is just raw storage.

---

## Session 3 — The `Student` class

Wrote my first real class with fields, a setter method, and a getter method.

**Bugs I hit, in order:**

1. Wrote `setStudent { ... }` as if I could re-open the method by name inside
   itself. Not valid C# — the if/else just needed to sit directly in the
   method body.
2. Tried testing a fragment of code (just the if/else block) by pasting it
   into the interactive C# prompt (`csi`) instead of running the whole file.
   Got `'age' does not exist in the current context` — because outside a
   real method, on a real object, `age` and `this` don't mean anything.
   Lesson: test the *whole program*, not snippets in isolation.
3. Left a stray extra `;` in `Console.WriteLine("...":+getStudent(););`
4. Created an empty `student display = new student();` and tried to print
   its data — but I never called `setStudent()` on it, so everything was
   default/null. Confused "a new empty object" with "a filled-in object."
5. Had both a loose top-level `Console.WriteLine("Hello, World!")` *and* an
   explicit `Main` method in the same file — apparently that's a real
   conflict in C#, only one entry point allowed.

**What I understand now that I didn't before:**
- `void` methods (like `displayStudent()`) just *do* something (print) and
  give nothing back.
- Methods that `return` something (like `getStudent()`) hand data back to
  whoever called them, so it can be reused, printed, sent elsewhere, etc.
  This matters a lot for backend work — an API can't "print to console,"
  it has to *return* data.

**Status:** still debugging why my `student` program isn't producing output
when run — working through it live.

---

## What's next on the list

- [ ] Get the `Student` program actually running end-to-end with real output
- [ ] Practice set: Book class, Rectangle class, BankAccount class, Movie
      array with "find highest rated," and a `ShortUrl` class (the real
      capstone — this one maps directly onto the actual project)
- [ ] Constructors
- [ ] Access modifiers or (public/private/protected)
- [ ] Encapsulation, inheritance, polymorphism, interfaces, abstract classes
- [ ] Back to the real project: Phase 1 MVP in ASP.NET Core

---

## Honest notes to self

- I keep wanting to test small fragments instead of full programs — need to
  break that habit, C# doesn't work like a REPL-first language for me yet.
- Typos (`reutrn`, missing braces, stray semicolons) are still my most common
  bug, not logic errors. Slowing down before running > running immediately.
- Understanding something after I've broken it is sticking way better than
  reading it first.
