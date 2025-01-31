---

title: Hello World in Crystal
layout: default
last-modified: 2020-05-02
featured-image: hello-world-in-crystal-featured-image.JPEG
tags: [crystal, hello-world]
authors:
  - the_renegade_coder

---

Welcome to the [Hello World](https://sampleprograms.io/projects/hello-world) in [Crystal](https://sampleprograms.io/languages/crystal) page! Here, you'll find the source code for this program as well as a description of how the program works.

## Current Solution

{% raw %}

```crystal
puts "Hello, World!"
```

{% endraw %}

[Hello World](https://sampleprograms.io/projects/hello-world) in [Crystal](https://sampleprograms.io/languages/crystal) was written by:

- Jeremy Griffith

If you see anything you'd like to change or update, [please consider contributing](https://github.com/TheRenegadeCoder/sample-programs).

## How to Implement the Solution

With the background out of the way, let's implement Hello World in Crystal:

```crystal
puts "Hello, World!"
```

If we think back, we might remember that this syntax is exactly the same in Ruby. 
Of course, this should come as no surprise as Ruby's syntax was a major influence 
on Crystal.

[Digging through the API][1] reveals that there are four definitions of puts:

```crystal
def puts(*objects : _) : Nil
def puts : Nil
def puts(obj) : Nil
def puts(string : String) : Nil
```

In our case, we're using option four which simply writes a string to standard output.

Now, puts is pretty interesting because it automatically appends a new line unless 
a new line already exists. Personally, that's the first time I've heard of a library 
call doing that kind of string formatting for the user. So, my question becomes: what 
happens if the string ends with multiple new lines?

Based on the source code:

```crystal
def puts(string : String) : Nil
self << string
puts unless string.ends_with?('\n')
nil
end
```

The puts library appears to only remove the last new line. After running it, I can 
confirm that's all this function does. Now, that's some bizarre behavior:

```crystal
puts 'Hello, World!' # Writes 'Hello, World!\n'
puts 'Hello, World!\n' # Writes 'Hello, World!\n'
puts 'Hello, World!\n\n' # Writes 'Hello, World!\n\n'
```

Honestly, I find this a little buggy. If, by default, this function adds a new 
line, then I would instinctively add a new line to the string (see line 2 above) to 
create extra space.

Of course, that doesn't work. I suspect that Crystal style would prefer the following:

```crystal
puts 'Hello, World!'
puts
```

Or, something along those lines. At any rate, I've gone a bit too far down a rabbit hole. 
Let's learn how to run our solution.


## How to Run the Solution

If we want to run our solution, perhaps the easiest thing to do is to copy our solution 
into the [online Crystal editor][2]. After that, we can hit run to see the output.

Alternatively, we can try to install the compiler on our system. However, I won't bother 
going into that because I'm using a Windows PC which doesn't appear to be supported.
