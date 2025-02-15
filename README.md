
# GO NOTEBOOK

## BASICS OF GO

### INTRODUCTION 
Go is a statically typed, compiled programming language designed for simplicity and efficiency. Its syntax is clean and concise, making it easy to read and write.

### Go Syntax

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





