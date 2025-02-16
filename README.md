📝 GO NOTEBOOK

# BASICS OF GO

## INTRODUCTION

Go is a **statically typed**, **compiled programming language** designed for **simplicity** and **efficiency**. Its syntax is **clean** and **concise**, making it easy to read and write.
Go is **cross-platform**, **open source** and **fast** and its syntax is **similar to C++** and it was developed at **Google** by **Robert Griesemer, Rob Pike, and Ken Thompson** in **2007**.

### Popular Companies are Using Go :

1. Web Development & Streaming Platforms
  Netflix: DynaStream – Go was used for efficient, real-time data processing to personalize recommendations.
  Twitch: Chat Service – Go handles the high concurrency needed for millions of real-time chat messages.
  SoundCloud: Monolith to Microservices – Migrated backend services to Go for better scalability and maintainability.
2. Networking & Infrastructure
  Google: Kubernetes – Go was chosen for its simplicity, performance, and built-in concurrency for container orchestration.
  Cloudflare: GoProxy – Go powers various network services due to its efficient memory management and performance.
  Dropbox: Sync Engine Rewrite – Dropbox rewrote its file synchronization engine in Go to improve performance and scalability.
3. Cloud-Native & Enterprise Applications
  Alibaba Cloud: Cloud Infrastructure – Go was used for scalable and efficient microservices in cloud environments.
  Microsoft Azure: Go SDK for Azure – Go supports infrastructure automation and cloud service management.
  Heroku: Heroku CLI – Go was chosen for its performance and ease of cross-platform development.
4. FinTech & Payments
  PayPal: Fraud Detection System – Go improved performance in real-time fraud detection pipelines.
  Capital One: Data Processing Services – Go was used to build efficient, scalable services for financial operations.
5. Ride-Hailing & Logistics
  Uber: Geofence Service – Go powers geospatial indexing and trip matching for real-time logistics.
  Lyft: Dispatch System – Go helps handle large volumes of requests in real-time ride matching.
6. DevOps & Tools
  Docker: Docker Engine – Go was chosen for its performance, concurrency, and simplicity in container orchestration.
  HashiCorp Terraform: Terraform Core – Go provides a reliable and efficient base for infrastructure automation.

### Why Use Go?

Go is fun and easy to learn

Go has fast run time and compilation time

Go supports concurrency

Go has memory management

Go works on different platforms (Windows, Mac, Linux, Raspberry Pi, etc.)

### Go Usages

Web development (server-side) { SoundCloud 🎶}

Developing network-based programs {Docker 🐳}

Developing cross-platform enterprise applications { Uber }

Cloud-native development { Kubernetes }

## 1.1 Go Code (File) Structure

Every Go program follows a specific structure to ensure clarity, simplicity, and consistency. Understanding this structure is crucial for writing clean, maintainable, and executable Go code.

### **Structure Overview**

1. **Package Declaration (Required)**
  
  - Every Go program begins with a `package main`. This package is special because it produces an executable file.
  - Other packages (non-main) are used for reusable code libraries and do not generate executables.
2. **Imports (Optional)**
  
  - Imports bring external or standard library packages into the code.
  - Two types of imports are available:
    - **Single Import:** For importing one package.
    - **Multiple Imports:** For importing several packages together.
  - Import paths are case-sensitive and must match the actual directory names.
3. **Declarations (Optional)**
  
  - Constants, variables, types, and functions can be declared after imports and before the `main` function.
4. **Main Function (Required)**
  
  - The `main` function serves as the entry point of the Go program.

### **Key Points to Remember**

- **Semicolon Handling:** Go automatically inserts semicolons at the end of statements; however, certain syntactical rules require braces `{` to be on the same line as the corresponding statement.
- **File Naming:** Go source files have a `.go` extension.
- **Execution:** Go programs with `package main` can be executed, while other packages are intended for code reuse.

### **Example Code**

```go
package main

import "fmt"

// Declaring a constant
const greeting = "Hello, World!"

// Declaring a function
func printGreeting() {
    fmt.Println(greeting)
}

func main() {
    printGreeting()
}
```

### **Explanation**

1. **`package main`:**
  - Declares the package as `main`, which is necessary for creating an executable program.
2. **`import "fmt"`:**
  - Imports the `fmt` package for formatted I/O.
3. **`const greeting`:**
  - Declares a string constant.
4. **`func printGreeting`:**
  - Defines a function that prints the greeting message.
5. **`func main`:**
  - The program's entry point, calling `printGreeting` to print the message.

### **Import Variations**

#### **1. Single Import**

```go
import "fmt"
```

#### **2. Multiple Imports**

```go
import (
    "fmt"
    "math"
    "time"
)
```

### **Special Import Cases**

- **Blank Import:**
  
  - Used to import a package solely for its side effects (e.g., initialization).
  
  ```go
  import _ "net/http"
  ```
  
- **Aliased Import:**
  
  - Assigns a custom alias to a package.
  
  ```go
  import f "fmt"
  f.Println("Aliased import example")
  ```
  

### **Best Practices**

- Always start executable programs with `package main`.
- Group related imports together for clarity.
- Use meaningful names for functions, variables, and constants.
- Follow Go's convention of placing braces on the same line as control statements.
- Run `go fmt` regularly to maintain code style consistency.

By following this structure, Go programs become more predictable, readable, and efficient.

### **Naming Convention**

The Go project emphasizes simplicity and readability, adopting straightforward conventions to ensure that source code remains maintainable and consistent.

### File Naming

- File names should be all **lowercase** with words separated by **underscores**.
- Compound file names use an underscore (`_`) to separate words.
- File names starting with `.` or `_` are ignored by the `go` tool.
- Files with the suffix `_test.go` are exclusively compiled and executed by the `go test` tool.

**Examples:**

- `user_data.go`
- `config_loader_test.go`

### Function and Method Naming

Go uses **camelCase** for function and method names, with case determining visibility:

- **Unexported** (package-private) functions start with a lowercase letter.
- **Exported** (public) functions start with an uppercase letter.
- This point is correct about variable names too .

**Examples:**

- `writeToDB` - unexported; accessible only within the package.
- `WriteToDB` - exported; accessible from other packages.

### Constant Naming

- Constants use **ALL_CAPS** with underscores (`_`) to separate words.
- For enumerations or grouped constants, `iota` is often used for cleaner syntax.

**Examples:**

- `MAX_RETRIES`
- `DEFAULT_TIMEOUT`

### Variable Naming

- Use **short and simple names** when possible, but ensure clarity.
- Maintain a **consistent naming style** throughout the source code.
- Use **descriptive names** when clarity is essential.

**Examples:**

- `user` → `u`
- `userID` → `uid`

### Boolean Naming

- Boolean variables should begin with verbs like `Has`, `Is`, `Can`, or `Allow`.

**Examples:**

- `isAvailable`
- `canExecute`
- `hasAccess`

### Loop Variables

- Use **single-letter names** like `i`, `j`, or `k` for **loop indices**.

**Example:**

```go
for i := 0; i < 10; i++ {
    fmt.Println(i)
}
```

### Key Points to Remember

- If the scope of use is small and the variable is used only for a few lines → use a short name.
  
- If the variable is used in important sections or longer code → use a full, descriptive name.
  
- In Go, abbreviations like ID, HTTP, URL must be written in all uppercase.
  
- ✅ **Golden rule:** Write the code in such a way that if you see it again in 3 months, you can understand what it does without thinking. 💡
  

### Best Practices

