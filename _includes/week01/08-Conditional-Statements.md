## 8. Conditional statements and truth values

So far, our programs have progressed from one command to another in a straightforward manner. In order for the program to *branch* to different execution paths based on e.g. user input, we need conditional statements.

```java
int number = 11;

if (number > 10) {
    System.out.println("The number was greater than 10");
}
```

The condition `(number > 10)` evaluates into a truth value; either `true` or `false`. The if command only handles truth values. The conditional statement above is read as "if the number is greater than 10".

Note that the `if` statement is not followed by semicolon as the condition path continues after the statement.

After the condition, the opening curly brace `{` starts a new *block*, which is executed if the condition is true. The *block* ends with a closing curly brace `}`. Blocks can be as long as desired.

The comparison operators are:

* \> Greater than
* \>= Greater than or equal to
* < Less than
* <= Less than or equal to
* == Equals
* != Not equal

```java
int number = 55;

if (number != 0) {
    System.out.println("The number was not equal to 0");
}

if (number >= 1000) {
    System.out.println("The number was greater than or equal to 1000");
}
```

A block can contain any code including other `if` statements.

```java
int x = 45;
int number = 55;

if (number > 0) {
    System.out.println("The number is positive!");
    if (number > x) {
        System.out.println(" and greater than the value of variable x");
        System.out.println("after all, the value of variable x is " + x);
    }
}
```

The comparison operators can also be used outside the if statements. In such case the truth value will be stored in a truth value variable.

```java
int first = 1;
int second = 3;

boolean isGreater = first > second;
```

In the example above the boolean (i.e. a truth value) variable `isGreater` now includes the truth value `false`.

A boolean variable can be used as a condition in a conditional sentence.

```java
int first = 1;
int second = 3;

boolean isLesser = first < second;

if (isLesser) {
    System.out.println(first + " is less than " + second + "!");
}
```

```output
1 is less than 3!
```

### 8.1 Code indentation

Note that the commands in the block following the if statement (i.e. the lines after the curly brace, { ) are not written at the same level as the if statement itself. They should be **indented** slightly to the right. Indentation happens when you press the tab key, which is located to the left of q key. When the block ends with the closing curly brace, indentation ends as well. The closing curly brace } should be on the same level as the original `if` statement.

The use of indentation is crucial for the readability of program code. During this course and generally everywhere, you are expected to indent the code properly. IntelliJ helps with the correct indentation. You can easily indent your program by pressing shift, alt, and f simultaneously. It's also possible to select a whole section of code, and press tab to indent this whole section

### 8.2 else

If the truth value of the comparison is false, another optional block can be executed using the `else` command.

```java
int number = 4;

if (number > 5) {
    System.out.println("Your number is greater than five!");
} else {
    System.out.println("Your number is equal to or less than five!");
}
```

```output
Your number is equal to or less than five!
```

{% include week01/exercise/014.md %}
{% include week01/exercise/015.md %}
{% include week01/exercise/016.md %}
{: .exercises }

### 8.3 else if

If there are more than two conditions for the program to check, it is recommended to use the `else if` command. It works like the `else` command, but with an additional condition. `else if` comes after the `if` command. There can be multiple `else if` commands.

```java
int number = 3;

if (number == 1) {
    System.out.println("The number is one.");
} else if (number == 2) {
    System.out.println("The number is two.");
} else if (number == 3) {
    System.out.println("The number is three!");
} else {
    System.out.println("Quite a lot!");
}
```

```output
The number is three!
```

Let us read out loud the example above: If number is one, print out "The number is one.". Otherwise if the number is two, print out "The number is two.". Otherwise if the number is three, print out "The number is three!". Otherwise print out "Quite a lot!".

### 8.4 Comparing strings

Strings cannot be compared using the equality operator (==). For string comparison, we use the `equals`. command, which is always associated with the string to compare.

```java
String text = "course";

if (text.equals("marzipan")) {
    System.out.println("The variable text contains the text marzipan");
} else {
    System.out.println("The variable text does not contain the text marzipan");
}
```

The `equals` command is always attached to the string variable with a dot in between. A string variable can also be compared to another string variable.

```java
String text = "course";
String anotherText = "horse";

if (text.equals(anotherText)) {
    System.out.println("The texts are the same!");
} else {
    System.out.println("The texts are not the same!");
}
```

When comparing strings, it is crucial to make sure that both string variables have been assigned some value. If a value has not been assigned, the program execution terminates with a *NullPointerException* error, which means that variable has no value assigned to it (null).

{% include week01/exercise/017.md %}
{% include week01/exercise/018.md %}
{: .exercises }

### 8.5 Logical operations

The condition statements can be made more complicated using logical operations. The logical operations are:

* `condition1 && condition2` is true if both conditions are true.
* `condition1 || condition2` is true if either of the conditions are true.
* `!condition` is true if the condition is false.

Below we will use the AND operation && to combine two individual conditions in order to check if the value of the variable is greater than 4 *and* less than 11 (i.e. in the range 5 - 10).

```java
System.out.println("Is the number between 5-10?");
int number = 7;

if (number > 4 && number < 11) {
    System.out.println("Yes! :)");
} else {
    System.out.println("Nope :(")
}
```

```output
Is the number between 5-10?
Yes! :)
```

Next up is the OR operation ||, which will be used to check if the value is less than 0 or greater than 100. The condition evaluates to true if the value fulfills either condition.

```java
System.out.println("Is the number less than 0 or greater than 100?");
int number = 145;

if (number < 0 || number > 100) {
    System.out.println("Yes! :)");
} else {
    System.out.println("Nope :(")
}
```

```output
Is the number less than 0 or greater than 100?
Yes! :)
```

Now we will use the negation operation ! to negate the condition:

```java
System.out.println("Is the string equal to 'milk'?");
String text = "water";

if (!(text.equals("milk"))) {  // true if the condition text.equals("milk") is false
    System.out.println("No!");
} else {
    System.out.println("Yes")
}
```

```output
Is the text equal to 'milk'?
No!
```

For complicated conditions, we often need parentheses:

```java
int number = 99;

if ((number > 0 && number < 10) || number > 100 ) {
    System.out.println("The number was in the range 1-9 or it was over 100");
} else {
    System.out.println("The number was equal to or less than 0 or it was in the range 10-99");
}
```

```output
The number was equal to or less than 0 or it was in the range 10-99
```

{% include week01/exercise/019.md %}
{% include week01/exercise/020.md %}
{% include week01/exercise/021.md %}
{: .exercises }