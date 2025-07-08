Tags: #programming #js #fundamentals 

### 📌 Core Idea

JavaScript **compiles code before executing it**. During the compilation phase, the engine:

- Finds all **declarations** (variables and functions).
    
- **Associates** them with their appropriate scopes.
    

---

### 🧠 Compilation vs Execution

Example:

`var a = 2; console.log(a);`

JavaScript interprets this as:

**Compilation phase:**
`var a;`

**Execution phase:**

`a = 2; console.log(a);`

---

### 🎣 Hoisting

> All declarations are “moved” to the top of their scope — this is called **hoisting**.  
> Only **declarations** are hoisted, not **assignments**.

Example:

`var a;  console.log(a); // undefined  a = 2;`

---

### 🧪 Function Example

`foo();  function foo() { 	console.log(a); // undefined 	var a = 2; }`

**Interpreted as:**

`function foo() { 	var a; 	console.log(a); // undefined 	a = 2; } foo();`

> Hoisting is **per-scope**, not global.

---

### ❌ Function Expression ≠ Function Declaration

`foo(); // ❗ TypeError var foo = function bar() { 	// ... };`

**What happens:**

`var foo; foo(); // TypeError: foo is undefined  foo = function bar() { 	// ... };`

> `foo` is hoisted as a variable, but the assignment happens during execution.

---

### 🧩 Named Function Expression


`foo(); // TypeError bar(); // ReferenceError  var foo = function bar() { 	// ... };`

- `foo` is hoisted but undefined during the call.
    
- `bar` exists **only inside** the function body.
    

---

### 📝 Summary

- 🔼 Declarations are hoisted; assignments are not.
    
- 📦 Hoisting works **within scope** (not globally).
    
- 📣 Function **declarations** are fully hoisted.
    
- 🔒 Function **expressions** are not hoisted as functions, only as undefined variables.