---

title: Palindromic Number in C
layout: default
date: 2022-04-28
last-modified: 2022-10-02

---

Welcome to the [Palindromic Number](https://sampleprograms.io/projects/palindromic-number) in [C](https://sampleprograms.io/languages/c) page! Here, you'll find the source code for this program as well as a description of how the program works.

## Current Solution

{% raw %}

```c
/*
 accept an integer, reverse it, compare it with original
 print true, if original and reversed number are same
 print false, if original and reversed number are same
*/
#include <stdio.h>
#include <stdlib.h>

void palindromic_number(int number){
  int temp = number, no_of_digits = 0,reversed_number = 0;

  while (temp > 0){
    reversed_number = (reversed_number * 10) + (temp % 10);
    temp = (int)(temp / 10);
    no_of_digits ++;
  } /*end of building reverse number*/
  
  if (no_of_digits < 2){
    printf("Usage: please input a number with at least two digits");
    exit(1);  
  }
  else{
    if (reversed_number == number){
      printf("true");
    }
    else{
      printf("false");
    }
  } /*end of more than 2 digit number check*/
 /*end of palindromic_number function*/
}

/*Return 1 if number, else return 0*/
int is_int(char *number_string){
  if(number_string[0] > '9' || number_string[0] < '0')
    return(0);
  for (int counter = 0; number_string[counter]; counter++){
    if(number_string[0] > '9' || number_string[0] < '0')
      return(0);
  }
  return(1);    

}

/* accept only integers with minimum 2 digits */
int main(int argc, char **argv){
  /*Read command line arg*/
  if (argc != 2 || is_int(argv[1]) != 1){
    printf("Usage: please input a number with at least two digits");    
    return(1);  
  }
   palindromic_number(atoi(argv[1]));
   return(0);
}
```

{% endraw %}

[Palindromic Number](https://sampleprograms.io/projects/palindromic-number) in [C](https://sampleprograms.io/languages/c) was written by:

- smjalageri

If you see anything you'd like to change or update, [please consider contributing](https://github.com/TheRenegadeCoder/sample-programs).

## How to Implement the Solution

No 'How to Implement the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).

## How to Run the Solution

No 'How to Run the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).