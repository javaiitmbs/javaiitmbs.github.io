<img src="../assets/logo.png" width=30% />

<hr>
<span style="display:flex; justify-content: space-between;">
	<a href="../index.html">Home</a>   <a href="../week-1/summary.html">Week-1</a>    <a href="../week-3/summary.html">Week-3</a>    
</span> 
<hr>

# Java - Week 2

[TOC]

This is an introduction to Java programming language, this chapter is an essential resource that will provide you with the knowledge and tools you need to begin writing Java code. We'll start by writing simple pieces of code, to saving them on the system and finally executing the programs to perform the desired operation.

Let's start with the most basic Java program as an example

## Basic JAVA Program

```java
public class FirstProgram{
	public static void main(String[] args){
		System.out.println("Hello World");
	}
}
```

Java is a case-sensitive programming language, meaning that it treats uppercase and lowercase letters as distinct characters. Writing Main instead of main will not work. Also, the variable names "firstName" and "firstname" are considered to be different variables in Java.

In Java, the main method is used by default as the starting point of a program.

## Modifiers

Modifiers play an important role in any Java program. A modifier in Java is a keyword that is used to change the behavior of a class, method, or field. Example visibility can be controlled using modifiers like public, private. Using the above program as example we can see two modifiers. Let us closely understand them

1. public - this is an access modifier and it allows access to the class, method or field from anywhere across the program.

   ```java
   class A{
     private int num;
     public A(int num){
       this.num = num;
     }
   }
   public class B{
     public static void main(String[] args){
       A var = new A();
       System.out.println(var.num);
       //Throws error since num is a private variable in class A, it cannot be accessed inside class B.
     }
   }
   ```

2. static - allows us to use the method or field without creating an instance of the class.

   ```java
   class A{
     public void printa(){
       System.out.println("We are inside class A.");
     }
   }
   class B{
     public static void printb(){
       System.out.println("We are inside class B.");
     }
   }
   public class C{
     public static void main(String[] args){
       A obj = new A();
       obj.printa(); //We need an object of class A in order to call printa method
       //A.printa() is not possible
       B.printb(); //We can directly call printb method because it's static
     }
   }
   ```

   We will learn them in more detail in the upcoming chapters, so it's normal if you find any of the given examples confusing.

## Return Type

In Java, return type refers to the data type of the value that is returned by the method. Let's look at a simple example to understand this.

```java
public int square(int num){
  return num*num;
}
```

In the given example, we can see that the function named square takes in a number which is of type integer and it returns the square of that number, which is an integer in itself. Therefore, we have specified int as the return type of the function.

## Saving a JAVA Program

There are certain rules we need to follow in order to save a Java program before we can finally run it. The file name needs to be exactly same as the class contained in the file.

```java
public class myprogram{
  public int num;
  public void printNum(){
    System.out.print(num);
  }
}
```

The above program needs to be saved in a file named myprogram.java for it to be ready for execution. Note that it is necessary for every file to have the extension .java

## Running a JAVA Program

In order to run a Java Program, we first need to compile the saved program to bytecode before we can finally run it, which can be done using the command javac, for example

```bash
javac myprogram.java
```

This creates a new file named myprogram.class which contains the bytecode that can be executed using the command java, like

```bash
java myprogram
```

Note that while running the bytecode we do not need to specify any extension like .java or .class

## Primitive Data Types

Data types are a fundamental concept any programming language and refer to the type of values that can be stored within a specific variable.

A primitive data type in Java is a basic data type that is built into the Java language and is not an object created from a class. There are 8 primitive data types in java:

- int

  An integer data type is a data type that represents whole numbers. An integer is typically represented using 4 bytes, or 32 bits. It can be used to represent values between -2,147,483,648 and 2,147,483,647.

  ```java
  int num = 1000000007; //an example of how to use integer
  ```

- short

  It is a 16-bit integer that can represent values ranging from -32,768 to 32,767. The `short` data type is smaller than the `int` data type, which is also used to store integers in Java. However, using `short` can be useful in situations where memory is a concern, or when the range of data we've to work with is small.

  ```java
  short num = 12345; //an example of how to use short
  ```

- byte

  In Java, the byte data type is an 8-bit signed integer that can represent values from -128 to 127. It is commonly used to store small integer values, ASCII values, etc.

  ```java
  byte num = 125; //an example of how to use byte
  ```

