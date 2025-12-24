<img src="../assets/logo.png" width=30% />

<hr>
<span style="display:flex; justify-content: space-between;">
	<a href="../index.html">Home</a>   <a href="../week-2/summary.html">Week-2</a>    <a href="../week-4/summary.html">Week-4</a>    
</span> 
<hr>

# Java - Week 3

[Toc]

## Philosophy of Structured programming and Object oriented programming

Structured programming consists of designing a set of procedures (or algorithms) to solve a problem. Once the procedures are determined, the next step was to find appropriate ways to store the data.

Object-oriented programming, or OOP for short, is the dominant programming paradigm. An object-oriented program is made of objects. Each object has a specific functionality, exposed to its users, and a hidden implementation. OOP reverses the order: puts the data first, then looks at the algorithms to operate on the data. For small problems, the breakdown into procedures works very well. But objects are more appropriate for larger problems.

Example: Consider a simple web browser. In structured programming style, it might require 2,000 procedures for its implementation, all of which manipulate a set of global data. In the object-oriented style, there might be 100 classes with an average of 20 methods per class. This structure is much easier for a programmer to grasp. It is also much easier to find bugs in. Suppose the data of a particular object is in an incorrect state. It is far easier to search for the culprit among the 20 methods that had access to that data item than among 2,000 procedures.

Object oriented programming design

Structured programming start with the main function. OOP often wonder where to begin,the answer is identify classes and then add methods to each class.

For example, in an order-processing system, some of the nouns are

- Item
- Order
- Shipping address
- Payment
- Account

These nouns signify the classes Item, Order, and so on.

Some of the verbs are

- Items are _added_ to orders
- Orders are _shipped_ or _canceled_
- Payments are _applied_ to orders

Verbs denote methods that operate on objects, `add` should be the method of `Order` class that takes an `Item` object as parameter

The key characteristics of objects are:

- Behavior — what methods do we need to operate on objects?

- State — how does the object react when methods are invoked?

- Identity — distinguish between different objects of the same class

All objects that are instances of the same class share a family resemblance by supporting the same behavior. State is the information in the instance variables, an object’s state may change over time, it must be a consequence of method calls. Each object has a distinct identity. For example, in an order processing system, two orders are distinct even if they request identical items.

## Relationship between classes

Dependence ("uses-a") — a class depends on another class if its methods use or manipulate objects of that class. For example, the `Order` class uses the `Account` class because `Order` objects need to access `Account` objects to check for credit status. But the `Item` class does not depend on the `Account` class, because Item objects never need to worry about customer accounts.

Aggregation ("has-a") — an Order object contains Item objects. Containment means that objects of class A contain objects of class B.

inheritance ("is-a") — a relationship between a more special and a more general class.

## Inheritance and Subclass

It is the process of reusing the properties of an existing class. The class whose properties are inherited is considered as parent class or super class, and the inheriting class is the child or sub class.

A subclass extends a parent class, inherits instance variables and methods from the parent class, cannot see private components of parent class, can add more instance variables and methods, can also override methods

```java
public class Employee{
	private String name;
	private double salary;
	// Constructor
    public Employee(String n, double s){
        name = n;
        salary = s;
    }
	// "mutator" methods
	public void setName(String s){
        name = s;
    }
	public void setSalary(double x){
        salary = x;
    }
	// "accessor" methods
	public String getName(){
        return name;
    }
	public double getSalary(){
        return salary;
    }
	// other methods
	public double bonus(float percent){
		return (percent/100.0)*salary;
	}
}
```

An Employee class has two private instance variables, a constructor to set up the object, accessor and mutator methods to set instance variables, a public method to compute bonus

```java
public class Manager extends Employee{
    private String secretary;
    public Manager(String n, double s, String sn){
		super(n,s); // super calls Employee constructor
        secretary = sn;
	}
    public void setSecretary(String s){
        secretary = s;
    }
	public String getSecretary(){
        return secretary;
    }
  public double bonus(float percent){
    return 1.5 * super.bonus(percent);
  }
  //this is overriding method, we can call the bonus method of parent using the keyword super
}
```

