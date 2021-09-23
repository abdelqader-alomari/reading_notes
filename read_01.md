# Read: 01 - Java Basics

## Variables:

A variable is a container which holds the value while the Java program is executed. A variable is assigned with a data type. Variable is a name of memory location. There are three types of variables in java: local, instance and static.

**Instance Variables:**

Variables declared inside the class but outside the body of the method, without the static keyword.
It is called an instance variable because its value is instance-specific and is not shared among instances.

**Class Variables:**

A variable that is declared as static. It cannot be local. You can create a single copy of the static variable and share it among all the instances of the class. Memory allocation for static variables happens only once when the class is loaded in the memory.

**Local Variables:**

A variable declared inside the body of the method. You can use this variable only within that method and the other methods in the class aren't even aware that the variable exists.it cannot be defined with "static" keyword.

**Parameters:**
Parameters are always classified as "variables"; `public static void main(String[] args)` args are parameters

### Naming:

1. The name should not start with special characters like & (ampersand), $ (dollar), \_ (underscore).
2. The name must not contain any white spaces. If the name contains multiple words, start it with the lowercase letter followed by an uppercase letter such as firstName, lastName.
3. Avoid using one-character variables such as x, y, z

## Operators:

Operators are special symbols that perform specific operations on one, two, or three operands, and then return a result. There are a lot of type for operators: Unary Operator,Arithmetic Operator, Shift Operator,
Relational Operator, Bitwise Operator, Logical Operator, Ternary Operator and Assignment Operator.

## Expressions, Statements, and Blocks:

Operators may be used in building expressions, which compute values; expressions are the core components of statements; statements may be grouped into blocks

### Expressions:

An expression is a construct made up of variables, operators, and method invocations, which are constructed according to the syntax of the language, that evaluates to a single value. int cadence = 0 example of expression.

1 _ 2 _ 3 is an example of compound expression... here the result of multiplication is independent of order.
x + y / 100 is ambiguous because we didn't specify how an expression will be evaluated we can use parenthesis()
Operators that have a higher precedence get evaluated first in this case division will evaluated before addition.

### Statements:

Are roughly equivalent to sentences in natural languages. A statement forms a complete unit of execution. The following types of expressions can be made into a statement by terminating the expression with a semicolon (;).

```
// assignment statement
aValue = 8933.234;
// increment statement
aValue++;
// method invocation statement
System.out.println("Hello World!");
// object creation statement
Bicycle myBike = new Bicycle();
// declaration statement
double aValue = 8933.234;
```

### Blocks:

A block is a group of zero or more statements between balanced braces and can be used anywhere a single statement is allowed. The following example, BlockDemo, illustrates the use of blocks:

```
class BlockDemo {
     public static void main(String[] args) {
          boolean condition = true;
          if (condition) { // begin block 1
               System.out.println("Condition is true.");
          } // end block one
          else { // begin block 2
               System.out.println("Condition is false.");
          } // end block 2
     }
}
```

### Control Flow Statements

The statements inside your source files are generally executed from top to bottom, in the order that they appear. Control flow statements, however, break up the flow of execution by employing decision making, looping, and branching, enabling your program to conditionally execute particular blocks of code. This section describes the decision-making statements (if-then, if-then-else, switch), the looping statements (for, while, do-while), and the branching statements (break, continue, return) supported by the Java programming language.

## What does it mean to compile code?

When you compile code, the compilor (usually another program) takes the program the human wrote, and converts it into the program the computer can understand (i.e. converts from Java to machine language).
So Compiling turns the human-readable language into a specific set of instructions understandable by the computer. Usually this ends up in an executable file.

## Reading Java Documentation (Java API)

Java has a standard Application Programming Interface (API) —a huge library consisting of over 4,000 classes, each with its own functionality, its own limitations, and its own rules for effective use.

You can find things in the API documentation in a number of different ways. Each way is convenient in one situation or another. For example, Java has a method named System.out.println. What follows describes two ways to look up the System.out.println method.

1. Visit docs.oracle.com/javase/8/docs/api/.
2. Click the INDEX link at the top of the page to open the index
3. A list of letters is near the top of the index. Click the P link to go to the section with println in it.
4. In the P section, do a search for println to find the println entries.
5. to go to more details click on the link for chosen entry

- you can use this method to find any of Java methods. Inline

Here’s how to find an entry in the API by starting in the list of classes:

1. Visit docs.oracle.com/javase/8/docs/api/.
2. Find the page that documents the System class.
3. On the documentation page for the System class, find the out variable.
4. In the table’s out row, click the PrintStream link.
5. On the documentation page for PrintStream, find println(String).
