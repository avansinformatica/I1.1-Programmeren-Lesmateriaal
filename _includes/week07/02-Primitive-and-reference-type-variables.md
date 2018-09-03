## 2. Primitive- and reference-type variables

Java is a strongly typed language, what this means is that all of its variables have a type. The types of the variables can be divided in to two categories: **primitive-type and reference-type variables**. Both types of variables have their own "slot", which holds the information belonging to them. Primitive-type variables hold the concrete value in their slot, while the reference-type variables hold a *reference* to a concrete *object*.

### 2.1 Primitive-type variables

The value of a primitive type variable is saved in a slot created for the variable. Each primitive-type variable has its own slot and its own value. A variable's slot is created when it is introduced (`int number;`, for example). A value is set to a slot with the assignment operator =. Below is an example of the introduction of a primitive-type int (integer) variable and setting of its value in the same expression.

```java
int number = 42;
```

Primtive type variables, among others, are `int`, `double`, `char`, `boolean` and the more rarely used `short`, `float`, `byte` and `long`. Another primitive-type is `void`, but it doesn't have its own slot or value. The `void`-type is used when we want to express that a method doesn't return a value.

Next we introduce two primitive-type variables and set values to them.

```java
int five = 5;
int six = 6;
```

The primitive-type variables introduced above are named five and six. When introducing the variable five the value 5 is set to the slot that was created for it (`int five = 5;`). When introducing the variable six the value 6 is set to the slot that was created for it (`int six = 6;`). The variables five and six are both of the type int, or integers.

Primitive-type variables can be visualized as boxes that both have the values belonging to them saved in to them:

![Primitives 5 and 6](images/7_2_primitive-five-and-six.png)

Next lets inspect how the values of primitive-type variables get copied.

```java
int five = 5;
int six = 6;

five = six; // the variable 'five' now holds the value 6 - the value that was in the variable 'six'.
six = 64; // the variable 'six' now holds the value 64

// the variable 'five' still holds the value 6
```

Above we introduce the variables five and six and we set values to them. After this the value held in the slot of the variable `six` is copied to the slot of the variable five (`five = six;`). If the value of the variable `six` is changed after this point the value in the variable `five` remains unaffected: the value of the variable `five` is in its own slot and is not related to the value in the slot of the variable `six` in any way. The end situation as a picture:

![Primitives 5 and 6 - 64](images/7_2_primitive-five-and-six-64.png)

### 2.1.1 Primitive type variable as a method parameter and return value

When a primitive type variable is passed to a method as a parameter, the method parameter is set to the value in the given variable's slot. In practice, the method parameters also have their own slots to which the value is copied, like in an assignment expression. Let us consider the following method `addToValue(int value, int amount`).

```java
public int addToValue(int value, int amount) {
    return value + amount;
}
```

The method `addToValue` is given two parameters: `value` and `amount`. The method returns a new value, which is the sum of the given parameters. Let us investigate how the method is called.

```java
int myValue = 10;
myValue = addToValue(myValue, 15);
// the variable 'myValue' now holds the value 25
```

In the example, `addToValue` is called using the variable myValue and the value 15. These are copied to the method parameters `value`, which will hold the value 10 (the contents of `myValue`), and `amount`, which wil hold the value 15. The method returns the sum of `value` and `amount`, which is equal to `10 + 15 = 25`.

Note! In the previous example, the value of the variable myValue is changed only because it is assigned the return value of `addToValue`; (myValue = addToValue(myValue, 15);). If the call to `addToValue` were as follows, the value of the variable `myValue` would remain unchanged.

```java
int myValue = 10;
addToValue(myValue, 15);
// the variable 'myValue' still holds the value 10
```

### 2.1.2 Minimum and maximum values

Each primitive data type can represent a specific range of values limited by its minimum and maximum value, which are the smallest and largest values representable by the type. This is because a predefined data size is used for the internal represetantion of the type in Java (and most other programming languages).

The minimum and maximum values for a few Java primitive types are:

