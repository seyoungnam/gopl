# 04. Composite Types

## 4.3. Maps

A map is a reference to a hash table. The hash table is an unordered collection of key/value pairs in which all the keys are distinct, and the value associated with a given key can be retrieved, updated, or removed.

The key type must be comparable using ==.

Three ways to create a map.

* use the built-in function `make`
    ```
    ages := make(map[string]int)
    ```
* use a `map literal` : 
    ```
    ages := map[string]int{
        "alice":    31,
        "charlie":  34,
    }
    ```
* an alternative expression
    ```
    ages := map[string]int{}
    ```

The way to access the value is `ages["alice"]`.
And the way to remove a key/value pair is using the built-in function `delete`:
```
deletes(ages, "alice") // remove element ages["alice"]
```