Manager is a subclass of Employee, managers are special types of employees with extra features. Manager objects inherit fields and methods from Employee. Every Manager has a name, salary and methods to access and manipulate these.

Manager objects do not automatically have access to private data of parent class. How can a constructor for Manager set instance variables that are private to Employee?

The constructors for Manager can make use of parent class’s constructor using the keyword super

Every Manager is an Employee, but not vice versa! We can use a subclass in place of a superclass.

```java
Employee e = new Manager(...) //This is correct
//But the following will not work
Manager m = new Employee(...) //This is not correct
```

## Static typechecking

The variable e here is defined as a variable of type Employee, therefore it can only call methods and access variables which are available in the class Employee, even though the object being referenced is of type Manager.

```java
e.getSalary() //this is a CORRECT call
e.getSecretory() //this is invalid since getSecretory() method is available in class manager
```

## Dynamic dispatch

Dynamic dispatch, also known as runtime polymorphism or inheritance polymorphism, is a mechanism in Java where the appropriate implementation of an overridden method is determined at runtime based on the actual type of the object being referenced, rather than the declared type of the reference variable.

```java
e.bonus(0.05);
```

This invokes the method bonus defined in the Manager class, since the actual object in the variable e is of type Manager. In case of static methods, this is not true. There, the method that will be called is decided based on the type of variable instead of the object that is getting referenced.

## Function signatures and method overloading

Signature of a function is its name and the list of argument types that it takes. It helps in uniquely identifying a method.

**Method overloading** is a feature that allows a class to have two or more methods with the same name, but with different parameters. When a method is overloaded, Java decides which method to call based on the number and types of arguments passed to the method.

```java
class A{
  public void printName(String name){
    System.out.println("Congratulations! "+name);
  }
  public void printName(String name, int age){
    System.out.println("Congratulations! "+name+" for turning "+age);
  }
}
public class B{
  public static void main(String[] args){
    A obj = new A();
    obj.printName("Harshal");
    //this calls the first printName method and outputs: Congratulations! Harshal
    obj.printName("Harshal", 21);
    //this calls the second printName method and outputs: Congratulations! Harshal for turning 21
  }
}
```

**Method overriding** allows a subclass to provide a specific implementation of a method that is already defined in its superclass. When a method is overridden, the subclass provides a new implementation for the method, and the new implementation is used instead of the implementation provided by the superclass. Method overriding is used to provide a different implementation of a method in the subclass that is more suited to the specific needs of the subclass.

```java
class Animal{
  public void makeSound(){
    System.out.println("Animal makes sound");
  }
}
class Cat extends Animal{
  public void makeSound(){
    System.out.println("Cat meows");
  }
}
public class A{
  public static void main(String[] args){
    Animal animal = new Animal();
    animal.makeSound();
    //this calls the makeSound method defined in Animal class and outputs: Animal makes sound
    Cat cat = new Cat();
    cat.makeSound();
    //this calls the makeSound method defined in Cat class and outputs: Cat meows
  }
}
```

## Type Casting

Taking the previous example of Employee and Manager, we can typecast the variable e into Manager in order to call methods only defined in Manager class.

```java
((Manager)e).getSecretory(); //this is valid
```

If e was not a Manager, this cast would have thrown error, therefore it's safe to check if a variable can be converted to some type before actually converting it to that type.

We can check this using the following code

```java
if(e instanceof Manager){
  ((Manager)e).getSecretory();
}
//e instanceof Manager returns True if e is an instance of class Manager
```

## Subtyping vs Inheritance

### Subtyping

Capabilities of a subtype are a superset of the main type, so wherever we want to use the main type, we can make use of the subtype because it can perform all the functions of the main type.

