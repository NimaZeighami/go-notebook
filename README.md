
# GO NOTEBOOK

## BASICS OF GO

### INTRODUCTION 
Go is a statically typed, compiled programming language designed for simplicity and efficiency. Its syntax is clean and concise, making it easy to read and write.

### 1.1 Go Code (File) Structure 
(Required) Every Go program starts with a `main` package. (main package is special package that creates executable file but other pakage  names doesn't)
(Optional) After package name  we can have imports (usually we have multiple imports but we can have no imports ! and we have 2 type of import : 1. Single Import  2. Multiple Import) 
(Optional) If we have some other functions or some constant or variables we can write it between imports and main function.
(Required) At the End we should have a main function that is entry point of every go program. 
**Example:**

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

In this example:

- `package main`: Defines the package name. Every Go program starts with a `main` package.
- `import "fmt"`: Imports the `fmt` package, which contains functions for formatted I/O.
- `func main() { ... }`: The `main` function is the entry point of the program.
- `fmt.Println("Hello, World!")`: Prints the string to the console.

### Enums in Go

Go doesn't have a traditional `enum` keyword. Instead, you can use `iota` to create enumerated constants. `iota` is a predeclared identifier representing successive untyped integer constants.

**Example:**

```go
package main

import "fmt"

type Size uint8

const (
    Small Size = iota
    Medium
    Large
    ExtraLarge
)

func main() {
    fmt.Println(Small, Medium, Large, ExtraLarge) // Output: 0 1 2 3
}
```

Here, `iota` starts at 0 and increments by 1 for each subsequent constant.

### Maps in Go

Maps are Go's built-in associative data type (hash/dictionary) that store key-value pairs.

**Syntax:**

```go
mapName := make(map[keyType]valueType)
```

**Example:**

```go
package main

import "fmt"

func main() {
    // Initializing a map
    personAge := map[string]int{
        "Ali":   20,
        "Reza":  30,
        "Mehdi": 40,
    }

    // Adding a new key-value pair
    personAge["Sara"] = 25

    // Deleting a key-value pair
    delete(personAge, "Mehdi")

    // Accessing a value
    age := personAge["Ali"]
    fmt.Println("Ali's age:", age)

    // Iterating over the map
    for name, age := range personAge {
        fmt.Printf("%s is %d years old.\n", name, age)
    }
}
```

**Output:**

```
Ali's age: 20
Ali is 20 years old.
Reza is 30 years old.
Sara is 25 years old.
```

**Notes:**

- To check if a key exists:

  ```go
  age, exists := personAge["Ali"]
  if exists {
      fmt.Println("Ali's age:", age)
  } else {
      fmt.Println("Ali not found.")
  }
  ```

- Maps are reference types. If you pass a map to a function, any changes made to the map within the function will affect the original map.

### Arrays and Slices in Go

**Arrays** have a fixed size, while **slices** are dynamically-sized, flexible views into arrays.

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

### Exported and Unexported Identifiers in Go

In Go, the visibility of identifiers (variables, types, functions, etc.) is determined by the case of the first letter:

- **Exported** (public) identifiers start with an uppercase letter and are accessible from other packages.
- **Unexported** (private) identifiers start with a lowercase letter and are not accessible from other packages.

**Example:**

```go
package mypackage

// Exported function
func ExportedFunction() {
    // ...
}

// Unexported function
func unexportedFunction() {
    // ...
}
```

In this example, `ExportedFunction` can be accessed from other packages, while `unexportedFunction` cannot.

### For Loop in Go

Go has only one looping construct: the `for` loop. It can be used in various forms:

**1. Traditional For Loop:**

```go
for initialization; condition; post {
    // code to execute
}
```

**Example:**

```go
for i := 0; i < 5; i++ {
    fmt.Println(i)
}
```

**2. While Loop:**

```go
for condition {
    // code to execute
}
```

**Example:**

```go
i := 0
for i < 5 {
    fmt.Println(i)
    i++
}
```

**3. Infinite Loop:**

```go
for {
    // code to execute
}
```

**Example:**

```go
for {
    fmt.Println("Infinite loop")
}
```

**4. Range Loop (for collections):**

```go
for index, value := range collection {
    // code to execute
}
```

**Example:**

```go
slice := []string{"a", "b", "c"}
for index, value := range slice {
    fmt.Printf("Index: %d, Value: %s\n", index, value)
}
```










### Removing Elements from a Slice in Go
In Go, removing an element from a slice requires creating a new slice that excludes the unwanted element, as Go does not provide a built-in function for this purpose.

**Example:**

```go
package main

import "fmt"

func main() {
    // Initial slice
    numbers := []int{1, 2, 3, 4, 5}

    // Index of the element to remove
    index := 2 // Removing the element at index 2 (value 3)

    // Removing the element
    numbers = append(numbers[:index], numbers[index+1:]...)

    fmt.Println(numbers) // Output: [1 2 4 5]
}
```

In this example:

- `numbers[:index]` retrieves the elements before the specified index.
- `numbers[index+1:]` retrieves the elements after the specified index.
- `append` combines these two slices, effectively removing the element at the specified index.

**Note:** This method maintains the order of elements. If preserving order is not necessary, you can replace the element to be removed with the last element and then truncate the slice:

```go
numbers[index] = numbers[len(numbers)-1]
numbers = numbers[:len(numbers)-1]
```

This approach is more efficient as it reduces the number of elements that need to be shifted. citeturn0search0

### Exported and Unexported Identifiers in Go

In Go, identifiers (such as variables, functions, and types) that begin with an uppercase letter are **exported**, meaning they are accessible from other packages. Identifiers starting with a lowercase letter are **unexported** and accessible only within the same package.

**Example:**

```go
package mypackage

// Exported function
func ExportedFunction() {
    // ...
}

// unexported function
func unexportedFunction() {
    // ...
}
```

In this example:

- `ExportedFunction` is accessible from other packages.
- `unexportedFunction` is accessible only within the `mypackage` package.

### For Loop in Go

The `for` loop is the only looping construct in Go, but it can be used in various forms.

**Basic Syntax:**

```go
for initialization; condition; post {
    // code to be executed
}
```

**Examples:**

1. **Traditional For Loop:**

   ```go
   for i := 0; i < 5; i++ {
       fmt.Println(i)
   }
   ```

   This loop prints numbers 0 through 4.

2. **While Loop:**

   ```go
   i := 0
   for i < 5 {
       fmt.Println(i)
       i++
   }
   ```

   This loop functions like a traditional `while` loop.

3. **Infinite Loop:**

   ```go
   for {
       // infinite loop
   }
   ```

   This loop runs indefinitely until a `break` statement is encountered.

4. **Range Loop:**

   Used for iterating over arrays, slices, maps, or strings.

   ```go
   // Iterating over a slice
   numbers := []int{1, 2, 3, 4, 5}
   for index, value := range numbers {
       fmt.Printf("Index: %d, Value: %d\n", index, value)
   }

   // Iterating over a map
   personAge := map[string]int{"Alice": 25, "Bob": 30}
   for name, age := range personAge {
       fmt.Printf("%s is %d years old.\n", name, age)
   }
   ```

   In these examples:

   - For slices and arrays, `range` provides both the index and value.
   - For maps, `range` provides the key and value.

**Note:** If you only need the value, you can use the blank identifier `_` for the index:

```go
for _, value := range numbers {
    fmt.Println(value)
}
```

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

### Pointers in Go

Pointers hold the memory address of a value. They are useful for sharing data between functions and for modifying variables in place.

**Example:**

```go
package main

import "fmt"

func main() {
    x := 10
    fmt.Println("Before:", x) // Output: Before: 10

    // Pass the address of x to the function
    increment(&x)

    fmt.Println("After:", x) // Output: After: 11
}

// Function that takes a pointer to an int
func increment(num *int) {
    *num++
}
```

In this example:

- `&x` returns the memory address of `x`.
- `*num` dereferences the pointer to access the value at that address.

**Key Points:**

- The zero value of a pointer is `nil`.
- Pointers can be used to share data between functions without copying.
- Use caution with pointers to avoid dereferencing `nil` or unintended modifications.

### Switch Statements in Go

The `switch` statement provides an efficient way to dispatch execution to different branches based on the value of an expression.

**Example:**

```go
package main

import "fmt"

func main() {
    day := "Tuesday"

    switch day {
    case "Monday":
        fmt.Println("Start of the work week.")
    case "Tuesday":
        fmt.Println("Second day of the work week.")
    default:
        fmt.Println("Another day.")
    }
}
```

**Key Points:**

- No need for explicit `break` statements; Go automatically breaks after each case.
- Multiple expressions can be evaluated in a single `case` by separating them with commas.
- A `switch` without an expression is equivalent to `switch true`, allowing for more complex conditions.






