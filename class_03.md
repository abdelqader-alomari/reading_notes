# Read: 03 - Maps, primitives, File I/O:

## Primitives vs. Objects:

![Primitives vs. Objects](https://th.bing.com/th/id/R.5b6777b2ca21a4bb89f0147041718d11?rik=dc9UCyW9PQqyuA&riu=http%3a%2f%2f1.bp.blogspot.com%2f-bpbdwrvRSaw%2fVflqVT6GaxI%2fAAAAAAAADxU%2fBSi7bF7ef34%2fs1600%2fPrimitive%2bvs%2bReference%2bType%2bJava.png&ehk=Mi%2b8%2b5HMpJb1H51EeCFSIutvTjomEPDpMJlojlOpD34%3d&risl=&pid=ImgRaw&r=0)

- Java has a two-fold type system consisting of primitives such as int, boolean and reference types such as Integer, Boolean. Every primitive type corresponds to a reference type.

- Every object contains a single value of the corresponding primitive type. The wrapper classes are immutable

- Java performs a conversion between the primitive and reference types if an actual type is different from the declared one:

- The decision what object is to be used is based on what application performance we try to achieve, how much available memory we have, the amount of available memory and what default values we should handle.

the primitive type variables have the following impact on the memory:

boolean – 1 bit
byte – 8 bits
short, char – 16 bits
int, float – 32 bits
long, double – 64 bits

### Performance:

The performance of a Java code is quite a subtle issue, it depends very much on the hardware on which the code runs, on the compiler that might perform certain optimizations, on the state of the virtual machine, on the activity of other processes in the operating system.

## Exception:

exception is an event that occurs during the execution of a program and disrupts the normal flow of the program's instructions. Bugs or errors that we don't want and restrict our program's normal execution of code are referred to as exceptions.

![call stack - exception](https://docs.oracle.com/javase/tutorial/figures/essential/exceptions-errorOccurs.gif)

### Catching and handling exceptions:

Java has special blocks of code for working with exceptions: try, catch and finally.

Code where the programmer believes an exception may occur is placed in the `try` block. That doesn't mean that an exception will occur here. It means that it might occur here, and the programmer is aware of this possibility.

The type of error you expect to occur is placed in the `catch` block. This also contains all the code that should be executed if an exception occurs.

![handling exception](https://th.bing.com/th/id/R.4c116fec51d52d19c42488bf75875208?rik=rB9Ro37EQMaiDw&riu=http%3a%2f%2f1.bp.blogspot.com%2f-tm7TO6xnaio%2fUqdY-HfByCI%2fAAAAAAAABwc%2f4DKWAomzw_Q%2fs1600%2fWhat%2bis%2bException%2bHandling%2bin%2bC%2b%2b%2b1.jpg&ehk=uncZkRusxf3nHsnR6gajhALleIpHJoKhFmxLkKubsXY%3d&risl=&pid=ImgRaw&r=0)

### The Catch or Specify Requirement:

Valid Java programming language code must honor the Catch or Specify Requirement. This means that code that might throw certain exceptions must be enclosed by either of the following:

A try statement that catches the exception. The try must provide a handler for the exception, as described in Catching and Handling Exceptions.
A method that specifies that it can throw the exception. The method must provide a throws clause that lists the exception, as described in Specifying the Exceptions Thrown by a Method.

## Scanner:

Scanner is a class in java.util package used for obtaining the input of the primitive types like int, double, etc. and strings. It is the easiest way to read input in a Java program, though not very efficient if you want an input method for scenarios where time is a constraint like in competitive programming.

To create an object of Scanner class, we usually pass the predefined object System.in, which represents the standard input stream. We may pass an object of class File if we want to read input from a file.
To read numerical values of a certain data type XYZ, the function to use is nextXYZ(). For example, to read a value of type short, we can use nextShort()
To read strings, we use nextLine().
To read a single character, we use next().charAt(0). next() function returns the next token/word in the input as a string and charAt(0) function returns the first character in that string.

![Scanner](https://www.sitesbay.com/java/images/scanner-class-in-java.png)
