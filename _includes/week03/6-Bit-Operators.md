## 3.6. Bit operators

So far we've been calculating with numbers using the `+`, `-`, `/`, `%` and `*` operators. These operations match with the normal math that we're used to. For computer programming however, there are also some other operations that operate on a bit level.

Internally, all numbers in the computer are represented using a binary format. So for instance the code

```java
int months = 12;
```

will store the number 12 in the memory of the computer. It is not stored as `12`, but more as `1100`. When it is printed out with `System.out.println` however, it is converted back to the decimal format, for human viewing. An explaination on the binary system is beyond the scope of this course, but the concept can be found on [wikipedia](https://en.wikipedia.org/wiki/Binary_number) or [other](https://learn.sparkfun.com/tutorials/binary) [sources](https://www.youtube.com/watch?v=LpuPe81bc2w). In java, by default, numbers are written in base 10. In the example above, `12` is the number 12 in base 10. Java supports other based numbers, by adding a prefix to the number.

```java
int decimalMonths = 12;        //base 10
int binaryMonths = 0b1100;     //base 2, binary
int octalMonths = 014;         //base 8, octal
int hexMonths = 0xC;           //base 16, hexadecimal
```

these variables will all contain the number 12. In order to view the binary representation of a number, we can use the helper method `Integer.toBinaryString()`

```java
System.out.println(Integer.toBinaryString(12));
```

```output
1100
```

There are also a number of interesting operations we can do on these numbers

## 3.6.1 Bitwise And operator

The bitwise And operator in java is written using the `&` operator. A bitwise And will combine the bits of 2 numbers with the And operator. An example

```java
int firstNumber =  0b1010;
int secondNumber = 0b1100;
int result = firstNumber & secondNumber;
System.out.println(Integer.toBinaryString(result));
```

```output
1000
```

As we can observe, the only bits set to 1 in the result are the ones where the bit is set to 1 both in the `firstNumber` and the `secondNumber`. This can be combined in this small table

| first | second | result |
|-------|--------|--------|
| 0     | 0      | 0      |
| 1     | 0      | 0      |
| 0     | 1      | 0      |
| 1     | 1      | 1      |

## 3.6.2 Bitwise Or operator

## 3.6.3 Bitwise Xor operator

## 3.6.4 Representation of negative numbers: Two's complement

## 3.6.5 Bitshift Operators

