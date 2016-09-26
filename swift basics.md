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

## Dictionaries:
```swift
let ages = ["Daniel": 24, "Christine": 23] // internal types can be inferred (optionally: [String, Int])

// Setters/getters
ages["Cameron"] = 24
let nitishAge: Int? = ages["Nitish"] // use optional type because here his age is `nil` in the original dict

// Type is required even for empty dictionaries
let emptyDict: [Any, Any] = [:]
```

Null value: `nil`

## String interpolation
```swift
let name = "Daniel"
let hello = "Hello \(Daniel)" // no type needed because can be inferred
```

## Switch statement
These are more similar to matchers like in scala/ocaml
```swift
let userName = "Daniel"
let isValid = false

// can match tuples:
switch (userName, isValid) {
case ("admin", true):
    // do stuff
// this catches all cases so this switch doesn't require a default case
// `_` ignores the first value so its essentially a wildcard
// creates new variable called valid (and also acts as wildcard)
case (_, let valid):
    // do stuff
}
```

## For in loop
### Ranges
Can use 3 dots to include end of range:
```swift
for i in 1...5 {
    print(i) // 1,2,3,4,5
}
```

More classically, we don't want to include the final term so we can use `..<`:
```swift
for i in 1..<5 {
    print(i) // 1,2,3,4
}
```

### Over Dictionaries
```swift
// can create tuple from each key/value pair:
for (name, age) in ages {
    print("\(name)'s age is \(age)")
}
```


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

Type definition - ((<parameter types>) -> <return type>)

## Default values:
```swift
func debounce(f: (Any?) -> Any?, waitTime: Int = 100) -> (Any?) -> Any? {
    // stuff
}
```

## Generic type params
Generic type params: the name is derived by the angle bracket syntax after the function name
Error is thrown when I don't provide a body, so we can ensure that the type system works
```swift
func filter<Element>(values: [Element], filter: (Element) -> Bool) -> [Element] {
    return []
}
```

## Closures
Have weird syntax (most similar to closures in Ruby, basically lambdas)
```swift
// Using same filter function as above
// full syntax
filter(values: [1,3], {number in
    if number %
})

## Pass by ref params
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

# Classes
`self.` is not required when accessing instance variables

# Protocols
Basically interfaces, set up a contract for how a Struct or Class will act
```swift
protocol Image {
    // indicates that this field will only be gettable but not settable from public interface
    var width: Int { get }
    var height: Int { get }
    var source: String { get }

    // allows method to mutate fields on current instance, will throw error if called on constant (not required for classes)
    mutating func resize(width: Int, height: Int)
}
```

# Extensions
Basically like prototypes in javascript
* Allows extending Class after creation, (all instances will get the extension)
* Extensions can also implement protocols
* can be conditionally extended (arguably the most compelling reason to use over regular inheritance)

# `where` clause
Acts as a dynamic filter for expressions
```swift
let first = 4
let second = 3
switch (first, second) {
case (x, y) where x == y:
    print("x and y are equal")
case (x, y) where x > y:
    print("x is greater than y")
default:
    print("Didn't match")
}

class List<T> {}
// we know that sort will always work because the values in the List must inherit from Comparable
extension List where T: Comparable {
    mutating func sort() {}
}
```
