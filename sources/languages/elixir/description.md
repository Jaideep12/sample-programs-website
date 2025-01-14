Elixir is yet another general-purpose language with functional tendencies. 
That said, Elixir is quite a bit different from some of our recent 
languages. For starters, Elixir runs on the Erlang virtual machine 
known as BEAM. This means that Elixir actually compiles down to bytecode 
much like Java.

In terms of features, Elixir has a lot to offer. For instance, Elixir 
has support for macros which modify the abstract syntax tree. You may 
recall that Rust has the same feature.

In addition, Elixir offers Python-like doc strings which leverage Markdown. 
This is a great feature for automatically generating documentation.

Another cool feature of Elixir is exactly what I found interesting about 
Scala: everything is an expression. In other words, everything evaluates 
to a value.

Finally, my favorite feature of Elixir has to be pattern matching. In 
Elixir, we can match patterns using the same operator most languages use 
for assignment: `=`. For example:

```elixir
myVal = 5
5 = myVal  # A valid match
6 = myVal  # (MatchError) no match of right hand side value: 5
```

In this example, we assign myVal a value of 5. Or in Elixir terminology, 
we actually bind a value of 5 to myVal through pattern matching. Then, we 
compare 5 to myVal which is a valid match. With that in mind, it's clear 
why we get an error when we try to match 6 to myVal.

Of course, pattern matching gets much more fun than that. We can also use 
pattern matching to destructure other data types:

```elixir
{x, y, z} = {:hi, 117, "some string"}
x  # :hi
y  # 117
z  # "some string"
```

In addition, there are several other ways pattern matching can be used, but 
we have to get to our implementation of Hello World in Elixir.
