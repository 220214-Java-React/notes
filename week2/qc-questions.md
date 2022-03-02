## Java Continued
* What is the root class from which every class extends?
  * The `Object` class
* Where are Strings stored?
  * In the String pool in the heap
* Explain stack vs heap?
  * Heap is where objects are stored in memory. Stack is where local variable references are kept - a new stack is created for each method invocation
* What are annotations?
  * A type of syntactic metadata added to the code, read by the compiler - use `@` syntax
* What is a POJO? What is a bean?
  * POJO - plain old Java object. Any Java object that you create.
  * Bean - a POJO that has private data members, public getters/setters, and overrides `.hashcode()`, `.equals()`, and `.toString()` methods
* Why are strings immutable in java?
  * Identical String literals are collected in the "String pool" in an effort to conserve memory. Reference variables will then point to the same String object instance. Changing the object's state in the String pool will make changes to all references to that String object. Instead, when a change to a String is made, the JVM makes a new String object, and the reference variable points to the new String in the String pool.
* What is the difference between `String`, `StringBuilder`, and `StringBuffer`?
  * Strings are immutable.  Both `StringBuilder` and `StringBuffer` are mutable.  Furthermore, `StringBuffer` is sychronized while `StringBuilder` is not.
* What are the access modifiers in Java? Explain them.
  * `public`  - can be accessed from any package.
  * `private` - only members of the same class can access.
  * `protected` - can be accessed by classes inside the package and subclasses anywhere.
  * `default` - no access by classes or subclasses outside the package
* What are the non-access modifiers in Java?
  * `static`, `final`, `abstract`, `default`, `synchronized`, `transient`, 
  * obscure keywords: `volatile`, `native`, `strictfp`
* What is the difference between `static` and `final` variables?
  * `static` variables are shared by all the instances of objects and it has only single copy. A `final` variable is a constant and it cannot be changed. However, if the variable holds a reference to an object, the state of the object may still be changed and manipulated.
* What are the default values for all data types in Java?
  * Objects - `null`
  * int, short, byte, long, float, double - 0
  * boolean - `false`
  * char - 'u0000' (null character)
* Is Java pass-by-value or pass-by-reference?
  * Java is strictly pass by value. Even when object references are passed as arguments, it is the value of the reference that is passed
* How to pass multiple values with a single parameter into a method?
  * Use varargs
* What methods are available in the Object class?
  * `.clone`, `.hashcode`, `.equals`, `.toString`
* How would you clone an object?
  * First, tag the class with the `Cloneable` marker interface. Next, invoke `clone()`. The clone method is declared in `java.lang.Object` and does a shallow copy.
## OOP
* What are the 4 pillars of OOP / Explain each?
  * Abstraction - Hiding implementation details
  * Polymorphism - Subclasses of a class can define their own unique behaviors and yet share some of the same functionality of the parent class. An object can also be referenced by its supertype "parent" class, for example `ParentClass obj = new SubClass()`;
  * Inheritance - A class that is derived from another class is called a subclass (also a derived class, extended class, or child class). The class from which the subclass is derived is called a superclass (also a base class or a parent class).
  * Encapsulation can be described as a protective barrier that prevents the code and data being randomly accessed by other code defined outside the class. Access to the data and code is tightly controlled by an interface.
* Is this allowed? Is this an example of method overloading or overriding?
  * Overriding. This is an example of covariant return types: a method is allowed to return objects that are child classes of the return type. Also, when overriding a method, the return type of the new method can be a child class of the original return type
```java
public abstract class Super {
  public abstract Collection getCollection();
}

public abstract class Sub extends Super {
  public abstract List getCollection();
}
```
* What is the difference between an abstract class and an interface?
  * An abstract class can have both concrete and abstract methods whereas an interface must have only abstract methods if any (unless the default keyword is used). Interface methods are implicitly public and abstract, interface variables are implicitly public, static, and final, but these do not apply in abstract classes. Neither can be instantiated
* What are the implicit modifiers for interface variables?
  * public static final
* What is the difference between method overloading and overriding?
  * Method overriding - In a subclass when one declares an identical method from the superclass, this method overrides the one in the superclass.
  * Method overloading - Within the same class when one declares more than method with the same name but different signature (parameters).
