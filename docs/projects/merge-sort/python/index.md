---

title: Merge Sort in Python
layout: default
last-modified: 2020-05-02
featured-image: merge-sort-in-python-featured-image.JPEG
tags: [python, merge-sort]
authors:
  - hmajid2301

---

Welcome to the [Merge Sort](https://sampleprograms.io/projects/merge-sort) in [Python](https://sampleprograms.io/languages/python) page! Here, you'll find the source code for this program as well as a description of how the program works.

## Current Solution

{% raw %}

```python
import sys


def merge_sort(xs):
    def sort(xs):
        if len(xs) <= 0:
            return []
        if len(xs) == 1:
            return xs
        return sort([merge(xs[0], xs[1])] + sort(xs[2:]))
    split_xs = [[x] for x in xs]
    return sort(split_xs)[0]


def merge(xs, ys):
    if len(xs) <= 0:
        return ys
    if len(ys) <= 0:
        return xs
    if xs[0] < ys[0]:
        return [xs[0]] + merge(xs[1:], ys)
    return [ys[0]] + merge(xs, ys[1:])


def input_list(list_str):
    return [int(x.strip(" "), 10) for x in list_str.split(',')]


def exit_with_error():
    print('Usage: please provide a list of at least two integers to sort in the format "1, 2, 3, 4, 5"')
    sys.exit(1)


def main(args):
    try:
        xs = input_list(args[0])
        if len(xs) <= 1:
            exit_with_error()
        print(merge_sort(xs))
    except (IndexError, ValueError):
        exit_with_error()


if __name__ == "__main__":
    main(sys.argv[1:])
```

{% endraw %}

[Merge Sort](https://sampleprograms.io/projects/merge-sort) in [Python](https://sampleprograms.io/languages/python) was written by:

- Jeremy Grifski
- Parker Johansen

If you see anything you'd like to change or update, [please consider contributing](https://github.com/TheRenegadeCoder/sample-programs).

**Note**: The solution shown above is the current solution in the Sample Programs repository as of Oct 15 2020 22:17:17. The solution was first committed on Dec 22 2018 23:50:12. As a result, documentation below may be outdated.

## How to Implement the Solution

At this point, let's dig into the code a bit. The following sections break
down the Merge Sort in Python functionality.

### Solution

```python
#!/usr/bin/env python
import sys


def merge_sort(xs):
    def sort(xs):
        if len(xs) <= 0:
            return []
        if len(xs) == 1:
            return xs
        return sort([merge(xs[0], xs[1])] + sort(xs[2:]))
    split_xs = [[x] for x in xs]
    return sort(split_xs)[0]


def merge(xs, ys):
    if len(xs) <= 0:
        return ys
    if len(ys) <= 0:
        return xs
    if xs[0] < ys[0]:
        return [xs[0]] + merge(xs[1:], ys)
    return [ys[0]] + merge(xs, ys[1:])


def input_list(list_str):
    return [int(x.strip(" "), 10) for x in list_str.split(',')]


def exit_with_error():
    print('Usage: please provide a list of at least two integers to sort in the format "1, 2, 3, 4, 5"')
    sys.exit(1)


def main(args):
    try:
        xs = input_list(args[0])
        if len(xs) <= 1:
            exit_with_error()
        print(merge_sort(xs))
    except (IndexError,ValueError):
        exit_with_error()


if __name__ == "__main__":
    main(sys.argv[1:])
```

### The Main Function

Breaking down this solution bottom up,

```python
if __name__ == "__main__":
    main(sys.argv[1:])
```

This bit of code checks to see if this is the main module run. If it is it then calls the main
function and passes user input to it. In this case the user input would be a string of numbers
like so `"2, 1, 10, 5, 3"` (to sort).

```python
def main(args):
    try:
        xs = input_list(args[0])
        if len(xs) <= 1:
            exit_with_error()
        print(selection_sort(xs))
    except (IndexError,ValueError):
        exit_with_error()
```

This is the main function of this file. It parses the input, then calls our selection sort
function (and prints the results). It also deals with any errors raised.

### Transform Input Parameters

```python
def input_list(list_str):
    return [int(x.strip(" "), 10) for x in list_str.split(',')]
```

This function takes a string like `"2, 1, 10, 5, 3"`, and turns into a list of numbers.
It does this using a list comprehension. First, we need to convert our string into a
list `list_str.split(',')` which is a list of strings split by comma (,).
As a result, our original input string becomes `["2", " 1", " 10", " 5", " 3"]`. Then for each
element in the list `for x in ...` ,  we do something to it.

In this example we convert it into a decimal integer, `int(x.strip(" "), 10)`
`x.strip(" ")`, removes any whitespace so `" 1"` becomes `"1"`, then `int("1", 10)`
converts the string `"1"` into a decimal number in this case `1`. This is done
for every item in the list so our original input of `"2, 1, 10, 5, 3"`
becomes `[2, 1, 10, 5, 3]`.

### Throw Errors

```python
def exit_with_error():
    print('Usage: please provide a list of at least two integers to sort in the format "1, 2, 3, 4, 5"')
    sys.exit(1)
```

This function prints a message and then exits the script with an error, `sys.exit(1)`.
If any non-zero value is returned then the program didn't complete properly. This function is called
if the user input isn't correct.

### Merge

```python
def merge(xs, ys):
    if len(xs) <= 0:
        return ys
    if len(ys) <= 0:
        return xs
    if xs[0] < ys[0]:
        return [xs[0]] + merge(xs[1:], ys)
    return [ys[0]] + merge(xs, ys[1:])
```

This function is used to sort two list together (`xs` and `ys`). There are different conditions
we must account for. The first two conditions check if either of the lists are empty. There are
a few ways to check if a list if empty such as `not xs` but in this case we are checking
if the length of the list is less than or equal to 0 `len(xs) <= 0`. If either of the
lists `xs` or `ys`, then we return the non empty list. So if `xs` is empty we will
return the list `ys`.

The next thing we check for is if the first element of `xs` is less than the `ys`,
We can get the first element of a list like so `xs[0]`, then we
`return [xs[0]] + merge(xs[1:], ys)`. This is an example of recursion where the function
calls itself within the function, in this case the `merge()` function calling the `merge()`
function again.

Since `xs[0]` is less than `y[0]` we know `xs[0]` must be
the smallest item in either list, as both lists are already sorted. So we then take `xs[0]` out
of the first list, and we convert it into a list `[xs[0]]` because we want to concatenate it with a
sorted list. The `+` operator can be used to concatenate two lists together.

We call `merge(xs[1:], ys)` to sort the remaining items in both lists. Where `xs[1:]` is the list
`xs` without the first element. This is called index splicing in Python, you can learn more about it
[here](https://www.pythoncentral.io/how-to-slice-listsarrays-and-tuples-in-python/).
We don't include the first element of `xs` because we already know it's the smallest element in
both lists. The final line `return [ys[0]] + merge(xs, ys[1:])` is the same as line above except
in this case `ys[0]` is smaller than `xs[0]` hence we use `ys[0]` at the start of the list
concatenation instead of `xs[0]`. The reason this isn't surrounded by an `else` statement is
because of the return statement. Nothing will be executed after it.

Let's take a look at an example, where `xs = [3, 4]` and `ys = [1, 10]`

Merge 1:

* xs = [3, 4]
* ys = [1, 10]
* len(xs) = 2 and 2 > 0
* len(ys) = 2 and 2 > 0
* `xs[0] = 3` and `ys[0] = 1` and 3 > 1
* [1] + merge([3, 4], [10])

Merge 2:

* xs = [3, 4]
* ys = [10]
* len(xs) = 2 and 2 > 0
* len(ys) = 1 and 1 > 0
* `xs[0] = 3` and `ys[0] = 4` and 3 < 4
* [3] + merge([4], [10])

Merge 3

* xs = [4]
* ys = [10]
* len(xs) = 1 and 1 > 0
* len(ys) = 1 and 1 > 0
* `xs[0] = 4` and `ys[0] = 10` and 4 < 10
* [4] + merge([], [10])

Merge 4

* xs = []
* ys = [10]
* len(xs) = 0 and 0 <= 0
* return `[10]`

Going backwards

* [4] + [10] = [4, 10] (Merge 3)
* [3] + [4, 10] = [3, 4, 10] (Merge 2)
* [1] + [3, 4, 10] = [1, 3, 4, 10] (Merge 1)

### Merge Sort

```python
def merge_sort(xs):
    def sort(xs):
        if len(xs) <= 0:
            return []
        if len(xs) == 1:
            return xs
        return sort([merge(xs[0], xs[1])] + sort(xs[2:]))
    split_xs = [[x] for x in xs]
    return sort(split_xs)[0]
```

This is the function that actually sorts our entire list. 

```python
    def merge_sort(xs):
        def sort(xs):
```

This is known as closure nested functions (a function within another function).
The nested function can access variables of the enclosing scope. They can read
variables but cannot edit them. In the example above, the `xs` variable is our
unsorted list.

The `sort()` function only exists within the scope of `merge_sort()` but other than that
is works exactly the same as a normal function. 

```python
split_xs = [[x] for x in xs]
return sort(split_xs)[0]
````

In this example, we execute the above lines. First. you can ignore the `sort()` function until
it's called within `merge_sort()`. `split_xs = [[x] for x in xs]` splits our lists into separate lists.
It takes each element with in `xs` and turns it into a list `[x]`. So `split_xs` is now a list of lists.
If `xs = [3, 10, 5]` then `split_xs = [[3], [10], [5]]`. The final sorted result will look something
like this [[3, 5, 10]] another list of lists hence we want to return the first element
`sort(split_xs)[0]`.

```python
def sort(xs):
    if len(xs) <= 0:
        return []
    if len(xs) == 1:
        return xs
    return sort([merge(xs[0], xs[1])] + sort(xs[2:]))
```

So what happens in the `sort()` function lets take a look. Using our example above the function
would be called by `sort([[3], [10], [5]])`. The first if statement checks if the `xs` list is
empty by checking that the length is less than or equal to 0 `len(xs) <= 0`. If so, we return an empty list `return []`.
The second statement checks if the list `xs` contains a single element `len(xs) == 1`.
If it does, we return the list `return xs`. Finally if the list `xs` has more than 1 element
`return sort([merge(xs[0], xs[1])] + sort(xs[2:]))`.

Breaking this down this is another example of a recursive function, the `sort()` function is
calling itself. Breaking down the argument passed to the sort function,
`[merge(xs[0], xs[1])]` here we call our `merge()` function with the first two items of the `xs`
list, then we convert the returned element into a list, hence being surronded by `[]`. The second
part of the argument `sort(xs[2:])` calls the `sort()` function again but without the first two
elements of `xs`, again using list comprehension.

We then combine these two lists together using
list concatenation using the plus `+` operator `[merge(xs[0], xs[1])] + sort(xs[2:]`. Taking a look
at an example where `xs = [[4], [10], [9], [5]]` the final sort function would look like
`sort([merge([4], [10]) + sort([[9], [5]]))`.

Lets take a look at how we would sort the list `xs = [4, 3, 1, 10]`

* `merge_sort([4, 3, 1, 10])`
* `split_xs = [[4], [3], [1], [10]]`

Sort 1

* `xs = [[4], [3], [1], [10]]`
* `len(xs) = 4`
* `sort([merge([4], [3])] + sort([[1], [10]]))`
* `[merge([4], [3])] = [[3, 4]]`
* `sort([[3, 4]] + sort([[1], [10]]))`

Sort 2

* `xs = [[1], [10]]`
* `len(xs) = 2`
* `sort([merge([1], [10])] + sort([]))`
* `[merge([1], [10])] = [[1, 10]]`
* `sort([[1, 10]] + sort([]))`

Sort 3

* `xs = []`
* `len(xs) = 0`
* `return []`

Going Backwards (Sort 2)

* `sort([[1, 10]] + [])`

Sort

* `xs = [[1, 10]]`
* `len(xs) = 1`
* `return xs = return [1, 10]`

Going Backwards (Sort 1)

* `sort([merge([3, 4])], [1, 10]))`
* `sort([[1, 3, 4, 10]])`

Sort

* `xs = [[1, 3, 4, 10]]`
* `len(xs) = 1`
* `return [1, 3, 4, 10]`

So

* `return sort([[3, 4]] + sort([[1], [10]])) = [1, 3, 4, 10]`


## How to Run the Solution

If we want to run this program, we should probably download a copy of [Selection Sort in Python](https://github.com/TheRenegadeCoder/sample-programs/blob/master/archive/p/python/merge-sort.py).
After that, we should make sure we have the latest Python interpreter. From there, we can run the
following command in the terminal:

`python merge-sort.py "3, 2, 10, 6, 1, 7"`

Alternatively, we can copy the solution into an online Python interpreter and hit run.
