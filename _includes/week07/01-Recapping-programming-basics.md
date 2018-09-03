## 1. Recapping programming basics

In this chapter we briefly recap a few concepts we became familiar with in Part 1. You can familiarize yourself with the programming basics course material here.

### 1.1 Program, commands and variables

A computer program consists of a series of commands that a computer runs one at a time, from top to bottom. The commands always have a predefined structure and semantics. In Java - the programming language we use in this course - the commands are read from top to bottom, left to right. Programming courses are traditionally started by introducing a program that prints the string `Hello World!`. Below is a command written in Java that prints the Hello World! string.

```java
    System.out.println("Hello World!");
```

In the command the method println - which belongs to the System class - gets called, which prints the string passed in to it as a parameter, and after that a linebreak. The method is given the string `Hello World!` as a parameter; consequently the program prints out `Hello World!` followed by a linebreak.

Variables can be used as part of the functionality of the program. Below is a program which introduces the variable length of the integer type. The value 197 is set to this variable on the next line. After this the value 179 of the variable length is printed.

```java
    int length;
    length = 179;
    System.out.println(length);
```

The execution of the program above would happen one line at a time. First the line `int length;` is executed, in which the variable length is introduced. Next the line `length = 179;` is executed, in which we set the value `179` to the variable that was introduced on the previous line. After this the line `System.out.println(length);` is run, in which we call the print method we saw earlier. To this method we give the variable length as a parameter. The method prints the content - the value - of the variable length, which is `179`.

In the program above we really wouldn't have to introduce the variable length on one line and then set its value on the next. The introduction of a variable and setting its value can be done on the same line.

```java
    int length = 179;
```

When executing the above line, the variable length is introduced and as it is introduced the value `179` is set to it.

In reality all information within a computer is represented as a series of bits - ones and zeros. Variables are an abstraction offered by the programming language with which we can handle different values more easily. The variables are used to store values and to maintain the state of the program. In Java, we have the primitive variable types `int` (integer), `double` (floating-point), `boolean` (truth value), `char` (character), and the reference variable types `String` (character string), `ArrayList` (array), and all classes. We'll return to primitive data type variables and to reference type variables and their differences later.

### 1.2 Comparing variables and reading input

The functionality of programs is built with the help of control structures. Control structures make different functions possible depending on the variables of the program. Below, an example of an `if - else if - else` control structure, in which a different function is executed depending on the result of the comparison. In the example a string Accelerate is printed if the value of the variable speed is smaller than 110, the string Break if the speed is greater than 120, and the string `Cruising` in other cases.

```java
int speed = 105;

if (speed < 110) {
    System.out.println("Accelerate");
} else if (speed > 120) {
    System.out.println("Break");
} else {
    System.out.println("Cruising");
}
```
    
Because in the example above the value of the variable `speed` is 105, the program will always print the string `Accelerate`. Remember that the comparison of strings is done with the equals method that belongs to the [`String`](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html) class. Below is an example in which an object created from Java's [`Scanner`](https://docs.oracle.com/javase/7/docs/api/java/util/Scanner.html) class is used to read the input of a user. The program checks if the strings entered by the user are equal.

```java
Scanner reader = new Scanner(System.in);

System.out.print("Enter the first string: ");
String first = reader.nextLine();

System.out.print("Enter the second string: ");
String second = reader.nextLine();

System.out.println();

if (first.equals(second)) {
    System.out.println("The strings you entered are the same!");
} else {
    System.out.println("The strings you entered weren't the same!");
}
```

The functionality of the program depends on the user's input. Below is an example; the red text is user input.

```output
Enter the first string: ~~carrot~~
Enter the second string: ~~lettuce~~

The strings you entered weren't the same!
```

### 1.3 Loops

Repetition is often required in programs. First we make a `so-called while-true-break` loop, which we run until the user inputs the string `password`. The statement `while(true)` begins the loop, which will then be repeated until it runs into the keyword `break`.

```java
Scanner reader = new Scanner(System.in);

boolean running = true;
while (running) {
    System.out.print("Enter password: ");
    String password = reader.nextLine();

    if (password.equals("password")) {
        break;
    }
}

System.out.println("Thanks!");
```

```output
Enter password: ~~carrot~~
Enter password: ~~password~~
Thanks!
```

You can also pass a comparison to a `while` loop instead of the boolean `true`. Below, the user input is printed so that there are stars above and below it.

