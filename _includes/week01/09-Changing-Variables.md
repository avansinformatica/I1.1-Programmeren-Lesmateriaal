## 9. Changing variables

We usually want to change the value of an existing variable. This can be done using the normal assignment statement. In the next example, we increase the value of the variable `age` by one:

```java
int age = 1;

System.out.println(age);  // prints 1
age = age + 1;            // the new value of age is the old value of age + 1
System.out.println(age);  // prints 2
```

The `age = age + 1` statement increments the value of the variable `age` by one. It is also possible to increment a variable by one as below:

```java
int age = 1;

System.out.println(age);  // prints 1
age++;                    // means the same as age = age + 1
System.out.println(age);  // prints 2
```

Another example:

```java
int length = 100;

System.out.println(length);  // prints 100
length = length - 50;
System.out.println(length);  // prints 50
length = length * 2;
System.out.println(length);  // prints 100
length = length / 4;
System.out.println(length);  // prints 25
length--;                    // means the same as length = length - 1;
System.out.println(length);  // prints 24
```

{% include week01/exercise/022.md %}
{: .exercises }