| Type      | Memory size   | Range  | Description |
|-----------|---------------|--------|---------|-------------|
| byte      | 1 byte        | -$$128$$ to $$127$$                                                         |  The smallest numeric datatype in java. Can be used for large collections of data to save memory. |
| short     | 2 bytes       | $$-32 768$$ to $$32 767$$                                                   | A small numeric datatype in java. Can be used for large collections of data to save memory |
| int       | 4 bytes       | $$-2^{31}$$ to $$2^{31} - 1$$                                       | The default datatype for numbers. This number is 32bit and processors are optimized to handle these numbers |
| long      | 8 bytes       | $$-2^{63}$$ to $$2^{63} - 1$$                                       | Used when the int datatype is not big enough |
| float     | 4 bytes       | $$-(2-2^{-23}) \times 2^{127}$$ to $$(2-2^{-23}) \times 2^{127}$$   | The floating point type is used for storing non-integer values. This is not a precise datatype, and should not be used for currency where precision is required
| double    | 8 bytes       | $$-(2-2^{-52}) \times 2^{1023}$$ to $$(2-2^{-52}) \times 2^{1023}$$ | The double is used for storing non-integer values. This is not a precise datatype, and should not be used for currency where precision is required. A double has more memory space than a float, which is used for storing numbers with more precision | 
| boolean   | not defined   | true, false                                                         | Used for simple truth values of true or false. Are used becaused they are easy to used in expressions | 
| char      | 2 bytes       | all unicode characters                                              | Used for storing the characters in a text. Can contain values like 'a', 'Z', '0' or '@' |

#### 2.1.2.1 Rounding errors

When using floating point data types, it is important to keep in mind that floating point types are always an approximation of the actual value. Because floating point types use a predefined data size to represent the value similarly to all other primitive data types, we may observe quite surprising rounding errors. For example, consider the following case.

```java
double a = 0.39;
double b = 0.35;
System.out.println(a - b);
```

The example prints the value `0.040000000000000036`. Programming languages usually include tools to more accurately handle floating point numbers. In Java, for example, the class `BigDecimal` can be used to store infinitely long floating point numbers.

When comparing floating point numbers, rounding errors are usually taken into account by comparing the distance between the values. For example, with the variables in the previous example, the expression `a - b == 0.04` does not produce the expected result due to a rounding error.

```java
double a = 0.39;
double b = 0.35;

if((a - b) == 0.04) {
    System.out.println("Successful comparison!");
} else {
    System.out.println("Failed comparison!");
}
```

```output
Failed comparison!
```

One method to calculate the distance between two values is as follows. The helper function Math.abs returns the absolute value of the value passed to it.

```java
double a = 0.39;
double b = 0.35;

double distance = 0.04 - (a - b);

if(Math.abs(distance) < 0.0001) {
    System.out.println("Successful comparison!");
} else {
    System.out.println("Failed comparison!");
}
```

```output
Successful comparison!
```

### 2.2 Reference-Type Variables

Reference-type variables memorize the information which has been assigned to them "on the other end of the line". Reference-type variables contain a reference to the location where the information is stored. Differently from primitive-type variables, reference-type variable do not have a limited scope because their value or *information* is stored at the referenced location. Another substantial difference between primitive-type and reference-type variables is that various different reference-type variables can point to the same object.

Let us have a look at two reference-type variables. In the following examples we make use of the class `Calculator`:

```java
public class Calculator {
    private int value;

    public Calculator(int originalValue) { // Contructor
        this.value = originalValue;
    }

    public void increaseValue() {
        this.value = this.value + 1;
    }

    public int getValue() {
        return value;
   }
}
```

Main:

```java
Calculator bonusCalculator = new Calculator(5);
Calculator axeCalculator = new Calculator(6);
```

