# Compile-Time Errors vs. Runtime Errors

## Learning Goals

- Define what a compile-time error is.
- Define what a runtime error is.
- Analyze the difference between the two types of errors.

## Introduction

Now that we have gotten more comfortable writing some Java code, let's discuss
some errors we might come across when compiling and running our programs. We
can break down these errors into two categories: compile-time errors and runtime
errors.

## What are Compile-Time Errors?

**Compile-time errors** are errors that occur when we try and compile the code.
These errors won't even allow us to run the program. If we think back to "The
Compiler and the JVM" lesson earlier in this module, there were two commands we
used: `javac` and `java`. The `javac` command would compile the source code in
order to turn it into something that the JVM could execute. If we try to compile
some code, and we see errors, these are called compile-time errors as they occur
at the time of compilation.

We can see these errors when we try to run our programs in IntelliJ too.
Remember back in the "Variables" lesson when we showed what happened if we
attempted to use a variable _before_ it was initialized?

![use-variable-without-initialization-intellij](https://curriculum-content.s3.amazonaws.com/java-mod-1/variables/intellij-use-variable-without-initialization.png)

We see IntelliJ warning us of an error. When we try to run the program, Java
will first try to compile the source code. But it stops before it can even
proceed to running it:

![build-error](https://curriculum-content.s3.amazonaws.com/java-mod-1/errors/intellij-compile-time-error.png)

We see that the build failed. This means, it failed to compile the code.

Some examples of compile-time errors include:

- Missing parentheses and curly brackets.

  ![missing-curly-bracket](https://curriculum-content.s3.amazonaws.com/java-mod-1/errors/compile-time-error-missing-curly-bracket.png)

- Missing terminator.

  ![missing-semicolon](https://curriculum-content.s3.amazonaws.com/java-mod-1/errors/compile-time-error-missing-terminator.png)

- And other syntax type errors.

  ![syntax-errors](https://curriculum-content.s3.amazonaws.com/java-mod-1/errors/compile-time-error-syntax-errors.png)

Imagine if the compiler didn't spit out these types of errors and simply just
ran the code. This would still cause a bug in the code, but it would be less
obvious. It might also be harder to identify what went wrong. Other languages
don't always have this benefit. Our IDE, IntelliJ, also helps us out even more
by highlighting and warning us of these types of compile-time errors. Luckily,
our tools and the language itself helps us out a lot in identifying these types
of errors so that we can quickly fix them!

## What are Runtime Errors?

**Runtime errors** are errors that occur when we try to execute the program.
These errors can be compiled successfully, but will occur when we are running
the code. So, if we were using a terminal window, these errors would show up
once we run the `java` command on the compiled code.

We can see these errors when we try to run our programs in IntelliJ too. A
common runtime error is a division by zero. As we may recall from math class,
we cannot divide another number by zero, as it results in a "not a number".

Let's see what happens when we run this code:

```java
public class Main {
    public static void main(String[] args) {
        int notANumber = 9 / 0;
        System.out.println(notANumber);
    }
}
```

There is nothing wrong with the syntax of the code, so the compiler will be able
to compile it into Java bytecode successfully. But the issue here is that 9 is
being divided by 0, which results in not a number. IntelliJ even warns us if we
hover over the expression that there could be something wrong here:

![numeric-overflow-in-expression](https://curriculum-content.s3.amazonaws.com/java-mod-1/errors/intellij-warn-division-by-zero.png)

If we ignore IntelliJ and try to run it, notice again that this gets past the
compilation step and throws the exception at runtime:

![arithmeticexception](https://curriculum-content.s3.amazonaws.com/java-mod-1/errors/runtime-error-divide-by-zero.png)

Notice in this example that the program compiled and was able to start running
successfully. It wasn't until the program tried to execute the
`int notANumber = 9 / 0;` that the program failed to continue executing. This is
an example of a runtime error.

## The Difference?

The difference between a compile-time error and a runtime error is when the
error happens. If it happens when we are compiling the source code into Java
bytecode, then it is a compile-time error. These typically have to do with
syntax errors. If the error occurs once the program is running, then it is a
runtime error. Usually runtime errors come in the form of **exceptions**.
