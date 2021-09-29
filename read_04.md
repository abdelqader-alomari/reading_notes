# Read: 04 - OOP

## Java OO Tutorial

OOP Stands for Object Oriented programming

### Object

An object is a software bundle of related state and behavior. Software objects are often used to model the real-world objects that you find in everyday life. Real-world objects share two characteristics: as example Bicycles have state (current gear, current pedal cadence, current speed) and behavior (changing gear, changing pedal cadence, applying brakes).

An object has three characteristics:

- State: represents the data (value) of an object.
- Behavior: represents the behavior (functionality) of an object such as deposit, withdraw, Saving.
- Identity: An object identity is typically implemented via a unique ID. The value of the ID is not visible to the external user. However, it is used internally by the JVM to identify each object uniquely.

Bundling code into individual software objects provides a number of benefits, including:

- Modularity: The source code for an object can be written and maintained independently of the source code for other objects. Once created, an object can be easily passed around inside the system.
- Information-hiding: By interacting only with an object's methods, the details of its internal implementation remain hidden from the outside world.
- Code re-use: If an object already exists (perhaps written by another software developer), you can use that object in your program. This allows specialists to implement/test/debug complex, task-specific objects.
- Pluggability and debugging ease: If a particular object turns out to be problematic, you can simply remove it from your application and plug in a different object as its replacement.

### Class

A class is a blueprint or prototype from which objects are created.

![Class](https://static.javatpoint.com/images/class-in-java.png)

#### Example:

```
class Bicycle {

    int cadence = 0;
    int speed = 0;
    int gear = 1;

    void changeCadence(int newValue) {
         cadence = newValue;
    }

    void changeGear(int newValue) {
         gear = newValue;
    }

    void speedUp(int increment) {
         speed = speed + increment;
    }

    void applyBrakes(int decrement) {
         speed = speed - decrement;
    }

    void printStates() {
         System.out.println("cadence:" +
             cadence + " speed:" +
             speed + " gear:" + gear);
    }
}

```

The fields cadence, speed, and gear represent the object's state, and the methods (changeCadence, changeGear, speedUp etc.) define its interaction with the outside world.

You may have noticed that the Bicycle class does not contain a main method. That's because it's not a complete application; it's just the blueprint for bicycles that might be used in an application. The responsibility of creating and using new Bicycle objects belongs to some other class in your application.

### Inheritance

Inheritance provides a powerful and natural mechanism for organizing and structuring your software.

The idea behind inheritance in Java is that you can create new classes that are built upon existing classes. When you inherit from an existing class, you can reuse methods and fields of the parent class. Moreover, you can add new methods and fields in your current class also.

Syntax:

```
class Subclass-name extends Superclass-name
{
   //methods and fields
}
```

## Binary, Decimal and Hexadecimal Numbers

Every digit in a decimal number has a "position", and the decimal point helps us to know which position is which:

![Decimal](https://www.mathsisfun.com/numbers/images/decimal.svg)

The position just to the left of the point is the "Ones" position. If we see a "7" there we know it means 7 ones.

Every position further to the left is 10 times bigger, and every position further to the right is 10 times smaller

#### Bases

The Decimal Number System is also called "Base 10", because it is based on the number 10, with these 10 symbols:

0, 1, 2, 3, 4, 5, 6, 7, 8 and 9

But notice something interesting: there is no symbol for "ten". "10" is actually two symbols put together, a "1" and a "0":

#### Counting with Different Number Systems

You could use 2 ("Binary"), 16 ("Hexadecimal"), or any number you want to as a base.

![](https://www.mathsisfun.com/numbers/images/number-odometer1.gif)

Count up until just before the "Base Number", then start at 0 again, but first you add 1 to the number on your left.

#### Binary Numbers

Binary Numbers are just "Base 2" instead of "Base 10". So you start counting at 0, then 1, then you run out of digits ... so you start back at 0 again, but increase the number on the left by 1.

Example : (0,1,10,11,100,101,110,111,1000,1001,1010,1011,1100,1001,1010,1011,1100,1101,1110,1111)

#### Hexadecimal Numbers

Hexadecimal numbers are interesting. There are 16 of them!

They look the same as the decimal numbers up to 9, but then there are the letters ("A',"B","C","D","E","F") in place of the decimal numbers 10 to 15.

So a single Hexadecimal digit can show 16 different values instead of the normal 10 like this:

Decimal: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
Hexadecimal: 0 1 2 3 4 5 6 7 8 9 A B C D E F

| Type        | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ----------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Decimal     | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  | 11  | 12  | 13  | 14  | 15  |
| HexaDecimal | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | A   | B   | C   | D   | E   | F   |