- Consistency is key: stick to these conventions across the entire codebase.
- Avoid unnecessarily long names but ensure readability.
- Use `go fmt` to enforce formatting rules automatically.

Following these conventions makes your Go code cleaner, more predictable, and easier to maintain.

##### Keywords and Identifiers

The Go language has only 25 keywords up to the current version, which are as follows:

| **Global Declaration Keywords** | **Composite Type Keywords** | **Control Flow Keywords** | **Concurrency Keywords** |
| --- | --- | --- | --- |
| package | struct | break | go  |
| import | interface | case | select |
| type | map | continue |     |
| var | chan | default |     |
| const |     | if  |     |
| func |     | else |     |
|     |     | for |     |
|     |     | fallthrough |     |
|     |     | goto |     |
|     |     | range |     |
|     |     | return |     |
|     |     | switch |     |

These keywords are reserved and cannot be used as identifiers (such as variable names, function names, etc.).

### **Keyword Categories**

The above keywords are divided into four categories:

1. **Global Declaration Keywords**
  
  - These keywords are used for defining the structure of the program, declaring types, variables, constants, and functions.
2. **Composite Type Keywords**
  
  - These keywords define complex data types for structuring data, creating maps, channels, and defining interfaces.
3. **Control Flow Keywords**
  
  - These keywords manage the control flow of the program through conditional logic, loops, and switch cases.
4. **Concurrency Keywords**
  
  - These keywords are central to Go's concurrency model, enabling goroutines and channel-based communication.

### **Identifiers in Go**

Identifiers are the names used to identify variables, types, functions, and other program elements. They must follow these rules:

- Should begin with a letter (A-Z or a-z ) or underscore `_`. Can use other language letters too but it's better to use English Letters using other languages letters is not common .
- Can contain letters, digits (0-9), and underscores.
- Are case-sensitive (`age` and `Age` are different).
- Cannot use reserved keywords.

**Examples:**

```go
var studentName string
const MAX_COUNT = 100
func calculateSum(a int, b int) int {
    return a + b
}
```

### **Exported vs Unexported Identifiers**

- Identifiers starting with an uppercase letter are **exported** (accessible from other packages).
- Identifiers starting with a lowercase letter are **unexported** (internal to the package).

**Example:**

```go
package mypackage

// Exported
func PublicFunction() {}

// Unexported
func privateFunction() {}
```

## **1.2. Basic Types in Go**

Go is a statically typed language, meaning that once a variable is declared with a numeric type, it cannot store non-numeric data. In Go, variable types must be specified with declaration (e.g., `var a, b int = 1, 2`) or compiler inference. If the type isn't specified, the compiler raises an error.

Go provides the following basic types:

| Type | Range | Default Value | Memory Usage |
| --- | --- | --- | --- |
| int | System-dependent (32/64-bit) | 0   | 4/8 bytes |
| int8 | -128 to 127 | 0   | 1 byte |
| int16 | -32768 to 32767 | 0   | 2 bytes |
| int32 | -2147483648 to 2147483647 | 0   | 4 bytes |
| int64 | -9223372036854775808 to 9223372036854775807 | 0   | 8 bytes |
| uint | System-dependent (32/64-bit) | 0   | 4/8 bytes |
| uint8 | 0 to 255 | 0   | 1 byte |
| uint16 | 0 to 65535 | 0   | 2 bytes |
| uint32 | 0 to 4294967295 | 0   | 4 bytes |
| uint64 | 0 to 18446744073709551615 | 0   | 8 bytes |
| uintptr | Memory address size | 0   | 8 bytes |
| float32 | IEEE-754 | 0.0 | 4 bytes |
| float64 | IEEE-754 | 0.0 | 8 bytes |
| complex64 | Complex numbers | 0+0i | 8 bytes |
| complex128 | Complex numbers | 0+0i | 16 bytes |
| bool | true/false | false | 1 byte |
| string | UTF-8 encoded text | ""  | 16 bytes |

**Aliases:**

- `byte` → alias for `uint8`
- `rune` → alias for `int32` (used for Unicode characters)

**Key Difference:**

- `int` stores both positive/negative integers.
- `uint` stores only positive integers.
- `uintptr` holds memory addresses and adjusts its size based on the OS architecture.

---

### **Customizing Types**

You can create custom names for existing types (type alias) or define new types based on existing ones.

**Type Aliases (same as base type):**

```go
type bul = bool
type content = string
type UI8 = uint8
type Word = rune
```

**New Types (distinct from base type):**

```go
type state bool
type str string
type ID uint64
type decimal float32
```

---

### Default Values

- `bool` → `false`
- Numeric types → `0`
- `string` → `""` (empty string, no spaces)

---

### Type Values

#### **Boolean:**

Accepts only `true` or `false`.

#### **Integer:**

Four numeric systems supported:

- Decimal: `15`
- Octal: `017` or `0o17`
- Hexadecimal: `0xF`
- Binary: `0b1111`

#### **Float:**

Floating-point numbers can include:

- Decimal parts: `1.23`
- Exponent: `1.23e2` (123.0)

#### **Rune:**

A `rune` is an `int32` representing Unicode characters:

```go
'a', '\u0061', '\U00000061', '众', 'π'
```

#### **Byte and String:**

`string` is a UTF-8 sequence of bytes. Unicode characters may use multiple bytes (e.g., `hello你好` has 11 bytes but 7 runes).

**Example:**

```go
s := "hello你好"
fmt.Printf("len(s): %d\n", len(s))        // 11 bytes
fmt.Printf("len([]rune(s)): %d\n", len([]rune(s))) // 7 runes
```

---

### Improved Readability with `_`

Go allows using underscores to separate digits for readability:

```go
1_000_000     // 1,000,000  
0x_Bad_Face   // hex  
0b1011_0111   // binary  
```

**Invalid usage:**