* Can you overload / override a main method? static method? a private method? a default method? a protected method?
  * Main method - overload, cannot override b/c is static method.
  * Static method - overload, cannot override b/c belongs to class (not inherited).
  * Private method - overload, cannot override b/c doesn't get inherited.
  * Default method - both.
  * Protected method - both (override if inherited). 
*  Explain the difference
```java
List<String> mylist = new ArrayList<>();
ArrayList<String> list2 = new ArrayList<>();
```
* Difference between extends and implements?
  * Extends is for classes, implements is for implementing interfaces
* What are enumerations (enums)?
  * A special Java type that defines a collection of constants
* What are the implicit modifiers for interface variables / methods?
  * methods - public abstract; variables - public static final
* First line of constructor?
  * The compiler will insert `super()` as the first line - it cannot be used anywhere else in constructor except for the first line
* Can you instantiate this class? Why or why not?
```java
public class Hello {}
```
## Exceptions
* What is the difference between `final`, `.finalize()`, and `finally`?
  * `final`: final keyword can be used for class, method and variables. A final class cannot be subclassed and it prevents other programmers from subclassing a secure class to invoke insecure methods. A final method can't be overridden. A final variable can't change from its initialized value.
  * `finalize()`: finalize method is used just before an object is destroyed and called just prior to garbage collection.
  * `finally`: finally, a key word used in exception handling, creates a block of code that will be executed after a `try/catch` block has completed and before the code following the `try/catch` block. The `finally` block will execute whether or not an exception is thrown. For example, if a method opens a file upon exit, then you will not want the code that closes the file to be bypassed by the exception-handling mechanism. This finally keyword is designed to address this contingency.
* `throw` vs `throws` vs `Throwable`?
  * `Throwable` - the root interface of exceptions, allow a class to be "thrown"
  * `throws` - keyword in method signature after params that declare which exception the method might throw
  * `throw` - the keyword that will actually "throw" an exception in code
* What is try-with-resources? What interface must the resource implement to use this feature?
  * Try-with-resources allows for automatically closing resources in a try/catch block using `try(resource) {...}` syntax. Must implement the `AutoCloseable` interface
* Do you need a catch block? Can have more than 1? Order of them?
  * Catch block is not necessary - try/finally will compile. You can have more than one catch block, but the order must be from most narrow exception to most broad/general.
* What is base class of all exceptions? What interface do they all implement?
  * The base class is `Exception`, which implements the `Throwable` interface
* List some checked and unchecked exceptions?
  * Checked - `IOException`, `ClassNotFoundException`, `InterruptedException`
  * Unchecked - `ArithmeticException`, `ClassCastException`, `IndexOutOfBoundsException`, `NullPointerException`
* Multi-catch block - can you catch more than one exception in a single catch block?
  * Yes, use the `|` operator
* Is this an example of a checked or unchecked exception?
```java
public class MyException extends RuntimeException {}
```

## JUnit
* What is JUnit?
  * A Java unit testing framework for testing code - use it for TDD
* What is TDD?
  * Test-driven development - write unit tests before application code, then write code to make tests pass. Repeat this process until functionality is complete.
* What are the annotations in JUnit? Order of execution?
  * BeforeClass, AfterClass, Before, After, Test, Ignore
* Give an example of a test case?
  * Adding two numbers, check that the method returns the sum


## PRACTICALS
From easiest to hardest:

* Read and predict the following code
* If I wanted to add another number to my list of favorite numbers, what should I do?

```java
int[] favoriteNumbers = {3, 7, 42};
favoriteNumbers[1] = 12;
System.out.println(favoriteNumbers[0]);
System.out.println(favoriteNumbers[1]);
System.out.println(favoriteNumbers[2]);
```

* Explain the code and predict the output
```java
String[] words = {"hello", "goodbye", "car", "motorcycle"};
int[] nums = new int[words.length];
int x = 0;
while (x < words.length) {
  nums[x] = words[x].length;
}
System.out.println(nums[2]);
```

* Predict the output
  * TESTS: String vs StringBuilder; String immutability
  * 1 prints "foo"; 2 prints "foobar"; 3 prints false; 4 prints true

```java
String str = "foo";
str.concat("bar");

StringBuilder sb = new StringBuilder("foo");
sb.append("bar");

System.out.println(str); // ?
System.out.println(sb);  // ?
```

* Which variable in the following code can be marked as final?

