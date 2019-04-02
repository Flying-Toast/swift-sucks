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
What the hell is this `case` hullabaloo?! Here is one of the **many** places that Swift pointlessly overloads a keyword, in a way that makes no sense, has no correlation to other uses of the keyword, and doesn't help the programmer *or* the compiler.

# No increment/deincrement operators

```Swift
var a = 12
a++ //NOPE!
```
These actually *were* implemented, but some really smart people decided that
>"These operators increase the burden to learn Swift as a first programming language - or any other case where you don't already know these operators from a different language."

And so they were removed in Swift 3.0.

Admittedly, it is actually does make sense why they would do this. After all, adding 1 to any given number is a hugely complex mathematical concept, which one could never expect any beginner to understand.

# Bloated error messages
(alright, this is actually a problem with the sucky compiler implementation, and not language itself, but still.)

Lets try compiling this code:
```Swift
printz("Swift Sucks")
```
annnd...
```
main.swift:1:1: error: use of unresolved identifier 'printz'                                     
printz("Swift Sucks")                                                                         
^~~~~~                                                                                        
Swift.print:1:13: note: did you mean 'print'?                                                 
public func print(_ items: Any..., separator: String = default, terminator: String = default)
            ^                                                                                 
Swift.print:1:13: note: did you mean 'print'?                                                 
public func print<Target>(_ items: Any..., separator: String = default, terminator: String = d
efault, to output: inout Target) where Target : TextOutputStream                              
            ^                                                                                 
Swift._rint:1:13: note: did you mean '_rint'?                                                 
public func _rint(_ x: Float) -> Float                                                        
            ^                                                                                 
Swift._rint:1:13: note: did you mean '_rint'?                                                 
public func _rint(_ x: Double) -> Double     
```

Holy crap! What's all this?! Well, it looks like Swift has decided to be helpful and show us every single function that is even remotely similar to "printz". Well, thanks for the effort, Swift, but I'd rather you just shut up and tell me what the problem is, and not try to fix it yourself.

`error: use of unresolved identifier 'sendMissileAlertTest()'. Did you mean 'sendATotallyRealDefinitelyNotADrillActualMissileAlert()'?`

Also, whats up with all the errors printing twice? How is that helping anything?


# error: multi-line string literal content must begin on a new line
```Swift
let swiftSucks = """I Hate
Swift"""
```
This gives us the following wonderful error:
```
main.swift:1:19: error: multi-line string literal content must begin on a new line
let swiftSucks = """I Hate
                  ^
main.swift:2:6: error: multi-line string literal closing delimiter must begin on a new line
Swift"""
     ^
```
(Here's that thing again with the double error messages. Weird.)

Swift requires that multi-line strings be declared like this:
```Swift
let swiftIsBad = """
I Hate
Swift
"""
```

But why the arbitrary restriction? All it does is make the code harder to read.