- long

  In Java, the long data type is a 64-bit signed integer that can represent values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807. It is used to store large integer values that exceed the range of the int data type.

  ```java
  long num = 123456789L; //an example of how to use long
  ```

  In this example, we declare a long variable named "num" and assign it the value 123456789. Note that we need to append the letter "L" to the end of the literal value to indicate that it is a long value. If we don't include the "L", Java will interpret the value as an int and raise a compilation error if it exceeds the maximum value of an integer.

- float

  Float data type is a 32-bit single-precision floating point number. It is used to represent decimal values that require less precision than the double data type (approximately 6–7 significant decimal digits).

  ```java
  float num = 3.1415f; //an example of how to use float
  ```

  Note that we need to append the letter "f" to the end of the literal value to indicate that it is a float value. If we don't include the "f", Java will interpret the value as a double and raise a compilation error.

- double

  In Java, the double data type is a 64-bit double-precision floating point number. It is used to represent decimal values that require more precision than the float data type (15 significant decimal digits).

  ```java
  double d = 3.14159; //an example of how to use double
  ```

- char

  The char data type is used to represent a single character. It is a 16-bit Unicode character that can store characters from the Unicode character set, which includes alphabets, digits, punctuation marks, and other symbols.

  ```java
  char c = 'A'; //an example of how to use char
  ```

- boolean

  The boolean data type is used to represent true/false values. It is a primitive data type that can only take two values, true or false.

  ```java
  boolean b = true; //an example of how to use boolean
  ```

## Declaring and Initializing Variables

A variable is used to store data in a Java program.

We can declare variables by specifying the type followed by the name of variable. Example if we want to initialize an integer with value 100, we can do it as follows:

```java
int num = 100; //declaring and initialising variable at the same time
```

or we can declare the variable before initialising it

```java
int num; //declaring variable
num = 100; //initialising variable
```

## Arithmetic Operators

Arithmetic operators are a set of mathematical operations used to perform arithmetic operations in Java programming language. They are used to perform basic mathematical operations like addition, subtraction, multiplication, division, and modulus (remainder) on numeric data types such as integers, floating-point numbers, etc. Arithmetic operators have the following symbols:

- Addition (+)
- Subtraction (-)
- Multiplication (\*)
- Division (/)
- Modulus ( % )

It's important to note that the type of the result of an arithmetic operation depends on the operand types. For example, when two integers are divided, the result is also an integer, but when a floating-point number is divided by an integer, the result is a floating-point number.

These operators can be used as following:

```java
int num1 = 5;
int num2 = 10;
int sum = num1 + num2; // 15
int mult = num1 * num2; // 50
int div = num2 / num1; // 2
int sub = num2 - num1; // 5
int mod = num2 % num1; // 0 (10 gets completely divided by 5 and it leaves no remainder)
```

## Type Casting

This is the process of converting variables from one data type to another, like an integer to float. There are two types of casting, implicit and explicit.

1. Implicit conversion is when a data is automatically converted to a different type. Below is a program which is an example of that.

```java
int num = 100;
float copynum;
copynum = num;
//copynum now contains the value 100.0 which is a float because we initialised it to a variable of type float.
```

1. Explicit conversion is when a data is converted to a different type by the programmer using the cast operator.

```java
double d = 9.99;
int i = (int) d;
// i now contains just 9 which is trucated version of 9.99
```

You may wonder why do we need to explicitly convert double to integer, but in the other case when we converted integer to double it was not required. The reason for this is that, Java implicitly casts data when we move from lower order to higher order since all the information is preserved.

Example, when we converted integer 100 to float 100.0, no information was lost about the integer. But on the other side, when we converted double 9.99 into integer 9, the precision after the point was lost. So, Java needs the programmer to explicitly specify that they intend to perform this type of cast where they may end up losing information.

## Strings

In Java, a String is a sequence of characters that represents text. They can be declared and initialized as follows

```java
String name = "Shubham";
```

Strings are represented as objects, which means they have methods that can be used to manipulate their contents. For example, you can concatenate two strings together using the "+" operator, or find the length of a string using the "length()" method.

```java
String fName = "Shubham";
String lName = "S.";
String fullName = fName + " " + lName;
System.out.println(fullName); // Shubham S.
System.out.println(fName.length()) //7
```

Strings in Java are also immutable, which means that once a string is created, its value cannot be changed. Instead, operations that appear to modify a string actually create a new string with the modified value.