### Inheritance

If class Manager inherits from class Employee, it means some methods of the class Manager are written in terms of methods of class Employee.

Let's understand these concepts with the help of an example

The following classes allows certain operations

- `queue` - insert_rear, delete_front
- `stack` - insert_front, delete_front
- `deque` - insert_front, delete_front, insert_rear, delete_rear

Here, `deque` has more functionality than `stack` or `queue`, therefore `deque` is a subtype of both `stack` and `queue`.

Wherever there is a need of `stack` or `queue`, we can use a `deque` instead, since it can perform all the operations from the other two.

We can suppress two method of `deque` and use it as `stack` or `queue`, therefore stack and queue both inherit from `deque`. The functionalities of both `stack` and `queue` can be written in terms of functionalities of `deque`.

## Modifiers in Java

Java uses many modifiers in declarations, to cover different features of object-oriented programming. These modifiers can be applied to classes, instance variables and methods

### public vs private

private modifier prevents access to a class's methods or properties from any code that is outside the class while public access modifier allows a code from outside or inside the class to access the class's methods and properties.

Typically, instance variables are private and methods used to interact with the instance variables (accessors and mutators) are public.

```java
public class Date{

  //Instance variables
  private int year;
  private int month;
  private int day;

  //Accessors
  public int getYear(){
    return year;
  }
  public int getMonth(){
    return month;
  }
  public int getDay(){
    return day;
  }

  //Mutators
  public void setYear(int year){
    this.year = year;
  }
  public void setMonth(int month){
    this.month = month;
  }
  public void setDay(int day){
    this.day = day;
  }
}
```

**Does it make sense to have private methods?**

**private** methods are invoked internally and they are not for the use of the user. For example the Date class needs to check if a day is <= 31 before storing it in the instance variable, so it can have the following private method to do that.

```java
private boolean validDate(int date){
  return date <= 31;
}

//The following can be a possible implementation of method setDay
public void setDay(int day){
  if(validDate(day)){
    this.day = day;
  }else{
    System.out.println("Invalid Day");
  }
}
```

### static

This access modifier allows components to exist without creating any objects. They are also usually **public**. For example, a class named Math created for performing various mathematical operations can contain variables such as PI. For using the value of PI there's no reason to create a new object of class Math. Declaring this variable as static allows us to use it directly.

```java
System.out.println(Math.PI); //3.14...
```

### final

This modifier denotes that values cannot be updated. Let's take the same example of the Math class. The value of PI is a constant and we won't ever have a need to change that. So it makes sense to declare the variable as final, otherwise by mistake someone can end up changing the value of PI.

```java
class Math{
  public final PI = 3.14;

  public changePI(){
    this.PI = 3.15; //Not allowed
  }
}
```

**Meaning of final in methods**

**final** modifier when used in front of a method, means that method can never be overridden in any of the subclasses.

```java
class A{
  public final void print(){
    System.out.println("Inside class A");
  }
}
class B extends A{
  public void print(){
    System.out.println("Inside class B");
  }
  //The above method declaration is invalid.
}
```

## Object Class

In Java, `Object` is a built-in class that serves as the base class for all other classes. It is the superclass of every other class in Java. As a result, every Java class is either a direct or an indirect subclass of the `Object` class.

The `Object` class provides several methods that can be used by any class. We can override these methods inside a class, to provide custom implementation for that particular class.

Example of some methods which are present in the `Object` class are:

- `equals(Object obj)` - This method is used to compare two objects for equality. We can override this method inside a class in order to provide custom implementation for checking equality between objects of that class. It returns `true` if the objects are equal, and `false` otherwise.
- `toString()` - This method returns a string representation of the object which gets printed, when we print the object. We can provide a specialized implementation of this method in a class to print objects of that class in a certain way.
- `hashCode()` - This method returns the hash code value for the object. It is a unique integer value generated using properties of an object.
