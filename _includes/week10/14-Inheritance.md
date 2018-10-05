## 14. Inheritance of Class Features

Classes are for the programmer a way to clarify problematic concepts. With each class we create, we add new functionality to the programming language. The functionality is needed to solve the problems we meet, and the solutions are born from the interaction among the objects we create. In object programming, an object is an independent unity which can change through its methods. Objects are used together with each other; each object has its own area of responsibility. For instance, our user interface classes have been making use of `Scanner` objects, so far.

Each Java's class descends from the class `Object`, which means that each class we create has all methods which are defined in Object. If we want to change the functionality of the methods defined in `Object`, we have to Override them and define a new functionality in the created class.

In addition to be possible to inherit the `Object` class, it is also possible to inherit other classes. If we check Java's `ArrayList` class API we notice that `ArrayList` inherits the class `AbstractList`. The class `AbstractList` inherits the class `AbstractCollection`, which descended from the class `Object`.

### ArrayList
> [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html)  
>>└── [java.util.AbstractCollection](http://docs.oracle.com/javase/8/docs/api/java/util/AbstractCollection.html)  
>>>└── [java.util.AbstractList](http://docs.oracle.com/javase/8/docs/api/java/AbstractList.html)  
>>>>└──java.util.ArrayList


Each class can inherit one class, directly, Indirectly, a class can still inherit all the feauters its parent class. The class `ArrayList` inherits directly the class `AbstractList`, and indirectly the classes `AbstractCollection` and `Object`. In fact, the class `ArrayList` has the methods and interfaces of `AbstractList`, `AbstractCollection` and `Object` at its disposal.

The class features are inherited using the keyword `extends`. The class which inherits is called *subclass*; the class which is inherited is called *superclass*. Let's get aquainted with a carmaker system, which handles car components. The basic component of component handling is the class `Component` which defines the identification number, the producer, and the description.

```java
public class Component {

    private String id;
    private String producer;
    private String description;

    public Component(String id, String producer, String description) {
        this.id = id;
        this.producer = producer;
        this.description = description;
    }

    public String getId() {
        return id;
    }

    public String getDescription() {
        return description;
    }

    public String getProducer() {
        return producer;
    }
}
```

One car component is its motor. As for all the other components, the motor has also got a producer, an identification number, and a description. In addition, a motor has also got a type: for instance, combustion engine, electric motor, or hybrid. Let's create the class `Motor` which inherits `Component`: a motor is a particular case of component.

```java
public class Motor extends Component {

    private String motorType;

    public Motor(String motorType, String id, String producer, String description) {
        super(id, producer, description);
        this.motorType = motorType;
    }

    public String getMotorType() {
        return motorType;
    }
}
```

The class definition `public class Motor extends Component` tells us that the class `Motor` inherits the functionality of `Component`. In the class `Motor`, we define the object variable `motorType`.

The `Motor` class constructor is interesting. In the first line of the constructor we notice the keyword `super`, which is used to call the superclass constructor. The call `super(id,producer,description)` class the constructor `public Component(String id, String producer, String description)` which is defined in the class `Component`; in this way the superclass object variables are assigned a value. After doing this, we assign a value to the object variable `motorType`.

When the class `Motor` inherits the class `Component`, in receives all the methods provides by `Component`. It is possible to create an instance of the class `Motor` as it is for any other class.

```java
Motor motor = new Motor("combustion engine", "hz", "volkswagen", "VW GOLF 1L 86-91");
System.out.println(motor.getMotorType());
System.out.println(motor.getProducer());
```

```output
combustion engine
volkswagen
```

As you notice, the class `Motor` has the methods defined in `Component` at its disposal.

### 14.1 Private, Protected and Public

If a method or a variable have got the `private` field accessibility, it can not be seen by its subclasses, and its subclasses do not have any straight way to access it. In the previous example Motor can't access directly the attributes defined in its superclass Component (id, producer, description). The subclass see naturally everything which has been defined `public` in its super class. If we want to define superclass variables or methods whose accessibility should be restricted to only its subclasses, we can use the `protected` field accessability.

### 14.2 Superclass

The superclass constructor is defined by the `super` keyword. In fact, the call `super` is similar to the this constructor call. The call is given the values of the type required by the super class constructor parameter.

When we call the constructor, the variables defined in the super class are initialized. In fact, with constructor call happens the same thing as in normal constructor calls. Unless the superclass has a constructor without parameter, in the subclass constructor call there must always be a call for its superclass constructor.

**Attention!** The `super` call must always be in the first line!

### 14.3 Calling the Superclass Methods

The method defined in the superclass can always be called using the `super` prefix, in the same way we call the methods defined in this class through the `this` prefix. For instance, we can make use of a method which overrives the superclass `toString` method in the following way:

```java
@Override
public String toString() {
    return super.toString() + "\n  And my personal message again!";
}
```

{% include week10/exercise/002.md %}
{: .exercises }

### 14.4 The Object Type defines the Called Method: Polymorphism

The method which can be called is defined through the variable type. For instance, if a `Student` object reference is saved into a `Person` variable, the object can use only the methods defined in the `Person` class:

```java
Person olli = new Student("Olli", "Ida Albergintie Street 1 00400 Helsinki");
olli.credits();        // NOT WORKING!
olli.study();              // NOT WORKING!
String.out.println( olli );   // olli.toString() IT WORKS!
```

If the object has many different types, it has available the methods defined by *all* types. For instance, a `Student` object has available the methods defined both in the class `Person` and in `Object`.

In the previous exercise, we were in the class `Student` and we replaced the `toString` method inherited from `Person` with a new version of it. Suppose we are using an object throw a type which is not its real, what version of the object method would we call, then? For instance, below there are two students whose references are saved into a `Person` and an `Object` variables. We call the `toString` method of both. What version of the method is executed: the one defined in `Object`, in `Person`, or in `Student`?

```java
Person olli = new Student("Olli", "Ida Albergintie Street 1 00400 Helsinki");
String.out.println( olli );

Object liisa = new Student("Liisa", "Väinö Auerin Street 20 00500 Helsinki");
String.out.println( liisa );
```

Printing:

```output
Olli
  Ida Albergintie Street 1 00400 Helsinki
  credits 0
Liisa
  Väinö Auerin Street 20 00500 Helsinki
  credits 0
```

As you see, the execution method is chosen based on its real type, that is the type of the variable which saved the reference!

More generally: **The execution method is always chosen based on the object real type, regardless of the variable type which is used. Objects are diverse, which means they can be used through different variable types. The execution method does always depend of the object actual type.** This diversity is called polymorphysm.

### 14.5 Another Example: Points

A point laying in a bidimensional coordinate system can be represented with the help of the following class:

```java
public class Point {

    private int x;
    private int y;

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public int manhattanDistanceFromOrigin(){
        return Math.abs(x)+Math.abs(y);
    }

    protected String location(){
        return x + ", " + y;
    }

    @Override
    public String toString() {
        return "("+this.location()+") distance "+this.manhattanDistanceFromOrigin();
    }
}
```

The location method is not supposed to be used outside its class, and its accessability field is protected, which means only subclasses can access it. For instance, if we use a [path fiding algorithm](http://wiki.gamegardens.com/Path_Finding_Tutorial), [the Manhattan distance](http://en.wiktionary.org/wiki/Manhattan_distance) is the distance of two points moving on a strictly horizontal and/or vertical path, along the coordinate system lines.

A coloured point is similar to a point, except that it contains a string which tells us its colour. The class can be created by inheriting Point:

```java
public class ColouredPoint extends Point {

    private String colour;

    public ColouredPoint(int x, int y, String colour) {
        super(x, y);
        this.colour = colour;
    }

    @Override
    public String toString() {
        return super.toString()+" colour: "+colour;
    }
}
```

The class defines an object variable which saves the colour. The coordinates are saved in the superclass. The string representation must be similar to the one of the point, but it also has to show the colour. The overwritten `toString` method, calls the superclass `toString` method, and it adds the point colour to it.

In the following example, we create a list which contains various different points, either normal or coloured. Thanks to polymorphysm, we call the actual toString method of all objects, even though the list knows them as if they were all `Point`-type:

```java
public class Main {
    public static void main(String[] args) {
        List<Point> points = new ArrayList<Point>();
        points.add(new Point(4, 8));
        points.add(new ColouredPoint(1, 1, "green"));
        points.add(new ColouredPoint(2, 5, "blue"));
        points.add(new Point(0, 0));

        for (Point point : points) {
            System.out.println(point);
        }
    }
}
```

Printing:

```output
(4, 8) distance 12
(1, 1) distance 2 colour: green
(2, 5) distance 7 colour: blue
(0, 0) distance 0
```

We also want a 3D point in our program. Because that is not a coloured point, it shall inherit Point:

```java
public class 3DPoint extends Point {

    private int z;

    public 3DPoint(int x, int y, int z) {
        super(x, y);
        this.z = z;
    }

    @Override
    protected String location() {
        return super.location() + ", " + z;    // printing as "x, y, z"
    }

    @Override
    public int manhattanDistanceFromOrigin() {
        // first, we ask the superclass for the distance of x+y
        // and then we add the value of z to it
        return super.manhattanDistanceFromOrigin() + Math.abs(z);
    }

    @Override
    public String toString() {
        return "(" + this.location() + ") distance " + this.manhattanDistanceFromOrigin();
    }
}
```

A 3D point defines an object variable corresponding to the third coordinate, and it overrides the methods `location`, `manhattanDistanceFromOrigin` and `toString` so that they would take into account the tridimensionality. We can now extend the previous example and add 3D points to our list:

```java
public class Main {

    public static void main(String[] args) {
        List<Point> points = new ArrayList<Point>();
        points.add(new Point(4, 8));
        points.add(new ColouredPoint(1, 1, "green"));
        points.add(new Point(2, 5, "blue"));
        points.add(new 3DPoint(5, 2, 8));
        points.add(new Point(0, 0));

        for (Point point : points) {
            System.out.println(point);
        }
    }
}
```

The output meets our expectations

```output
(4, 8) distance 12
(1, 1) distance 2 colour: green
(2, 5) distance 7 colour: blue
(5, 2, 8) distance 15
(0, 0) distance 0
```

We notice that the tridimensional point `toString` method is exactly the same as the point's `toString`. Could we leave the `toString` method untouched? Of course! A tridimensional point can be reduced to the following:

```java
public class 3DPoint extends Point {

    private int z;

    public 3DPoint(int x, int y, int z) {
        super(x, y);
        this.z = z;
    }

    @Override
    protected String distance() {
        return super.distance()+", "+z;
    }

    @Override
    public int manhattanDistanceFromOrigin() {
        return super.manhattanDistanceFromOrigin()+Math.abs(z);
    }
}
```

What does exactly happen when we call a tridimensional point's `toString` method? The execution proceeds in the following way:

* we look for a `toString` method in the class `3DPoint`; this is not found and we move to its parent class
* we look for a toString method in the superclass `Point`; the method is found and we execute its code
* the code to execute is `return "("+this.location()+") location "+this.manhattanDistanceFromOrigin();`
* first, we execute the method `location`
* we look for a `location` method in the class `3DPoint`; the method is found and we executes its code
* the location method `calculates` its result by calling the superclass method `location`
* next, we look for the definition of the method `manhattanDistanceFromOrigin` in the class `Point3D`; the method is found and we execute its code
* once again, the method `calculates` its result by calling its homonym in the superclass

The operating sequence produced by the method call has many steps. The idea is clear, anyway: when we want to execute a method, we first look for its definition in the object real type, and if it is not found, we move to the super class. If the method is not found in the parent class either, we move to the parent parent class, and so on...

### 14.6 When Do We Have to Use Inheritance?

Inheritance is a tool to build and qualify object hierarchy; a subclass is always a special instance of the superclass. If the class we want to create is a special instance of an already existent class, we can create it by inheriting the class which already exists. For instance in our auto components example, motor is a component, but the motor has additional functionality which not all the classe s have.

Through inheritance, a subclass receives the superclass functionality. If a subclass does not need or use the inherited functionality, inheritance is not motivated. The inherited classes inherit the upperclass methods and interfaces, and therefore we can use a subclass for any purpose the superclass was used. It is good to stick to low inheritance hierarchy, because the more complex the inheritance hierarchy is, the more complex maintainance and further development will be. In general, if the hierarchy is higher than two or three, the program structure is usually to improve.

It is good to think about inheritance use. For instance, if `Car` inherited classes like `Component` or `Motor`, that would be wrong. A car *contains* a motor and components, but a car is not a motor or a component. More generally, we can think that if an object owns or is composed of the other objects, inheritance is wrong.

Devoloping hierachy, you have to make sure the Single Responsibility Principle applies. There must be only one reason to change a class. If you notice that the hierarchy increases a class responsibilities, that class must be divided into various different classes.

#### 14.6.1 An Example of Inheritance Misuse

Let's think about the `Customer` class, in relation to post service. The class contains the customer personal information, and `Order`, which inherits the customer personal information and contains the information of the object to order. The class `Order` has also got the method `mailingAddress`, which tells the mailing address of the order.

```java
public class Customer {

    private String name;
    private String address;

    public Customer(String name, String address) {
        this.name = name;
        this.address = address;
    }

    public String getName() {
        return name;
    }

    public String getAddress() {
        return address;
    }

    public void setAddress(String address) {
        this.address = address;
    }
}
```

```java
public class Order extends Customer {

    private String product;
    private String amount;

    public Order(String product, String amount, String name, String address) {
        super(name, address);
        this.product = product;
        this.amount = amount;
    }

    public String getProduct() {
        return product;
    }

    public String getAmount() {
        return amount;
    }

    public String mailingAddress() {
        return this.getName() + "\n" + this.getAddress();
    }
}
```

The inheritance above is used erroneously. When a class inherits another, the subclass has to be a special instance of the superclass; order is not a special instance of customer. The misuse becomes apparent by breaking the single responsibility principle: the class `Order` is responsible for both the customer and the order information maintenance.

The problem with the previous solution becomes apparent when we think of what would happen if a customer changes their own address.

With a change of address, we would have to change each `Order` object of the customer, which is a hint about a bad situation. A better solution would be encapsulating `Customer` as an object variable of `Order`. If we think more specifically about the order semantics this becomes clear. An order has a customer. Let's change the class `Order` so that it contains a reference to `Customer`.

```java
public class Order {

    private Customer customer;
    private String product;
    private String amount;

    public Tilaus(Customer customer, String product, String amount) {
        this.customer = customer;
        this.product = product;
        this.amount = amount;
    }

    public String getProduct() {
        return product;
    }

    public String getAmount() {
        return amount;
    }

    public String mailingAddress() {
        return this.customer.getName() + "\n" + this.customer.getAddress();
    }
}
```

The `Order` class above is better now. The method `mailingAddress` uses a `Customer` reference to retrieve the mailing address, instead of inheriting the class `Customer`. This makes easier both the maintanance and the concrete functionality of our program.

Now, when we modify a customer, we only need to change their information; we don't have to do anything about the orders.

{% include week10/exercise/003.md %}
{: .exercises }

### 14.7 Inheritance, Interfaces, Both, or None?

Inheritance does not exclude using interfaces, and viceversa. Interfaces are like an agreement on the class implementation, and they allow for the abstraction of the concrete implementation. Changing a class which implements an interface is quite easy.

As with interfaces, when we make use of inheritance, the subclasses are committed to provide all the superclass methods. Because of polymorphism, inheritance works as interfaces do. We can assign a subclass instance to a method which receives its superclass as parameter.

Below, we create a farm simulator, where we simulate the life in a farm. Note that the program does not make us of inheritance, and the interface use is scarce. With programs, we often create a first version which we improve later on. Typically, we don't already understand the scope of the problem when we implement the first version; planning interfaces and inheritance hierarchy may be difficult and it may slow down the work.

{% include week10/exercise/004.md %}
{: .exercises }

### 14.8 An Abstract Class

Abstract classes combine interfaces and inheritance. They do not produce instances, but you can create instances of their subclasses. An abstract class can contain both normal and abstract methods, the first containing the method body, the second having only the method definition. The implementation of the abstract methods is left to the inheriting class. In general, we use abstract classes when the object they represent is not a clear, self-defined concept. In such cases, it is not possible to create instances of it.

Both when we define abstract classes and abstract methods, we use the keyword `abstract`. An abstract class is defined by the statement `public abstract class ClassName`, whereas an abstract method is defined by `public abstract returnType methodName`. Let's consider the following abstract class `Operation`, which provides a framework for operations, and their excecutions.

```java
public abstract class Operation {

    private String name;

    public Operation(String name) {
        this.name = name;
    }

    public String getName() {
        return this.name;
    }

    public abstract void execute(Scanner reader);
}
```

The abstract class `Operation` works as a framework to excetute different operations. For instance, an addition can be implemented by inheriting the class `Operation` in the following way.

```java
public class Addition extends Operation {

    public Addition() {
        super("Addition");
    }

    @Override
    public void execute(Scanner reader) {
        System.out.print("Give the first number: ");
        int first = Integer.parseInt(reader.nextLine());
        System.out.print("Give the second number: ");
        int second = Integer.parseInt(reader.nextLine());

        System.out.println("The sum is " + (first + second));
    }
}
```

Because all classes which descend from `Operation` are also Operation-type, we can create a user interface based on `Operation`-type variables. The following class `UserInterface` contains a list of operations and a reader. The operations can be added dynamically in the user interface.

```java
public class UserInterface {

    private Scanner reader;
    private List<Operation> operations;

    public UserInterface(Scanner reader) {
        this.reader = reader;
        this.operations = new ArrayList<Operation>();
    }

    public void addOperation(Operation operation) {
        this.operations.add(operation);
    }

    public void start() {
        while (true) {
            printOperations();
            System.out.println("Choice: ");

            String choice = this.reader.nextLine();
            if (choice.equals("0")) {
                break;
            }

            executeOperation(choice);
            System.out.println();
        }
    }

    private void printOperations() {
        System.out.println("\t0: Quit");
        for (int i = 0; i < this.operations.size(); i++) {
            String operationName = this.operations.get(i).getName();
            System.out.println("\t" + (i + 1) + ": " + operationName);
        }
    }

    private void executeOperation(String choice) {
        int operation = Integer.parseInt(choice);

        Operation chosen = this.operations.get(operation - 1);
        chosen.execute(reader);
    }
}
```

The user interface works in the following way:

```java
        UserInterface ui = new UserInterface(new Scanner(System.in));
        ui.addOperation(new Addition());

        ui.start();
```

```output
Operations:
        0: Quit
        1: Addition
Choice: **1**
Give the first number: **8**
Give the second number: **12**
The sum is 20

Operations:
        0: Quit
        1: Addition
Choice: **0**
```

The difference between interfaces and abstract classes is that abstract classes provide the program with more structure. Because it is possible to define the functionality of abstract classes, we can use them to define the default implementation, for instance. The user interface above made use of a definition of the abstract class to store the operation name.

{% include week10/exercise/005.md %}
{: .exercises }

### 50.9 Removing Objects from an ArrayList

In the following exercise we see what you may end up to, when you want to remove a part of the list objects while parsing an ArrayList:

```java
// somewhere, with a definition like:
// ArrayList<Object> list = new ...

for ( Object object : list ) {
    if ( hasToBeRemoved(object) ) {
        list.remove(object);
    }
}
```

The solution does not work and it throws a `ConcurrentModificationException`, because it is not possible to modify a list while parsing it with a *foreach iterator*. We will come back to the topic better on week 12. If you run into such a situation, you can handle it in the following way:

```java
// somewhere, with a definition like:
// ArrayList<Object> list = new ...

ArrayList<Object> toBeRemoved = new ArrayList<Object>();

for ( Object object : list ) {
    if ( hasToBeRemoved(object) ) {
        toBeRemoved.add(object);
    }
}

list.removeAll(toBeRemoved);
```

The objects which have to be deleted are gathered together while we parse the list, and the remove operation is executed only after parsing the list.

{% include week10/exercise/006.md %}
{: .exercises }
