# swift-sucks
Specific examples of swift sucking even more than usual.

# Stupid enum syntax
```Swift
enum SwiftIsBad {
	case swift
	case is
	case bad
}
```
What the hell is this `case` hullabaloo?! Here is one of the **many** places that Swift pointlessly overloads a keyword, in a way that makes no sense, has no correlation to other uses of the keyword, and doesn't help the human *or* the compiler.

# No increment/deincrement operators

```Swift
var a = 12
a++ //NOPE!
```
These actually *were* implemented, but some really smart people decided that
>"These operators increase the burden to learn Swift as a first programming language - or any other case where you don't already know these operators from a different language."

And so they were removed in Swift 3.0.

Admittedly, it is actually does make sense why they would do this. After all, adding 1 to any given number is a hugely complex mathematical concept, which one could never expect any beginner to understand.