```java
name[0] = "A";
//This is not allowed
```

### Some helpful methods that can be used on string objects -

- `charAt(int index)`: Returns the character at the specified index.
- `substring(int beginIndex, int endIndex)`: Returns a substring of the string starting from the specified begin index and ending at the specified end index.
- `toUpperCase()` and `toLowerCase()`: These methods return a new string with all characters converted to uppercase or lowercase, respectively.
- `equals(Object obj)`: This method compares the string to the specified object and returns true if they are equal.
- `indexOf(char c)` or `indexOf(String str)`: These methods return the index of the first occurrence of the specified character or substring in the string, respectively.

## Arrays

An array in Java is a data structure that allows you to store a fixed-size sequential collection of elements of the same data type. It can be thought of as a container that holds a group of items of the same type, such as integers or strings.

You can access each element in the array by its index, which is a numeric value that represents its position in the array. The first element in the array has an index of 0, the second has an index of 1, and so on.

```java
//Declaring an array to store 100 integers

int arr[] = new int[100];
arr[0] = 5; //setting the first element of the array
arr[1] = 10; //setting the second element of the array
arr[2] = 15; //setting the third element of the array
arr[3] = 20; //setting the fourth element of the array

System.out.println(arr[0]); //5 (prints the first element of the array)
```

## Conditional Execution

Conditional statements allow the program to make decisions based on conditions. They allow a program to execute a certain section of code only if a specified condition is true. There are two ways by which we can do this:

### if-else

```java
String name = "ABC"
if(name=="DEF"){
		//Do something if name is DEF
}else if(name=="ABC"){
		//Do something if name is ABC
}else{
		//Do something if none of the above conditions are met
}
```

### switch-case

The switch statement is used to perform different actions based on different conditions. It evaluates the expression inside the switch statement and then matches the value of that expression against a set of possible case values. If the value matches any of the case values, the corresponding code block is executed.

```java
String name = "DEF";
switch(name){
	case "ABC":
		//Do something if name is ABC
		break;
	case "DEF":
		//Do something if name is DEF
		break;
	default:
		//Do something if none of the above cases match
}
```

We have to use break in every case because if there is no break statement, then once a case is met all the cases after that are executed unless a break statement is found. Let's see this through an example

```java
int day = 5;
switch (day) {
  case 1:
    System.out.println("Monday");
  case 2:
    System.out.println("Tuesday");
  case 3:
    System.out.println("Wednesday");
  case 4:
    System.out.println("Thursday");
  case 5:
    System.out.println("Friday");
  case 6:
    System.out.println("Saturday");
  case 7:
    System.out.println("Sunday");
}
```

Now, notice that there are no break statements inside any of these cases. So, here the output of this program is

```
Friday
Saturday
Sunday
```

break statement is optional in the default block, since anyway that's the last code block and there's nothing which will get executed after it.

## Conditional Loops

Conditional loops in Java are control structures that allow the program to execute a certain block of code repeatedly, as long as a certain condition is met. We have 3 types of conditional loops in Java, let us see them one by one in detail.

### while

A `while` loop in Java is a control flow statement that allows a block of code to be executed repeatedly while a particular condition is true.

The condition is evaluated at the beginning of each iteration of the loop. If the condition is true, the code inside the loop is executed. After the code is executed, the condition is evaluated again, and the process continues until the condition becomes false.

Here's an example of a `while` loop that prints the string "Print this line..." 10 times:

```java
int i = 0;
while(i < 10){
		System.out.println("Print this line...");
		i++;
}
```

The output of the above loop is

```
Print this line...
Print this line...
Print this line...
Print this line...
Print this line...
Print this line...
Print this line...
Print this line...
Print this line...
Print this line...
```

The program iterates over the values of `i` from 0 to 9, inclusive, and outputs a single line for each iteration. Once `i` reaches 10, the loop terminates as the condition in the parentheses is no longer satisfied.

### do-while

A `do-while` loop in Java is similar to a `while` loop, but with one key difference: the code inside the loop is guaranteed to be executed at least once, regardless of whether the condition is true or false.

The code inside the loop is executed once, and then the condition is evaluated. If the condition is true, the loop will execute again, and the process will continue until the condition becomes false. If the condition is false from the beginning, the loop will still execute once.

Let us understand the do while loop using a simple example

```java
int i = 1;
do{
		System.out.println("Printing...");
		i++;
}while(i<0);
```

