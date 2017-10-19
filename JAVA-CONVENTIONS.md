# Java Coding Style Conventions

The following tips are meant as formatting guidelines for FIRST Team 612 when writing Java robot code. These rules are not set in stone; what is most important is to write logically designed code. However, these guidelines are meant to make the code easier to understand quickly and maintain consistancy across code written by the whole team. Therefore, these rules should not be broken without good reason.

---

## Classes

Classes should always be `public` and the names should have each word start with a capital letter. For example, `public class DriveLeft`, `public class MoveArm`, or `public class Stop`.

Class fields should be `private` unless specifically needed to be `public`. If a private variable must be changed, instead use a public `get` and `set` method. These methods should be named `getVariableName()` and `setVariableName(variable_type new_variable_name)`

When declaring fields and methods, fields should be declared before methods and private class members should be declared before public members. For example,

    public class FooBar {
        private double spam = 0.8;
        public int eggs = 4;
        private double Method();
        public int anotherMethod();
    }

---

## Methods

Formatting for method names is similar to class names; however, the first letter of the method name should be lower case, like in `public int anotherMethod()` above. In general, these should only be a few lines long. If a function becomes too complex and does multiple tasks, it should be split up into different functions. Methods should have a verb in their name to indicate what they do.

---

## Incrementing and Decrementing

Use the postfix form, i.e. `i++` and `i--` rather than `++i` or `--i` when either form fits.

---

## Numbers

All numeric variables that store integers should be of type `int`; numeric variables that store decimal numbers should be of type `double`. Exceptions are when WPILib methods return `floats` or other code that returns other types.

---

## Variables

Variable names are formatted as `variable_name`, all lower case with underscores separating individual words. Boolean variables (which hold `true` or `false`), should have a prefix denoting that they are a boolean such as `is` or `are`.

---

## Constants

Constants should be named in `ALL_UPPER_CASE` with underscores separating words, and type should be `static final`. I.e. `public static final double VALUE_OF_PI  = 3.14159`.

---

## Comments

Comments that span one line should be single line comments, i.e. `// Single line comment`. Longer comments, such as documentation for methods, should use

    /* multi
       line
       code
       formatting */
       
Notice that no matter the situation, there should be a space between the start of the comment (`//` or `/*`) and the actual comment. 
---

## General formatting

### Line Length
Lines should never be longer than 80 characters. If the situation comes up, the line should be split up at logical location at the coder's discretion.

### White Spaces
Tabs should be used for logical indentation. Eclipse, however, should be set to use 4 spaces for tabs which prevents disalignment from different tab sizes.

### Curly Braces
Curly Braces should be placed on the same line as the expression that creates a new block. For example:

    if() {
        // Indented code
    }
    
rather than:

    if()
    {
        // Indented code
    }
    
Notice that there is a space after the closing paranthesis and before the opening curly brace.

### Paranthesis

When doing math, paranthesis should be used to make order of operations explicitly clear, even when not necessarily required. For example, `3 + (2*5)`.


### Operators

There should always be a space before and after the operators, for example `num1 + num2` instead of `num1+num2`.

### Print Statements

`System.out.println` should always be used when debugging code. Each `System.out.println` statement should begin with one of the following descriptor:

* Info: General information. Generally used when debugging code and figuring out when specific lines of code are called or what a variable contains at a certain time in code.
* Warning: Used to tell drivers or programmers that something may have gone wrong.
* ERROR: Used to indicate a situation that may contain a fatal problem in the execution of robot code.

In addition, each print statement should contain the file name, method name, and approximate line number it is called from in paranthesis. 
