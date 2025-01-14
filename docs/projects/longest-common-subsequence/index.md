---

title: Longest Common Subsequence in Every Language
layout: default
date: 2018-11-01
last-modified: 2020-05-02
featured-image:
tags: [longest-common-subsequence]
authors:

---

Welcome to the Longest Common Subsequence page! Here, you'll find a description of the project as well as a list of sample programs written in various languages.

## Description

Given two arrays of numbers, find the longest common subsequence. For example, let's say we have the
following pair of arrays:

```python
A = [1, 4, 5, 3, 15, 6]
B = [1, 7, 4, 5, 11, 6]
```

The longest common subsequence is `1, 4, 5, 6`.


## Requirements

Write a program which accepts two command line arguments--each list--and outputs the longest
common subsequence between the two lists. Input arguments should be in comma separated list notation:
`1, 2, 14, 11, 31, 7, 9`.

Your program should be able to parse these lists into some internal representation in your
choice language (ideally an array). From there, the program should compare the two arrays
to find the longest common subsequence and output it in comma separated list notation to the user.

The following is recursive pseudocode that you can use for reference:

```python
LCS(arrayA, arrayB, indexA, indexB):
  if indexA == 0 || indexB == 0:
    return 0
  else if arrayA[indexA - 1] == arrayB[indexB - 1]:
    return 1 + LCS(arrayA, arrayB, indexA - 1, indexB - 1)
  else:
    return max(LCS(arrayA, arrayB, indexA - 1, indexB), LCS(arrayA, arrayB, indexA, indexB - 1))
```

Unfortunately, this pseudocode only gives us the length of the longest common subsequence. Since we
want to actually *print* the result, we'll probably need to augment this algorithm a bit. Also,
it may be useful to implement the memoized solution for the sake of efficiency.


## Testing

The following table contains various test cases that you can use to
verify the correctness of your solution:

| Description | Input | Output |
|-------------|-------|--------|
| No Input | | "Usage: please provide two lists in the format "1, 2, 3, 4, 5" |
| Empty Input | "" | "Usage: please provide two lists in the format "1, 2, 3, 4, 5" |
| Missing Input | "25, 15, 10, 5" | "Usage: please provide two lists in the format "1, 2, 3, 4, 5" |
| Sample Input: Same Length | "1, 4, 5, 3, 15, 6" "1, 7, 4, 5, 11, 6" | "1, 4, 5, 6" |
| Sample Input: Different Lengths | "1, 4, 8, 6, 9, 3, 15, 11, 6" "1, 7, 4, 5, 8, 11, 6" | "1, 4, 8, 11, 6" |


## Articles

- [Longest Common Subsequence in C](https://sampleprograms.io/projects/longest-common-subsequence/c)
- [Longest Common Subsequence in C#](https://sampleprograms.io/projects/longest-common-subsequence/c-sharp)
- [Longest Common Subsequence in C++](https://sampleprograms.io/projects/longest-common-subsequence/c-plus-plus)
- [Longest Common Subsequence in Elixir](https://sampleprograms.io/projects/longest-common-subsequence/elixir)
- [Longest Common Subsequence in Go](https://sampleprograms.io/projects/longest-common-subsequence/go)
- [Longest Common Subsequence in Haskell](https://sampleprograms.io/projects/longest-common-subsequence/haskell)
- [Longest Common Subsequence in Java](https://sampleprograms.io/projects/longest-common-subsequence/java)
- [Longest Common Subsequence in Javascript](https://sampleprograms.io/projects/longest-common-subsequence/javascript)
- [Longest Common Subsequence in Kotlin](https://sampleprograms.io/projects/longest-common-subsequence/kotlin)
- [Longest Common Subsequence in Python](https://sampleprograms.io/projects/longest-common-subsequence/python)

---

<nav class="project-nav">

<div id="prev">

[<-- Previous Project (Linear Search)](https://sampleprograms.io/projects/linear-search)

</div>

<div id="next">

[Next Project (Longest Palindromic Substring) -->](https://sampleprograms.io/projects/longest-palindromic-substring)

</div>

</nav>