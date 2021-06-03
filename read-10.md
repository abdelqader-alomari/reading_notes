### Read: 10 - JS Debugging:

## Execution Context:

Every statement in a script lives in one of three execution contexts:

* Global Context: Code in the script, but not in a function. there is only one global context in any page.
* Function Context: Code that is being run within a function. Each function has its own function context.
* Eval Context (hidden): Text is executed like code in an internal function.

#### Execution contexts by Scope:

* Global Scope:If a variable is declared outside a function, it can be used anywhere
* Function-Level Scope:When a variable is declared within a function, it can only be used within that function.

### Error Objects:

**When an error object is created, it will contain the following properties:**

| Property | Description |
| -------- | ----------- |
| name | Type of execution |
| message | description |
| fileNumber | Name of the JavaScript file |
| lineNumber | Line number of error |

**JavaScript Built-in Errors:**

| Object | Description |
| ------ | ----------- |
| Error | Generic Error |
| SyntaxError | Syntax has not been followed |
| ReferenceError | Tried to reference a variable that is not declared/within scope |
| TypeError | An unexpected data type that cannot be coerced | 
| RangeError | Numbers not in acceptable range |
| URLError| encodeURI ().decodeURI(),and  similar methods used incorrectly |
| EvalError | eval () function used incorrectly |

*The eval() function: evaluates text through theinterpreter and runs it as code


### Deal with Errors:

1. Debug the script to fix errors
2. Handle errors gracefully (try,catch,throw, and statement)

### Break Points:

You can pause the execution of a script on any line using breakpoints.
Then you can check the values stored in variables at that point in time.

#### How to use Break points @Google_Chrome?

1. Select the Sources option. 
2. Select the script you are working with from the left-hand pane. The code will appear to the right.
3. Find the line number you want to stop on and click on it.
4. When you run the script, it will stop on this line. You can now hover over any variable to
see its value at that time in the script's execution.

#### Conditional Breakpoints:

You can indicate that a breakpoint should be triggered only if a condition that you
specify is met. The condition can use existing variables.

**To use it:**
1. Right-click on a line number.
2. Select Add Conditional Breakpoint...
3. Enter a condition into the popup box.
4 . When you run the script, it will only stop on this line if the condition is true
    (e.g., if area is less than 20).

You can see video for how to use it from here:
[![Conditional Breakpoints]({https://res.cloudinary.com/practicaldev/image/fetch/s--MhPrNDVD--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/xosjosjyf4eagl7149y6.png})]({https://youtu.be/l6PKY-l6wys} "Conditional Breakpoints")

### Finally... Book Chapter Built-in Summary:

* If you understand execution contexts and stacks, you are more likely to find the error in your code.
* Debugging is the process of finding errors. It involves a process of deduction.
* The console helps narrow down the area in which the error is located, so you can try to find the exact error.
* JavaScript has 7 different types of errors. Each creates its own error object, which can tell you its line number and gives a description of the error.
* If you know that you may get an error, you can handle it gracefully using the try, catch, finally statements.
Use them to give your users helpful feedback.