The output of the above loop is

```
Printing...
```

The condition is initially not met, however, it is evaluated after the first iteration of the loop has been executed. As a result, the statement within the `do` block will be executed once.

### for

A `for` loop in Java is a control flow statement that allows a block of code to be executed repeatedly for a fixed number of times, based on a specified condition.

Syntax of for loop is as follows:

```java
for (initialization; condition; update) {
 		 // code to be executed
}
```

The `initialization` statement is executed once at the beginning of the loop, and is typically used to initialize a loop counter variable. The `condition` is evaluated at the beginning of each iteration of the loop. If the condition is true, the code inside the loop is executed. After the code is executed, the `update` statement is executed, and the condition is evaluated again. The loop continues to execute as long as the condition is true.

Let us look at it through a simple example

```java
for(int i = 0; i < 10; i++){
		System.out.println("Hello");
}
```

The output of the above code will be

```
Hello
Hello
Hello
Hello
Hello
Hello
Hello
Hello
Hello
Hello
```

The program iterates over the values of `i` from 0 to 9, inclusive, and outputs a single line for each iteration. Once `i` reaches 10, the loop terminates as the condition is no longer satisfied.

## Class

In Java, a class is a blueprint or template for creating objects. It defines the variables and methods that an object of that class will have.

You can think of a class as a complex type let's say Fruits, each fruit will have a certain properties like it's weight and amount of calories, it contains. Also, we can do something with each fruit, like eat it.

In order to represent all properties and methods to manipulate objects of a complex type like Fruits, we can define a class.

### Defining a class

To declare a class in Java, you use the "class" keyword followed by the name of the class.

```java
public class Fruits {

  	//Instance variables
	private int weight;
  	private int calories;

  	//Methods
	public void eat(){
		System.out.println("Fruit finished.");
	}
}
```

Each object of class Fruits will have two properties, weight and calories. Also eat() method can be invoked on every object of the class.

## Object

An object, is an instance of a class and is used to access the variables and methods defined by the class. Each object of class Fruits will have a local copies of the variables weight and calories, therefore changing the weight of one object will not affect others.

### Creating an object

In order to create objects, the type of variable is the class for which we want to create that particular object. Objects are created using the new operator, followed by a call to the constructor of the class. For example

```java
ClassName objectName = new ClassName();
```

Like if we want to create an object of Fruits class we can write the following code

```java
Fruits myBanana = new Fruits();
```

### Manipulating objects

We can define public mutator methods inside a class, which can be used by the objects of that class to modify themselves.

Note: this keyword is used to reference the current object

Example, this is a mutator method which can be defined inside Fruits class in order to modify variables of an object.

```java
public void setDetails(int weight, int calories){
	this.weight = weight;
	this.calories = calories;
}
//this can be used as myBanana.setDetails(200,50) to set weight and calories of the object myBanana

public void setWeight(int weight){
  this.weight = weight;
}
//this can be used as myBanana.setWeight(200) to set weight of the object myBanana

public void setCalories(int calories){
  this.calories = calories;
}
//this can be used as myBanana.setCalories(50) to set calories of the object myBanana
```

### Reading variables

Public accessor methods can be defined inside a class in order to read values of the variables inside the objects of that class. Example, in order to read weight and calories of objects of Fruits class, we can define the following methods inside the class.

```java
public int getWeight(){
	return this.weight;
}
//myBanana.getWeight() gives 200

public int getCalories(){
	return this.calories;
}
//myBanana.getCalories() gives 50
```

## Constructors

These are special functions which have the same name as the class without any return type and are called at the time of creation of an object. We can create constructors in order to set up certain properties of an object at the time of creation of that object.
Constructor for Fruits class:

```java
public Fruits(int weight, int calories){
		this.weight = weight;
		this.calories = calories;
}
Fruits myApple = new Fruits(200, 50);
//creates an object of class Fruits with weight equal to 200 and calories 50
```

By default, a class includes a non parameterized constructor when no explicit constructor is defined. However, when a constructor is explicitly defined, the default empty constructor is no longer automatically generated.

### Overloading

Method overloading in Java allows a class to have multiple methods with the same name, but different parameters. Example