In the examples we first create a reference-type variable called `bonusCalculator`. The `new` operator tells that we define storage space for the information to be assigned to the variable, then we execute the code which follows the `new` operator, and we return a reference to the object that has been so created. The reference which is returned is assigned to the `bonusCalculator` variable through the `=` equal sign. The same thing happens with the variable called `axeCalculator`. If we want to think about it with pictures, we can imagine a reference-type variable as it were a box, the variable itself, with a line or an arrow, which starts at the box and points to an object. In fact, the variable does not contain the object, but it points to the object information.

![7_2_reference-type-calculators.png](images/7_2_reference-type-calculators.png)

Next, let us have a look at how a reference-type object is duplicated.

```java
Calculator bonusCalculator = new Calculator(5);
Calculator axeCalculator = new Calculator(6);

bonusCalculator = axeCalculator; // the reference contained by the variable axeCalculator is copied to the variable bonusCalculator
                                 // that is to say, a reference to a Calculator-type object which received the value 6 in its constructor
                                 // is copied to the variable bonusCalculator
```

When we copy a reference-type variable (see above `bonusCalculator = axeCalculator;`), the reference to the variable duplicates as well. In this case, a reference to the `axeCalculator` variable slot is copied to the bonusCalculator variable slot. Now, both the objects point to the same place!

![7_2_reference-type-calculators-ref-changed.png](images/7_2_reference-type-calculators-ref-changed.png)

Let us continue with the example above and let us set a new reference to the variable `axeCalculator`; this new reference will point to a new object created by the command `new Calculator(10)`.

```java
Calculator bonusCalculator = new Calculator(5);
Calculator axeCalculator = new Calculator(6);

bonusCalculator = axeCalculator; // the reference contained by the variable axeCalculator is copied to the variable bonusCalculator
                                 // that is to say, a reference to a Calculator-type object which received the value 6 in its constructor
                                 // is copied to the variable

axeCalculator = new Calculator(10); // a new reference is assigned to the axeCalculator variable
                                    // which points to the object created by the command new Calculator(10)

// the bonusCalculator variable still contains a reference to the Calculator object which received value 6 in its parameter
```

In these examples, we do the same operations which were shown in the assignment example in the primitive-type variables section. In the very last example, we copied the reference of reference-type variables, whereas in the primitive-type variables section we copied the value of primitive-type variables. In both cases, we copy the contents of a slot: the primitive-type variable slot contains a value, whereas the reference-type variable slot contains a reference.

At the end of the previous example no variable points to the Calculator object which received value 5 in its constructor. Java's garbage collection deletes such useless objects from time to time. Our final situation looks like the following:

![7_2_reference-type-calculators-3rd-object.png](images/7_2_reference-type-calculators-3rd-object.png)

Let us have a look to a third example still, and let us focus on an essential difference between primitive-type and reference-type variables.

```java
Calculator bonusCalculator = new Calculator(5);
Calculator axeCalculator = new Calculator(6);

bonusCalculator = axeCalculator; // the reference contained by the variable axeCalculator is copied to the variable bonusCalculator
                                 // that is to say, a reference to a Calculator-type object which received the value 6 in its constructor
                                 // is copied to the variable

axeCalculator.increaseValue(); // we increase by one the value of the object referenced by axeCalculator

System.out.println(bonusCalculator.getValue());
System.out.println(axeCalculator.getValue());
```

```output
7
7
```

Both `bonusCalculator` and `axeCalculator` point to the same object, after we have run the command `bonusCalculator = axeCalculator;`, and therefore, now they both have the same value 7, even though we have increased only one of them.

The situation might be clear if we look at the following picture. The method `axeCalculator.increaseValue()` increases by one the value variable of the object pointing to the `axeCalculator` variable. Because `bonusCalculator` points to the same object, the method `bonusCalculator.getValue()` returns the same value which was increased by the method `axeCalculator.increaseValue()`.

![7_2_reference-type-calculators-val-changed.png](images/7_2_reference-type-calculators-val-changed.png)

In the following example, three reference-type variables all point to the same `Calculator` object.

```java
Calculator bonus = new Calculator(5);
Calculator ihq = bonus;
Calculator lennon = bonus;
```
    
