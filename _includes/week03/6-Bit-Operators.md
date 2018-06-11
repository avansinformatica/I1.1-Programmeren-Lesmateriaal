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

These bits have an order. There are 2 ways of storing these bits in memory. The bit representing `1` is the **Least Significant Bit**, and the bit representing the largest value (128 in an 8-bit number for instance) is the **Most Significant Bit**. These way these values are stored in memory is called the [Endianness](https://en.wikipedia.org/wiki/Endianness), and is not the same on all computersystems. Java uses **Big Endian**, meaning the bit on the end is the most significant bit. This is only important on the way memory is stored, and won't affect us as a programmer.

Besides writing down numbers in different number systems, there are also a number of interesting operations we can do on these numbers

### 3.6.1 Bitwise And operator

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

### 3.6.2 Bitwise Or operator

The bitwise Or operator in java is written using the `|` operator. A bitwise And will combine the bits of 2 numbers with the Or operator. An example

```java
int firstNumber =  0b1010;
int secondNumber = 0b1100;
int result = firstNumber | secondNumber;
System.out.println(Integer.toBinaryString(result));
```

```output
1101
```

As we can observe, the bits set to 1 in the result are the ones where the bit is set to 1 either one of the `firstNumber` and the `secondNumber`. This can be combined in this small table

| first | second | result |
|-------|--------|--------|
| 0     | 0      | 0      |
| 1     | 0      | 1      |
| 0     | 1      | 1      |
| 1     | 1      | 1      |

### 3.6.3 Bitwise Xor operator

The bitwise Xor operator, or Exclusive Or, in java is written using the `^` operator. A bitwise Xor will combine the bits of 2 numbers with the Xor operator. An example

```java
int firstNumber =  0b1010;
int secondNumber = 0b1100;
int result = firstNumber ^ secondNumber;
System.out.println(Integer.toBinaryString(result));
```

```output
0110
```

As we can observe, the bits set to 1 in the result are the ones where only one bit is set to 1 either one of the `firstNumber` and the `secondNumber`. This can be combined in this small table

| first | second | result |
|-------|--------|--------|
| 0     | 0      | 0      |
| 1     | 0      | 1      |
| 0     | 1      | 1      |
| 1     | 1      | 0      |


### 3.6.4 Representation of negative numbers: Two's complement

So far we've only worked with positive numbers, but how do we store negative numbers? A first thought would be to reserve a single bit for the sign. If the on the most left is 1, it is a negative number, if it is a 0, it is a positive number. So for an 8bit number, we could do

```java
byte a = 0b00000001;    // 1
byte b = 0b10000001;    // -1
byte c = 0b00000000;    // 0
byte d = 0b10000000;    // -0?????
```

This leads to some problems though. For one, there is the problem of a double representation for 0. It also represents some challenges for computers to compute. [Two's complement](https://en.wikipedia.org/wiki/Two's_complement) is another system that was suggested back in 1945. In two's complement, there is only one representation of 0 (`0b00000000`) and it has some other additional advantages.

In Two's complement, the most significant bit is used to indicate a negative number, and all other bits are flipped (the complement), with one added. This can be seen in the following table, for 3-bit numbers. 3 bits range from -4 to 3.

| Decimal | Binary |
|---------|--------|
| 0       | 0`00`  |
| 1       | 0`01`  |
| 2       | 0`10`  |
| 3       | 0`11`  |
| -4      | 1`00`  |
| -3      | 1`01`  |
| -2      | 1`10`  |
| -1      | 1`11`  |

As seen in the table, for positive numbers, there's nothing special. For negative number, the MSB is set to 1, and the number is represented as the flipped bits, plus 1. For instance for `-4`, the bits are set to `00`. flipped around this is `11` or 3, and then with 1 added, makes 4. Expanding this to the 8-bit range, we can make the following table

| Decimal | Binary    |
|---------|-----------|
| 0       | 0000 0000 |
| 1       | 0000 0001 |
| 2       | 0000 0010 |
| 126     | 0111 1110 |
| 127     | 0111 1111 |
| −128    | 1000 0000 |
| −127    | 1000 0001 |
| −126    | 1000 0010 |
| −2      | 1111 1110 |
| −1      | 1111 1111 |

### 3.6.5 Bitshift Operators

### 3.6.6 Not Operator

### 3.6.7 Practical applications