As usual, let's dig right into the complete solution of Reverse a String in Java:

```java
public class ReverseString {
  public static void main(String args[]) {
    if (args.length > 0) {
      StringBuilder builder = new StringBuilder(args[0]);
      String reversed = builder.reverse().toString();
      System.out.println(reversed);
    }
  }
}
```

If you previously read this article, you may remember the following snippet:

```java
public class ReverseString {

  public static String reverse(String toReverse) {
    char[] characters = toReverse.toCharArray();
    int start = 0;
    int end = characters.length - 1;
    char temp;
    while(end > start){
      temp = characters[start];
      characters[start] = characters[end];
      characters[end] = temp;
      end--;
      start++;
    }
    return new String(characters);
  }

  public static void main(String args[]) {
    if (args.length > 0) {
      System.out.println(reverse(args[0]));
    }
  }
}
```

As it turns out, the snippet above works but has a couple pitfalls. The major
pitfall being that it doesn't work for special character sets such as Chinese.
However, I plan to keep it's explanation for the sake of showing off the language.

At any rate, let's dive in![^1]

### The General Solution

As we can see, the general solution leverages the StringBuilder library to
reverse a String in Java. Originally, I was against this idea because it really
hides some of the cool features of Java. However, this method is far superior to
the one I shared before as it works for every string you throw at it.

Anyway, let's dig into it.[^1]

#### The Class Declaration

Like any Java program, we're stuck creating a class before we can do anything:

```java
public class ReverseString {
  // Insert code here
}
```

As an added restriction, we're also stuck using the same name for the file:
ReverseString.java.[^1]

#### The Main Method Declaration

Again, if we want a executable program in Java, we'll need to create a main method:

```java
public static void main(String args[]) {
  // Insert code here
}
```

The main method structure is always the same.

First, we declare a public static method which basically means anyone with
access to the class can run this method without creating an instance of the
class. Of course, no one does this with main methods, but you get the idea.

Next, we declare a return type of void. In some languages, we might return an
integer, but in Java we return nothing. That's just the convention.

Finally, we use the main method name and declare a String array as the input.
The input array will be how we access our command line arguments.[^1]

#### The Main Method Core

Up to this point, everything has been exactly the same in both solution. In
other words, if you don't like the way something is worded so far, check down
below for another explanation.

Next, we'll take a look at the inside of the main method:

```java
if (args.length > 0) {
  StringBuilder builder = new StringBuilder(args[0]);
  String reversed = builder.reverse().toString(); 
  System.out.println(reversed);
}
```

All we're really doing here is checking that we have command line arguments. If
we do, we attempt to reverse them and print them to the user, that simple!

Of course, instead of reversing the string using the character array, we
leverage the StringBuilder library which handles surrogates for us. In other
words, we don't have to worry about corrupting Strings.

However, that's a rather high-level explanation. If we look closer, we create a
StringBuilder using the first command line argument. Then, we call the reverse
method of StringBuilder which reverses the String. At that point, we convert our
StringBuilder back into a String and return it. Done![^1]

### The Incomplete Solution

If you previously read this article, you know that I implemented the string
reversal by hand. In other words, I used a loop to swap characters in the
character array. Unfortunately, that solution is incomplete, but I think it shows
off a lot of cool features of Java. So, I'm keeping the code breakdown below.[^1]

#### The Class Declaration

As with any program in Java, our first step is to create a class:

```java
public class ReverseString {
  // Insert code here
}
```

In this case, I created a public class with the name ReverseString. Consequently,
the file must also share that name.[^1]

#### The Main Method Declaration

Within the class, I've declared two methods. The first method I want to focus on
is the main method toward the bottom. This method is where the program drops in
when we run it:

```java
public static void main(String args[]) {
  // Insert code here
}
```

As we can see, the main method is declared as public and static which means
anyone can access it without an instance of the ReverseString class. In addition,
the main method has a return type of void. In other words, the method doesn't
return anything.

In terms of parameters, the main method in Java is required to accept an array of
strings. This array contains each of the command line arguments. However, unlike
Python, the first argument is not reserved for the file name. In fact, it's possible
that the array of arguments is empty.[^1]

#### The Main Method Code

Inside the main method is where the magic happens:

```java
if (args.length > 0) {
  System.out.println(reverse(args[0]));
}
```

Here, we can see an if statement and a print statement. According to the
conditional logic, we only execute the print statement if the list of arguments
is not empty. We do this by checking that the length of the list of arguments
is greater than zero.

In the case where we have an argument, we run our print statement. At that point,
we have to make a call to reverse, our reverse a string method. Notice that we
pass the first argument always. All other arguments are ignored.[^1]

#### The Reverse Method Declaration

To get a better idea what the main method is doing, we need to dig into the
reverse method declaration.

The reverse method is very similar to our main method in that it is also public
and static. That means that we could call the reverse method without an instance
of the ReverseString class:

```java
ReverseString.reverse("Hello, World!")  // returns "!dlroW ,olleH"
```

The advantage here is we're able to call reverse directly in the main method.

Unlike the main method, the reverse method returns a String. That probably makes
sense since we want the reverse method to give us a reversed String.

As a result, the reverse method also takes a String as input. In other words, the
reverse method takes in a String and outputs the reverse of that String as seen
in the snippet above.[^1]

#### The String to Character Array Transformation

Now, when I wrote this solution, I specifically avoided the StringBuilder library
because it completely masks the String reversal:

```java
new StringBuilder(toReverse).reverse().toString()
```

Notice how we could have easily just wrapped our string in a StringBuilder,
called the reverse method, and converted it back to a String. Of course, I think
that defeats the purpose of this series.

Instead, we start by converting our input String to a character array:

```java
// i.e. ['H', 'e', 'l', 'l', 'o', ',', ' ', 'W', 'o', 'r', 'l', 'd', '!'] 
char[] characters = toReverse.toCharArray();
```

A character array is simply a set of characters which we can freely manipulate.
Normally, we can't manipulate characters in a String because Strings are
immutable in Java. That means that any changes to a String results in the
creation of a new String.

The Local Variables
Before we can actually start reversing this character array, we define and
declare a few variables:

```java
int start = 0;
int end = characters.length - 1;
char temp;
```

As we can probably imagine, start and end refer to the indices at the start and
end of the character array. The temp variable will be used to track swaps.
We'll see that play out later.[^1]

#### The Loop Structure

Okay, so now we're going to perform the String manipulation. To do so, we need
to create a loop:

```java
while(end > start) {
  // Insert code here
}
```

Our loop condition is pretty simple. All we do is monitor the start and end
variables. If at any point start crosses end, we break out of the loop. As we
can probably imagine, we will be manipulating start and end inside the loop.[^1]

#### The Loop Internals

Inside the loop, we pretty much just swap the characters at the start and end
indices and move those pointers inward by one:

```java
temp = characters[start];
characters[start] = characters[end];
characters[end] = temp;
end--;
start++;
```

To do this, we leverage the temp variable to hold the start character. Then, we
overwrite the start character with the end character. At that point, we overwrite
the end character with the start character that we stored in temp.

When we've completed the character swap, we decrement the end pointer and increment
the start pointer. This allows us to slowly reverse each pair of characters
until we reach the middle of the String.[^1]

#### The Return Statement

Finally, we convert our character array to a String, and we return it:

```java
return new String(characters);
```

At a high level, we take a string from the command line, reverse it, and output
it to the user. That's it!
