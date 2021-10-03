# Read: 06 - Inheritance and Interfaces

## Object Oriented Overview

Tries to mimic real life with objects that have behaviors or methods and states.

### Classes

- Classes are blueprint or prototypes to create objects

- Classes has two main element: variables or fields and methods.

- Field/State: anything can be represented with data such as: number of seats, number of horsepower...

- Methods: such as start the engine, get color, get horsepower, stop engine, turn left, get average fuel consumption...

**Defining a class:** start with an access modifier(optional), then class keyword, after that ClassName, curly braces, inside the curly braces you can define the states (fields) and methods.

```
accessModifier class ClassName{
    variables
    methods
}
```

### Objects

Objects are instances of classes

**Defining an Object:** start with a ClassName, then the object name, equals new keyword, the ClassName.

`ClassName objectName = new ClassName(parameters);`

### Difference between classes and objects

| Class                                     | Object                             |
| ----------------------------------------- | ---------------------------------- |
| Blueprint or template to create object    | Instance of class                  |
| Declaring using class keyword             | Declaring using new keyword        |
| Declare once                              | Can be created many times          |
| Doesn't allocate memory when it's created | Allocates memory when it's created |

### Accessing fields and methods

Access Variables(Fields):
`objectName.variableName`

Access Methods:
`objectName.methodName(parameters)`

### Constructor

Special method in the class which called when you use new keyword to create objects, it is used to set up fields of the object at creation.

**To use:**
`ClassName objectName = new ClassName(parameters)`

**To define:**
`accessModifier ClassName(parameters){...}`

- example:

```
class FootballPlayer{
    short name;
    FootballPlayer(short name){
        this.name = Messi;
    }
    <!-- this keyword is used to refer object that you are going to create -->
}
```

`FootballPlayer ronaldo = new FootballPlayer();`

- Every class has a default constructor, even if you don't say it or don't define it.

---

## Inheritance

- The 4 Object Oriented principles: Inheritance, Encapsulation, Abstraction, Polymorphism.

- Inheritance is a relationship between classes, where class can have variables and methods of another class.

- Inheritance allows you define new class from an existing one and inherit its attributes and methods

- Advantages: avoid duplication and maintain relationship between classes.

- The idea of inheritance is simple but powerful: When you want to create a new class and there is already a class that includes some of the code that you want, you can derive your new class from the existing class. In doing this, you can reuse the fields and methods of the existing class without having to write (and debug!) them yourself.

**Use Inheritance:**

```
accessModifier class ClassName extends OtherClassName{
    class fields
    methods
}
```

Where ClassName here is subclass and OtherClassName is superclass

**Super VS. Subclass:**

| superClass           | Subclass                                                       |
| -------------------- | -------------------------------------------------------------- |
| parent or base class | child or derived class                                         |
| -------------------- | The subclass inherits the fields and methods of the superclass |

**What You Can Do in a Subclass**:

- The inherited fields can be used directly, just like any other fields.
- You can declare a field in the subclass with the same name as the one in the superclass, thus hiding it (not recommended).
- You can declare new fields in the subclass that are not in the superclass.
- The inherited methods can be used directly as they are.
- You can write a new instance method in the subclass that has the same signature as the one in the superclass, thus overriding it.
- You can write a new static method in the subclass that has the same signature as the one in the superclass, thus hiding it.
- You can declare new methods in the subclass that are not in the superclass.
- You can write a subclass constructor that invokes the constructor of the superclass, either implicitly or by using the keyword super.

* Inheritance is used only if an is a relationship is present between classes.

example:
A basketball is a(n) athlete
A football is a (n) athlete

So if we can form such sentences with the superclass and the subclass, we can use inheritance.

**An Example of Inheritance**

```
public class Bicycle {

    // the Bicycle class has three fields
    public int cadence;
    public int gear;
    public int speed;

    // the Bicycle class has one constructor
    public Bicycle(int startCadence, int startSpeed, int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;
    }

    // the Bicycle class has four methods
    public void setCadence(int newValue) {
        cadence = newValue;
    }

    public void setGear(int newValue) {
        gear = newValue;
    }

    public void applyBrake(int decrement) {
        speed -= decrement;
    }

    public void speedUp(int increment) {
        speed += increment;
    }

}
```

A class declaration for a MountainBike class that is a subclass of Bicycle might look like this:

```
public class MountainBike extends Bicycle {

    // the MountainBike subclass adds one field
    public int seatHeight;

    // the MountainBike subclass has one constructor
    public MountainBike(int startHeight,
                        int startCadence,
                        int startSpeed,
                        int startGear) {
        super(startCadence, startSpeed, startGear);
        seatHeight = startHeight;
    }

    // the MountainBike subclass adds one method
    public void setHeight(int newValue) {
        seatHeight = newValue;
    }
}
```

MountainBike inherits all the fields and methods of Bicycle and adds the field seatHeight and a method to set it. Except for the constructor, it is as if you had written a new MountainBike class entirely from scratch, with four fields and five methods. However, you didn't have to do all the work. This would be especially valuable if the methods in the Bicycle class were complex and had taken substantial time to debug.

---

### Interfaces

An interface is a completely "abstract class" that is used to group related methods with empty bodies:

To access the interface methods, the interface must be "implemented" (kinda like inherited) by another class with the implements keyword (instead of extends). The body of the interface method is provided by the "implement" class:

```
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void sleep(); // interface method (does not have a body)
}

// Pig "implements" the Animal interface
class Pig implements Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
  public void sleep() {
    // The body of sleep() is provided here
    System.out.println("Zzz");
  }
}

class Main {
  public static void main(String[] args) {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}

```

---

References:

- For Object Oriented: summarize from my study include lecture, internet videos... etc.
- For Inheritance: summarize from videos + https://docs.oracle.com/javase/tutorial/java/IandI/subclasses.html
- For Interfaces: I looked here https://docs.oracle.com/javase/tutorial/java/IandI/createinterface.html
  but I find this clear and take quotes from : https://www.w3schools.com/java/java_interface.asp

---
