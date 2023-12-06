# 04. Composite Types

## 4.3. Maps

A map is a reference to a hash table. The hash table is an unordered collection of key/value pairs in which all the keys are distinct, and the value associated with a given key can be retrieved, updated, or removed.

The key type must be comparable using ==.

Three ways to create a map.

* use the built-in function `make`
    ```go
    ages := make(map[string]int)
    ```
* use a `map literal` : 
    ```go
    ages := map[string]int{
        "alice":    31,
        "charlie":  34,
    }
    ```
* an alternative expression
    ```go
    ages := map[string]int{}
    ```

The way to access the value is `ages["alice"]`.
And the way to remove a key/value pair is using the built-in function `delete`:
```go
deletes(ages, "alice") // remove element ages["alice"]
```

A map lookup using a key that isn't present returns the zero value for its type:
```go
ages["bob"] = ages["bob"] + 1 // 1
```

A map element is not a variable, thus we cannot take its address:
```go
_ = &ages["bob"] // compile error: cannot take address of map element
```

To enumerate all the key/value pairs in the map, use a range-based for loop. The order is random:
```go
for name, age := range ages {
    fmt.Printf("%s\t%d\n", name, age)
}
```

To enumerate the key/value pairs in order, use `sort.Strings` function:
```go
import "sort"

var names []string
for name := range ages {
    names = append(names, name)
}
sort.Strings(names)
for _, name := range names {
    //
}
```

The zero value for a map type is `nil`:
```go
var ages map[string]int
fmt.Println(ages == nil)    // "true"
fmt.Println(len(ages) == 0) // "true"
```

To know whether the element was really there or not:
```go
if age, ok := ages["bob"]; !ok { /* ... */}
```

Go does not provide a `set` type, but since the keys of a map are distinct, a map can serve this purpose.

