---

title: The Wren Programming Language
layout: default
last-modified: 2020-05-02
featured-image: 
tags: [wren]
authors:
  - the_renegade_coder

---

Welcome to the Wren page! Here, you'll find a description of the language as well as a list of sample programs in that language.

## Description

Last time we covered a relatively a relatively new language called Elm, 
but it still managed to have a Wikipedia page. Our language today, Wren, 
does not. As a result, I had to do a bit of digging to learn about this 
language.

According to the GitHub page, Wren is a new scripting language. Of course, 
there are plenty of those including Python, Lua, and JavaScript. So, what 
makes Wren different?

Well, according to the website, Wren was created as an object-oriented game 
scripting language. Apparently, Lua is the go-to for game scripting currently, 
but it's class system is pretty unnatural. Thus, Wren was born!

In addition to filling the object-oriented game scripting niche, Wren has some 
pretty sweet support for concurrency through a feature called fibers. Fibers 
are lightweight threads which eliminate random context switching. In other words, 
fibers generally only switch when they are told to, much like coroutines.

Finally, Wren is incredibly fast for a scripting language. In fact, the website 
shares some benchmarks which demonstrate it outperforming Python, Lua, and 
JavaScript. Game developers should be pretty happy about this.


## Articles

- [Hello World in Wren](https://sampleprograms.io/projects/hello-world/wren)