## 16. Abstract class

In the shape example of last chapter, there's still a big problem. It is possible in java to make a new `Shape`

```java
Shape shape = new Shape(Color.green);
```

This would of course be nonsense, as a 'shape' does not really have a surface area or circumference. The methods in this class now return 0, but we can also remove the code for these methods, by turning this class into an `abstract` class

```java
class Shape {
    private Color color;

    public Shape(Color color) {
        this.color = color;
    }
    public abstract double getArea();
    public abstract double getCircumference();
}
```

An abstract class can contain abstract methods, which are methods that do not have an implementation. There is no code for these methods because it makes no sense, like in our Shape example. This also makes sure that there can be no new Shape objects, because it has abstract methods. 

```java
Shape shape = new Shape(Color.green); // won't compile, as Shape is an abstract class
```

In order to make an object, just extend the Shape class, and implement the abstract methods, as done before. This new class is **not** abstract anymore
