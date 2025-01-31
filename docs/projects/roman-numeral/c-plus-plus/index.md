---

title: Roman Numeral in C++
layout: default
date: 2022-04-28
last-modified: 2022-10-02

---

Welcome to the [Roman Numeral](https://sampleprograms.io/projects/roman-numeral) in [C++](https://sampleprograms.io/languages/c-plus-plus) page! Here, you'll find the source code for this program as well as a description of how the program works.

## Current Solution

{% raw %}

```c++
#include <iostream>
#include <bits/stdc++.h>
 
using namespace std;

/*
	a function which returns false when a character belongs to Roman literals else returns true
*/
bool is_roman(char x){
	return !(x=='I' || x=='V' || x=='X' || x=='L' || x=='C' || x=='D' || x=='M');
}

/*
	Roman to Numerical convert function
*/
int main(int argc,char* argv[]){
	//condition to check null input
	if(argv[1]==NULL){
		cerr<<"Usage: please provide a string of roman numerals"<<endl;
		exit(0);
	}

	//storing the roman number in a string
	string s;
	s=argv[1];

	//checking each character for any invalid input
	for(char c:s){
		if(is_roman(c)){
			cerr<<"Error: invalid string of roman numerals"<<endl;
			exit(0);
		}
	}

	//map to store the values of Roman characters and their corresponding integer value
	map<char,int> value;
	value['I']=1;
	value['V']=5;
	value['X']=10;
	value['L']=50;
	value['C']=100;
	value['D']=500;
	value['M']=1000;

	//variable to store the value
	int num=0;

	for(int i=s.size()-1;i>=0;i--){
		//To handle cases like IV where it should be considered as 4
		if(value[s[i]]>value[s[i-1]] && i>0){
			num+=value[s[i]]-value[s[i-1]];
			i--;
		}else{
			num+=value[s[i]];
		}
	}

	cout<<num<<endl;
}
```

{% endraw %}

[Roman Numeral](https://sampleprograms.io/projects/roman-numeral) in [C++](https://sampleprograms.io/languages/c-plus-plus) was written by:

- Sailok Chinta

If you see anything you'd like to change or update, [please consider contributing](https://github.com/TheRenegadeCoder/sample-programs).

## How to Implement the Solution

No 'How to Implement the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).

## How to Run the Solution

No 'How to Run the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).