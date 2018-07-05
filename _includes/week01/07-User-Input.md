## 7. Reading User Input

So far our programs have been rather one-sided. Next we will learn how to read *input* from the user. We will use a special `Scanner` tool to read the user input.

Let us add the `Scanner` to our existing main program body. Do not worry if the main program body seems obscure as we will continue to write our code in the part marked *// program code.*

```java
import java.util.Scanner;

public class ProgramBody {
    public static void main(String[] args) {
        Scanner reader = new Scanner(System.in);

        // program code
    }
}
```

### 7.1 Reading a string

```java
System.out.print("What is your name? ");
String name = reader.nextLine(); // Reads a line of input from the user and assigns it
                                 //     to the variable called name

System.out.println("Hi, " + name);
```

```output
What is your name? ~~John~~
Hi, John
```

The program above combined along with the main program body is shown below. The name of the program is *Greeting*, which means that it must be located in a file named `Greeting.java`.

```java
import java.util.Scanner;

public class Greeting {
    public static void main(String[] args) {
        Scanner reader = new Scanner(System.in);

        System.out.print("Who is greeted: ");
        String name = reader.nextLine(); // Reads a line of input from the user and assigns it
                                         //     to the variable called name

        System.out.print("Hi " + name);
    }
}
```

When the program above is executed, you can type the input. The output tab in IntelliJ (at the bottom) looks as follows when the program has finished (the user inputs the name "John").

```output
Who is greeted: ~~John~~
Hi John
Process finished with exit code 0
```

### 7.2 Reading integers

Our Scanner tool is not good for reading integers, so we will use another special tool to read an integer. The command `Integer.parseInt` converts the string given to it into an integer. The command's parameter is given between brackets and it returns an integer that can be assigned to an integer variable.

Basically, we are joining two commands together. First we read the input as a string from the user and immediately give it to the command `Integer.parseInt`.

```java
System.out.print("Type an integer: ");
int number = Integer.parseInt(reader.nextLine());

System.out.println("You typed " + number);
```

Next we will ask the user to give us his name and age. The program body is included this time.


```java
import java.util.Scanner;

public class NameAndAgeGreeting {
    public static void main(String[] args) {
        Scanner reader = new Scanner(System.in);

        System.out.print("Your name: ");
        String name = reader.nextLine();   // Reads a line from the users keyboard

        System.out.print("How old are you: ");
        int age = Integer.parseInt(reader.nextLine()); // Reads a string variable from the keyboard and transfers it to an integer

        System.out.println("Your name is: " + name + ", and you are " + age + " years old, nice to meet you!");
    }
}
```

### 7.3 Summary

The program body for interaction with the user is as follows:

```java
import java.util.Scanner;
public class ProgramName {
    public static void main(String[] args) {
        Scanner reader = new Scanner(System.in);

        // code here
    }
}
```

Reading a string:

```java
String text = reader.nextLine();
```

Reading an integer:

```java
int number = Integer.parseInt(reader.nextLine());
```

{% include week01/exercise/008.md %}
{% include week01/exercise/009.md %}
{% include week01/exercise/010.md %}
{% include week01/exercise/011.md %}
{% include week01/exercise/012.md %}
{% include week01/exercise/013.md %}
{: .exercises }