```java
Scanner reader = new Scanner(System.in);

System.out.print("Enter string: ");
String characterString = reader.nextLine();

int starNumber = 0;
while (starNumber < characterString.length()) {
    System.out.print("*");
    starNumber = starNumber + 1;
}
System.out.println();

System.out.println(characterString);

starNumber = 0;
while (starNumber < characterString.length()) {
    System.out.print("*");
    starNumber = starNumber + 1;
}
System.out.println();
```

```output
Enter string: ~~carrot~~
******
carrot
******
```
    
The example above should make you feel a little bad inside. The bad feelings are hopefully because you see that the example violates the rules learned in the programming basics. The example has unneccessary repetition which should be removed with the help of methods.

In addition to the `while-loop` we also have two versions of the `for-loop` at our disposal. The newer `for-each-loop` is used for going through lists.

```java
ArrayList<String> greetings = new ArrayList<String>();
greetings.add("Hei");
greetings.add("Hallo");
greetings.add("Hi");

for (String greet: greetings) {
    System.out.println(greet);
}
```

```output
Hei
Hallo
Hi
```
    
The more traditional `for-loop` is used in situations similar to where you would use a `while-loop`. It can, for example, be used to go through arrays. In the following example all values in the array values will be multiplied by two and then finally printed using the newer `for-loop`.

```java
int[] values = new int[] {1, 2, 3, 4, 5, 6};

for (int i = 0; i < values.length; i++) {
    values[i] = values[i] * 2;
}

for (int value: values) {
    System.out.println(value);
}
```

```output
2
4
6
8
10
12
```
 
The traditional `for-loop` is very useful in cases where we go through indices one at a time. The loop below will go through the characters of a character string one by one, and prints the character string `Hip!` every time we encounter the character `a`.

```java
String characterString = "saippuakauppias";
for (int i = 0; i < characterString.length(); i++) {
    if (characterString.charAt(i) == 'a') {
        System.out.println("Hip!");
    }
}
```

```output 
Hip!
Hip!
Hip!
Hip!
```

### 1.4 Methods

Methods are a way of chopping up the functionality of a program into smaller entities. All Java programs start their execution from the `main` program method, which is defined with the statement `public static void main(String[] args)`. This statement defines a `static` method - that is a method which belongs to the `class` - which receives a character string array as its parameter.

The program defines methods to abstract the functionalities of the program. When programming, one should try to achieve a situation in which the program can be looked at from a `higher level`, in such a case the main method consists of calls to a group of self-defined, well-named methods. The methods then specify the functionality of the program and perhaps are based on calls to other methods.

Methods that are defined using the keyword `static` belong to the *class* that holds the method, and work as so-called support methods. The methods that are defined without the keyword static belong to the instances - the objects - created from the class and can modify the state of that individual object.

A method always has a visibility modifier (`public`, visible to 'everyone', or `private`, only visible within its class), a return type (in the main method this is `void`, which returns nothing) and a name. In the following code we create a method which belongs to a class, `public static void print(String characterString, int times)`. This method prints a character string the defined amount of times. This time we use the method `System.out.print`, which works just like `System.out.println`, but doesn't print a linebreak.

```java
public static void print(String characterString, int times) {
    for (int i = 0; i < times; i++) {
        System.out.print(characterString);
    }
}
```

The method above prints the character string it receives as a parameter an amount of times equal to the integer - which was also passed in as a parameter.

In the section on loops we noticed that the code had some nasty copy-paste stuff in it. With the help of methods, we can move the printing of stars to a separate method. We create a method `public static void printStars(int times)`, which prints the amount of stars it receives as a parameter. The method uses a for loop instead of a while.

```java
public static void printStars(int times) {
    for (int i = 0; i < times; i++) {
        System.out.print("*");
    }
    System.out.println();
}
```

When making use of a method, our previous (and hideous) example now looks like the following.

```java
Scanner reader = new Scanner(System.in);

System.out.print("Enter characterString: ");
String characterString = reader.nextLine();

printStars(characterString.length());
System.out.println(characterString);
printStars(characterString.length());
```

### 1.5 Class

