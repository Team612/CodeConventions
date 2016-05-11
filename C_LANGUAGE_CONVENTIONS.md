# C++ Coding Style Guide
These rules are meant as guidelines for writing C++ for FIRST Team 612. These
are not hard-and-fast rules; code should first and foremost be designed in a
logical manner. However, these guidelines allow consistency and readability to
be maintained across all of the robot's code. Do not break them without good
reason.

This document is modeled after the [Google Code C++ style guide]
(http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml).

## Header Files

### Guards
Every header file **must** be wrapped in an include guard, which prevents them from 
being compiled multiple times. This is best accomplished through the use of 
a `#pragma once` compiler macro at the beginning of the file. Eclipse-default `#define`
style include guards will not be permitted.

### `using namespace` Statements
Statements beginning with `using namespace` should never be used in header
files, as they pollute the global namespace. Instead, names should be referenced
by their full name, e.g. `std::vector`, especially in the case of the standard
library functions. If needed, an alternative to this in some cases, as in types
is to use a type definition to accomplish the following.

    class Foo {
        typedef std::really_long_type::internal_type anothername;
    };

This should always be done inside of the class that it is being used in as to not
pollute the global namespace.

## Scoping

### Global Variables
Avoid using global variables and functions. Use methods and member variables of
classes when possible.

### Local Variables
Declare local variables at the top of their enclosing scope, that is, at the top
of the block in which they are declared. Initialize variables on declaration,
like this:

    int i = 0;

Rather than this:

    int i;
    i = 0;

If variables are used only once, for readability, make them `const`
and keep them directly above the line that they are used in, at the
beginning of the function they are used in, or as a private `const`
member of the enclosing class.

## Classes

### Constructors

#### Initialization Lists
When assigning values to member variables in a constructor, use the
initialization list rather than the body of the constructor when possible. That
is, do this:

    Foo::Foo() : bar(0), baz(1) {
        // Initialize
    }

or this if the list is long:

    Foo::Foo() : bar(0),
                 baz(1) {
        // Initialize
    }

Rather than this:

    Foo::Foo() {
        bar = 0;
        baz = 1;
        // Initialize
    }

This method is both more efficient and the only valid method to initialize
constant member variables, so using it consistently helps prevent errors.

#### Default Constructors
Default constructors should be labeled as such:

    class Foo {
    public:
        Foo() = default;
    }

Default constructors are required and must be defined for all classes, 
excluding Command-based classes.

#### Deconstructors
Unless the deconstructor is being used for a valid reason, they should not
be defined. If necessary, an unimplemented virtual deconstructor can be used.

    class Foo {
    public:
        Foo() = default;
        virtual ~Foo() = 0;
    }

or

    class Foo {
    public:
        Foo() = default;
        //no deconstructor needed
    }

### Structs vs. Classes
Structs should be used only for containers for data, they must not have
methods. When in doubt, use a class.

### Encapsulation
Class members should be declared as `private` unless absolutely
necessary. Getters and setters should be used for changing member variables of
classes, rather than making the variables public. Getters and setters should be
named `getVariableName()` and `setVariableName( variable_type new_variable_name )`
respectively.

### Order of Declaration
`public` class members should be declared before `private` class members, and
variables should be declared before methods, e.g.

    class Foo {
        public:
            int i;
            Bar();
        private:
            int j;
            Baz();
    };

## Functions and Methods
Functions should be as short as possible. Functions ought to accomplish one and
only one task, and be descriptively named to fit that task, e.g. `raiseArm()`.

## Exceptions
Do not use exceptions, as they make control flow difficult to understand and
require extremely safe coding to avoid memory leaks.

## Casting
Preferentially use C++ style casting, i.e. `static_cast<int>(i)`, rather than
C-style casting, i.e. `(int)i`.

## Increment and Decrement
Use the postfix form of `++` and `--` whenever either form would be acceptable,
e.g. `i++;` rather than `++i;`

## Integer Types
Use only `int`,`long`, `short`, and/or `unsigned`. Do not use the types from
`<stdint.h>`, such as `int_32_t` or `uint_64_t`, unless specifically relying
on bit length as in code related to I2C or other bit-shifting-related code.

## Preprocessor Macros
Preprocessor macros should not be used in the main code base. They can be used for
debugging purposes in unit tests but must be removed before being re-implemented.

