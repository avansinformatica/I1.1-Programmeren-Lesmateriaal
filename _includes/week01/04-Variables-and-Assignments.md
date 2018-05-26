## 4. Variables and assignment

### 4.1 Variables and data types

A *variable* is one of the most important concepts in computer programming. A variable should be imagined as a box in which you can store information. The information stored in a variable always has a type. Java only has a limited number of data types, but it can be extended with custom types. Those custom types can be recognized, as their name is always spelled with a capital. The basic set of variable types in java is as followed:

| Type      | Memory size   | Range  | Default | Description |
|-----------|---------------|--------|---------|-------------|
| byte      | 1 byte        | -$$128$$ to $$127$$                                                         | 0       | The smallest numeric datatype in java. Can be used for large collections of data to save memory. |
| short     | 2 bytes       | $$-32 768$$ to $$32 767$$                                                   | 0       | A small numeric datatype in java. Can be used for large collections of data to save memory |
| int       | 4 bytes       | $$-2^{31}$$ to $$2^{31} - 1$$                                       | 0       | The default datatype for numbers. This number is 32bit and processors are optimized to handle these numbers |
| long      | 8 bytes       | $$-2^{63}$$ to $$2^{63} - 1$$                                       | 0L      | Used when the int datatype is not big enough |
| float     | 4 bytes       | $$-(2-2^{-23}) \times 2^{127}$$ to $$(2-2^{-23}) \times 2^{127}$$   | 0.0f    | The floating point type is used for storing non-integer values. This is not a precise datatype, and should not be used for currency where precision is required
| double    | 8 bytes       | $$-(2-2^{-52}) \times 2^{1023}$$ to $$(2-2^{-52}) \times 2^{1023}$$ | 0.0d    | The double is used for storing non-integer values. This is not a precise datatype, and should not be used for currency where precision is required. A double has more memory space than a float, which is used for storing numbers with more precision | 
| boolean   | not defined   | true, false                                                         | false   | Used for simple truth values of true or false. Are used becaused they are easy to used in expressions | 
| char      | 2 bytes       | all unicode characters                                              | '\u0000'| Used for storing the characters in a text. Can contain values like 'a', 'Z', '0' or '@' |

Another type that you have seen so far is the `String`. A string is a variable that contain text

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
The variable's type is String. Its value is includes text
The variable's type is int. Its value is 123
The variable's type is double. Its value is 3.141592653
The variable's type is boolean. Its value is true
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

### 4.2 Variable data types are immutable

When a variable is declared with a data type, it cannot be changed later. For example, a text variable cannot be changed into an integer variable and it cannot be assigned integer values.

```java
String text = "yabbadabbadoo!";
text = 42; // Does not work! :(
```

Integer values can be assigned to decimal number variables, because whole numbers are also decimal numbers.

```java
double decimalNumber = 0.42;
decimalNumber = 1; // Works! :)
```

{% include week01/exercise/004.md %}
{: .exercises }

### 4.3 Allowed and descriptive variable names

There are certain limitations on the naming of our variables. Even though umlauts, for example, can be used, it is better to avoid them, because problems might arise with [character encoding](http://en.wikipedia.org/wiki/Character_encoding). For example, it is recommended to use A instead of Ä.

Variable names must not contain certain special characters like exclamation marks (!). Space characters cannot be used, either, as it is used to separate commands into multiple parts. It is a good idea to replace the space character using a [camelCase](https://en.wikipedia.org/wiki/Camel_case) notation. **Note**: The first character is always written in lower case when using the camel case notation.

```java
int camelCaseVariable = 7;
```

Variable names can contain numbers as long it does not start with one. Variable names cannot be composed solely of numbers, either.

```java
int 7variable = 4; // Not allowed!
int variable7 = 4; // A valid, but not descriptive variable name
```

Variable names that have been defined before cannot be used. Command names such as `System.out.print` cannot be used, either.

```java
int camelCase = 2;
int camelCase = 5; // Not allowed, the variable camelCase is already defined!
```

It is strongly recommended to name variables so that their purpose can be understood without comments and without thinking. Variable names used in this course **must** be descriptive.

#### 4.3.1 Valid variable names

* lastDay = 20
* firstYear = 1952
* name = "Matti"

#### 4.3.2 Invalid variable names

* last day of the month = 20
* 1day = 1952
* watchout! = 1910
* 1920 = 1