- `_69` (can't start with `_`)
- `69_` (can't end with `_`)

### **English Translation and Summary: Operators in Go**

---

## **1.3. Operators in Go**

Like other programming languages, Go includes various operators such as arithmetic, comparison, logical, and bitwise operators.

### Arithmetic Operators

Go provides five arithmetic operators:

| Operator | Name |
| --- | --- |
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Modulus (Remainder) |

Example:

```go
a := 1
b := 2

c := a + b // 3
d := a - b // -1
e := a * b // 2
f := a / b // 0
g := a % b // 1
```

**Note:** `/` returns an integer result when both operands are integers.

---

### Comparison Operators

Go has six comparison operators:

| Operator | Meaning |
| --- | --- |
| `==` | Equal to |
| `!=` | Not equal to |
| `<` | Less than |
| `<=` | Less than or equal to |
| `>` | Greater than |
| `>=` | Greater than or equal to |

These operators return a boolean (`true` or `false`).

Example:

```go
a := 1
b := 2
c := 1

println(a == b) // false
println(a == c) // true
println(a < b)  // true
println(b > c)  // true
println(c <= a) // true
println(c >= b) // false
println(b != a) // true
println(c != a) // false
```

---

### Logical Operators

Go provides three logical operators:

| Operator | Meaning |
| --- | --- |
| `&&` | AND |
|     | \\| |
| `!` | NOT (Negation) |

- `&&` returns `true` if both operands are `true`.
- `||` returns `true` if at least one operand is `true`.
- `!` negates a boolean value.

Example:

```go
a := true  
b := true  
c := false  

fmt.Println(a && b) // true  
fmt.Println(a || b) // true  
fmt.Println(!a)     // false  
fmt.Println(!c)     // true
```

---

### Bitwise Operators

Go provides five bitwise operators:

| Operator | Name |
| --- | --- |
| `>>` | Left Shift |
| `<<` | Right Shift |
| `&` | AND |
|     | \\| |
| `^` | XOR (Exclusive OR) |

#### **Bitwise Shift Operators (`>>`, `<<`)**

- `>>` (Right Shift) moves bits to the right, filling left positions with `0`.
- `<<` (Left Shift) moves bits to the left, filling right positions with `0`.

Example:

```go
a := 0b01000101  // 69 in binary
b := a << 1      // Left shift
c := a >> 1      // Right shift

fmt.Printf("binary:%08b,value:%v\n", a, a) // binary: 01000101, value: 69
fmt.Printf("binary:%08b,value:%v\n", b, b) // binary: 10001010, value: 138
fmt.Printf("binary:%08b,value:%v\n", c, c) // binary: 00100010, value: 34
```

#### **Bitwise AND (`&`)**

Keeps bits that are `1` in both operands.

```go
a := 0b01000101  // 69
b := 0b01010100  // 84
c := a & b       // 68

fmt.Printf("binary:%08b,value:%v\n", c, c) // binary: 01000100, value: 68
```

#### **Bitwise OR (`|`)**

Sets bits to `1` if at least one operand has `1`.

```go
d := 0b01000101  // 69
e := 0b01010100  // 84
f := d | e       // 85

fmt.Printf("binary:%08b,value:%v\n", f, f) // binary: 01010101, value: 85
```

#### **Bitwise XOR (`^`)**

Sets bits to `1` if only one operand has `1` (exclusive OR).

```go
g := 0b01000101  // 69
h := 0b01010100  // 84
i := g ^ h       // 17

fmt.Printf("binary:%08b,value:%v\n", i, i) // binary: 00010001, value: 17
```

---

### Operator Precedence

In Go, operators have specific precedence levels, and parentheses `()` can be used to override default precedence.

| Priority | Operators |
| --- | --- |
| 1   | `*`, `/`, `%`, `<<`, `>>`, `&`, `&^` |
| 2   | `+`, `-`, ` |
| 3   | `==`, `!=`, `<`, `<=`, `>`, `>=` |
| 4   | `&&` |
| 5   | `\\| |

**Note:** `<<` and `>>` have higher precedence than `+` and `-`.

---

## **1.4. Variables and Constants**

A variable is a named location in memory used to store data. In Go, variables are declared using the `var` keyword or the short declaration syntax `:=`.

---

### Reassigning a Variable

Variables can be assigned new values after declaration:

```go
var s string
s = "Hello World"
fmt.Println(s)
```

---

### Assigning a Mismatched Type

Go is strongly typed, meaning you cannot assign a string to an integer variable:

```go
var i int
i = "One"
```

**Error:** `cannot use "One" (type string) as type int in assignment.`

---

### Short Variable Declaration (`:=`)

Inside functions, you can declare variables using `:=` without specifying the type:

```go
s := "Hello World"
fmt.Println(s)
```

**Key Note:**

- `:=` can only be used within functions.
- Use `var` for global variables.

**Global Variable Example:**

---

### Declaring Multiple Variables in One Line

Go allows declaring multiple variables simultaneously:

```go
a, b, c := "hello", 1, 1.5
var d, e, f = "world", 13, 24
var g, h, j, l int = 1, 3, 5, 7
```

**Note:** If you use the `type` keyword, it is only possible to declare **one type** of variable per line.If the `type` keyword is not specified, you can declare different types of variables on the same line

---

### Go Variable Declaration in a Block

Multiple variable declarations can also be grouped together into a block for greater readability

```go
package main
import ("fmt")

func main() {
   var (
     a int
     b int = 1
     c string = "hello"
   )

  fmt.Println(a)
  fmt.Println(b)
  fmt.Println(c)
}
```

*Q1* : Does Declaration in a Block makes any differences ? accessbilty or etc?

---

### Declaring Variables with Default Values

If you declare a variable without assigning a value, it gets a default:

```go
var i int
var f float32
var b bool
var s string

fmt.Printf("%v %v %v %q\n", i, f, b, s)
```

**Output:**

```
0 0 false ""
```

**Default Values:**

- **Integers** → `0`
- **Floats** → `0.0`
- **Booleans** → `false`
- **Strings** → `""` (empty string)

---

## Constants

Constants are declared using `const` and are immutable (cannot be reassigned).

**Basic Example:**

```go
const s string = "Hello World"

func main() {
    fmt.Println(s)
}
```

---

### Untyped Constants

You don't need to specify a type for constants; Go infers it:

```go
const a = 1       // int
const b = "circle"// string
const c = 5.4     // float64
const d = true    // bool
const e = 'a'     // rune
const f = 3+5i    // complex128
```

---

## Checking the Type of Variables or Constants

Use `fmt.Printf` with `%T` to print the type:

```go
const a = 123
var b = "circle"

func main() {
    fmt.Printf("Type: %T Value: %v\n", a, a)
    fmt.Printf("Type: %T Value: %v\n", b, b)
}
```

---

### Using `iota` for Auto-Increment

`iota` generates sequential integer constants starting from 0.

**Without `iota`:**

```go
const (
    a = 0
    b = 1
    c = 2
)
```

**With `iota`:**

```go
const (
    a = iota // 0
    b        // 1
    c        // 2
)
```

**Explanation:**

- `iota` starts at 0 and increments by 1 automatically.

---

### Creating Enums with `iota`

Go doesn't have a traditional `enum` keyword. Instead, you can use `iota` to create enumerated constants. `iota` is a predeclared identifier representing successive untyped integer constants.

Enums can be created using `iota`:

```go
type Size uint8

const (
    small Size = iota
    medium
    large
    extraLarge
)

func main() {
    fmt.Println(small)      // 0
    fmt.Println(medium)     // 1
    fmt.Println(large)      // 2
    fmt.Println(extraLarge) // 3
}
```

---

### Skipping Initial `iota` Values

You can ignore the first value using an underscore (`_`):

```go
const (
    _ = iota // skip 0
    a        // 1
    b        // 2
    c        // 3
)
```

---

### **English Translation and Summary: Zero Values in Go**

---

###  Zero Values of Types in Go

In Go, variables declared without an explicit initial value are automatically assigned a **zero value**, which represents the default value for that type.

The table below shows the zero values for various types:

| **Type** | **Zero Value** |
| --- | --- |
| `int` | `0` |
| `int8` | `0` |
| `int16` | `0` |
| `int32` | `0` |
| `int64` | `0` |
| `uint` | `0` |
| `uint8` | `0` |
| `uint16` | `0` |
| `uint32` | `0` |
| `uint64` | `0` |
| `uintptr` | `0` |
| `float32` | `0.0` |
| `float64` | `0.0` |
| `complex64` | `0+0i` |
| `complex128` | `0+0i` |
| `bool` | `false` |
| `string` | `""` (empty string) |
| `interface` | `nil` |
| `slice` | `nil` |
| `channel` | `nil` |
| `map` | `nil` |
| `pointer` | `nil` |
| `function` | `nil` |
| `struct` | **zero values of its fields** |

---

### **Key Insights**

- Go ensures that all variables are initialized with zero values to avoid undefined behavior.
- For **structs**, each field gets its own zero value automatically.
- **`nil`** is the zero value for all reference types like `slice`, `map`, `channel`, `pointer`, `function`, and `interface`.

This mechanism simplifies the code by eliminating the need to initialize variables manually before use.

---

## **1.6 Functions in Go**

A **function** is a reusable block of code designed to perform a specific task. Functions help break code into smaller, manageable parts, reducing repetition and improving readability and maintainability.

#### **Why Use Functions?**

- **Reusability:** Write once, use multiple times.
- **Efficiency:** Reduces code duplication and speeds up development.
- **Clarity:** Code becomes easier to read, debug, and maintain.

---

## Functions Syntax in Go

Go functions have a simple syntax and support various features like multiple return values, variadic arguments, anonymous functions, and closures.

### **Basic Function Syntax**

```go
func function_name([parameter_list]) [return_types] {
    // Function body
}
```

---

### **Example: Simple Function**

```go
package main

import "fmt"

func plus(a int, b int) int {
    return a + b
}

func main() {
    fmt.Println(plus(4, 13))
}
```

**Explanation:**

- The `plus` function takes two `int` parameters and returns their sum.
- `int` after the parameters indicates the return type.
- Go requires specifying the type for each parameter, but you can group parameters of the same type:

```go
func plus(a, b int)
```

---

### Anonymous Functions

Functions can be assigned to variables and making them **anonymous**:

```go
package main

import "fmt"

func main() {
    plus := func(a int, b int) int {
        return a + b
    }
    fmt.Println(plus(3, 4))
}
```

---

### Multiple Return Values

Go supports returning multiple values from a function:

```go
package main

import "fmt"

func vals() (int, int) {
    return 3, 7
}

func main() {
    a, b := vals()
    fmt.Println(a, b) // 3 7

    _, c := vals()    // Ignore the first value
    fmt.Println(c)    // 7
}
```

**Explanation:**

- `vals` returns two integers.
- The **blank identifier** (`_`) ignores unneeded return values.

---

### Named Return Values

You can assign names to return values:

```go
package main

import "fmt"

func split(sum int) (x, y int) {
    x = sum * 4 / 9
    y = sum - x
    return // Naked return
}

func main() {
    fmt.Println(split(17)) // 7 10
}
```

**Note:**

- **Naked returns** omit explicit arguments.
- Use them only in short functions to maintain clarity.

---

### Variadic Functions

**Variadic functions** accept an unlimited number of arguments of the **same type**.

```go
package main

import "fmt"

func sum(nums ...int) {
    fmt.Print(nums, " ")
    total := 0
    for _, num := range nums {
        total += num
    }
    fmt.Println(total)
}

func main() {
    sum(1, 2)               // [1 2] 3
    sum(1, 2, 3)            // [1 2 3] 6
    nums := []int{1, 2, 3, 4}
    sum(nums...)            // [1 2 3 4] 10
}
```

**Explanation:**

- The `...` operator allows passing a slice as multiple arguments.

---

### **Anonymous Functions**

Anonymous functions are functions without a name, often used for short-term or one-off tasks.

**Example:**

```go
package main

import "fmt"

func main() {
    sum := func(n1, n2 int) int {
        return n1 + n2
    }
    result := sum(5, 3)
    fmt.Println("Sum is:", result)
}
```

**Note:**

- Anonymous functions are often passed as arguments to higher-order functions.

### **Passing Anonymous Functions as Parameters**

```go
package main

import "fmt"

func add10AndSum(n1 int, n2 int, sumFunc func(int, int) int) {
    result := sumFunc(n1+10, n2+10)
    fmt.Println("Sum by adding 10 is:", result)
}

func main() {
    add10AndSum(5, 3, func(a, b int) int {
        return a + b
    })
}
```

**Output:** `Sum by adding 10 is: 28`

---

### **Built-in Functions**

Go includes several built-in functions like `len()`, `cap()`, `new()`, `make()`, `append()`, `copy()`, and `delete()` for common operations.

---

### **Closures (Function Closure)**

**Closures** are anonymous functions that capture and use variables from an enclosing scope.

**Example:**

```go
package main

import "fmt"

func main() {
    number := 1

    func() {
        fmt.Println(number * 2)
    }()
}
```

**Output:** `2`

**Explanation:**

- The anonymous function accesses `number` from the surrounding scope.

### **Closure and Concurrency Gotcha**

In concurrent code, closures can lead to unexpected behavior if variables are directly accessed:

```go
package main

import (
    "fmt"
    "time"
)

func main() {
    for i := 0; i < 10; i++ {
        go func() {
            fmt.Println(i)
        }()
    }
    time.Sleep(time.Second * 1)
}
```

**Unexpected Output:**

- Prints `10` ten times instead of `0–9`.

**Reason:**

- The closure captures the **reference** to `i`, which has the final value `10` after the loop ends.

**Fix:** Pass `i` as a parameter:

```go
for i := 0; i < 10; i++ {
    go func(n int) {
        fmt.Println(n)
    }(i)
}
```

Now, the goroutines print `0` to `9` correctly.

---

## 1.7. Arrays and Slices in Go

### Array

**Definition:** An **array** stores multiple values of the **Same Type**. The size is **fixed** at declaration.

**Example:**

```go
arrayInts := [5]int{1, 25, 12354, 654, 32}
fmt.Println(arrayInts)
// Output: [1 25 12354 654 32]
```

**Key Points:**

- **<u>Fixed Size</u>**: Cannot exceed the declared size.
- **<u>Indexing</u>:** Elements are accessed via indices.
- **<u>Zero-Initialization</u>:** Default elements are set to their zero value.

---

### Array Size and Capacity

- **Size:** The number of elements.
- **Capacity:** The total available space.
- Size and capicity are equal in arrays .

Use `len()` for size and `cap()` for capacity:

```go
array := [3]string{"a", "b", "c"}
fmt.Printf("Array: %v, Length: %d, Capacity: %d\n", array, len(array), cap(array))
```

**Output:**

```
Array: [a b c], Length: 3, Capacity: 3
```

---

### Array Initialization

- **Empty Array:**

```go
nums := [5]int{}
```

- **Auto-Sized Array:**

```go
nums := [...]int{1, 2, 3}
```

- **Multi-Dimensional Array:**

```go
matrix := [2][2]int{{1, 2}, {3, 4}}
```

---

### Array Comparisons

Arrays are comparable only if:

- **Same Type**
- **Same Size**
- **Same Values**

```go
a := [2]int{1, 2}
b := [2]int{1, 3}
fmt.Println(a == b) // false
c := [2]int{1, 2}
d := [2]int{1, 2}
fmt.Println(c == d) // true
```

---

### Slices in Go

A **Slice** is a **flexible**, **dynamic view** of an underlying array.

**Key Features:**

- **Dynamic Size:** Can grow or shrink at runtime.
- **Shared Memory:** Changes affect the underlying array.
- **Simplified Syntax:** Created without specifying size.

---

### Slice Creation

- **Using `make()`:**

```go
slice := make([]int, 5)         // length 5, capacity 5
slice := make([]int, 3, 5)      // length 3, capacity 5
```

**Key Points**:

- We can't use `make` for creating `array` in go because size of them should be specify at the compile time ( initializing )
  
- `copy()` ,`make()` and `append()` just works on slice but not on array
  
- Without making an `Slice` or assigning value in the declaration we can't have access to its items
  
- **Short Declaration:**
  

```go
slice := []string{"Red", "Blue", "Green"}
```

- **With Index Specification:**

```go
slice := []int{99: 88}  // slice of length 100 with the last element set to 88
```

- **Empty Slice:**

```go
slice := []int{}
```

---

### Accessing and Modifying Elements

- **Modify by Index:**

```go
slice := []int{1, 2, 3}
slice[1] = 42
fmt.Println(slice) // [1 42 3]
```

- **Create Subslice:**

```go
base := []int{10, 20, 30, 40}
sub := base[1:3]
fmt.Println(sub) // [20 30]
```

---

### Slice Operations

- **Append Elements:**

```go
slice := []int{1, 2}
slice = append(slice, 3, 4)
fmt.Println(slice) // [1 2 3 4]
```

- **Delete Element:**In Go, removing an element from a slice requires creating a new slice that excludes the unwanted element, as Go does not provide a built-in function for this purpose.

```go
// FIRST WAY

index := 2
slice := []int{1, 2, 3, 4, 5}
slice = append(slice[:index], slice[index+1:]...)
fmt.Println(slice) // [1 2 4 5]

// In this example:
// - `numbers[:index]` retrieves the elements before the specified index.
// - `numbers[index+1:]` retrieves the elements after the specified index.
// - `append` combines these two slices, effectively removing the element
//    at  the specified index.




// SECOND WAY

numbers[index] = numbers[len(numbers)-1]
numbers = numbers[:len(numbers)-1]


```

**Note:** First method maintains the order of elements. If preserving order is not necessary, you can replace the element to be removed with the last element and then truncate the slice.

Second approach is more efficient as it reduces the number of elements that need to be shifted. 

- **Copy Slices:**

```go
src := []int{1, 2, 3}
dst := make([]int, len(src))
copy(dst, src)
fmt.Println(dst) // [1 2 3]
```

- **Sort Slice:**

```go
import "sort"

s := []int{4, 2, 3, 1}
sort.Ints(s)
fmt.Println(s) // [1 2 3 4]
```

---

### Differences Between Arrays and Slices

| **Feature** | **Array** | **Slice** |
| --- | --- | --- |
| **Size** | Fixed, defined at compile-time | Dynamic, grows automatically |
| **Declaration** | `[5]int{1,2,3,4,5}` | `[]int{1,2,3,4,5}` |
| **Empty State** | Zero-filled array | `nil` when empty |
| **Flexibility** | Rigid size | Flexible size |

---

### Common Pitfalls

- **Index Out of Range:** Occurs when accessing indices beyond the slice boundary.
  
- **Shared Underlying Array:** Changes in one slice can affect other slices from the same array.
  

---

#### Arrays and Slices Summary

#### **Arrays** have a fixed size, while **slices** are dynamically-sized, flexible views into arrays.

**Array Syntax:**

```go
var arrayName [length]elementType
```

**Slice Syntax:**

```go
sliceName := []elementType{values}
```

**Example:**

```go
package main

import "fmt"

func main() {
    // Array
    var arr [3]int = [3]int{1, 2, 3}
    fmt.Println("Array:", arr)

    // Slice
    slice := []int{1, 2, 3, 4, 5}
    fmt.Println("Slice:", slice)

    // Appending to a slice
    slice = append(slice, 6)
    fmt.Println("After append:", slice)

    // Slicing a slice
    subSlice := slice[1:4]
    fmt.Println("Sub-slice:", subSlice)

    // Copying a slice
    copiedSlice := make([]int, len(slice))
    copy(copiedSlice, slice)
    fmt.Println("Copied slice:", copiedSlice)

    // Removing an element from a slice (preserving order)
    index := 2 // Remove the element at index 2
    slice = append(slice[:index], slice[index+1:]...)
    fmt.Println("After removal:", slice)
}
```

**Output:**

```
Array: [1 2 3]
Slice: [1 2 3 4 5]
After append: [1 2 3 4 5 6]
Sub-slice: [2 3 4]
Copied slice: [1 2 3 4 5 6]
After removal: [1 2 4 5 6]
```

**Notes:**

- Arrays have a fixed length, and their size is part of their type.
- Slices are more flexible and are the preferred way to work with collections of data in Go.
- The `append` function adds elements to the end of a slice.
- The `copy` function copies elements from one slice to another.
- Removing elements from a slice requires creating a new slice without the unwanted elements.
  
  ---
  

## 1.8. Loops in Go

Go uses a single keyword, **`for`**, to implement various types of loops such as:

- **Three-part (traditional) loops**
- **While-like loops**
- **Infinite loops**
- **For-range loops**

---

### Three-Part Loop (Classic `for` Loop)

This is the most common loop, consisting of three parts:

- **Initialization**
- **Condition**
- **Counter** (increment/decrement)

**Syntax:**

```go
for initialization; condition; counter {
    // code to execute
}
```

**Example:**

```go
package main
import "fmt"

func main() {
    sum := 0
    for i := 1; i < 10; i++ {
        sum += i
    }
    fmt.Println(sum) // Output: 45
}
```

---

### While-Like Loop

Go doesn’t have a `while` keyword, but you can simulate it by omitting the initialization and increment parts.

**Example (while loop):**

```go
package main
import "fmt"

func main() {
    i := 0
    for i < 10 {
        fmt.Println(i)
        i++
    }
}
```

---

### Infinite Loop

Omit all three parts in a `for` loop, and you get an infinite loop.

**Example:**

```go
package main
import "fmt"

func main() {
    sum := 0
    for {
        sum++
    }
    // This line will never run
    fmt.Println(sum)
}
```

This loop runs indefinitely until manually stopped or encountering a `break` statement.

---

### For-Range Loop

This loop is commonly used with:

- **Arrays**
- **Slices**
- **Maps**
- **Strings**

**Syntax:**

```go
for index, value := range collection {
    // code to execute
}
```

#### For-Range with Arrays and Slices

**Example:**

```go
package main
import "fmt"

func main() {
    letters := []string{"a", "b", "c"}

    // Access index and value
    for i, letter := range letters {
        fmt.Printf("Index: %d, Value: %s\n", i, letter)
    }

    // Access only values
    for _, letter := range letters {
        fmt.Println(letter)
    }

    // Access only indices
    for i := range letters {
        fmt.Printf("Index: %d\n", i)
    }
}
```

---

#### For-Range with Maps

**Example:**

```go
package main
import "fmt"

func main() {
    sample := map[string]string{"a": "x", "b": "y"}

    // Iterate over keys and values
    for k, v := range sample {
        fmt.Printf("Key: %s, Value: %s\n", k, v)
    }

    // Iterate over keys only
    for k := range sample {
        fmt.Printf("Key: %s\n", k)
    }

    // Iterate over values only
    for _, v := range sample {
        fmt.Printf("Value: %s\n", v)
    }
}
```

---

#### For-Range with Strings

Strings are iterated **rune-by-rune**, with `index` representing the byte index.

**Example:**

```go
package main
import "fmt"

func main() {
    str := "a£b"

    for i, ch := range str {
        fmt.Printf("Index: %d, Char: %s\n", i, string(ch))
    }
}
```

**Note:** Unicode characters like `£` may occupy more than **one byte**.

---

### `break` Keyword

The `break` statement **exits the current loop** immediately.

**Example:**

```go
package main
import "fmt"

func main() {
    sum := 0
    for {
        sum++
        if sum == 10 {
            break
        }
    }
    fmt.Println(sum) // Output: 10
}
```

---

### `continue` Keyword

The `continue` statement **skips the rest of the loop body** and moves to the **next iteration**.

**Example:**

```go
package main
import "fmt"

func main() {
    for i := 1; i <= 10; i++ {
        if i%2 == 0 {
            continue
        }
        fmt.Println(i)
    }
}
```

---

### Labeled Loops

Go supports **labeled loops**, which help manage nested loops by specifying which loop to **break** or **continue**.

**Example:**

```go
package main
import "fmt"

func main() {
    letters := []string{"a", "b", "c"}

outerLoop:
    for i := 1; i < 5; i++ {
        for _, letter := range letters {
            if letter == "b" {
                break outerLoop
            }
            fmt.Println(letter)
        }
    }
}
```

**Explanation:**

- When `letter == "b"`, the `break outerLoop` exits the **outer loop** entirely.
- Without the label, it would only exit the **inner loop**.

**Output:**

```
a
```

---

### Summary

| **Loop Type** | **Structure** | **Purpose** |
| --- | --- | --- |
| **Three-Part** | `for i := 0; i < n; i++ {}` | Classic loop with increments |
| **While-Like** | `for i < n {}` | Condition-based repetition |
| **Infinite** | `for {}` | Endless loop (needs `break`) |
| **For-Range** | `for i, v := range collection {}` | Iterating arrays, slices, maps |

**Go’s loop structures** are concise yet flexible, relying solely on the `for` keyword to cover all looping needs.

---

## 1.9. Maps in Go

### Introduction

A **map** is a data structure that stores **key-value pairs**. Maps in Go are **unordered collections** and belong to the **associative data type** (hash).

---

### Definition

Maps are defined using the following format:

```go
map[KeyType]ValueType
```

**Key Requirements:**

- Must be a **comparable type** (e.g., booleans, numbers, strings, arrays, pointers, structs, interfaces with comparable values).
- **Cannot** use slices, maps, or functions as keys.

**Value Requirements:**

- No restrictions; values even **can be maps** (nested maps).

**Example:**

```go
package main
import "fmt"

func main() {
    myMap := make(map[int]string)
    myKey := 13
    myMap[myKey] = "thirteen"

    fmt.Println(myMap)        // map[13:thirteen]
    fmt.Println(myMap[myKey]) // thirteen
}
```

---

### Initializing Maps

Maps default to **`nil`** if only declared with `var`.

**Initialization Methods:**

- **Literal:**
  
  ```go
  var sampleMap = map[string]int{"one": 1, "two": 2}
  ```
  
- **Short Declaration:**
  
  ```go
  sampleMap := map[string]int{"three": 3, "four": 4}
  ```
  
- **Using `make`:**
  
  ```go
  sampleMap := make(map[string]int)
  ```
  

---

### Working with nil Maps

A **`nil` map** cannot store data until **initialized**:

```go
var sampleMap map[string]string
sampleMap["key"] = "value" // panic: assignment to entry in nil map
```

**Fix:**

```go
sampleMap = make(map[string]string)
```

---

### Map Functions

- **`len(map)`**: Returns the **number of elements**. `len(nilMap)` returns **0**.

---

### CRUD Operations

1. **Create (Insert)**:
  
  ```go
  sampleMap := map[string]int{"three": 3, "four": 4}
  ```
  
2. **Read (Access)**:
  
  ```go
  value := myMap["name"]
  fmt.Println(value)
  ```
  
3. **Update**:
  
  ```go
  myMap["name"] = "Bob"
  ```
  
4. **Delete**:
  
  ```go
  delete(myMap, "name")
  ```
  

---

### Check for Key Existence

Use the **comma-ok idiom**:

```go
value, exists := myMap["key"]
if exists {
    fmt.Println("Key found:", value)
} else {
    fmt.Println("Key not found")
}
```

---

### Reference Behavior

Maps are **reference types**. Assigning one map to another **makes both point to the same underlying data**.

**Example:**

```go
mapA := map[string]int{"a": 1}
mapB := mapA
mapB["a"] = 42

fmt.Println(mapA["a"]) // Output: 42
```

**To Clone a Map we should iterate over it :**

```go
original := map[string]int{"x": 1, "y": 2}
clone := make(map[string]int)
for k, v := range original {
    clone[k] = v
}
```

---

### Iterating Over a Map

Use **`for-range`**:

```go
myMap := map[string]int{"one": 1, "two": 2}
for key, value := range myMap {
    fmt.Printf("Key: %s, Value: %d\n", key, value)
}
```

**Note:** Maps are **unordered**; iteration **order varies** each run.

---

### Converting Between Strings, Maps, and Slices

Maps can be **converted into slices** by **iterating over elements**:

```go
myMap := map[string]int{"a": 1, "b": 2}
keys := make([]string, 0, len(myMap))
values := make([]int, 0, len(myMap))

for k, v := range myMap {
    keys = append(keys, k)
    values = append(values, v)
}

fmt.Println("Keys:", keys)
fmt.Println("Values:", values)
```

---

## 1.10. Conditional Statements in Go

Go supports **conditional logic** similar to other programming languages, with structures like **`if`**, **`else if`**, **`else`**, and **`switch`**.

---

### Basic if-else Structure

```go
if condition {
   // Do something
} else if condition {
   // Do something
} else {
   // Do something
}
```

**Key Points:**

- Conditions evaluate to **`true`** or **`false`**.
- Operators like `&&`, `||`, `>`, `<`, `<=`, `>=`, `!` can be used to create conditions.

---

### Types of Conditionals

- **Simple `if`**
- **Nested `if-else`**
- **Short variable declaration with `if`**

---

### Simple `if`

```go
if condition {
    // Do something
}
```

**Example:**

```go
package main
import "fmt"

func main() {
    a := 6
    if a > 5 {
        fmt.Println("a is greater than 5")
    }
}
```

---

### Multiple Conditions

```go
package main
import "fmt"

func main() {
    a := 4
    if a > 3 && a < 6 {
        fmt.Println("a is within range")
    }
}
```

---

### if-else Structure

When the `if` condition is false, the `else` block runs.

```go
package main
import "fmt"

func main() {
    a := 1
    b := 2
    if a > b {
        fmt.Println("a is greater than b")
    } else {
        fmt.Println("b is greater than a")
    }
}
```

---

### if-else if Structure

The `else if` clause checks additional conditions after the `if` condition is false.

```go
package main
import "fmt"

func main() {
    age := 29
    if age < 18 {
        fmt.Println("Kid")
    } else if age >= 18 && age < 40 {
        fmt.Println("Young")
    } else {
        fmt.Println("Old")
    }
}
```

---

### Nested Conditions

Conditions can be nested but should be minimized for better code readability.

```go
package main
import "fmt"

func main() {
    a, b, c := 1, 2, 3
    if a > b {
        if a > c {
            fmt.Println("a is the largest")
        }
    } else {
        if b > c {
            fmt.Println("b is the largest")
        } else {
            fmt.Println("c is the largest")
        }
    }
}
```

---

### Short Variable Declaration in `if`

Go allows **variable declaration** directly within the `if` statement.

```go
package main
import "fmt"

func main() {
	if a := 4; a > 5 {
		println("a is greater than 5")
	} else if a == 4 {
		println("a is equal to 4")
		fmt.Printf("a is %d", a)
	} else {
		println("a is less than 5")
		fmt.Printf("a is %d", a)
	}
}
```

**Explanation:**

- The variable `a` is declared and checked within the same statement.
- The variable `a` can be used even in `else if` or `else` body statements.

---

### Switch Statement

The `switch` statement provides **cleaner code** when many conditions must be checked.

```go
switch variable {
case value1:
    // Do something
case value2:
    // Do something
default:
    // Do something
}
```

**Example:**

```go
package main
import "fmt"

func main() {
    switch ch := "b"; ch {
    case "a":
        fmt.Println("a")
    case "b", "c":
        fmt.Println("b or c")
    default:
        fmt.Println("No match")
    }
}
```

**Key Points:**

- Multiple cases can share a code block (e.g., `case "b", "c":`).
- The `default` case runs if no other case matches.

---

### `fallthrough` in `switch`

The `fallthrough` keyword forces execution of the **next case** regardless of its condition.

```go
package main
import "fmt"

func main() {
    var day = 3
    switch day {
    case 1:
        fmt.Println("Monday")
        fallthrough
    case 2:
        fmt.Println("Tuesday")
        fallthrough
    case 3:
        fmt.Println("Wednesday")
        fallthrough
    case 4:
        fmt.Println("Thursday")
    }
}
```

**Explanation:**

- Once the case for day `3` matches, `fallthrough` ensures the **subsequent case** runs **without condition checks**.

---

## 1.11. Defer, Panic, and Recovery in Go

---

### **Defer**

**Definition**  
The `defer` keyword delays the execution of a function until the surrounding function returns. It's commonly used for resource cleanup (e.g., closing files or releasing locks).

**Example:**

```go
package main
import "fmt"

func main() {
    defer fmt.Println("world")
    fmt.Println("hello")
}
```

**Output:**

```
hello
world
```

Explanation: `defer` postpones "world" until the `main` function finishes.

---

**Anonymous Functions with defer**  
You can defer anonymous (inline) functions.

```go
package main
import "fmt"

func main() {
    defer func() { fmt.Println("In inline defer") }()
    fmt.Println("Executed")
}
```

**Output:**

```
Executed
In inline defer
```

Explanation: `defer` runs just before `return`.

---

**Multiple defer Statements**  
Deferred calls are executed in a LIFO (Last In, First Out) order.

```go
package main
import "fmt"

func main() {
    i := 0
    i = 1
    defer fmt.Println(i)
    i = 2
    defer fmt.Println(i)
    i = 3
    defer fmt.Println(i)
}
```

**Output:**

```
3
2
1
```

Explanation: Deferred calls are pushed onto a stack and executed in reverse order.

---

**Parameter Evaluation in defer**  
Parameters for deferred functions are evaluated at the moment of the `defer` statement, not when the deferred function runs.

```go
package main
import "fmt"

func main() {
    i := 1
    defer fmt.Println(i) // i is evaluated here
    i++
    fmt.Println(i)
}
```

**Output:**

```
2
1
```

Explanation: `fmt.Println(i)` in the `defer` statement captures the value `1` immediately.

---

---

### **Panic**

**Definition**  
`panic` is a built-in function that stops normal execution and begins panicking. It's typically used for unexpected errors that shouldn't be ignored.

**panic can occur due to:**

- Runtime errors (e.g., array out-of-bounds).
- Direct invocation by the programmer.

**Syntax:**

```go
panic("some error message")
```

---

**Example of Runtime Panic**

```go
package main
import "fmt"

func main() {
    a := []string{"a", "b"}
    fmt.Println(a[2]) // index out-of-range panic
}
```

**Output:**

```
panic: runtime error: index out of range [2] with length 2
```

Explanation: Accessing `a[2]` causes a panic since the slice has only two elements (index 0 and 1).

---

**Programmer-Initiated Panic**

```go
package main
import "fmt"

func main() {
    a := []string{"a", "b"}
    checkAndPrint(a, 2)
}

func checkAndPrint(a []string, index int) {
    if index >= len(a) {
        panic("Out of bound access for slice")
    }
    fmt.Println(a[index])
}
```

**Output:**

```
panic: Out of bound access for slice
```

Explanation: The `panic` call explicitly stops the program when `index` exceeds the slice bounds.

---

**When to use panic:**

- Critical issues that must halt program execution.
- Incorrect program states that can lead to unpredictable behavior.
- Invalid configurations provided by users.

---

### **Recovery**

**Definition**  
`recover` is a built-in function that can catch a panic and restore normal execution. It's useful to prevent crashes in certain scenarios.

**Syntax:**

```go
recover() // returns an interface{} type
```

**Usage:**

- `recover` only works inside deferred functions.
- If called outside `defer`, it returns `nil`.

---

**Example of Recovery**

```go
package main
import "fmt"

func main() {
    a := []string{"a", "b"}
    checkAndPrint(a, 2)
    fmt.Println("Exiting normally")
}

func checkAndPrint(a []string, index int) {
    defer handleOutOfBounds()
    if index >= len(a) {
        panic("Out of bound access for slice")
    }
    fmt.Println(a[index])
}

func handleOutOfBounds() {
    if r := recover(); r != nil {
        fmt.Println("Recovering from panic:", r)
    }
}
```

**Output:**

```
Recovering from panic: Out of bound access for slice
Exiting normally
```

Explanation:

- `panic` is triggered due to an out-of-bounds index.
- The `recover` function catches the panic, preventing program termination.

---

---

### **Printing Stack Trace After Recovery**

**Stack Trace**  
A stack trace shows the sequence of function calls leading to a panic. It helps with debugging.

**Example:**

```go
package main
import (
    "fmt"
    "runtime/debug"
)

func main() {
    a := []string{"a", "b"}
    checkAndPrint(a, 2)
    fmt.Println("Exiting normally")
}

func checkAndPrint(a []string, index int) {
    defer handleOutOfBounds()
    if index >= len(a) {
        panic("Out of bound access for slice")
    }
    fmt.Println(a[index])
}

func handleOutOfBounds() {
    if r := recover(); r != nil {
        fmt.Println("Recovering from panic:", r)
        debug.PrintStack()
    }
}
```

**Output:**

```
Recovering from panic: Out of bound access for slice
Stack Trace:
goroutine 1 [running]:
runtime/debug.Stack(0x0, 0x0, 0x0)
    runtime/debug/stack.go:24 +0x9d
runtime/debug.PrintStack()
    runtime/debug/stack.go:16 +0x22
main.handleOutOfBounds()
    main.go:27 +0x10f
```

Explanation:

- `debug.PrintStack()` prints the function call history that led to the panic.

---

---

### **Key Insights**

1. **Defer**: Executes functions in LIFO order, ideal for cleanup tasks.
2. **Panic**: Stops program execution during critical failures.
3. **Recover**: Catches a panic to restore normal execution, useful in robust applications.

Proper use of these features helps build safer, more maintainable Go programs.

## 1.12. String Formatting in Go

---

### **Formatting with Printf and Sprintf**

Go provides powerful string formatting capabilities through the `Printf` and `Sprintf` functions from the `fmt` package.

- **`Printf`**: Formats and prints the result to standard output.
- **`Sprintf`**: Formats and returns the result as a string without printing it.

**Example:**

```go
package main
import "fmt"

func main() {
    x := fmt.Sprintf("age %s is %d years", "Javad", 30)
    fmt.Println(x)
}
```

**Output:**

```
age Javad is 30 years
```

**Explanation:**

- `Printf` is used for direct output.
- `Sprintf` stores the formatted string in a variable.

---

### **Formatting Slices**

**Verbs for Slices:**

- **`%v`**: Default format.
- **`%#v`**: Go-syntax representation.
- **`%T`**: Type of the variable.

**Example:**

```go
fmt.Printf("%v\n", []int64{0, 1})    // [0 1]
fmt.Printf("%#v\n", []int64{0, 1})   // []int64{0, 1}
fmt.Printf("%T\n", []int64{0, 1})    // []int64
```

---

### **Formatting Integers**

**Common Verbs:**

- **`%d`**: Decimal (base 10).
- **`%+d`**: Decimal with a plus sign if positive.
- **`%b`**: Binary.
- **`%o`**: Octal.
- **`%x`/`%X`**: Hexadecimal (lower/upper case).
- **`%#x`**: Hex with `0x` prefix.
- **`%04d`**: Zero-padded decimal.

**Example:**

```go
package main
import "fmt"

func main() {
    num := 15
    fmt.Printf("%d\n", num)    // 15
    fmt.Printf("%+d\n", num)   // +15
    fmt.Printf("%b\n", num)    // 1111 (binary)
    fmt.Printf("%o\n", num)    // 17 (octal)
    fmt.Printf("%x\n", num)    // f (hex, lowercase)
    fmt.Printf("%#x\n", num)   // 0xf (hex with prefix)
    fmt.Printf("%04d\n", num)  // 0015 (zero-padded)
}
```

---

### **Formatting Floating-Point Numbers**

**Verbs:**

- **`%f`**: Decimal format with six digits after the decimal.
- **`%.2f`**: Two decimal places.
- **`%e`**: Scientific notation.
- **`%g`**: Flexible (scientific or decimal depending on the value).
- **`%8.2f`**: Minimum width of 8 characters with 2 decimal places.

**Example:**

```go
package main
import "fmt"

func main() {
    num := 123.456
    fmt.Printf("%f\n", num)    // 123.456000
    fmt.Printf("%.2f\n", num)  // 123.46
    fmt.Printf("%e\n", num)    // 1.234560e+02
    fmt.Printf("%g\n", num)    // 123.456
    fmt.Printf("%8.2f\n", num) //    123.46 (width 8, right-aligned)
    fmt.Printf("%08.2f\n", num) // 00123.46 (zero-padded)
}
```

---

### **Formatting Characters**

**Verbs:**

- **`%c`**: Character.
- **`%q`**: Quoted character.
- **`%U`**: Unicode code point.
- **`%#U`**: Unicode code point with character.

**Example:**

```go
package main
import "fmt"

func main() {
    ch := 'A'
    fmt.Printf("%c\n", ch)    // A
    fmt.Printf("%q\n", ch)    // 'A'
    fmt.Printf("%U\n", ch)    // U+0041
    fmt.Printf("%#U\n", ch)   // U+0041 'A'
}
```

---

### **Formatting Strings and Byte Slices**

**Verbs:**

- **`%s`**: Simple string.
- **`%q`**: Quoted string.
- **`%x`**: Hexadecimal string.
- **`% x`**: Hexadecimal with spaces.

**Example:**

```go
package main
import "fmt"

func main() {
    str := "gophers"
    fmt.Printf("%s\n", str)    // gophers
    fmt.Printf("%q\n", str)    // "gophers"
    fmt.Printf("%x\n", str)    // 676f7068657273
    fmt.Printf("% x\n", str)   // 67 6f 70 68 65 72 73
    fmt.Printf("%8s\n", str)   //   gophers (right-aligned, width 8)
    fmt.Printf("%-8s\n", str)  // gophers   (left-aligned, width 8)
}
```

---

### **Formatting Booleans**

**Verb:**

- **`%t`**: Outputs `true` or `false`.

**Example:**

```go
fmt.Printf("%t\n", true)  // true
fmt.Printf("%t\n", false) // false
```

---

### **Formatting Pointers**

**Verb:**

- **`%p`**: Memory address (hexadecimal with `0x` prefix).

**Example:**

```go
package main
import "fmt"

func main() {
    var x int
    fmt.Printf("%p\n", &x) // e.g., 0xc0000120f0
}
```

---

### **Special Characters in Strings**

**Special Characters:**

- **`\a`**: Bell sound.
- **`\b`**: Backspace.
- **`\\`**: Backslash.
- **`\t`**: Horizontal tab.
- **`\n`**: Newline.
- **`\f`**: Form feed.
- **`\r`**: Carriage return.
- **`\v`**: Vertical tab.
- **`%%`**: Percent sign.

**Example:**

```go
package main
import "fmt"

func main() {
    fmt.Printf("Line1\nLine2\n")  // Newline
    fmt.Printf("Tab\tSeparated\n") // Tab
    fmt.Printf("100%% Complete\n") // Percent sign
}
```

---

### **The `strings` Package**

The `strings` package provides many useful string manipulation methods.

---

**`Contains` and `ContainsAny`**

- **`Contains`**: Checks if a substring exists.
- **`ContainsAny`**: Checks if any character of a string is present.

```go
package main
import (
    "fmt"
    "strings"
)

func main() {
    text := "Go will make you love programming"
    fmt.Println(strings.Contains(text, "Golang"))   // false
    fmt.Println(strings.ContainsAny(text, "Golang")) // true
}
```

---

**`Count`**  
Counts the occurrences of a substring (case-sensitive).

```go
package main
import (
    "fmt"
    "strings"
)

func main() {
    text := "Golang go Go will make you love programming"
    fmt.Println(strings.Count(text, "Go")) // 2
}
```

---

**`Index` and `LastIndex`**  
Finds the index of the first or last occurrence of a substring.

```go
package main
import (
    "fmt"
    "strings"
)

func main() {
    text := "Go will make you love programming"
    fmt.Println(strings.Index(text, "o"))    // 1 (first occurrence)
    fmt.Println(strings.LastIndex(text, "o")) // 46 (last occurrence)
}
```

---

**`Split`**  
Splits a string into a slice based on a delimiter.

```go
package main
import (
    "fmt"
    "strings"
)

func main() {
    text := "Go will make you love programming"
    words := strings.Split(text, " ")
    for _, word := range words {
        fmt.Println(word)
    }
}
```

---

**`Join`**  
Joins a slice of strings into a single string with a separator.

```go
package main
import (
    "fmt"
    "strings"
)

func main() {
    words := []string{"Go", "is", "fun"}
    result := strings.Join(words, " ")
    fmt.Println(result) // Go is fun
}
```

---

**`HasPrefix` and `HasSuffix`**

- **`HasPrefix`**: Checks if a string starts with a given prefix.
- **`HasSuffix`**: Checks if a string ends with a given suffix.

```go
package main
import (
    "fmt"
    "strings"
)

func main() {
    text := "Go will make you love programming"
    fmt.Println(strings.HasPrefix(text, "Go")) // true
    fmt.Println(strings.HasSuffix(text, "ing")) // true
}
```

---

# GO MECHANISM

# CONCURRENCY

# ADVANCED

### Function Receivers in Go

In Go, you can define methods on types. The receiver appears in its own parameter list between the `func` keyword and the method name.

**Example:**

```go
package main

import "fmt"

// Define a type
type Rectangle struct {
    Width, Height int
}

// Define a method on the Rectangle type
func (r Rectangle) Area() int {
    return r.Width * r.Height
}

func main() {
    rect := Rectangle{Width: 10, Height: 5}
    fmt.Println("Area:", rect.Area()) // Output: Area: 50
}
```

In this example:

- `Rectangle` is a struct type with `Width` and `Height` fields.
- `Area` is a method with `Rectangle` as its receiver, allowing any `Rectangle` instance to call the `Area` method.

**Pointer Receivers:**

Methods can also have pointer receivers. This is useful when the method needs to modify the receiver or when avoiding copying the receiver is desired.

```go
func (r *Rectangle) Scale(factor int) {
    r.Width *= factor
    r.Height *= factor
}
```

Using a pointer receiver allows the method to modify the original `Rectangle` instance.

## Genrics in Go

# TEST

# DESGIN PATTERNS

# ALGORITHM AND DATA STURCTURE

# SOFTWARE ARCHITECTURE

# BLOCKCHAIN
