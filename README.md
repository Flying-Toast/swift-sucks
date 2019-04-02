<h1 align="center">Swift Sucks.</h1>
Swift is a terrible programming language. If you didn't already know that, here is some proof:

# Stupid `enum` Syntax
```Swift
enum SwiftIsBad {
	case swift
	case is
	case bad
}
```
What the hell is this `case` hullabaloo?! Here is one of the **many** places that Swift pointlessly overloads a keyword, in a way that makes no sense, has no correlation to other uses of the keyword, and doesn't help the programmer *or* the compiler.

# No Increment/Deincrement Operators

```Swift
var a = 12
assert(++a == 13) //NOPE!
```
These actually *were* implemented, but some really smart people decided that
>"These operators increase the burden to learn Swift as a first programming language - or any other case where you don't already know these operators from a different language."

And so they were removed in Swift 3.0.

Admittedly, it is actually does make sense why they would do this. After all, adding 1 to any given number is a hugely complex mathematical concept, which one could never expect any beginner to understand.

# Bloated Error Messages
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

Also, what's up with all the errors printing twice? How is that helping anything?

___

`error: use of unresolved identifier 'testMissileAlert()'. Did you mean 'sendATotallyRealDefinitelyNotADrillActualMissileAlert()'?`


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
let swiftSucks = """
I Hate
Swift
"""
```

But why the arbitrary restriction? All it does is make the code harder to read.

# Underscores Galore
_ Imagine _ having _ to _ put _ an _ underscore _ before _ every _ word _ you _ type. _ Oh _ Wait. _ You _ don't _ have _ to _ imagine. _ You _ can _ just _ write _ some _ code _ in _ Swift.

For some unfathomably stupid reason, function parameters in Swift default to being "named parameters".  
"Named parameters" roughly translated from Swift-speak to English means "now, every single time you look up a function in the documentation, in addition to remembering the *name* of the function, you get the pleasure of having to remember and additional identifier for every parameter the function takes!".

In all honesty though, there are some cases where it actually does make sense to use named parameters. Python sure understands that. Python allows you to optionally use named parameters.  
Notice the distinction: Python allows you to use named parameters if/when you want to, whereas Swift SHOVES NAMED PARAMETERS DOWN YOUR THROAT ALL THE TIME, NO MATTER WHAT.

If you want to disable named parameters, as any sane person would, you have to prepend "_ " to each parameter. This quickly clutters the code, making it much harder to read.

# No Regex
Swift: What's a regex?  
Smart programmers that don't use Swift: 🖕

# No Windows Support
Swift: What's Windows?  
Smart programmers that don't use Swift: 🖕

# Meaningless Warnings
Swift seems to think that in addition to actual warnings, compiler warnings should be used to tell the programmer about absolutely pointless things.
```Swift
for i in 0 ... 10 {
	print("Swift sucks.")
}
```
Gives the warning:
```
main.swift:1:5: warning: immutable value 'i' was never used; consider replacing with '_' or removing it
for i in 0 ... 10 {
    ^
```
This is equivalent to a police officer pulling you over to tell you that your shoes are untied.

Shut up, Swift! Do you really think that anyone cares about that? If I wanted someone to review my code, I would have posted it on codereview.stackexchange.com.

___

Let's take a look at what a *good* warning looks like. Unfortunately, we can't do this in Swift. To demonstrate a *good* compiler warning, we are going to need a *good* programming language. Let's use D.

```D
int dIsWayBetterThanSwift() {
	return 8;
	return 7; //This is an oopsie
}

void main() {
	int result = dIsWayBetterThanSwift();
}
```
This shows the following warning at compilation:
```
main.d(3): Warning: statement is not reachable
```
Now **that** is a legitimate warning. We made a legitimate oopsie, and the D compiler gave us a kind notification about it.

C'mon Swift - is it really that hard to only give useful warnings?