```java
public Fruits(int weight, int calories){
		this.weight = weight;
		this.calories = calories;
}

public Fruits(int weight){
		this.weight = weight;
		this.calories = 50;
}

// If constructor is called with 2 arguments we set the values for weight and calories, else if constructor is called by passing 1 argument we set the calories equal to 50 by default.

//First Constructor new Fruits(200,50);
//Second Constructor new Fruits(200);

```

### Copy constructor

A copy constructor in Java is a constructor that creates a new instance of an object from an existing one. It takes an object of the same class as input and then copies the properties of that object to the newly created instance.

```java
public Fruits(Fruits fruit){
	this.weight = fruit.weight;
	this.calories = fruit.calories;
}
```

**Note:** If the instance variables of an object are object themselves then we may end up aliasing instead of copying the variable. This results in these variables sharing the same memory location across different objects, and any modifications made to the variables in one object will also be reflected in all other objects.

### Deep Copying vs Shallow Copying

Shallow copying refers to creating a new object and then copying the reference to the original object's memory address into the new object. This means that the new object points to the same memory location as the original object, and any changes made to the new object will also affect the original object.

Deep copying, on the other hand, creates a new object and then copies all of the original object's attributes and values to the new object. This means that the new object is completely independent of the original object, and any changes made to the new object will not affect the original object.

Let's see this with the help of an example

```java
class Person{

  //Instance variables
  String name;
  int age;
  Fruits favouriteFruit;

  public Person(String name, int age, Fruits favouriteFruit){
    this.name = name;
    this.age = age;
    this.favouriteFruit = favouriteFruit;
  }

  public Person(Person p){
    this.name = p.name;
    this.age = p.age;
    this.favouriteFruit = p.favouriteFruit; //shallow
  }

  public changeFruitWeight(int weight){
    this.name = "Ayush";
    this.age = 25;
    favouriteFruit.setWeight(weight);
  }

  public void printDetails(){
    System.out.println(name+" "+age);
    System.out.println("Details of favourite fruit:");
    System.out.println("Weight: "+favouriteFruit.getWeight()+", Calories: "+favouriteFruit.getCalories());
  }
}

public class MainClass{
  public static void main(String[] args){
    Fruits apple = new Fruits(150, 50); //An apple with 150gm weight and 50gm calories
    Person person1 = new Person("Shubham", 20, apple);
    //A person with name Shubham, age 20 and favourite fruit as the apple object.
    Person person2 = new Person(person1);
    //Another person with the same properties.
    person2.changeFruitWeight(250);
    //Sets the name of person2 as Ayush, age as 25 and changes the weight of favourite fruit to 250gm.
    person1.printDetails();
    person2.printDetails();
  }
}
```

```bas
Output:
Shubham 20
Details of favourite fruit:
Weight: 250, Calories: 50
Ayush 25
Details of favourite fruit:
Weight: 250, Calories: 50
```

The weight of `person1` also gets changed, even though we changed it only for `person2`. The reason for this change is that since `favouriteFruit` instance variable in the class `Person` is an object of type `Fruits`, when we copy it from `person1` to `person2 `using the `=` symbol, it shares the same memory location because it's a shallow copy.

Any changes made to the `favouriteFruit` of `person2` will also affect the `favouriteFruit` of `person1` and vice versa.

## Input / Output in JAVA

### Taking Input

We use input() method to read data in Python, similarly Java provides us various ways to take input from the user.

Simplest way to do this, would be to use the Console class in Java. There are two methods defined within System which help us read input using the console class. The methods are readLine() and readPassword().

**Note:** readPassword returns an array of characters for security reasons instead of a string

Here's an example to demonstrate the use of Console class, for the purpose of taking inputs

```java
Console cons = System.console();
String username = cons.readLine("Enter your username: ");
//whatever is read from readLine is stored in a string.
char[] password = cons.readPassword("Enter your password: ");
//whatever is read from readPassword is stored in an array of characters.
```

There are better ways to take inputs in Java, like the Scanner class which gives more control over which types of inputs do we want to take. For example taking a single integer or a complete line of text.

```java
Scanner in = new Scanner(System.in);
String message = in.nextLine(); //reads one complete line of text
int number = in.nextInt() //reads one integer
```

### Printing Output

Similar to input, there are multiple ways by which we can output something in Java. Two of the most simple ways are:

```java
System.out.print("Hello"); //prints the string to the console.
System.out.print(" World");
//Output:
//Hello World

System.out.println("Hello"); //println adds a new line after printing the string to the console
System.out.print("World");
//Output:
//Hello
//World
```
