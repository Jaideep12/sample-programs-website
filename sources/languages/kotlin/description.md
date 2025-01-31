Since Kotlin is a bit more popular than most of the newer languages, it 
actually has a Wikipedia page. So, we'll use that to learn more.

According to Wikipedia, Kotlin is a programming language that runs on 
the Java Virtual Machine. In other words, Kotlin compiles down to Java 
bytecode. In fact, developers have the option to decide which version 
of Java bytecode they want. In addition to the JVM, Kotlin can also 
compile down to JavaScript.

In terms of features, Kotlin offers an aggressive form of type inference. 
In other words, the language supports static type checking on implicit 
types. Of course, the benefit is a far less verbose syntax than Java.

Of course, I think my favorite feature is extension methods. In Kotlin, 
we can take a class that already exists and tack on our own methods 
without creating an extension class. For instance, Wikipedia shares 
the following snippet:

```kotlin
fun String.lastChar():  Char = this.get(this.length - 1)
```

In this example, the lastChar method is added to the String class. How cool is that?
