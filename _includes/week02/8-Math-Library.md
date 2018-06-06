## 2.8 Math Library

A lot of functionality can be implemented by now, using the basic code stuctures that we've encountered so far. We could for example, write a method to determine the [absolute value](https://en.wikipedia.org/wiki/Absolute_value) of a number. The code for such a method could be as follows

```java
public static int abs(int number)
{
    if(number < 0) {
        return -number;
    } else {
        return number;
    }
}
```

Writing these methods for all basic math concepts is not very hard, but it is a lot of work to write them. Fortunately, a lot of this has already been written, and combined in the `Math` structure. We can find a lot of information on this in the [documentation](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html). In this documentation, we can typically find some very important information on these method. The document starts with a long list of available methods, followed by a short description. Clicking on a method will show a longer description

![abs](images/2_8_abs.png)

In the line `public static int abs(int a)` we can see the parameter type, and a description of the parameter. We can also see the *return type*, which will be covered next week. Also a precise description is available, to see exactly what this method will do.

Some convenient methods are:

- `abs` Returns the absolute value of a value.
- `ceil` Returns the smallest (closest to negative infinity) double value that is greater than or equal to the argument and is equal to a mathematical integer.
- `cos` Returns the trigonometric cosine of an angle. (parameter is in radians)
- `floor` Returns the largest (closest to positive infinity) double value that is less than or equal to the argument and is equal to a mathematical integer.
- `log` Returns the natural logarithm (base e) of a double value.
- `max` Returns the greater of two values.
- `min` Returns the smaller of two values.
- `pow` Returns the value of the first argument raised to the power of the second argument.
- `random` Returns a double value with a positive sign, greater than or equal to 0.0 and less than 1.0.
- `round` Returns the closest int to the argument, with ties rounding to positive infinity.
- `signum` Returns the signum function of the argument; zero if the argument is zero, 1.0 if the argument is greater than zero, -1.0 if the argument is less than zero.
- `sin` Returns the trigonometric sine of an angle. (parameter is in radians)
- `sqrt` Returns the correctly rounded positive square root of a double value.
- `tan` Returns the trigonometric tangent of an angle.
- `toDegrees` Converts an angle measured in radians to an approximately equivalent angle measured in degrees.
- `toRadians` Converts an angle measured in degrees to an approximately equivalent angle measured in radians.

Also you can use `Math.PI` as a value of $$\pi$$

