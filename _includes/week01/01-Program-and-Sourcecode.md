## 1. The program and the source code

### 1.1 Source code

A computer program is composed of commands written in the _source_ code. A computer generally runs _commands_ in the source code from top to bottom and from left to right. Source code is saved in a textual format and will be executed somehow.

### 1.2 Commands
Computers execute different operations, or actions, based on the commands. For example, when printing the text "Hello world!" on the screen, it is done by the command System.out.println.

```java
System.out.println("Hello world!");
```

The `System.out.println` command prints the string given inside the brackets on the screen. The suffix ln is short for the word line. Therefore, this command prints out a line. This means that after the given string has been printed, the command will also print a line break.

### 1.3 Compiler and interpreter
Computers do not directly understand the programming language we are using. We need a compiler between the source code and the computer. When we are programming using the command line interface, the command `javac Hello.java` will compile the `Hello.java` file into bytecode, which can be executed using the Java interpreter. To run the compiled program, you can use the command `java Hello` where Hello is the name of the original source code file.

When using a modern development environment (more on this later), it will take care of compiling the source code. When we choose to run the program, the development environment will compile and execute the program. All development environments compile source code while it is being written by the programmer, which means that simple errors will be noticed before executing the program.

### 1.4 Components of commands

#### 1.4.1 Semicolon
A semicolon ; is used to separate different commands. The compiler and the interpreter both ignore line breaks in the source code, so we could write the entire program on a single line.

In the example below we will use the System.out.print command, which is similar to the System.out.println command except that it will not print a line break after printing the text.

Example of how the semicolons are used
```java
System.out.print("Hello "); System.out.print("world");
System.out.print("!");
```

```output
Hello world!
```

Even though neither the compiler nor the interpreter need line breaks in the source code, they are very important when considering human readers of the source code. Line breaks are required to divide source code in a clear manner. Readability of source code will be emphasized throughout this course.

#### 1.4.2 Parameters (information passed to commands)

The information processed by a command are the parameters of a command. They are passed to the command by placing them between () brackets that follow the command name. For example, the System.out.print command is given the text hello as a parameter as follows: `System.out.print("hello")`.

#### 1.4.3 Comments

Comments are a useful way to make notes in the source code for yourself and others. There are 2 different ways of adding comments to your code.

* By adding `//` in front of the comment.  
  Everything on a line after the `//` will be treated as comments
* By putting `/*` and `*/` around the comment.  
  Everything inbetween the `/*` and `*/` will be treated as comments, even newlines. This can be used for multiline comments. This is very often used for adding documentation to your code, more on that in week 2

#### 1.4.4 Example of using comments
```java
// We will print the text "Hello world"
System.out.print("Hello world");

System.out.print(" and all the people of the world."); // We print more text to the same line.

/*
System.out.print("This line will also not be executed");
*/

System.out.print("Hello" /* this was hello world*/);

// System.out.print("this line will not be executed, because it is commented out");
```
The last line of the example introduces a particularly handy use for comments: you can comment out code instead of completely deleting it if you want to temporarily try out something.

> You can quickly comment and uncomment multiple lines in IntelliJ by selecting the lines you want to comment, and pressing *Ctrl*{: .key} + */*{: .key}.
{: .tip}

### 1.5 More about printing

As we can see from the examples above, there are two commands for printing.

- `System.out.print` prints the text without the line break at the end
- `System.out.println` prints the text and the line break

The printed text can contain both traditional characters and special characters. The most important special character is \n, which stands for a line break. There are also other special characters.

```java
System.out.println("First\nSecond\nThird");
```

When executed, the example above prints:

```output
First
Second
Third
```

These special characters are called *escape characters*, and always start with a `\`. Other special characters are

* `\t`  
  Prints a tab character and aligns the next text
* `\\`  
  Prints a backspace (\) character
* `\"`  
  Prints a " character
* `\'`  
  Prints a ' character

A full reference of characters can be found at the [java](https://docs.oracle.com/javase/tutorial/java/data/characters.html) website