Methods can abstract a program up to a certain point, but as the program becomes larger it's sensible to chop down the program even further into smaller and more logical entities. With the help of classes, we can define higher level concepts of a program and functionalities related to those concepts. Every Java program requires a class in order to work, so the Hello World! example wouldn't work without the class definition. A class is defined with the keywords `public class nameOfTheClass`.

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```
 
In a program, classes are used to define concepts and functionalities related to those concepts. Objects can be created from a class and are the embodiments of that class. Every object that belongs to a certain class has the same structure, but the variables belonging to each objects can be different. The methods of objects handle the *state* of the object, that is, the variables of the object.

Let's inspect the class `Book` below; the class has the object variables `name` (String) and `publishingYear` (integer).

```java
public class Book {
    private String name;
    private int publishingYear;

    public Book(String name, int publishingYear) {
        this.name = name;
        this.publishingYear = publishingYear;
    }

    public String getName() {
        return this.name;
    }

    public int getPublishingYear() {
        return this.publishingYear;
    }
}
```

The definition in the beginning, `public class Book`, tells the name of the class. This is followed by the definitions of object variables. Object variables are variables which for each of the objects created from the class are their own -- the object variables of one object are unrelated to the state of the same variables of another object. It's usually appropriate to hide the object variables from the users of the class, to define the visibility modifier `private` for them. If the visibility modifier is set to public, the user of the object will be able to directly access the object variables.

Objects are created from a class with a `constructor`. A constructor is a method that initializes an object (creates the variables belonging to the object) and executes the commands that are within the constructor. The constructor is always named the same as the class that has the constructor in it. In the constructor `public Book(String name, int publishingYear)` a new object is created from the class `Book` and its variables are set to the values that were passed in as parameters.

Two methods that handle the information in the object are also defined for the class above. The method `public String getName()` returns the name of the object in question. The method `public int getPublishingYear()` returns the publishing year of the object in question.

### 1.6 Object

*Objects* are created with the help of the constructor that is defined within a class. In the program code the costructor is called with the new command, which returns a reference to the new object. Objects are instances created from classes. Let's inspect a program that creates two different books, after which it prints the values returned by the `getName` methods belonging to the objects.

```java
Book senseAndSensibility = new Book("Sense and Sensibility", 1811);
Book prideAndPrejudice = new Book("Pride and Prejudice", 1813);

System.out.println(senseAndSensibility.getName());
System.out.println(prideAndPrejudice.getName());
```

```output
Sense and Sensibility
Pride and Prejudice
```

So, each object has its own internal state. The state is formed from object variables that belong to the object. Object variables can be both primitive type variables and reference type variables. If reference type variables belong to the objects, it is possible that other objects also refer to the same referenced objects! Let's visualize this with the bank example, in which there are accounts and persons.

```java
public class Account {
    private String accountID;
    private int balanceAsCents;

    public Account(String accountID) {
        this.accountID = accountID;
        this.balanceAsCents = 0;
    }

    public void deposit(int sum) {
        this.balanceAsCents += sum;
    }

    public int getBalanceAsCents() {
        return this.balanceAsCents;
    }

    // .. other methods related to an account
}
```

```java
import java.util.ArrayList;

public class Person {
    private String name;
    private ArrayList<Account> accounts;

    public Person(String name) {
        this.name = name;
        this.accounts = new ArrayList<Account>();
    }

    public void addAccount(Account account) {
        this.accounts.add(account);
    }

    public int moneyTotal() {
        int total = 0;
        for (Account account: this.accounts) {
            total += account.getBalanceAsCents();
        }

        return total;
    }

    // ... other methods related to a person
}
```

Each object created from the Person class has its own name and its own list of accounts. Next, let's create two persons and two accounts. One of the accounts is owned by only one person and the other one is shared.

```java
Person matti = new Person("Matti");
Person maija = new Person("Maija");

Account salaryAccount = new Account("NORD-LOL");
Account householdAccount = new Account("SAM-LOL");

matti.addAccount(salaryAccount);
matti.addAccount(householdAccount);
maija.addAccount(householdAccount);

System.out.println("Money on Matti's accounts: " + matti.moneyTotal());
System.out.println("Money on Maija's accounts: " + maija.moneyTotal());
System.out.println();

salaryAccount.deposit(150000);

System.out.println("Money on Matti's accounts: " + matti.moneyTotal());
System.out.println("Money on Maija's accounts: " + maija.moneyTotal());
System.out.println();

householdAccount.deposit(10000);

System.out.println("Money on Matti's accounts: " + matti.moneyTotal());
System.out.println("Money on Maija's accounts: " + maija.moneyTotal());
System.out.println();
```

```output
Money on Matti's accounts: 0
Money on Maija's accounts: 0

Money on Matti's accounts: 150000
Money on Maija's accounts: 0

