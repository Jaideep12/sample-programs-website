---

title: File IO in Python
layout: default
last-modified: 2020-05-02
featured-image:
tags: [python, file-io]
authors:
  - noah11012

---

Welcome to the [File Input Output](https://sampleprograms.io/projects/file-input-output) in [Python](https://sampleprograms.io/languages/python) page! Here, you'll find the source code for this program as well as a description of how the program works.

## Current Solution

{% raw %}

```python
def write_file():
    try:
        with open("output.txt", "w") as out:
            out.write("Hi! I'm a line of text in this file!\n")
            out.write("Me, too!\n")
    except OSError as e:
        print(f"Cannot open file: {e}")
        return


def read_file():
    try:
        with open("output.txt", "r") as in_file:
            for line in in_file:
                print(line.strip())
    except OSError as e:
        print(f"Cannot open file to read: {e}")
        return


if __name__ == '__main__':
    write_file()
    read_file()
```

{% endraw %}

[File Input Output](https://sampleprograms.io/projects/file-input-output) in [Python](https://sampleprograms.io/languages/python) was written by:

- Ganesh Naik
- Jeremy Grifski
- Noah Nichols

If you see anything you'd like to change or update, [please consider contributing](https://github.com/TheRenegadeCoder/sample-programs).

**Note**: The solution shown above is the current solution in the Sample Programs repository as of Oct 15 2020 22:17:17. The solution was first committed on Sep 12 2018 13:00:03. As a result, documentation below may be outdated.

## How to Implement the Solution

We'll first present the solution in its entirety. Then, we'll go over the code
line by line:

```python
def write_file():

    try:
        out = open("output.txt", "w")
    except OSError as e:
        print("Cannot open file: {}", e)
        return

    out.write("Hi! I'm a line of text in this file!\n")
    out.write("Me, too!\n")

    out.flush()
    out.close()

def read_file():

    try:
        in_file = open("output.txt", "r")
    except OSError as e:
        print("Cannot open file to read: {}", e)
        return

    line = in_file.readline()
    while line:
        print(line.rstrip('\n'))
        line = in_file.readline()

    in_file.close()

if __name__ == '__main__':
    write_file()
    read_file()
```

Afterward, we'll take a look at how to run the solution.

### Writing to a File

As you may have noticed above, our file writing procedure has been broken out
into its own function:

```python
def write_file():

    try:
        out = open("output.txt", "w")
    except OSError as e:
        print("Cannot open file: {}", e)
        return

    out.write("Hi! I'm a line of text in this file!\n")
    out.write("Me, too!\n")

    out.flush()
    out.close()
```

First, we setup up a try..except block to catch any exceptions that might occur
when we want to open a file:

```python
try:
    out = open("output.txt", "w")
except OSError as e:
    print("Cannot open file: {}", e)
```

The Python documentation tells us if open() fails to create a new file, it will
raise an OSError exception. If we do get an exception, we will exit the method.

Next, if no exceptions occurred, we can now write to the file using the write() 
method:

```python
out.write("Hi! I'm a line of text in this file!\n")
out.write("Me, too!\n")
```

As we can see, we attempt to output a couple of lines to the text file.

At this point, we need to flush the output buffer and close the file:

```python
out.flush()
out.close()
```

On the first line we do something known as "flushing". When we call write() not
everything may be written to the file and as some content may be in a buffer in
memory. flush() ensures that everything is written to disk.

The final line closes the file as it is good practice to close any resources like
files when you are finished using them.

### Reading From a File

After we write to a file, we can read back from that file. Naturally, we've
broken the reading procedure into its own function:

```python
def read_file():

    try:
        in_file = open("output.txt", "r")
    except OSError as e:
        print("Cannot open file to read: {}", e)
        return

    line = in_file.readline()
    while line:
        print(line.rstrip('\n'))
        line = in_file.readline()

    in_file.close()
```

Just like when we were opening the file for writing purposes, we surround the
code that could potentially raise exceptions in a try..except block:

```python
try:
    in_file = open("output.txt", "r")
except OSError as e:
    print("Cannot open file to read: {}", e)
    return
```

If an exception occurs, we report the error and exit the function.

Next, we have a while loop that iterates over each line in the file:

```python
line = in_file.readline()
while line:
    print(line.rstrip('\n'))
    line = in_file.readline()
```

As we can see, the loop performs some basic processing before we print the line
out onto the screen. When we get a line from the file, we also get the newline.
If we print it with the newline we print an extra empty line because print 
automatically adds a newline by default. To fix this problem we use rstrip() to
strip away any newlines at the end of the line. This loop will end when we reach
EOF (end of file).

Finally, we close the file as expected:

```python
in_file.close()
```

We don't flush the file because we didn't write anything to it, so we just close
the file.

### The Main Function

All of this code would be useless if we didn't execute it somewhere. Thankfully,
we can drop everything into the main function:

```python
if __name__ == '__main__':
    write_file()
    read_file()
```

And, that's it! We've conquered File IO in Python.


## How to Run the Solution

As usual, you're free to use an online Python interpreter such as the one on 
Repl and run the solution there. Alternatively, if you have a Python interpreter
installed on your machine, you can use the following command:

```console
python file-io.py
```

After you execute this command, you should be able to find a nearby output.txt 
file containing the arbitrary text we used earlier. If so, you've successfully
run the program.
