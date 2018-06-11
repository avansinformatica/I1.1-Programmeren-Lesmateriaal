## 16. Object

Strings and integers have some differences. Integers are "just values", they can be used in calculations and they can be printed on the screen:

```java
int x = 1;
int y = 2;

y = 3*x;

System.out.println( "value of y now: " + y );
```

Strings are a bit "cleverer" and for example know how long they are:

```java
String word1 = "Programming";
String word2 = "Java";

System.out.println( "String "+ word1 +" length: " + word1.length() );

System.out.println( "String "+ word2 +" length: " + word2.length() );
```

Program output:

```output
String Programming length: 11
String Java length: 4
```

We can determine the length by calling the String method `length()`. Strings have other methods as well. Integers (or whole numbers, variables of type `int`) have no methods at all. They do not "know" anything.

Strings are *objects*, or "something that has methods and a value". Later we will see many other objects as well.

As we can see in the previous example, an object's methods are called by adding a dot and a method call after the name of the object:

```java
word1.length()    // String object's name is word1 and its method length() is called
word2.length()    // String object's name is word2 and its method length() is called
```

The method call is made explicitly to the object. In the above example, we have two objects and first we call the ```length()``` method of the String object `word1` and then do the same for the object `word2`.

Our old friend `reader` is also an object:

```java
Scanner reader = new Scanner(System.in);
```

Even though readers and strings are both objects, they are not very similar. For example, readers (Scanners) have the `nextLine()` method, but Strings do not. In the Java programming language, objects must be "born", in other words created with the `new` command. Strings are objects that make an exception to this rule! -- There are two ways to create a String object:

```java
String banana = new String("Banana");
String carrot = "carrot";
```

Both of the commands above create a new String object. Using the `new` command when creating a String objects is uncommon.

The object's "type" is called a *class*. The class of a string of characters is called `String` and the class of readers is called `Scanner`. Later we learn much more about classes and objects.
