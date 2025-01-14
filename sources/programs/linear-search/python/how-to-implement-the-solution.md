Let us check out the entire code first, then we will break it into parts and get a deeper understanding of the entire code.

### Solution

```python
#!/usr/bin/env python
import sys

def sysarg_to_list(string):
    return [int(x.strip(" "), 10) for x in string.split(',')]

key = int(sys.argv[1])
array = sysarg_to_list(sys.argv[2])
size = len(array)

flag = 0
pos = -1

for i in range(size):
    if array[i] == key:
        flag = 1
        pos = i
        break

if(flag):
    print(key, "found at position", pos, ".")
else:
    print(key, "not in the array.")
```

### Getting user input and processing it

```python
def sysarg_to_list(string):
    return [int(x.strip(" "), 10) for x in string.split(',')]

key = int(sys.argv[1])
array = sysarg_to_list(sys.argv[2])
size = len(array)
```

This function takes a string like `"2, 1, 10, 5, 3"`, and turns into a list of numbers.
It does this using a list comprehension, first we need to convert our string into a
list `list_str.split(',')` which is a list of strings split by comma (,). So our
original input string becomes `["2", " 1", " 10", " 5", " 3"]`.
Then for each element in the list `for x in ...` ,  we do something to it.

In this example we convert it into a decimal integer, `int(x.strip(" "), 10)`. Then `x.strip(" ")`,
removes any whitespace so `" 1"` becomes `"1"`. Then `int("1", 10)`
converts the string `"1"` into a decimal number in this case `1`. This is done
for every item in the list so our original input of `"2, 1, 10, 5, 3"` becomes `[2, 1, 10, 5, 3]`.

The first argument passed to the python code should be the key to search followed by the string containing the elements of array in which the key is to be searched.

### Set flags

```python
flag = 0
pos = -1
```

The following are the uses of these variables:
1) flag: The flag variable is used to check whether a key is present in the array or not. 0 value means that the key is not present in the array and 1 means that key is in the array.
2) pos: The pos variable is used to keep track of the position in the array where key is found. It has a default value of -1 which indicates it is not found.

### Linear Search

```python
for i in range(size):
    if array[i] == key:
        flag = 1
        pos = i
        break
```

Finally we have the actual loop which performs the linear search operation.
This iterates from 0 till size (which is the length of the array).
In each iteration it compares the key with the element of array at the current iteration.
If it is found the flag is set to 1 and pos is set to current iteration (i), finally the loop is stopped there using break statement.

### Result

```python
if(flag):
    print(key, "found at position", pos, ".")
else:
    print(key, "not in the array.")
```

We then check the value of the flag variable.
If it has a value of 0, then it means that the key is not present in the array.
On the other hand, if the value of flag is 1, then it means that the key is found in the array and the corresponding position is displayed to the user.
