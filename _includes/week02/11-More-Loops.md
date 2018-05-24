## 11. More loops

we have previously learned to use repetition using the `while (true)` loop, which repeats commands until the `break` command is used.

The `break` command is not the only way to end a loop. A common structure for a loop is `while (condition)`, where the condition can be **any statement with a truth value**. This means that the condition works exactly like conditions in an `if` statements.

In the following example, we print the numbers 1, 2, …, 10. When the value of the variable number increases above 10, the condition of the while statement is no longer true and the loop ends.

```java
int number = 1;

while (number < 11) {
    System.out.println(number);
    number++;  // number++ means the same as number = number + 1
}
```

The example above can be read "as long as the variable number is less than 11, print the variable and increment it by one".

Above, the variable `number` was incremented in each iteration of the loop. Generally the change can be anything, meaning that the variable used in the condition does not always need to be incremented. For example:

```java
int number = 1024;

while (number >= 1) {
    System.out.println(number);
    number = number / 2;
}
```

>Complete the following exercises using the while statement:
{% include week02/exercise/005.md %}
{% include week02/exercise/006.md %}
{% include week02/exercise/007.md %}
{% include week02/exercise/008.md %}
{% include week02/exercise/009.md %}
{: .exercises }

### 11.1 Assignment operations

Because changing the value of a variable is a very common operation, Java has special assignment operations for it.

```java
int length = 100;

length += 10;  // same as length = length + 10;
length -= 50;  // same as length = length - 50;
```

When performing the assignment operation on an existing variable, it is written as `variable operation= change`, for example `variable += 5`. Note that a variable must be defined before you can assign a value to it. Defining a variable is done by specifying the variable type and the name of the variable.

The following example will not work because the type of the variable `length` has not been defined.

```java
length = length + 100;  // error!
length += 100;          // error!
```

When the type is defined, the operations will also work.

```java
int length = 0;
length = length + 100;
length += 100;

// the variable length now holds the value 200
```

There are also other assignment operations:

```java
int length = 100;

length *= 10;   // same as length = length * 10;
length /= 100;  // same as length = length / 100;
length %= 3;    // same as length = length % 3;

// the variable length now holds the value 1
```

Often during a loop, the value of a variable is calculated based on repetition. The following program calculates 3*4 somewhat clumsily as the sum 3+3+3+3:

```java
int result = 0;

int i = 0;
while (i < 4) {
   result = result + 3;
   i++;  // means the same as i = i + 1;
}
```

In the beginning `result = 0`. During the loop, the value of the variable is incremented by 3 on each iteration. Because there are 4 iterations, the value of the variable is 3*4 in the end.

Using the assignment operator introduced above, we can achieve the same behavior as follows:

```java
int result = 0;

int i = 0;
while (i < 4) {
   result += 3;  // this is the same as result = result + 3;
   i++;          // means the same as i = i+1;
}
```

{% include week02/exercise/010.md %}
{% include week02/exercise/011.md %}
{% include week02/exercise/012.md %}
{% include week02/exercise/013.md %}
{: .exercises }

### 11.2 Infinite loops

One of the classic errors in programming is to accidentally create an infinite loop. In the next example we try to print "Never again shall I program an eternal loop!" 10 times:

```java
int i = 0;

while (i < 10) {
    System.out.println("Never again shall I program an eternal loop!");
}
```

The variable `i`, which determines is supposed to index the loops, is initially set to 0. The block is looped as long as the condition `i < 10` is true. But something funny happens. Because the value of the variable `i` is never changed, the condition stays true forever.

### 11.3 Ending a while loop

So far, we have used the while loop with a structure similar to this:

```java
int i = 1;
while (i < 10) {
    // Some code.
    i++;
}
```

With the structure above, the variable `i` remembers the number of times the the loop has been executed. The condition to end the loop is based on comparing the value of `i`.

Let us now recall how a while loop is stopped. Ending a while loop does not always need to be based on the amount of loops. The next example program asks for the user's age. If the given age is not in the range 5-85, the program prints a message and asks for the user's age again. As you can see, the condition for the while loop can be any expression that results in a boolean (truth value).

```java
System.out.println("Type your age: ");

int age = Integer.parseInt(reader.nextLine());

while (age < 5 || age > 85) {  // age less than 5 OR greater than 85
    System.out.println("You are lying!");
    if (age < 5) {
        System.out.println("You are so young that you cannot know how to write!");
    } else if (age > 85) {
        System.out.println("You are so old that you cannot know how to use a computer!");
    }

    System.out.println("Type your age again: ");
    age = Integer.parseInt(reader.nextLine();
}

System.out.println("Your age is " + age);
```

The program could also have been implemented using the good old `while (true)` structure:

```java
System.out.println("Type your age ");
int age;
while (true) {
    age = Integer.parseInt(reader.nextLine());

    if (age >= 5 && age <= 85) {  // age between 5 AND 85
        break;  // end the loop
    }

    System.out.println("You are lying!");
    if (age < 5) {
        System.out.println("You are so young that you cannot know how to write!");
    } else {  // that means age is over 85
        System.out.println("You are so old that you cannot know how to use a computer!");
    }

    System.out.println("Type your age again: ");
}

System.out.println("Your age is " + age);
```

{% include week02/exercise/014.md %}
{: .exercises }

### Note: creating a program in small steps
>In these exercises we actually created one single program, but programming happened in very small steps. This is *ALWAYS* the preferred way to program.
>
>When you are programming something, no matter if it is an exercise or a project of your own, it is advised to do it in very tiny pieces. Do not ever try to solve the whole problem in one go. Start with something easy, something you know that you can do. In this recent set of exercises, for example, we focused first on stopping the program when the user types -1. When one part of the program is complete and working, we can move on to work out the solution for the next sub-problem of the big main problem.
>
>Some of the exercises in this course are sliced into smaller pieces like the set of exercises we just introduced. Usually the pieces need to be sliced again into smaller pieces depending on the problem. It is advised that you execute the whole program after almost every new line of code you write. This enables you to be sure that your solution is going in the right and working direction.
