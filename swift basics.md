# Variables/constants

`let/var` -
Unlike, in ES6, let is used for constants and var for variables.
Declaration is done like so:
```swift
let x: String = 'Hi' // notice no semicolons ;)
var y: String = 'world'
```
Basic types:
1. Bool
1. Int
1. Double
1. String
1. Array, demarcated as: `[<Other primitive>]`
1. Dictionary, noted as: `[<Key type>, <value type>]`
1. Any (matches any type), AnyObject (matches any class instance)

Types aren't required, because Swift can often infer them (especially for constants)

Optional types:
```swift
let x: Int? = Int('4') // if 4 wasn't a string then it would be nil
```

Null value: `nil`


# Functions
Can have local and external param names:
```swift
func sayHi(to personName: String) {
    // from within the function, only personName is available
    print("Hi \(personName)!")
}

// outside only to is available
sayHi(to: 'Daniel')
```
With return value:
```swift
func sum(a: Int, b: Int) -> Int {
    return a + b
}
```
Params are passed by value and constant, therefore you can't reassign to params
Params can be passed by reference though:
```swift
func swap(a: inout Int, b: inout Int) {
    let tempA = a
    a = b
    b = tempA
}

var x: Int = 4
var y: Int = 5

swap(a: &x, b: &y)
```
Preventing the need to name params externally:
```swift
func sum(_ a: Int, _ b: Int) -> Int {
    return a + b
}

sum(1, 2)
```