Money on Matti's accounts: 160000
Money on Maija's accounts: 10000
```

Initially, the accounts of both persons are empty. When money is added to the salaryAccount - which `matti` has a reference to - the amount of money on Matti's accounts grows. When money is added to the householdAccount the amount of money each person has grows. This is because both Matti and Maija have "access" to the householdAccount, so in each of the persons' object variable `accounts`, there's a reference to the householdAccount.

### 1.7 The structure of a program

A program should be clear and easy to understand for both the original  writer and others. The most important aspects of a clear program are class structure and good naming conventions. Each class should have a single, clearly defined responsibility. Methods are used to reduce repetition and to create a structure for the internal functionality of the class. A method should also have a clear responsibility to ensure it stays short and simple. Methods that do many things should be divided into smaller helper methods, which are called by the original method. A good programmer writes code that can be understood even weeks after it was originally written.

Good, understandable code uses descriptive naming of variables, methods and classes, and consistent indentation. Let's look at the example below, a small program for buying and selling goods. Even though the only thing available is carrots, with no bookkeeping, the user interface could be extended to use a storage class to keep track of items.

```java
public class UserInterface {
    private Scanner reader;

    public UserInterface(Scanner reader) {
        this.reader = reader;
    }

    public void start() {
        while (true) {
            String command = reader.nextLine();

            if (command.equals("end")) {
                break;
            } else if (command.equals("buy")) {
                String line = null;
                while(true) {
                    System.out.print("What to buy: ");
                    line = reader.nextLine();
                    if(line.equals("carrot")) {
                        break;
                    } else {
                        System.out.println("Item not found!");
                    }
                }

                System.out.println("Bought!");
            } else if (command.equals("sell")) {
                String line = null;
                while(true) {
                    System.out.print("What to sell: ");
                    line = reader.nextLine();
                    if(line.equals("carrot")) {
                        break;
                    } else {
                        System.out.println("Item not found!");
                    }
                }

                System.out.println("Sold!");
            }
        }
    }
}
```

This example has numerous problems. The first problem is the long start method. It can be shortened by moving most of the command handling to a separate method.

```java
public class UserInterface {
    private Scanner reader;

    public UserInterface(Scanner reader) {
        this.reader = reader;
    }

    public void start() {
        while (true) {
            String command = reader.nextLine();

            if (command.equals("end")) {
                break;
            } else {
                handleCommand(command);
            }
        }
    }

    public void handleCommand(String command) {
        if (command.equals("buy")) {
            String line = null;
            while(true) {
                System.out.print("What to buy: ");
                line = reader.nextLine();
                if(line.equals("carrot")) {
                    break;
                } else {
                    System.out.println("Item not found!");
                }
            }

            System.out.println("Bought!");
        } else if (command.equals("sell")) {
            String line = null;
            while(true) {
                System.out.print("What to sell: ");
                line = reader.nextLine();
                if(line.equals("carrot")) {
                    break;
                } else {
                    System.out.println("Item not found!");
                }
            }

            System.out.println("Sold!");
        }
    }
}
```

`handleCommand` still has some repetition for reading the user input. Both buying and selling first print a character string with the question, then take input from the user. If the input is incorrect (other than "carrot"), "Item not found!" is printed. We will create a new method, `public String readInput(String question)`, to handle this. Note that if the program used some other object to keep track of inventory, we would compare user input to the inventory's contents instead.

```java
public class UserInterface {
    private Scanner reader;

    public UserInterface(Scanner reader) {
        this.reader = reader;
    }

    public void start() {
        while (true) {
            String command = reader.nextLine();

            if (command.equals("end")) {
                break;
            } else {
                handleCommand(command);
            }
        }
    }

    public void handleCommand(String command) {
        if (command.equals("buy")) {
            String input = readInput("What to buy: ");
            System.out.println("Bought!");
        } else if (command.equals("sell")) {
            String input = readInput("What to sell: ");
            System.out.println("Sold!");
        }
    }

    public String readInput(String question) {
        while (true) {
            System.out.print(question);
            String line = reader.nextLine();

            if (line.equals("carrot")) {
                return line;
            } else {
                System.out.println("Item not found!");
            }
        }
    }
}
```

The program is now divided into appropriate parts. There are still a few things, other than implementing more methods, we can do to improve readability. The `start` method has an `if` branch that ends in `break`, which exits the loop. We can remove the unnecessary `else` branch, simply moving the `handleCommand` method to be called after the `if` statement. The program still works exactly as before, but the method is now shorter and easier to read. A similar situation exists in the `readInput` method, so we will clean it up too.

```java
public class UserInterface {
    private Scanner reader;

