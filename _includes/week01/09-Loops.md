## 9. Introduction to loops

Conditional statements allow us to execute different commands based on the conditions. For example, we can let the user login only if the username and password are correct.

In addition to conditions we also need repetitions. We may, for example, need to keep asking the user to input a username and password until a valid pair is entered.

The most simple repetition is an infinite loop. The following code will print out the string *I can program!* forever or "an infinite number of times":

```java
while (true) {
    System.out.println("I can program!");
}
```

In the example above, the `while (true)` command causes the associated block (i.e. the code between the curly braces `{}`) to be *looped* (or repeated) infinitely.

We generally do **not** want an infinite loop. The loop can be interrupted using e.g. the break command.

```java
while (true) {
    System.out.println("I can program!");

    System.out.print("Continue? ('no' to quit)? ");
    String command = reader.nextLine();
    if (command.equals("no")) {
        break;
    }
}

System.out.println("Thank you and see you later!");
```

Now the loop progresses like this: First, the program prints *I can program!*. Then, the program will ask the user if it should continue. If the user types *no*, the `break` command is executed and the loop is interrupted and *Thank you and see you again!* is printed.

```output
I can program!
Continue? ('no' to quit)? ~~yeah~~
I can program!
Continue? ('no' to quit)? ~~jawohl~~
I can program!
Continue? ('no' to quit)? ~~no~~
Thank you and see you again!
```

Many different things can be done inside a loop. Next we create a simple calculator, which performs calculations based on commands that the user enters. If the command is *quit*, the `break` command will be executed to end the loop. Otherwise two numbers are asked. Then, if the initial command was *sum*, the program calculates and prints the sum of the two numbers. If the command was *difference*, the program calculates and prints the difference of the two numbers. If the command was something else, the program reports that the command was unknown.

```java
System.out.println("welcome to the calculator");

while (true) {
    System.out.print("Enter a command (sum, difference, quit): ");
    String command = reader.nextLine();
    if (command.equals("quit")) {
        break;
    }

    System.out.print("enter the numbers");
    int first = Integer.parseInt(reader.nextLine());
    int second = Integer.parseInt(reader.nextLine());

    if (command.equals("sum") ) {
        int sum = first + second;
        System.out.println( "The sum of the numbers is " + sum );
    } else if (command.equals("difference")) {
        int difference = first - second;
        System.out.println("The difference of the numbers is " + difference);
    } else {
        System.out.println("Unknown command");
    }

}

System.out.println("Thanks, bye!");
```


{% include week01/exercise/022.md %}
{% include week01/exercise/023.md %}
{% include week01/exercise/024.md %}
{: .exercises }