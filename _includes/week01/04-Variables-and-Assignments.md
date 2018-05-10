## 4. Variables and assignment

### 4.1 Variables and data types

A *variable* is one of the most important concepts in computer programming. A variable should be imagined as a box in which you can store information. The information stored in a variable always has a type. These types include
* text (String)
* whole numbers (int)
* decimal numbers (double)
* truth values (boolean). 

A value can be assigned to a variable using the equals sign (=).

```java
int months = 12;
```

In the statement above, we assign the value 12 to the variable named `months` whose data type is integer (int). The statement is read as "the variable months is assigned the *value* 12".

The value of the variable can be appended to a string with the plus + sign as shown in the following example.

```java
String text = "includes text";
int wholeNumber = 123;
double decimalNumber = 3.141592653;
boolean isTrue = true;

System.out.println("The variable's type is text. Its value is " + text);
System.out.println("The variable's type is integer. Its value is  " + wholeNumber);
System.out.println("The variable's type is decimal number. Its value is " + decimalNumber);
System.out.println("The variable's type is truth value. Its value is " + isTrue);
```
Printing:
```output
The variable's type is text. Its value is includes text
The variable's type is integer. Its value is 123
The variable's type is decimal number. Its value is 3.141592653
The variable's type is truth value. Its value is true
```

A variable holds its value until it is assigned a new one. Note that the variable type is written only when the variable is first declared in the program. After that we can use the variable by its name.

```java
int wholeNumber = 123;
System.out.println("The variable's type is integer. Its value is  " + wholeNumber);

wholeNumber = 42;
System.out.println("The variable's type is integer. Its value is  " + wholeNumber);
```

The output is:

```output
The variable's type is integer. Its value is 123
The variable's type is integer. Its value is 42
```