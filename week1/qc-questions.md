# QC Questions that may be asked on Tuesday

## Java Basics
* What is Java? / Why Java?
  * A high-level OOP language with rich API libraries, widely used around the world, supported by Oracle. Write once run anywhere (WORA), static types, compiled language
* What is JRE / JDK / JVM?
  * JVM - Java virtual machine. Runs compiled Java code
  * JRE - Java runtime environment. Contains the JVM.
  * JDK - Java developer kit. Has a compiler, debugger, etc. Contains JRE and JVM.
* What is an object / class?
  * Class is a blueprint for an object
* What is the root class from which every class extends?
  * The `Object` class
* What are the primitive data types in Java?
  * boolean, byte, short, int, long, float, double, char
* Where are Strings stored?
  * In the String pool in the heap
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
  * `static` variables are shared by all the instances of objects and it has only single copy. 
  * A `final` variable is a constant and it cannot be changed. However, if the variable holds a reference to an object, the state of the object may still be changed and manipulated.
* What are the default values for all data types in Java?
  * Objects - `null`
  * int, short, byte, long, float, double - 0
  * boolean - `false`
  * char - 'u0000' (null character)
* What is a wrapper class?
  * Wrapper class is a wrapper around a primitive data type. It represents primitive data types in their corresponding class instances e.g. a boolean data type can be represented as a `Boolean` class instance. All of the primitive wrapper classes in Java are immutable i.e. once assigned a value to a wrapper class instance cannot be changed further.
* What is autoboxing / unboxing?
  * Auto-boxing is the automatic conversion of primitives to their wrapper classes by the compiler. Useful for adding primitives to collections
* Is Java pass-by-value or pass-by-reference?
  * Java is strictly pass by value. Even when object references are passed as arguments, it is the value of the reference that is passed
* What data types are supported in switch statements?
  * `String`, `int`, `char`, `short`, `byte`, `enums`
* How to pass multiple values with a single parameter into a method?
  * Use varargs
* Can we access static/non-static variables from static/non-static methods (see example)?
```java
public class A {
  public static int x = 1;
  public int y = 2;

  public static void doStuff() {
    System.out.println(y);
  }

  public void doMoreStuff() {
    System.out.println(x);
  }
}
```
* What methods are available in the Object class?
  * `.clone`, `.hashcode`, `.equals`, `.toString`
* What is the difference between `==` and `.equals()`?
  * `==` -  tests to see if two reference variables refer to the exact same instance of an object.
  * `.equals()` - tests to see if the two objects being compared to each other are equivalent, but they need not be the exact same instance of the same object.
* What are 3 usages of `super` keyword?
  * to refer to immediate parent class instance variable.
  * `super()` is used to invoke immediate parent class constructor (also can pass params)
  * to invoke immediate parent class method.
  
## OOP
* What are the 4 pillars of OOP / Explain each?
  * Abstraction - Hiding implementation details
  * Polymorphism - Subclasses of a class can define their own unique behaviors and yet share some of the same functionality of the parent class. An object can also be referenced by its supertype "parent" class, for example `ParentClass obj = new SubClass()`;
  * Inheritance - A class that is derived from another class is called a subclass (also a derived class, extended class, or child class). The class from which the subclass is derived is called a superclass (also a base class or a parent class).
  * Encapsulation can be described as a protective barrier that prevents the code and data being randomly accessed by other code defined outside the class. Access to the data and code is tightly controlled by an interface.

## Git

* What is version control? What makes git different from other version control software?
  * Git is distributed version control system
  * Allows tracking changes, viewing past changes, reverting to old versions, etc
  * Git does not rely on "single point of truth", you can add many different codebase locations and keep them in sync
  * Git tracks units of work in "commits" that are linked to each other
  * Older centralized version control include subversion (`svn`)
* List the git commands you know and what they do
  * pull, push, add, commit, checkout, branch, merge
* How would you prevent a file from being tracked by git?
  * Add the filepath to a file called `.gitignore`
* What is a branch? What are some common branching strategies?
  * A branch is a separate path of changes made to the codebase
  * Typically you'll have a main or master branch from which production deployments are made, a dev branch for changes in progress, and feature branches that branch from dev for features being worked on
* How to create a new branch?
  * `git checkout -b mynewbranch` OR `git branch mynewbranch && git checkout mynewbranch`
* What is a merge conflict? How do you prevent these and resolve if it happens?
  * If two changes attempt to merge and have different code in them, git will not allow this to happen
  * To resolve, go to the file with the conflict. Remove the special markings that designate the merge conflict and select the code to keep
  * Finally commit your change to finish the merge
* What is a GitHub pull request?
  * A request to merge changes made in the code from one branch into another
  * Usually this is where code reviews take place and feedback is given on the code
  * Any changes can be made here before code is merged
* What is the git workflow for editing code and saving changes?
  1. Pull any updates from central repo `git pull`
  2. Make changes to codebase
  3. Stage the changes `git add <files>`
  4. Make a commit `git commit -m my commit message`
  5. Push to the central repo `git push`
* What is a commit?
  * A unit of work, records the current state of the codebase in git
* How would you go back in your commit history if you make a mistake?
  * `git checkout <commit hash>`
