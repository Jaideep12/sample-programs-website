---

title: Merge Sort in Matlab
layout: default
date: 2022-04-28
last-modified: 2022-10-02

---

Welcome to the [Merge Sort](https://sampleprograms.io/projects/merge-sort) in [Matlab](https://sampleprograms.io/languages/matlab) page! Here, you'll find the source code for this program as well as a description of how the program works.

## Current Solution

{% raw %}

```matlab
function [result] = MyMergeSort( x )
% Sort vector 'x' using the merge sort algorithm
% result is a vector consisting of the sorted values of 'x' 
% in ascended order
% Takes O( n log n ) time
% Requires extra memory for merging results

n = length(x);
if n == 1
    % Stop the recursion, if we are down to one element in list
    result = x;
else
    m = floor(n/2);  % Get the half way point

    r1 = MyMergeSort( x(1:m) );    % Sort first half recursively...
    r2 = MyMergeSort( x(m+1:n) );  % Sort 2nd half recursively...
    result = MyMerge( r1, r2 );    % Merge the two halves in sorted order
end

function c = MyMerge( a, b )
% Merges 2 vectors a,b into a result vector c 
%   assumes a, b are already sorted
%   'c' will also be in sorted order

aLen = length(a);  % get length of a
bLen = length(b);  % get length of b
cLen = aLen+bLen;
c = zeros(1,cLen); % pre-allocate 'c' to correct size

% Initialize starting indices
aIdx = 1;
bIdx = 1;
for cIdx = 1:cLen
  % Should we grab from 'a' or 'b' ???
  if aIdx > aLen
    % All done with 'a' vector, grab from 'b' vector.
    c(cIdx) = b(bIdx); 
    bIdx = bIdx + 1;
  elseif bIdx > bLen
    % All done with 'b' vector, grab from 'a' vector
    c(cIdx) = a(aIdx); 
    aIdx = aIdx + 1;
  elseif a(aIdx) <= b(bIdx)
     % a(i) <= b(i), grab from 'a' vector
     c(cIdx) = a(aIdx); 
     aIdx = aIdx + 1;
  else
    % b(i) < a(i), grab from 'b' vector
    c(cIdx) = b(bIdx); 
    bIdx = bIdx + 1;
  end
end

% BY - Nikhil Gupta
% GitHub - nikkkhil067
```

{% endraw %}

[Merge Sort](https://sampleprograms.io/projects/merge-sort) in [Matlab](https://sampleprograms.io/languages/matlab) was written by:

- Nikhil Gupta

If you see anything you'd like to change or update, [please consider contributing](https://github.com/TheRenegadeCoder/sample-programs).

## How to Implement the Solution

No 'How to Implement the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).

## How to Run the Solution

No 'How to Run the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).