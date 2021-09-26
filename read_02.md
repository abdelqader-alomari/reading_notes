# Read: 02 - Arrays, Loops, Imports

## Java Imports:

![Java imports and packages](https://ftp.examtray.com/sites/default/files/styles/wordpress_800x460/public/2020-07/java-package-import-tutorial-infographic.jpg?itok=cglLnIDC)

A package in Java is used to group related classes. Think of it as a folder in a file directory. We use packages to avoid name conflicts, and to write a better maintainable code. Packages are divided into two categories:

Built-in Packages (packages from the Java API) User-defined Packages (create your own packages)

### package declaration syntax:

- Package statment (optional).
- Imports (optional).
- Class or interface definitions.

### import options:

```
* import javax.swing.*;  // Make all classes visible altho only one is used.
* import javax.swing.JOptionPane;  // Make a single class visible.
* Alternately we can the fully qualified class name without an import.
```

## Common imports:

There are 166 packages containing 3279 classes and interfaces in Java 5. However, only a few packages are used in most programming. GUI programs typically use at least the first three imports.

| import type                | used for                                                   |
| -------------------------- | ---------------------------------------------------------- |
| import java.awt.\*;        | Common GUI elements.                                       |
| import java.awt.event.\*;  | The most common GUI event listeners.                       |
| import javax.swing.\*;     | More common GUI elements. Note "javax".                    |
| import java.util.\*;       | Data structures (Collections), time, Scanner, etc classes. |
| import java.io.\*;         | Input-output classes.                                      |
| import java.text.\*;       | Some formatting classes.                                   |
| import java.util.regex.\*; | Regular expression classes.                                |

![packages](https://i2.wp.com/simplesnippets.tech/wp-content/uploads/2018/04/packages-in-java-programming-featured-image.jpg?resize=750%2C350&ssl=1)

---

## Different types of loops in Java:

In programming languages, looping is a feature which facilitates the execution of a set of instructions until the controlling Boolean-expression evaluates to false.

**Types of loops:**

- Simple for loop: control structure that used to repeat certain operations by incrementing & evaluating a loop counter.
- Enhanced for-each loop: It provides an alternative approach to traverse the array or collection in Java
- While loop: It repeats a statement or a block of statements while its controlling Boolean-expression is true.
- Do-While loop: looks like while loop but the first condition evaluation happens after the first iteration of the loop.

![Types of loops](https://www.javatpoint.com/images/java-loops.png)
