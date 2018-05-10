## 5. Calculation

The calculation operations are pretty straightforward: +, -, * and /. A more peculiar operation is the modulo operation %, which calculates the remainder of a division. The order of operations is also pretty straightforward: the operations are calculated from left to right taking the parentheses into account.

```java
int first = 2;   // variable of whole number type is assigned the value 2
int second = 4;  // variable of whole number type is assigned the value 4
int sum = first + second;  // variable of whole number type is assigned the value of first + second
                           //     (which means 2 + 4)

System.out.println(sum); // the value of the sum of variables is printed
```

```java
int calcWithParens = (1 + 1) + 3 * (2 + 5);  // 23
int calcWithoutParens = 1 + 1 + 3 * 2 + 5;   // 13
```

The parentheses example above can also be done step by step.

```java
int calcWithParens = (1 + 1);
calcWithParens = calcWithParens + 3 * (2 + 5);  // 23

int calcWithoutParens = 1 + 1;
calcWithoutParens = calcWithoutParens + 3 * 2;
calcWithoutParens = calcWithoutParens + 5;      // 13
```

Calculation operations can be used almost anywhere in the program code.

```java
int first = 2;
int second = 4;

System.out.println(first + second);
System.out.println(2 + second - first - second);
```

### 5.1 Floating point numbers (decimal numbers)

Calculating the division and remainder of whole numbers is a little trickier. A floating point number (decimal number) and integer (whole number) often get mixed up. If all the variables in a calculation operation are integers, the end result will also be an integer.

```java
int result = 3 / 2;  // result is 1 (integer) because 3 and 2 are integers as well
```

```java
int first = 3:
int second = 2;
double result = first / second;  // the result is again 1 because first and second are integers
```

The remainder can be calculated using the remainder operation (%). For example, the calculation 7 % 2 yields 1.

```java
int remainder = 7 % 2;  // remainder is 1 (integer)
```

If either the dividend or the divisor (or both!) is a floating point number (decimal number) the end result will also be a floating point number.

```java
double whenDividendIsFloat = 3.0 / 2;  // result is: 1.5
double whenDivisorIsFloat = 3 / 2.0;   // result is: 1.5
```

If needed, integers can be converted to floating point using the type cast operation `(double)` as follows

```java
int first = 3;
int second = 2;
double result1 = (double)first / second;  // result is: 1.5

double result2 = first / (double)second;  // result is: 1.5

double result3 = (double)(first / second);  // result is: 1
```

In the last example calculation, the result is rounded incorrectly because the calculation between the integers is done before the type cast to a floating point number.

If the quotient is assigned to a variable of integer type, the result will be an integer as well.

```java
int integerResultBecauseTypeIsInteger = 3.0 / 2;  // quotient is automatically integer: 1
```

The next example will print "1.5" because the dividend is transformed into a floating point number by multiplying it with a floating point number (1.0 * 3 = 3.0) before the division.

```java
int dividend = 3;
int divisor = 2;

double quotient = 1.0 * dividend / divisor;
System.out.println(quotient);
```

What does the following code print?

```java
int dividend = 3;
int divisor = 2;

double quotient = dividend / divisor * 1.0;
System.out.println(quotient);
```

From now on, make sure that you name your variables that follow good conventions like the variables in the examples above.

{% include week01/exercise/005.md %}
{: .exercises }
