---
id: x5fb7qzjf0tvyysb818w787
title: Computer Science 109 - Introduction to Programming
desc: ''
updated: 1699332251708
created: 1699330491987
---

# CHAPTER TWO - BUILT-IN DATA TYPES FOR PROGRAMMING

### Java Type Conversion
![Alt text](image-3.png)

There's **implicit conversion** and **explicit conversion**. Depending on whether the data type that the value is being converted takes up more or less space than the type it was before will govern whether or not Java can implicitly convert it or whether it will need to be explicitly converted. 

IMPLICIT CONVERSION
```
// My age in years
byte myAge = 23;    //(8 bits)
// Arbitrary integers
long someNumber;    //(64 bits)
int anotherNumber;    //(32 bits)
// My age plus a fractional year
double myAgePlus;    //(64 bits)
// Implicit conversion
someNumber = myAge;    //8 bits to 64 bits
/* someNumber implicitly converted to 64-bit; then a floating point
value of 0.5 is added. Result is then stored in myAgePlus */
myAgePlus = someNumber + 0.5;
/* These implicit conversions are NOT allowed!
Java will report an error */
anotherNumber = someNumber;
float anotherAge = myAgePlus;
```

EXPLICITY CONVERSION
```
// Arbitrary integers
long someNumber = 123;    // (64 bits)
int anotherNumber;    // (32 bits)
// First letter of the alphabet
char firstLetter = 'A';    // (16 bits)
// Explicit conversions using a type-cast
// Cast down from 64 bit to 32 bit
anotherNumber = (int) someNumber;
/* Cast from a char (16 bits) to a 16-bit integer. The
Unicode value for capital 'A' is \u0041 (which is 65 decimal),
so the 16-bit integer value of 65 will be stored in letterValue. */
short letterValue = (short) firstLetter;
```

# CHAPTER THREE - CONDITIONALS AND LOOPS IN PROGRAMMING

You know a lot of these concepts from JavaScript and your experience with other programming languages.
