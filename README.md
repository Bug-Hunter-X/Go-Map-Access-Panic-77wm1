# Go Map Access Panic

This repository demonstrates a common error in Go: panicking when accessing a nil map.

## The Bug

In Go, attempting to access a map that hasn't been initialized (i.e., is `nil`) will cause a runtime panic. This is because the program tries to dereference a nil pointer.

```go
package main

import "fmt"

func main() {
    var m map[string]int
    m["a"] = 1 // This will panic if m is nil
    fmt.Println(m["a"])
}
```

## The Solution

The best solution is to check if the map is `nil` before accessing it.

```go
package main

import "fmt"

func main() {
    var m map[string]int
    if m == nil {
        m = make(map[string]int)
    }
    m["a"] = 1
    fmt.Println(m["a"])
}
```

This approach ensures that the map is initialized before any attempts to read or write its values.