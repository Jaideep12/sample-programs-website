---

title: Selection Sort in C++
layout: default
date: 2022-04-28
last-modified: 2022-10-02

---

Welcome to the [Selection Sort](https://sampleprograms.io/projects/selection-sort) in [C++](https://sampleprograms.io/languages/c-plus-plus) page! Here, you'll find the source code for this program as well as a description of how the program works.

## Current Solution

{% raw %}

```c++
#include <iostream>
#include <bits/stdc++.h>
 
using namespace std;

// A function to Swap two values provided
void swap(int *x,int *y){
	int t=*x;
	*x=*y;
	*y=t;
}

//Function to handle errors
void handle_error(){
	cout<<"Usage: please provide a list of at least two integers to sort in the format \"1, 2, 3, 4, 5\""<<endl;
	exit(0);
}

//Function to check whether inputs satisfy given constraints
int check(string s){
	int x1=0,x2=s.size()-1;

	//x1 gives first index position where integer occurs
	for(int i=0;i<s.size();i++){
		if(s[i]!=' '){
			x1=i;
			break;
		}
	}

	//x2 gives last index position where integer occurs
	for(int i=s.size()-1;i>=x1;i--){
		if(s[i]!=' '){
			x2=i;
			break;
		}
	}
	
	//if any space occurs between this substring then throw error
	for(int i=x1;i<=x2;i++){
		if(s[i]==' '){
			handle_error();
		}
	}

	return stoi(s);
}

//Function for converting string input into integer vector 
vector<int> convert(string s){
	/*
		Loop to convert numbers in string to integers
	*/
	vector<int> v;
	string num="";
	for(int i=0;i<s.size();i++){
		if((int)s[i]>=48 && (int)s[i]<=57 || s[i]==' '){
			num+=s[i];
		}else if(s[i]==','){
			v.push_back(check(num));
			num="";
		}else{
			handle_error();	
		}
	}


	if(num.size()>0){
		v.push_back(check(num));
	}
	
	return v;
}

int main(int argc,char* argv[]){
	/*
		Condition to check for No String as Input
	*/
	if(argc<2){
		handle_error();
	}

	vector<int> v=convert(argv[1]);

	/*
		Conditon to check if given input has more than 2 integers
	*/
	if(v.size()<2){
		cout<<"Usage: please provide a list of at least two integers to sort in the format \"1, 2, 3, 4, 5\""<<endl;
		exit(0);
	}

	int n=v.size();
	int min_idx;

	/*
		Loop to iterate all values in array
	*/
	for(int i=0;i<n-1;i++){
		min_idx=i;
		for(int j=i+1;j<n;j++){
			if(v[j]<v[min_idx]){
				min_idx=j;
			}
		}
		//swapping of ith value with current min_idx value
		swap(v[min_idx],v[i]);
	}

	for(int i=0;i<n-1;i++){
		cout<<v[i]<<", ";
	}
	cout<<v[n-1];
}
```

{% endraw %}

[Selection Sort](https://sampleprograms.io/projects/selection-sort) in [C++](https://sampleprograms.io/languages/c-plus-plus) was written by:

- Parker Johansen
- Sailok Chinta

If you see anything you'd like to change or update, [please consider contributing](https://github.com/TheRenegadeCoder/sample-programs).

**Note**: The solution shown above is the current solution in the Sample Programs repository as of Oct 25 2019 08:29:10. The solution was first committed on Oct 23 2019 18:57:11. As a result, documentation below may be outdated.

## How to Implement the Solution

No 'How to Implement the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).

## How to Run the Solution

No 'How to Run the Solution' section available. [Please consider contributing](https://github.com/TheRenegadeCoder/sample-programs-website).