## 3. Static and Non-Static

Let's further investigate a topic we introduced in the 30th section of Introduction to Programming. The static or non-static nature of a variable or of a method depends on their scope. Static methods are always related to their class, whereas non-static methods can modify the variables of the object itself.

### 3.1 Static, Class Libraries and Final

The methods which receive the definition static are not related to objects but to classes. it is possible to define class-specific variables by adding the word `static` to their name. For instance, `Integer.MAX_VALUE`, `Long.MIN_VALUE` and `Double.MAX_VALUE` are all static variables. Static methods are called via their class name, for instance `ClassName.variable` or `ClassName.method()`.

We call class library a class which contains common-use methods and variables. For instance, Java `Math` class is a class library. It provides the `Math.PI` variable, inter alia. Often, creating your own class libraries can prove useful. Helsinki Regional Transport Authority (Finnish: Helsingin Seudun Liikenne, HSL) could use a class library to keep its ticket prices at its fingertips.

```java
public class HslPrices {
    public static final double SINGLETICKET_ADULT = 2.50;
    public static final double TRAMTICKET_ADULT = 2.50;
}
```

The keyword `final` in the variable definition tells that once we assign a value to a variable, we can not assign a new one to it. Final-type variables are constant, and they always have to have a value. For instance, the class variable which tells the greatest integer, `Integer.MAX_VALUE`, is a constant class variable.

Once we have the class presented above, `HslPrices`, all the programs which need the single or tram-ticket price can have access to it through the class `HslPrices`. With the next example, we present the class `Person`, which has the method `enoughMoneyForSingleTicket()`, which makes use of the ticket price found in the class `HslPrices`.

```java
public class Person {
    private String name;
    private double money;
    // more object variables

    // constructor

    public boolean enoughMoneyForSingleTicket() {
        if(this.money >= HslPrices.SINGLETICKET_ADULT) {
            return true;
        }

        return false;
    }

    // the other methods regarding the class Person
}
```

The method `public boolean enoughMoneyForSingleTicket()` compares the object variable money of class Person to the static variable `SINGLETICKET_ADULT` of class `HslPrices`. The method `enoughMoneyForSingleTicket()` can be called only through an object reference. For instance:

```java
Person matti = new Person();

if (matti.enoughMoneyForSingleTicket()) {
    System.out.println("I'll buy a ticket.");
} else {
    System.out.println("Fare dodging, yeah!");
}
```

Note the naming convention! All **constants**, i.e. all variable which are provided with the definition final, are written with CAPITAL_LETTERS_AND_UNDERLINE_CHARACTERS.

Static methods function analogously. For instance, the class `HslPrices` could encapsulate the variables and only provide *accessors*. We call accessors the methods which allow us to either read a variable value or to assign them a new one.

```java
public class HslPrices {
    private static final double SINGLETICKET_ADULT = 2.50;
    private static final double TRAMTICKET_ADULT = 2.50;

    public static double getSingleTicketPrice() {   // Accessor
        return SINGLETICKET_ADULT;
    }

    public static double getTramTicketPrice() {   // Accessor
        return TRAMTICKET_ADULT;
    }
}
```
    
In such cases, when we code a class such as `Person`, we can't call the variable straight, but we have to get it through the method `getSingleTicketPrice()`.

```java
public class Person {
    private String name;
    private double money;
    // other object variables

    // constructor

    public boolean enoughMoneyForSingleTicket() {
        if(this.money >= HslPrices.getSingleTicketPrice()) {
            return true;
        }

        return false;
    }

    // other methods regarding the class Person
}
```

Even though Java allows for static variable use, we do not usually require it. Often, using static methods causes problems with the program structure, because static variables are as inconvenient as [global variables](http://c2.com/cgi/wiki?GlobalVariablesAreBad). **The only static variables we use in this course are constant, i.e. final!**

### 3.2 Non-Static

Non-static methods and variables are related to objects. The object variables, or attributes, are defined at the beginning of the class. When an object is created with the `new` operator, we allocate storage space for all its object variables. The variable values are personal of the object, which means that every object receives personal variable values. Let us focus again on the class `Person`, which has the object variable `name` and `money`.

```java
public class Person {
  private String name;
  private double money;

  // other details
}
```
    
When we create a new instance of class `Person`, we also initialize its variables. If we do not initialize the reference-type variable `name`, it receives value `null`. Let us add the constructor and a couple of methods to our class `Person`.

```java
public class Person {
  private String name;
  private double money;

    // constructor
    public Person(String name, double money) {
        this.name = name;
        this.money = money;
    }

    public String getName() {
        return this.name;
    }

    public double getMoney() {
        return this.money;
    }

    public void addMoney(double amount) {
        if(amount > 0) {
          this.money += amount;
        }
    }

    public boolean enoughMoneyForSigleTicket() {
        if(this.money >= HslPrices.getSingleTicketPrice()) {
            return true;
        }

        return false;
    }
}
```

The constructor `Person(String name, double money)` creates a new `Person` object, and it returns its reference. The method `getName()` returns the reference to a `name` object, and the `getMoney()` method returns the original-type variable `money`. The method `addMoney(double amount)` receives as parameter an `amount` of money, and it adds it to the `money` object variable if the parameter's value is greater than 0.

Object methods are called through their object reference. The following code example creates a new Person object, increases its money, and prints its name, at the end. Note that the method calls follow the pattern `objectName.methodName()`

```java
Person matti = new Person("Matti", 5.0);
matti.addMoney(5);

if (matti.enoughMoneyForSingleTicket()) {
    System.out.println("I'll buy a single ticket.");
} else {
    System.out.println("Fare dodging, yeah!");
}
```

The example prints `"I'll buy a single ticket."`

#### 3.2.1 Class Methods

Non-static class methods can be also called without specifying the object which indicates the class. In the following example, the `toString()` method points to the class `Person`, which calls the object method `getName()`.

```java
public class Person {
    // earlier written content

    public String toString() {
        return this.getName();
    }
}
```

The `toString()` method calls the class method `getName()`, which belongs to the object in question. The this prefix emphasizes that the call refers precisely to this object.

Non-static methods can also call static methods, that is the class-specific ones. On the other hand, static methods can not call non-static methods without a reference to the object itself, which is essential to retrieve the object information.

#### 3.2.2 A Variable within a Method

The variables which are defined inside a method are auxiliary variables used during the method execution, and they are not to be confused with object variables. The example below shows how a local variable is created inside a method. The index variable exists and is accessible only during the method execution.

```java
public class ... {
    ...

    public static void printTable(String[] table) {
        int index = 0;

        while(index < table.length) {
            System.out.println(table[index]);
            index++;
        }
    }
}
```
    
In the `printTable()` method, we create the auxiliary variable `index` which we use to parse the table. The variable `index` exists only during the method execution.

{% include week07/exercise/004.md %}
{: .exercises }