Functions
=========

In this assignment, we'll be working with functions. A _function_ is simply a piece of code
that takes inputs and gives you outputs. Sometimes a function takes no inputs (we'll see these
especially when we talk about _constructors_), and sometimes they return no outputs (so-called
_void_ functions). In this assignment, we'll work through several kinds of functions and see
why they are useful.

The overall goal
----------------

By the end of this assignment, you should be able to:
* describe what a function is,
* explain the difference between an `int` and a `double`,
* call a function,
* use the following functions: `String.format`, `Math.pow`, `Math.sqrt`, `System.out.println`.

Problems
--------

### Problem 1 (The basics)

A function is called by passing it *arguments*. For instance, when you type

```java
System.out.println("Hello, world!");
```

you are calling the function `println` of the object `System.out`. (Don't worry too much about
what an object is right now.) It's *name* is `println` and its *argument* in this case is the
string `"Hello, world!"`.

Another example of a function is `String.format`. This function takes *at least* one argument
and returns a formatted string. For instance,

```java
String.format("Let's count: %s, %s, %s", 1, 2, 3);
```

will return the string "Let's count: 1, 2, 3". Note that it filled in every `%s` in its first
argument (`"Let's count: %s, %s, %s"`) with its later arguments, `1`, `2`, and `3`.

In Canvas, please answer the following questions:
* What is the name of the function in this call: `String.format("%s", 27);`
* What are the arguments in this function call: `Math.pow(2, 4);`

Problem 2 (Composing functions)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions can be *composed*, i.e., you may pass the output of one function as the argument of
another. For instance, if we wanted to print the string "Let's count: 1, 2, 3", we could pass
the output of `String.format` to `System.out.println`. For instance,

```java
System.out.println(String.format("Let's count: %s, %s, %s", 1, 2, 3));
```

**NOTE**: The number of parentheses must match! A function call is denoted in Java by `()`, so
if you have an opening parenthesis `(`, you **must** have a closing one `)`.

In Canvas, please answer the following questions:
* What does the following code print: `System.out.println(Math.pow(2, 4));`
* How do I print the output of `Math.sqrt(27)`?

Problem 3 (Writing your own functions)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

So far, we've talked about the following functions:
* `System.out.println`
* `String.format`
* `Math.pow`
* `Math.sqrt`
Each of these comes with Java. But how would you write your own function? Heck, *why* would
you want to write your own function?

Let's suppose that you're solving your pre-calculus homework and you want to be able to quickly
find the distance between two points when they are specified by their *x* and *y* coordinates. Then
you could write

```java
Math.sqrt(Math.pow(x1 - x2, 2) + Math.pow(y1 - y2, 2));
```

every time. But wouldn't it be great to just write

```java
distance(x1, y1, x2, y2);
```

Well, to do that, you would need to *define* a function. That looks something like this:

```java
public class MathExample {
    public static double distance(double x1, double y1, double x2, double y2) {
        return Math.sqrt(Math.pow(x1 - x2, 2) + Math.pow(y1 - y2, 2));
    }

    public static void main(String[] args) {
        // your code here...
    }
}
```

There are a couple features of every function that we define:
* Its name (`distance`),
* Its arguments (`x1`, `y1`, `x2`, `y2`),
* The *types* of the arguments (e.g., the `double` in `double x1`), and
* The *return type* of the function (i.e., the `double` in `double distance`).

You'll also notice that we precede the type and name of the function with `public static`.
Don't worry about that for now. We'll get there.

Also, notice that this function has a `return` statement. This tells you what the function
will be given back to whoever called it.

In Canvas, answer the following questions:
* What is output when you put this in the `main` above: `System.out.println(distance(0, 0, 0, 1));`
* How about `System.out.println(distance(8.2, 9.7, 8.2, 10.7))`
* Or `System.out.println(distance(9.7, 13.2, 102.8, 9))`
* Everywhere you see the word `double` in the code snippet above, change it to `int`. What happens
  when you try to run `System.out.println(distance(1, 2, 3, 8.7))`

Problem 4 (An interlude on types)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You've already seen `int` in class, e.g.,

```java
public class FirstProgram {
    public static void main(String[] args) {
        System.out.println("Hello, world!");
        int eight = 8;
        System.out.print(String.format("%s is a number", eight));
    }
}
```

And we know that `int eight = 8;` is interpreted to mean that we are declaring a *variable*
called `eight` and we are assigning the value `8` to it.

The *type* of this variable is `int`, which stands for *integer*. `int` variables can *only*
hold integers.

Try running these two programs. What happens?

```java
public class TruncatingProgram {
    public static void main(String[] args) {
        System.out.println("Hello, world!");
        int eight = 8.8;
        System.out.print(String.format("%s is a number", eight));
    }
}
```

and

```java
public class BadProgram {
    public static void main(String[] args) {
        System.out.println("Hello, world!");
        int eight = "8";
        System.out.print(String.format("%s is a number", eight));
    }
}
```

What's happening is that Java requires you to declare a variable with the right *type*. We'll
talk a bunch more about why this is later, but for now, there are three types that you should
be aware of:
* `int` holds integers, like `10`, `-7`, `290348`, `0`,
* `double` holds any decimal number, like `2829.17`, `293.1, -19.13892`, `Math.PI`, and
* `String` holds any string, e.g., "Hello, world!", "8", "The number 8 is spelled eight".

Problem 5 (A long challenge)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We're going to keep doing your algebra homework for you. Let's write a function that solves
quadratic equations for you!

Write a program that uses the quadratic formula to solve the following quadratic equations
* *x*<sup>2</sup> + 10\**x* + 2 = 0
* *x*<sup>2</sup> + 5\**x* + 1 = 0
* 2*x*<sup>2</sup> - 2819\**x* + 372 = 0

To get full marks, you must define a function which you call with the coefficients of the
quadratic equations and you must print that function's return value.