    public UserInterface(Scanner reader) {
        this.reader = reader;
    }

    public void start() {
        while (true) {
            String command = reader.nextLine();

            if (command.equals("end")) {
                break;
            }

            handleCommand(command);
        }
    }

    public void handleCommand(String command) {
        if (command.equals("buy")) {
            String input = readInput("What to buy: ");
            System.out.println("Bought!");
        } else if (command.equals("sell")) {
            String input = readInput("What to sell: ");
            System.out.println("Sold!");
        }
    }

    public String readInput(String question) {
        while (true) {
            System.out.print(question);
            String line = reader.nextLine();

            if (line.equals("carrot")) {
                return line;
            }

            System.out.println("Item not found!");
        }
    }
}
```

Dividing a program into smaller parts, like we did above, is called *refactoring*. It does not change how the program works, but the internal structure is changed to be more clear and easier to maintain. The current version is clearer than the original, but it can be improved further. For example, `handleCommand` can be further divided into two different methods, one for handling buying and the other for selling.

```java
public class UserInterface {
    private Scanner reader;

    public UserInterface(Scanner reader) {
        this.reader = reader;
    }

    public void start() {
        while (true) {
            String command = reader.nextLine();

            if (command.equals("end")) {
                break;
            }

            handleCommand(command);
        }
    }

    public void handleCommand(String command) {
        if (command.equals("buy")) {
            commandBuy();
        } else if (command.equals("sell")) {
            commandSell();
        }
    }

    public void commandBuy() {
        String input = readInput("What to buy: ");
        System.out.println("Bought!");
    }

    public void commandSell() {
        String input = readInput("What to sell: ");
        System.out.println("Sold!");
    }

    public String readInput(String question) {
        while (true) {
            System.out.print(question);
            String line = reader.nextLine();

            if (line.equals("carrot")) {
                return line;
            } else {
                System.out.println("Item not found!");
            }
        }
    }
}
```
    
The program now has a clear structure with descriptively named methods. Every method is short and has a small task to handle. Note that refactoring the code did not add any new functionality, it merely changed the way the program works internally.

### 1.8 Programming and the importance of practicing

As far as we know, nobody has yet learned programming by listening to lectures. To develop the skill required in programming, it is essential to practice both what you have learned earlier and things that are new to you. Programming can be compared to speaking languages or playing an instrument, both of which can only be learned by doing. Master violinists are probably not good at playing *only* because they practice a lot. Playing an instrument is fun, which makes one more motivated to practice. The same applies to programming.

As Linus Torvalds said, *"Most good programmers do programming not because they expect to get paid or get adulation by the public, but because it is fun to program"*.

Dr. Luukkainen has written a list of instructions for new programmers to follow when learning to program. Follow this advice to become a great programmer!

- Take small steps
  - Divide the problem you are trying to solve into smaller parts and solve them **one at a time**
  - Keep testing that your solution is moving in the right direction, ensuring that you have solved the current part correctly
- Keep the code as clean as you can
  - use proper indentation
  - use descriptive names for variables, methods, classes, everything
  - keep all methods short, including main
  - write methods that only do one thing
  - **remove all copy-paste code by refactoring (or don't copy and paste code in the first place!)**
  - replace "bad" and unclear code with clean, easy to read code

### 1.9 Visibility

Until now, we have been using two different keywords to define the *visibility* of methods and instance variables. public makes the method or instance variable visible and accessable to everyone. Methods and constructors are usually marked as `public`, so that they can be called from outside the class.

Declaring a method or instance variable `private` hides it from the outside, making it only accessible from inside the same class.

```java
public class Book {
    private String name;
    private String contents;

    public Book(String name, String contents) {
        this.name = name;
        this.contents = contents;
    }

    public String getName() {
        return this.name;
    }

    public String getContents() {
        return this.contents;
    }

    // ...
}
```

The instance variables in the `Book` class above can only be accessed with the public methods `getName` and `getContents`. Fields declared as private are only accessible in code inside the class. Methods can also be declared as private, which prevents them from being called outside the class.

Now it's time to start practicing!

{% include week07/exercise/001.md %}
{% include week07/exercise/002.md %}
{% include week07/exercise/003.md %}
{: .exercises }