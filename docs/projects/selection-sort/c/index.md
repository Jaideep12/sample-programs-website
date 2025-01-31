---

title: Selection Sort in C
layout: default
date: 2022-04-28
last-modified: 2022-10-02

---

Welcome to the [Selection Sort](https://sampleprograms.io/projects/selection-sort) in [C](https://sampleprograms.io/languages/c) page! Here, you'll find the source code for this program as well as a description of how the program works.

## Current Solution

{% raw %}

```c
// Selection Sort In C Language

#include <stdio.h>
#include <errno.h>
#include <stdlib.h>
#include <string.h>

void selectionSort(long arr[], size_t n);   // Function for Selection Sort
void swap(long *xp, long *yp); 		   // Swap two numbers

size_t parse_list(const char *orig_list, long **arr)          // used for parsing the input in array arr
{
    char *list;
    char *token;
    size_t num_elements = 0;
    int i;
    int curr_index = 0;
    long temp_num;

    /* figure out the length of the list first */
    for (i = 0; orig_list[i]; i++) {
        if (orig_list[i] == ',') {
            num_elements++;
        }
    }

    /* if there are no commas, it's an invalid list */
    if (num_elements == 0) {
        *arr = NULL;
        return 0;
    }

    /* since there's one more number than there are commas, add one */
    num_elements++;

    /* alloc our array */
    *arr = malloc(num_elements * sizeof(long));

    /* find the numbers */
    list = strdup(orig_list);
    token = strtok(list, ",");
    while (token != NULL) {
        errno = 0;
        temp_num = strtol(token, NULL, 10);
        if (errno != 0) {
            *arr = NULL;
            return 0;
        }

        (*arr)[curr_index++] = temp_num;

        token = strtok(NULL, ",");
    }

    free(list);

    return num_elements;
}

/* printing array in desired form */
void printArray(long *arr, size_t num_elems)               
{
    int i;

    for (i = 0; i < num_elems - 1; i++) {
        printf("%ld, ", arr[i]);
    }

    printf("%ld\n", arr[num_elems - 1]);
}

/* Error message if input is not in desired format */
void errorMsg()
{
    fputs("Usage: please provide a list of at least two integers to sort in the format \"1, 2, 3, 4, 5\"\n", stderr);
}


int main(int argc, char **argv)
{
    long *arr;
    long num_elements;

    if (argc < 2) {
        errorMsg();
        return 1;
    }

    num_elements = parse_list(argv[1], &arr);
    if (num_elements == 0) {
        errorMsg();
        return 1;
    }

    selectionSort(arr,num_elements);                     // call for complete array [0....n-1]
    printArray(arr, num_elements);

    free(arr);
}

void swap(long *xp, long *yp) 
{ 
    int temp = *xp; 
    *xp = *yp; 
    *yp = temp; 
} 
  
void selectionSort(long arr[], size_t n) 
{ 
    int i, j, min_idx; 
  
    // One by one move boundary of unsorted subarray 
    for (i = 0; i < n-1; i++) 
    { 
        // Find the minimum element in unsorted array 
        min_idx = i; 
        for (j = i+1; j < n; j++) 
          if (arr[j] < arr[min_idx]) 
            min_idx = j; 
  
        // Swap the found minimum element with the first element 
        swap(&arr[min_idx], &arr[i]); 
    } 
}
```

{% endraw %}

[Selection Sort](https://sampleprograms.io/projects/selection-sort) in [C](https://sampleprograms.io/languages/c) was written by:

- vidit624

If you see anything you'd like to change or update, [please consider contributing](https://github.com/TheRenegadeCoder/sample-programs).

## How to Implement the Solution

No 'How to Implement the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).

## How to Run the Solution

No 'How to Run the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).