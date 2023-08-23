# Physics 427 Homework 1

__Due 9:00am Monday 9/4/2023__

## 1. Float vs Double

Write a C++ program to find the machine precision for `float` and
`double` data types.

Name your source file `problem1.cpp` in the homework repository. Include its
output in a separate text file `problem1.txt`. You can create such a file using the "redirect" command `>`, which takes the standard output from the command on the left and pass it as input to the file on the right. For example, the following command can generate such a text file:

``` sh
./a.out > problem1.txt
```

Commit and push both `problem1.cpp` and `problem1.txt` to the homework repository.

## 2. Quadratic Solver

Write a C++ header that defines two functions. The two functions should have the
following signatures:

``` c++
std::tuple<double, double> solve_quadratic_1(double a, double b, double c);
std::tuple<double, double> solve_quadratic_2(double a, double b, double c);
```

Function 1 implements the usual quadratic formula that solves the algebraic
equation $ax^{2} + bx + c = 0$:

$$
    x_{1,2} = \frac{-b \pm\sqrt{b^{2} - 4ac}}{2a}.
$$

Function 2 implements the more stable quadratic formula:

$$
    \displaystyle x_{1} = \frac{q}{a},\quad x_{2} = \frac{c}{q}
$$

where

$$
    q = -\frac{1}{2}\left[b + \text{sgn}(b)\sqrt{b^{2} - 4ac}\right]
$$

The `std::tuple<double, double>` type is a two-element tuple that contains two
`double` numbers. This is the main way to return multiple results from a single
function, since by default C++ only allows one return value for a function.
You'll need to include the header file `<tuple>`. You can create a tuple from
two numbers `x1` and `x2` using the function `std::make_tuple(x1, x2)`.

You can print the content of a tuple $x$ using the following line of code:

``` c++
std::cout << "x1 = " << std::get<0>(x) << ", x2 = " << std::get<1>(x) << std::endl;
```

Name your header file `problem2.h` in the homework repository. Write a program
`problem2.cpp` to test out these functions for a few different combinations of
$(a, b, c)$ parameters. Include:

1. At least one example of $(a, b, c)$ that produces no real solutions. Note what
the output is.
2. At least one example of $(a, b, c)$ that produces different results for these two implementations. 

Include the
output in a separate text file `problem2.txt`. Commit and push all 3 files to
the homework repository. Remember to make sure that `problem2.txt` is the exact
output of the program compiled from `problem2.cpp`.

## 3. Stability of a Recurrence Relation

Verify that the "Golden mean":

$$
    \phi \equiv \frac{\sqrt{5} - 1}{2} \approx 0.61803398
$$

satisfies the following recursion relation:

$$
    \phi^{n+1} = \phi^{n-1} - \phi^{n}
$$

Use this recursion relation to write a simple function to calculate $\phi^{n}$
for a given positive integer $n$. Print out $\phi^{n}$ for $n\in
[0,1,\dots,20]$. Do this for both `float` and `double` data types to see whether
it stays stable for longer with double precision.

Your source code should be written in `problem3.cpp`, and its output should be
included in file `problem3.txt`. Commit and push both files to the homework
repository.
