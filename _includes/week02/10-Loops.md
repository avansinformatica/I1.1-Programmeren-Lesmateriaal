## 10. Introduction to loops

Conditional statements allow us to execute different commands based on the conditions. For example, we can let the user login only if the username and password are correct.

In addition to conditions we also need repetitions. We may, for example, need to keep asking the user to input a username and password until a valid pair is entered.

The most simple repetition is an infinite loop. The following code will print out the string *I can program!* forever or "an infinite number of times":

```java
while (true) {
    System.out.println("I can program!");
}
```

In the example above, the `while (true)` command causes the associated block (i.e. the code between the curly braces `{}`) to be *looped* (or repeated) infinitely.

We generally do **not** want an infinite loop. The loop can be interrupted by changing the condition in the while-loop

```java
boolean running = true;
while (running) {
    System.out.println("I can program!");

    System.out.print("Continue? ('no' to quit)? ");
    String command = reader.nextLine();
    if (command.equals("no")) {
        running = false;
    }
}

System.out.println("Thank you and see you later!");
```

Now the loop progresses like this: First, the program prints *I can program!*. Then, the program will ask the user if it should continue. If the user types *no*, the variable `running` is set to false, and the loop stops and *Thank you and see you again!* is printed. Take note that the commands in the loop will continue to execute, and the loop will stop at the end of the code block in the loop. As there is no other code in the loop, it stops immediately 

```output
I can program!
Continue? ('no' to quit)? ~~yeah~~
I can program!
Continue? ('no' to quit)? ~~jawohl~~
I can program!
Continue? ('no' to quit)? ~~no~~
Thank you and see you again!
```

Many different things can be done inside a loop. Next we create a simple calculator, which performs calculations based on commands that the user enters. If the command is *quit*, the variable running will be set to false, and the program will quit. Otherwise two numbers are asked. Then, if the initial command was *sum*, the program calculates and prints the sum of the two numbers. If the command was *difference*, the program calculates and prints the difference of the two numbers. If the command was something else, the program reports that the command was unknown.

```java
System.out.println("welcome to the calculator");
boolean running = true;
while (running) {
    System.out.print("Enter a command (sum, difference, quit): ");
    String command = reader.nextLine();
    if (command.equals("quit")) {
        running = false;
    } else {
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
}

System.out.println("Thanks, bye!");
```

{% include week02/exercise/001.md %}
{% include week02/exercise/002.md %}
{% include week02/exercise/003.md %}
{% include week02/exercise/004.md %}
{: .exercises }
