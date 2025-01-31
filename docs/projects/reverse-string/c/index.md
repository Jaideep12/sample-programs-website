---

title: Reverse a String in C
layout: default
last-modified: 2020-10-01
featured-image: reverse-a-string-in-c.jpg
tags: [c, reverse-a-string]
authors:
  - abhishek_raut

---

Welcome to the [Reverse String](https://sampleprograms.io/projects/reverse-string) in [C](https://sampleprograms.io/languages/c) page! Here, you'll find the source code for this program as well as a description of how the program works.

## Current Solution

{% raw %}

```c
#include <stdio.h>
#include <string.h>

int main(int argc, char **argv)
{
    char *text;
    size_t textlen;

    /* check argument count (trailing arguments are ignored) */
    if (argc < 2) {
        fputs("Not enough arguments", stderr);
        return 1;
    }

    /* get text from command line and calculate length */
    text = argv[1];
    textlen = strlen(text);

    /* print characters in reverse */
    while (textlen-- > 0) {
        putchar(text[textlen]);
    }

    /* put a newline at the end */
    putchar('\n');

    return 0;
}
```

{% endraw %}

[Reverse String](https://sampleprograms.io/projects/reverse-string) in [C](https://sampleprograms.io/languages/c) was written by:

- Christoph Böhmwalder

If you see anything you'd like to change or update, [please consider contributing](https://github.com/TheRenegadeCoder/sample-programs).

**Note**: The solution shown above is the current solution in the Sample Programs repository as of Jul 25 2018 01:24:39. The solution was first committed on Jul 24 2018 12:26:56. As a result, documentation below may be outdated.

## How to Implement the Solution

Below is the whole code for reversing a string in C :

```c
#include <stdio.h> 
#include <string.h> 
  
void reverseString(char* str) 
{ 
    int len, i; 
    char *start, *end, temp;
    len = strlen(str); 
    start = str; 
    end = str; 
  
    for (i = 0; i < len - 1; i++) 
    {
        end++; 
    }

    while (start<end) 
    { 
        temp = *end; 
        *end = *start; 
        *start = temp; 

        start++; 
        end--; 
    } 
} 
  
// Driver method 
int main() 
{   
    // Change Input as needed
    char str[400] = "AbCdeF"; 
    printf("Input string: %s\n", str); 
    reverseString(str); 
    printf("Reversed string: %s\n", str);   
    return 0; 
} 
```
<br/>

### Approach


Here we create two pointers, one that points to the string's start and the other to the end of the string. Using a third character *variable* as a place holder, we swap the character positions indicated by the pointers. We continue to do so until the entire input string is reversed by moving the *pointers*. 

[Time complexity][1]: O(n)

<br/>

### Breakdown

Now let us see step-by-step how the code works.

```c
#include <stdio.h> 
#include <string.h> 
```
Here we are including header files (.h files) to use functions like printf(). Header files provided us with tested ready to use functions to ease the software development work. 

By including `#include <stdio.h>` we can use printf() method without worrying about how it is implemented. Can you guess why we have included `#include <string.h>`? Keep on reading for the answer.

```c
void reverseString(char* str) {
    // code
} 
```
This is the function that will take a string as input and reverse it. Here, we will be modifying the value pointed by *pointer* str. Hence, the function doesn't need to return anything, and the return type of our method is *void*. 

```c
    int len, i; 
    char *start, *end, temp;
    len = strlen(str); 
    start = str; 
    end = str; 
```
Here we are declaring *variables* to store the length of the string and *pointers* to point start and end points (of the logical substring) to be swapped. Note that currently, the `end` pointer is pointing to the start of the string instead of the end of the string. We will see how to fix it in the next step.

And yes, the function `strlen()`, which gives us the length of string, can be used because of the statement: `#include <string.h>`. 

```c
     for (i = 0; i < len - 1; i++) 
    {
        end++; 
    }
```
We traverse through the entire string so that *pointer* `end` can point to the last character of the string. It's important to note that *for loop* traverse till `len-1` this is because, in C, arrays are zero-indexed i.e., indexing starts from 0. The `++` syntax at the end of the *variable* `end` is called an Increment operator. The increment operator increments the value of the variable by one in each iteration. Thus, after *for loop* is executed, *variable* `end` points to the string's last character.

```c
  while (start<end) 
    { 
        temp = *end; 
        *end = *start; 
        *start = temp; 

        start++; 
        end--; 
    } 
```
And this is the Meat of the matter; this is the logic that reverses the string. The *while loop*  condition `start<end` make sure that once reversed, we don't reverse back the string to the original string (For Math geeks; only 180<sup>o</sup> and not 360<sup>o</sup> rotation of string). The `temp` *variable* is used for swapping the characters pointed by two *pointers*. The `--` syntax at the end of the* variable* `end` is called a Decrement operator, and it decrements the value of `end` by 1. Both of these operators change characters pointed by the *pointers*, and we can swap all characters of the string. 

```c
 int main() 
{   
    // Change Input as needed
    char str[400] = "AbCdeF"; 
    printf("Input string: %s\n", str); 
    reverseString(str); 
    printf("Reversed string: %s\n", str);   
    return 0; 
} 
```
The `main()` function is acting as a utility function to use the `reverseString()`.  Using the instructions in the next step, try changing the value of *variable* `str` by typing your desired string inside double quotes *("")*.

Also, think about how the length of the string being odd or even can affect our code.



## How to Run the Solution

The easiest way to run this program is to go to this [LeetCode Playground][2] and run the program. You can tweak the program or provide different input strings to understand the working better.  

Alternatively, you copy GitHub's code and run the program on an online C compiler or in an IDE.
