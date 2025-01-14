---

title: Reverse a String in Swift
layout: default
last-modified: 2020-05-02
featured-image:
tags: [swift, reverse-a-string]
authors:
  - martyav

---

Welcome to the [Reverse String](https://sampleprograms.io/projects/reverse-string) in [Swift](https://sampleprograms.io/languages/swift) page! Here, you'll find the source code for this program as well as a description of how the program works.

## Current Solution

{% raw %}

```swift
import Foundation

guard CommandLine.argc > 1 else {
    exit(0)
}

let usersString = CommandLine.arguments[1]
let reversedCollection = usersString.reversed()
let reversedString = String(reversedCollection)

print(reversedString)
```

{% endraw %}

[Reverse String](https://sampleprograms.io/projects/reverse-string) in [Swift](https://sampleprograms.io/languages/swift) was written by:

- Marty A/V

If you see anything you'd like to change or update, [please consider contributing](https://github.com/TheRenegadeCoder/sample-programs).

**Note**: The solution shown above is the current solution in the Sample Programs repository as of Aug 10 2018 23:25:53. The solution was first committed on May 10 2018 10:37:34. As a result, documentation below may be outdated.

## How to Implement the Solution

At long last, let's take a look at the solution to Reverse a String in Swift:

```swift
import Foundation
guard CommandLine.argc > 1 else {
  exit(0)
}

let usersString = CommandLine.arguments[1]
let reversedCollection = usersString.reversed()
let reversedString = String(reversedCollection)
print(reversedString)
```

As we can see, reversing a string in Swift is pretty short and sweet. At this
point, let's dig into the code a bit.

### Foundation

On line 1 of our sample code, we import [Foundation][1]:

```swift
import Foundation
```

Foundation is a framework that contains many basic data types. This framework
also bridges between Swift types, such as String, and Objective-C types, such
as [NSString][2]. When you import almost any of Apple's Swift frameworks, you are
implicitly importing Foundation along with them.

### Guard

The guard statement on line 3 is one of Swift's many syntax features which favor
safety and human readability:

```swift
guard CommandLine.argc > 1 else {
  exit(0)
}
```

A [guard statement][3] is a conditional that only fires off if something isn't true.
This is good for highlighting error conditions, and prevents code from becoming
littered with nested if-else statements. It is especially powerful when dealing
with Swift's Optionals.

### Commandline

`Commandline.arguments` is a built-in way to access user input:

```swift
let usersString = CommandLine.arguments[1]
```

Because `Commandline.arguments` is a String array, not an Optional, we check its
length, rather than look for nil, in order to see if the user has passed us any
input. In Swift, only Optionals can contain nil.

Furthermore, `Commandline.arguments` is always initialized with at least one thing
inside it: the path of the particular file the code is stored in. Therefore, to
access user input, we check if the array contains more than one String. Then we
call the String at the second index; the first index will always contain the path.

Finally, Commandline has a special property, .argc, which allows us to know how
many Strings are inside Commandline.arguments. We could also call .length on
Commandline.arguments to access this information. This is the usual way we access
the number of things in an array, but here we use .argc to highlight a unique
feature of working with Commandline.

### String

When we reverse a String in many languages, we may opt for the manual way, by
looping over each character. Instead, we can reverse the string directly through
a builtin call:

```swift
let reversedCollection = usersString.reversed()
```

Swift has an unusual approach to Strings. Swift stores all characters in Strings
as Unicode, even if they are within the ASCII character set. Therefore, we don't
need to do anything funky to cover all our edge cases: Swift can innately handle
accented characters, Cyrillic, kanji, and so on.

While this allows Swift to seamlessly handle emoji and languages that use
non-English characters, it can make working with Strings a bit more complicated.

Swift's String API has changed frequently from version to version, as Apple
continually tries to balance universal language support with ease of use. In
early versions, Swift Strings were more like Javascript's String implementation,
where Strings were not quite arrays, but you could still call a specific
character by indexing into it with an integer value.

As of Swift 4, Strings are composed of a special kind of character collection,
quite distinct from arrays. Indexing into a String is done via special methods
and indexing objects specific to the task. This makes looping over all of the
characters in a String a more difficult task than in other languages.

Thankfully, we do not have to resort to this to reverse a String ,  we can simply
call the .reversed() method (or .reverse(), in earlier Swift versions).

### Reversed()

The `.reversed()` method does not mutate the original String, nor does it return a
new String. Instead, it works over the character collection making up our String,
and we get back an instance of ReversedCollection, an incompatible type. This
forces us to be more precise about what we intend to do with our return values.
Later, we use our ReversedCollection to make a new String object:

```swift
let reversedString = String(reversedCollection)
```

Fortunately, we can perform a quick cast to get our reversed string.

### Print

Finally, on line 11, we come to a nice, straight-forward print statement:

```swift
print(reversedString)
```

Unlike other languages, we don't need to specify the console. The compiler
implicitly knows. Apple also offers a logging system, for more robust results
when debugging.


## How to Run the Solution

The most common way for programmers to run Swift code is via Apple's XCode IDE.
It's free and available on the Mac App Store. You can paste this code snippet
directly into an XCode file and run it.

You should use an online Swift compiler if your machine can't handle XCode, or
you just don't want to download it (it's quite big). This web compiler is
up-to-date with Swift 4. Note that Swift updates yearly, so many web compilers
are out of date and unable to run this code.
