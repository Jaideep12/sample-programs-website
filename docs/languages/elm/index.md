---

title: The Elm Programming Language
layout: default
date: 2020-05-02
last-modified: 2022-05-18
featured-image: 
tags: [elm]
authors:
  - the_renegade_coder

---

Welcome to the Elm page! Here, you'll find a description of the language as well as a list of sample programs in that language.

## Description

According to Wikipedia, Elm is a functional programming language 
used for building web-based graphical user interfaces.

In terms of features, Elm offers immutability, static typing, and 
a module system.

## Static Typing

At this point in the series, we've seen a lot of languages which 
support static typing. Because of that, I'm slowly starting to draw 
a distinction between statically and dynamically typed languages.

Originally, my understanding of static typing came from languages 
like Java and C where we have to explicitly state the types of our 
variables:

```java
// Java Explicit Typing Example
int x = 5;
String helloWorld = "Hello, World!";
```

Meanwhile, my understanding of dynamically typed languages came 
from Python where variables don't need type annotations:

```python
# Python Implicit Typing Example
x = 5
hello_world = "Hello, World!"
```

Because of this rather naive distinction, I was under the impression 
that Elm couldn't actually be statically typed because the language 
supports type annotations. Instead, I thought that maybe Elm was more 
like Hack, a gradually typed language.

Of course, the true distinction between static and dynamic typing is 
at what point the type checking occurs: before or at runtime. In other 
words, languages don't need explicit typing to be statically typed. 
Likewise, languages don't need implicit typing to be dynamically typed.

In the case of Elm, type inference is used to determine value types. 
However, type annotations can be used to improve program readability.
And, the compiler will even verify the annotations are correct. However, 
the annotations, in this case, have nothing to do with gradual typing.

## Immutability

While debating type systems is great, Elm's most interesting feature 
to me is immutability. Immutability, a byproduct of value semantics, describes
a value's inability to be changed. In other words, immutable values are 
values that cannot be changed after creation.

To me, the concept of immutability is interesting because code like the 
following will fail in Elm:

```elm
a = 10
a = a - 5
```

Because a is immutable, the code above will actually cause a recursion 
error. You can read more about that in Elm's documentation. At any rate, 
let's get to the solution!


## Articles

- [Hello World in Elm](https://sampleprograms.io/projects/hello-world/elm)