```java
public class Counter {
  private static String MESSAGE = "counting...";
  private int count = 0;

  public void increment() {
    while (count < 10) {
      count++;
      System.out.println(MESSAGE);
    }
  }

  public void decrement() {
    while (count > 0) {
      count--;
      System.out.println(MESSAGE);
    }
  }
}
```

* Which, if any, lines are valid/invalid?
  * TESTS: STATIC KEYWORD
  * Ans: line B is NOT allowed (compilation error). Instance variables cannot be accessed from `static` context

```java
public class Example {
  public static int x = 1;
  public int y = 1;

  public static void incrementStatic() {
    x++;
  }

  public void incrementInstance() {
    y++;
  }

  public static void printBothStatic() {
    System.out.println(x);  // A
    System.out.println(y);  // B
  }

  public void printBothInstance() {
    System.out.println(x);  // C
    System.out.println(y);  // D
  }
}
```

* Using the class above, predict the output

```java
Example e1 = new Example();
Example e2 = new Example();
e1.incrementInstance();
e2.incrementInstance();
e2.incrementInstance();
Example.incrementStatic();
Example.incrementStatic();
System.out.println(e1.y);
System.out.println(e2.y);
System.out.println(Example.x);
```

* What is the output of this code? Does it do what we expect? If not, how would you change it?
  * TESTS: STRING, STRINGBUILDER
  * Ans: prints out the starting string instead of building a new string. Refactor: reassign to "toBuild" variable or use StringBuilder (more efficient)

```java
public void buildString(String start, String add) {
  String toBuild = start;
  for(int i=0; i < 100; i++) {
    toBuild.concat(add);
  }
  System.out.println(toBuild);
}
```

* How many objects are created? What is the output?
  * TESTS: `==` vs `.equals()` method
  * Ans: 2 objects; a = true; b = true; c = false; d = true; e = true; f = true

```java
String s1 = "hello";
String s2 = "hello";
String s3 = new String("hello");

System.out.println(s1 == s2);       // a
System.out.println(s1.equals(s2));  // b
System.out.println(s1 == s3);       // c
System.out.println(s1.equals(s3));  // d
```

* Is this an example of method overloading or overriding? Also, refactor this class. BONUS: use varargs
  * TESTS: POLYMORPHISM, VARARGS

```java
public class FlexiblePrinter {
  public void printSingleString(String s) {
    System.out.println(s);
  }
  public void printTwoStrings(String s1, String s2) {
    System.out.println(s1);
    System.out.println(s2);
  }
  public void printThreeStrings(String s1, String s2, String s3) {
    System.out.println(s1);
    System.out.println(s2);
    System.out.println(s3);
  }
}
```

* Instantiate this class using the constructor
  * TESTS: CONSTRUCTOR

```java
public class Car {
  String make;
  Engine engine = new Engine();
  public void start() {
    engine.turnOn();
  }
  public Car(String make) {
    this.make = make; 
  }
```
* In the above code, can we use a no-args constructor? If not, add one.
* BONUS: modify the above code to use dependency injection
* Using the above code as reference, predict the output.

```java
Car ford = new Car("Focus");
Car toyota = new Car("Camry");
Car anotherFord = new Car("Focus");
System.out.println(ford == toyota);
System.out.println(ford.equals(toyota));
System.out.println(ford == anotherFord);
System.out.println(ford.equals(anotherFord));
```

* Change the Car class so that the last line in the above code print "true"?
  * Ans: override the `.equals` method

* Predict the output of this code
  * TESTS: MAIN METHOD

```java
public class Program {
   public static void main(String[] args) {
     System.out.println(args[1]);
   }
}
```
```bash
# command line:
javac Program.java
java Program foo bar baz
```

* Consider the following example. What gets printed on lines A-D? Is this method overloading or overriding?
  * TESTS: POLYMORPHISM
  * A prints "WOOF!"; B prints "WOOF!"; C prints "HELLO"; D is not allowed

```java
public class Animal {
  public void speak() {System.out.println("HELLO");}
}
public class Dog extends Animal {
  public void speak() {System.out.println("WOOF!");}
}
public class Driver {
  public static void main(String[] args) {
    Animal dog1 = new Dog();
    dog1.speak();  // A
    Dog dog2 = new Dog();
    dog2.speak();  // B
    Animal animal1 = new Animal();
    animal1.speak(); // C
    Dog animal2 = new Animal();
    animal2.speak();  // D
  }
}
```
