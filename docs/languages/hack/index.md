---

title: The Hack Programming Language
layout: default
date: 2020-05-02
last-modified: 2022-05-11
featured-image: 
tags: [hack]
authors:
  - the_renegade_coder

---

Welcome to the Hack page! Here, you'll find a description of the language as well as a list of sample programs in that language.

## Description

According to Wikipedia, Hack is a dialect of PHP used by Facebook. 
Beyond that, Wikipedia was really only able to tell me that the 
open source language was released in 2014. So for once, I had to 
dig into the documentation.

Apparently, the most important features of Hack are:

- Generics
- Nullable Types
- Type Annotations
- Collections
- Lambdas

Now, I think the most interesting feature has to be the type annotations. 
That's because Hack is actually dynamically typed like Python.

However, if you've used Python, then you know that it has a relatively 
new type hinting feature. Typing hinting allows you to arbitrarily 
enforce static type checking in your code. I say arbitrarily because 
no one is forcing you to use type hints.

At any rate, Hack has essentially the same feature, but it's restricted 
to parameters, class variables, and return values. For example:

```hack
function foo(int $x): int {
  return $x * 2;
}
```

Here we've defined some function foo which takes an integer parameter and 
returns an integer. Of course, nothing is stopping us from removing those 
annotations:

```hack
function bar($x) {
  return $x * 2;
}
```

Now, this function would run exactly the same except we wouldn't discover 
any type issues until runtime.

So, what kind of typing system does Hack have? Is it static? How about 
dynamic? Well, there's actually a new term for the kind of type system that 
languages like Hack and Python have. It's called gradual typing, and it allows 
users to specify exactly when they want static or dynamic typing.

Once again, I think I've explored a topic a bit too deeply, so I'll stop there.


## Articles

- [Hello World in Hack](https://sampleprograms.io/projects/hello-world/hack)