In the example, we create only one Calculator object, but all the three Calculator variables point to that same one. Therefore, bonus, ihq, and lennon method calls all modify the same object. To tell it once again: when reference-type variables are copied, their references also duplicate. The same concept in a picture:

![7_2_three-calculators-1.png](images/7_2_three-calculators-1.png) 

Let's use this example to focus on duplication once more.

```java
Calculator bonus = new Calculator(5);
Calculator ihq = bonus;
Calculator lennon = bonus;

lennon = new Calculator(3);
```

The modification of the `lennon` variable contents – that is to say the change of reference – does not affect the references of either `bonus` or `ihq`. When we assign a value to a variable, we **only** change the contents of that variable's own slot. The same concept in a picture:

![7_2_three-calculators-2.png](images/7_2_three-calculators-2.png);

### 2.2.1 A Reference-Type Variables and Method Parameters

When a reference-type variable is given to a method as its parameter, we create a method parameter which is the copy of the reference of a variable. In other words, we copy the reference to the parameter's own slot. Differently from what happens with original-type variables, we copy the reference and not their value. In fact, we can modify the object behind the reference even from within the method. Let us take the method `public void addToCalculator(Calculator calculator, int amount)`.

```java
public void addToCalculator(Calculator calculator, int amount) {
    for (int i = 0; i < amount; i++) {
        calculator.increaseValue();
    }
}
```

We give two parameters to the method `addToCalculator` – a reference-type value and an original-type variable. The contents of both variable slots are copied to method parameter slots. The reference-type parameter `calculator` receives a copy of a reference, whereas the original-type parameter `amount` receives the copy of value. The method will call the `increaseValue()` method of the `Calculator`-type parameter, and it will do it as many times as the value of the amount variable. Let us analyze the method call a little more deeply.

```java
int times = 10;

Calculator bonus = new Calculator(10);
addToCalculator(bonus, times);
// the bonus variable value is now 20
```

In the example we call the `addToCalculator` method, whose given variables are `bonus` and `times`. This means that the reference of the reference-type variable `bonus` and the value of the original-type variable `times` (which is 10) are copied as parameters whose names are `calculator` and `amount`, respectively. The method executes the `increaseValue()` method of the calculator variable a number of times which equals the value of amount. See the following picture:

![7_2_refs-main-and-method-world.png](images/7_2_refs-main-and-method-world.png)

*The method contains variables which are completely separated from the main program!*

As far as the reference-type variable is concerned, a reference duplicates and it is given to the method, and the variable inside the method will still point to the same object. As far as the original-type variable is concerned, a value is copied, and the variable inside the method will have its completely independent value.

The method recognises the calculator which the `bonus` variable points to, and the alterations made by the method have a direct impact on the object. The situation is different with original-type variables, and the method only receives a copy of the value of the `times` variable. In fact, it is not possible to modify the value of original-type variables directly within a method.

#### 2.2.2 A method which returns a reference-type variable

When a method returns a reference-type variable, it returns the reference to an object located elsewhere. Once the reference is returned by a method, it can be assigned to a variable in the same way as a normal assignment would happen, through the equal sign (=). Let us have a look at the method `public Calculator createCalculator(int startValue)`, which creates a new reference-type variable.

```java
public Calculator createCalculator(int startValue) {
    return new Calculator(startValue);
}
```
    
The `createCalculator` method creates an object and returns its `newCalculator` reference. By calling the method, we always create a new object. In the following example we create two different `Calculator`-type objects.

```java
Calculator bonus  = createCalculator(10);
Calculator lennon = createCalculator(10);
```

The method `createCalculator` always creates a new `Calculator`-type object. With the first call, `Calculator bonus = createCalculator(10);` we assign the method return reference to the bonus variable. With the second call, we create another reference and we assign it to the `lennon` variable. The variables `bonus` and `lennon` do not contain the same reference because the method creates a new object in both cases, and it returns the reference to that particular object.

