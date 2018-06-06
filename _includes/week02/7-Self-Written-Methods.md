## 2.7. Self-written methods

This far we have been using a programming style where code is written (and read and executed) from top to bottom.

It was mentioned before that "a method is a piece of code that can be called from different places of the program code". Ready-made methods of Java have been used since our very first program.

In addition to using these ready-made methods programmers can write their own methods for programs to call. In the real world, it is really exceptional if the program does not include any self-written methods. From now on almost every program we create during this course will include self-written methods.

The methods are written in the program body outside the main's braces ( { and } ) but still inside the outermost braces, for example like this: :

```java
import java.util.Scanner;

public class ProgramBody {
    public static void main(String[] args) {
        Scanner reader = new Scanner(System.in);
        // program code
    }

    // self-written methods
}
```

Let us create a method `greet`.

```java
public static void greet() {
    System.out.println("Greetings from the world of methods!");
}
```

And let us place it in the right spot.

```java
import java.util.Scanner;

public class ProgramBody {
    public static void main(String[] args) {
        Scanner reader = new Scanner(System.in);
        // program code
    }

    // self-written methods
    public static void greet() {
        System.out.println("Greetings from the world of methods!");
    }
}
```

In order to define a new method we need to write two things. In the first row of the method definition, you will find the name of the method, in this case greet. On the left side of the name you will find the definitions `public static void`. On the next line, the code block marked by the braces ({ and }). Inside it, the method's code, or the commands that will be executed when the method is called. Our method `greet` only writes one line of text to the screen.

It is easy to call a self-written method. It happens by writing the method name, brackets () and a semicolon. In the next example main (or the main program) calls for our method, first once and then several times.

```java
import java.util.Scanner;

public class ProgramBody {
    public static void main(String[] args) {
        Scanner reader = new Scanner(System.in);

        // program code
        System.out.println("Let us try if we can get to the method world:");
        greet();

        System.out.println("It seems like we can, let us try again:");
        greet();
        greet();
        greet();
    }

    // self-written methods
    public static void greet() {
        System.out.println("Greetings from the world of methods!");
    }
}
```

When the program is executed, we see the following output:

```output
Let us try if we can get to the method world:
Greetings from the world of methods!
It seems like we can, let us try again:
Greetings from the world of methods!
Greetings from the world of methods!
Greetings from the world of methods!
```

What is noteworthy here is the execution order of the program code. The execution starts with the main program's (or main's) lines of code, from top to bottom, one by one. When the line of code to be executed happens to be a method call, the lines of code in the method block are executed again one by one. When the method block ends, the execution continues from the place where the method was called. To be exact, the execution continues from the next line after the original method call.

To be even more exact, the main program is also a method. When the program starts, the operation system calls for the main method. That means that the main method is the starting point of the program and the execution starts from the first code line of main. The program execution ends when it reaches the end of main.

From now on when we introduce methods, we will not point out that they need to be written in the right place inside the program code. For example, a method cannot be defined inside another method.


{% include week02/exercise/016.md %}
{% include week02/exercise/017.md %}
{: .exercises }

### 2.7.1 Method parameters

We can make our methods more useful by giving it *parameters*! Parameters are variables that we define inside brackets in the first line, just after the method name. When the method is called, the parameters are assigned values.

In the next example we define a method with a parameter, its name will be greet and its parameter will be a variable of the type String called `name`.

```java
public static void greet(String name) {
    System.out.println("Hi " + name + ", greetings from the world of methods!");
}
```

Let us next call the `greet` method so that on the first try we give its parameter the value `Matt` and on the second try `Arthur`.

```java
public static void main(String[] args) {
    greet("Matt");
    greet("Arthur");
}
```

```output
Hi Matt, greetings from the world of methods!
Hi Arthur, greetings from the world of methods!
```

More complicated expressions can also be used as a parameter for our self-written methods, the same way we used them together with the ready-made `System.out.println()` method.

```java
public static void main(String[] args) {
    String name1 = "Anne";
    String name2 = "Green";
    greet( name1 + " " + name2 );

    int age = 24;
    greet("John " + age + " years");
}
```

```output
Hi Anne Green, greetings from the world of methods!
Hi John 24 years, greetings from the world of methods!
```

In both cases the method has only one parameter. The value for the parameter is calculated before calling the method. In the first case the parameter value comes from the String concatenation (a cool word that means putting the text together) `name1 + " " + name2`. The value for the concatenation is *Anne Green*. In the second case we get the parameter value from the String concatenation `"John " + age + " years"`.

### 2.7.2 Many parameters

A method can be defined to have more than one parameter. In this case, the parameters are always listed in the same order.

```java
public static void greet(String name, String greetingsFrom) {
    System.out.println("Hi " + name + ", greetings from " + greetingsFrom);
}
```

```java
String who = "Matt";
String greetings = "Alabama";

greet(who, greetings);
greet(who, greetings + " from Nevada");
```

In the last `greet` function (or method) call the second parameter is formed by concatenating (or adding) the text “from Nevada” to the variable `greetings`. This is done before the actual function call.

```output
Hi Matt, greetings from Alabama
Hi Matt, greetings from Alabama from Nevada
```

### 2.7.3 Method calling another method

Methods can also be called outside of main. Methods can call each other! Let us create a method greetManyTimes that greets the user many times getting assistance from the method `greet`:

```java
public static void greet(String name) {
    System.out.println("Hi " + name + ", greetings from the world of methods!");
}

public static void greetManyTimes(String name, int times) {
    int i = 0;
    while ( i < times ) {
        greet(name);
        i++;
    }

}

public static void main(String[] args) {
    greetManyTimes("Anthony", 3);
    System.out.println("and");
    greetManyTimes("Martin", 2);
}
```

Output:

```output
Hi Anthony, greetings from the world of methods!
Hi Anthony, greetings from the world of methods!
Hi Anthony, greetings from the world of methods!
and
Hi Martin, greetings from the world of methods!
Hi Martin, greetings from the world of methods!
```

{% include week02/exercise/018.md %}
{% include week02/exercise/019.md %}
{% include week02/exercise/020.md %}
{% include week02/exercise/021.md %}
{: .exercises }
