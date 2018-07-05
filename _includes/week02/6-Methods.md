## 2.6. Methods

We have so far used many different commands of Java: assignment, calculations, comparison, if structures and while structures. We have been using a "command" `System.out.println()` to print text. We can also count the maximum of two numbers with the help of the "command" `Math.max()`. We are also familiar with `reader.nextLine()`, usually seen together with `Integer.parseInt()`.

If we take a closer look, we notice that those commands differ from if and while (etc). The first difference is that after the command there are brackets () and sometimes an input for the command inside those brackets. Actually, the commands ending with brackets are not called commands, but **methods**.

Technically speaking, a method is a piece of code that can be called from different places of the program code. The line of code `System.out.println("I am a parameter given to the method!")` means that we call a method that actually handles the printing. After the method has been executed we go back to where we called the method, and continue executing. The input given to the method inside the brackets is called a *method parameter*.

In addition to a parameter, the method can also have a return value, for example, a familiar line of code:

```java
int number = Integer.parseInt( reader.nextLine() );
```

includes two method calls. First the inner method `reader.nextLine` is called. That method has the integer typed by the user as a return value. Next the outer method `Integer.parseInt` is called. As a parameter for that method there is the string of characters that was received from the `reader.nextLine` method as a return value. The return value for the method `Integer.parseInt` is the string of characters transformed into an integer (whole number).

Method names also seem to include a dot, for example `reader.nextLine()`. Actually the method name starts after the dot, here it is `nextLine()`. The first part of the command that comes before the dot shows whose method is in question. Here the method belongs to the reader, which means that we have the *reader*'s method `nextLine`. Later we will learn more precisely about the owner of the method (or the name on the left side of the dot). An attentive reader will notice that the method `System.out.println()` has two dots. Here, the method name is `println` and `System.out` is the owner of the method. Roughly `System.out` means the computer monitor.

This far we have been using ready-made methods from Java libraries. Next we will learn how to create our own methods.