## Values of Zero
Use 0 for integers, nullptr for pointers, 0.0 for reals (i.e. doubles), 0.0f
for floats, and '\0' for chars.

## Constant Values
Constants should be declared as `const type name = value;`, rather than using
`#define`. This prevents unexpected behavior, for example when subtracting
negative constants.

## Naming
Use descriptive names, avoid abbreviations.

### File Names
File names should be in CamelCase.

### Type Names
Type names are in CamelCase. This applies to classes, structs, enums, and all
other user-defined types. These should correspond to the file name, but multiple
types can be defined in one file when nested, i.e.

    class Foo {
        enum class Bar { BAZ, BOB };
        struct Thing {
            int i;
        };
    };

### Variable Names
Variable names are in lower\_case. Additionally, boolean variables should imply
their type by beginning with "is" or "are", such as `is_robot_moving`.

### Constant Names
Constants should be named in UPPER\_CASE.

### Function Names
Functions should be in CamelCase, and usually should contain a verb in their
name, e.g. `MoveForward()` not just `Forward()`.

### Enums
Enums should be named in CamelCase; enum values should be named in CamelCase.

Values in enums should be in UUPER\_CASE.

### Macro Names
Macros should be named in UPPER\_CASE.

## Comments

### Multi-line Comments
Comments within the body of a method, function, and/or class should avoid using
the multi-line form. Instead, these multiple-line comments should simply have `//` at
the beginning of each line. For block comments in header files or outside of methods,
multi-line form should be used, i.e. `/* COMMENT */`.

## Formatting

### Line Length
Every line should be no more than 80 characters long. If more than this, newlines
should be added for formatting.

### Whitespace
Tabs should be used for logical indentation, and for alignment. However, Eclipse should
be set to use 4 spaces for tabs. This prevents alignment from being distorted by different tab sizes.

### Curly Braces
Curly braces should appear on the same line as the compared expression that requires
a new block. For example:
    int Foo() {
        // Function body
    }


Rather than:
    int Foo()
    {
        // Function body
    }

Conditional statements must always use curly braces, even when they only span
one line.

### Enumerations
Enums should be all on the same line, unless they are significantly long, then each element can
appear on its own line. For example:
    enum MyEnum { FOO, BAR, BAZ };

or
    enum MyLongEnum { FOO,
                      BAR,
                      BAZ,
                      BOO,
                      CAR,
                      LOP };

### Boolean Expressions
Boolean expressions spanning more than one line should have the joining operator
(either `||`or `&&`) at the beginning of each line, not the end.

### Parentheses
Parentheses should indicate order of operations in all expressions containing
more than one operator, even when technically unnecessary, e.g. `1 + (1 * 2)`.

Parentheses used for grouping should not have a space before and after their
contents.

### Operators
Operators should have a single space placed before and/or after their position in an
expression. These should follow the special case above for parentheticals.

### Classes
Access specifiers (`public`, `private`, and `protected`) should not be indented
with the body of the class.

## Misc

### Arrays
Standard library arrays are preferable to C-style arrays. For example:

    std::array<int, 5> values = { /*values*/ };

instead of

    int values[5] = { /*values*/ };

### Pointers
std::shared_ptr and std::unique_ptr should be use in place of raw pointers at
**all times**.    

### Print statements

#### standard cout
std::cout should never be used anywhere in the robot code. Use std::printf instead.

#### `printf`
printf should print serious, descriptive messages to aid the drivers or to aid
debugging. All printfs usually should start with one three descriptors, but others
can be made if appropriate:

* *Info:* - general information. Used for example, when you to know if a line of code
is being called.

* *Warning:* - used to tell drivers or programmers that something may have gone wrong.
Warnings are colored yellow in the Driverstation console.

* *ERROR:* - used to indicate a situation that may indicate a fatal problem in the
execution of a block of code. Errors are colored red in the Driverstation console.

In addition, `printf` statements must contain the file, method, and line number it is
being called from in parentheses after the main message. Example:

    std::printf("ERROR: Autonomous not initialized properly! (Robot.cpp, AutonomousInit(), 100)\n");

`printf` statements must also end in a new line. So this:

    std::printf("Info: Hello!\n");

instead of this:

    std::printf("\nInfo: Hello!");
