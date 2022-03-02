## Collections / Generics

42. What are collections in Java?

- A general data structure that contains Objects. Also the name of the API

43. What are the interfaces in the Collections API?

- Iterable, Collection, List, Queue, Set, Map, SortedSet, SortedMap

44. What is the difference between a `Set` and a `List`?

- `Set` does not allow duplicates (its members are unique)

45. What is the difference between a `Array` and an `ArrayList`?

- An array is static and its size cannot be changed, but an ArrayList can grow/shrink

46. What is the difference between `ArrayList` and `Vector`?

- `Vector` is synchronized whereas `ArrayList` is not.

47. What is the difference between `TreeSet` and `HashSet`?

- The two general purpose `Set` implementations are `HashSet` and `TreeSet`. `HashSet` is much faster (constant time versus log time for most operations) but offers no ordering guarantees.

48. What is the difference between HashTable and HashMap?

- a. `Hashtable` is synchronized whereas `Hashmap` is not.

- b. `Hashmap` permits `null` values and the `null` key.

49. Are Maps in the Collections API?

- Yes, but they do not implement `Collection` or `Iterable` interfaces

50. What are generics? What is the diamond operator (`<>`)?

- A way of specifying a type within a data structure - they enforce type safety. `<>` operator lets you infer generic types from the LHS of assignment operation

## Threads

51. What is multi-threading?

- Handling multiple threads / paths of execution in your program.

52. In what ways can you create a thread?

- By extending the Thread Class or by implementing the `Runnable` Interface. You must call Thread's `.start()` method to start it as a new thread of execution.

53. Lifecycle of a thread

- When created, in NEW state.
- When `.start()` is called, it goes to RUNNABLE state.
- When `.run()` is called, goes to RUNNING state.
- If `.sleep()` or `.wait()` is called, will go to WAITING.
- If dependent on another thread to release a lock, it will go to BLOCKED state.
- When finished executing, will be in DEAD state and cannot be restarted.

54. What is deadlock?

- When two or more threads are waiting on locks held by the others, such that no thread can execute

55. What is synchronized keyword?

- Only allowing one thread access to the method or variable at a time - enforces thread-safety

## IO / Serialization

56. How do you serialize / deserialize an object in Java?

- a. Step 1: An object is marked serializable by implementing the `java.io.Serializable` interface, which signifies to the underlying API that the object can be flattened into bytes and subsequently inflated in the future.

- b. Step 2: The next step is to actually persist the object. That is done with the `java.io.ObjectOutputStream` class. That class is a filter stream--it is wrapped around a lower-level byte stream (called a node stream) to handle the serialization protocol for us. Node streams can be used to write to file systems or even across sockets. That means we could easily transfer a flattened object across a network wire and have it be rebuilt on the other side!

- c. To restore the object back, you use `ObjectInputStream.readObject()` method call. The method call reads in the raw bytes that we previously persisted and creates a live object that is an exact replica of the original. Because `readObject()` can read any serializable object, a cast to the correct type is required. With that in mind, the class file must be accessible from the system in which the restoration occurs. In other words, the object's class file and methods are not saved; only the object's state is saved.

57. What is a Marker interface?

- A marker interface is an interface which has no methods at all. Example: `Serializable`, `Remote`, `Cloneable`. Generally, they are used to give additional information about the behavior of a class.

58. What are transient variables?

- Transient variables are those variables which cannot be serialized.

59. Difference between FileReader and BufferedReader?

- `FileReader` is just a `Reader` which reads a file, so it reads characters and uses the platform-default encoding.

- `BufferedReader` reads text from a character-input stream, buffering characters so as to provide for the efficient reading of characters, arrays, and lines (e.g. can read one line at a time).

- So you can wrap a `BufferedReader` around a `FileReader`

## Design patterns

67. What are Singleton / Factory design patterns?

- Singleton - allows for creation of only 1 object. Method for retrieving object returns reference to the same object in memory. Implement via private constructor

- Factory - abstracts away instantiation logic, usually used in conjunction with singleton pattern

## Log4j

79. What is an advantage to using a logging library?

- Allows you to set logging thresholds

80. What is log4j?

- Logging library for Java

81. What are the logging levels of log4j?

- TRACE, DEBUG, INFO, WARN, ERROR, FATAL

## Advanced

86. What are functional interfaces?

- Functional interfaces only have one method, and can be used in conjuntion with lambdas

87. What are lambdas?

- Like anonymous functions, they allow implementation of functional interfaces directly without creating a class

88. What is try-with-resources? What interface must the resource implement to use this feature?

- Try-with-resources allows for automatically closing resources in a try/catch block using `try(resource) {...}` syntax. Must implement the `AutoCloseable` interface

89. How to make numbers in your code more readable?

- Use the `_` for numeric literals - must be placed between numbers

90. Which collections cannot hold null values?

- `HashTable`, `TreeSet`, `ArrayDeque`, `PriorityQueue`

91. If 2 interfaces have default methods and you implement both, what happens?

- The code will NOT compile unless you override the method. However, the code WILL compile if one interface is implemented further up in the class hierarchy than the other - in this case, the closest method implementation in the hierarchy will be called

92. If 2 interfaces have same variable names and you implement both, what happens?

- The code will compile unless you make a reference to the variable (this is an ambiguous reference). You must explicitly define the variable by using the interface name: `int a = INTERFACENAME.a;`

93. Why does `HashTable` not take `null` key?

- The hash table hashes the keys given as input, and the `null` value cannot be hashed

94. What new syntax for creating variables was introduced with Java 10?

- The `var` keyword was introduced - with type inference

95. Is there an interactive REPL tool for Java like there is for languages like Python?

- Yes, the `jshell` tool introduced in Java 9

96. What are collection factory methods?

- They allow you to directly populate collections, e.g. `Set.of(1,2,3)`

## Practicals

- What is wrong with this line of code? `Set<int> myints = new HashSet<>()`

  - Ans: Primitives cannot be used with collections; instead, use the wrapper class

- Can you refactor this using a better method or more efficient data structure?
  - TESTS: SET
  - Ans: use a `Set`

```java
public List<String> removeDuplicates(String[] stringArr) {
  List<String> withoutDuplicates = new ArrayList<>();
  for(int i=0; i < stringArr.length; i++) {
    if (!withoutDuplicates.contains(stringArr[i])) {
      withoutDuplicates.add(stringArr[i]);
    }
  }
  return withoutDuplicates;
}
```

- What prints here?
  - TESTS: SET

```java
Set<Integer> nums = new HashSet<>();
nums.add(1); // what is this implicit operation called?
nums.add(2);
nums.add(1);
nums.add(3);
nums.forEach((i) -> {System.out.println(i)}); // predict the output
```

- Can you refactor this using a better method or more efficient data structure?
  - TESTS: MAP

```java
// this method should return the number of times each word is repeated
public List<Integer> countWords(String sentence) {
  String[] words = sentence.split(" ");
  List<String> uniqueWords = new ArrayList<>();
  List<Integer> wordCounts = new ArrayList<>();
  for (String word : words) {
    int wordIndex = uniqueWords.indexOf(word);
    if (wordIndex == -1) {
      uniqueWords.add(word);
      wordCounts.add(1);
    } else {
      wordCounts.set(wordIndex, wordCounts.get(wordIndex)+1); // increment
    }
  }
  return wordCounts;
}
```

- BONUS: could you make this method faster for extremely large inputs? if so, how? (HINT: multithreading)

- Explain the difference between line 1 and 2.
- TESTS: POLYMORPHISM
- Ans: first line uses polymorphic declaration; we can swap out implementations of `List` at any time, so the code is more decoupled and uses abstraction properly

```java
List<String> mylist = new ArrayList<>();
ArrayList<String> list2 = new ArrayList<>();
mylist.add("hello");
mylist.add(new Person()); // what happens?
```

- Predict the output of the code. Also, explain what `@Override` is and what it does?
  - TESTS: COMPARABLE

```java
public class Person implements Comparable<Person> {
  String name;
  int age;

  public Person(String name, int age) {
    this.name = name;
    this.age = age;
  }

  @Override
  public int compareTo(Person p) {
    if (age == p.age) {
      return 0;
    } else if (age > p.age) {
      return 1;
    } else {
      return -1;
    }
  }

  public static void main(String[] args) {
    Person alice = new Person("Alice",30);
    Person bob = new Person("Bob",25);
    Person charlie = new Person("Charlie",35);
    List<Person> people = new ArrayList<>();
    people.add(alice);
    people.add(bob);
    people.add(charlie);
    Collections.sort(people);
    for (Person p : people) {
      System.out.println(p.name);
    }
  }
}
```

- Is the below allowed? Is this an example of method overloading or overriding?
  - TESTS: POLYMORPHISM
  - Overriding. This is an example of covariant return types: a method is allowed to return objects that are child classes of the return type. Also, when overriding a method, the return type of the new method can be a child class of the original return type

```java
public abstract class Super {
  public abstract Collection getCollection();
}
public abstract class Sub extends Super {
  public abstract List getCollection();
}
```

- Predict the output here
  - TESTS: MAP

```java
Map<String, Integer> namesAndAges = new TreeMap<>();
namesAndAges.put("Alice", 30);
namesAndAges.put("Bob", 25);
namesAndAges.put("Charlie", 35);
for (Integer val : namesAndAges.values()) {
  System.out.println(val);
}
for (String key : namesAndAges.keySet()) {
  System.out.println(key);
}
```

- Which of these is a marker interface and which is a functional interface?

```java
public interface Movable {
  public void move();
}
public interface Cloneable {}
public interface Writable {
  public void writeString(String s);
  public void writeInt(int i);
}
```

- What happens here? Can you fix and rewrite this using a lambda?
  - TESTS: THREADS, LAMBDA
  - Ans: a thread is created but is not started. Calling the `run` method only executes the method in the same thread.

```java
class MyRunnable implements Runnable {
  public void run() {
    System.out.println("running!");
  }
}
Thread t = new Thread(new MyRunnable());
t.run();
```

- Explain the following code and what it will print out? How many threads are created?
- Is there anything you could do to ensure that e always prints last?

```java
Runnable r1 = () -> {
  System.out.println("a");
  System.out.println("b");
}
Runnable r2 = () -> {
  System.out.println("c");
  System.out.println("d");
}
Thread t1 = new Thread(r1);
Thread t2 = new Thread(r2);
t1.start();
t2.start();
System.out.println("e");
```

- Is this an example of a checked or unchecked exception? How would you change it to a checked exception?
  - TESTS: EXCEPTIONS

```java
public class MyException extends RuntimeException {}
```

- What happens here?
  - Ans: `ArithmeticException` gets thrown

```java
int x = 4;
int y = 0;
System.out.println(x / y);
```

- What exception could be thrown here? Are we required to handle it? BONUS: use a try-with-resources block
  - Ans: `IOException` could be thrown; must either handle in try/catch or use `throws` declaration on method

```java
public void readFile() {
  BufferedReader in = new BufferedReader(new FileReader("foo.txt"));
  System.out.println(in.read());
}
```

- Write a test to validate the functionality of this code. Be sure to include a positive AND negative test.
- Bonus: refactor using ternary operator.

```java
public class LoanApplication {
  int creditScore;
  double salary;
  double loanAmount;
}
/* Requirements for loan approval:
  - Credit score above 620
  - Loan amount less than 50% of salary
*/
public class LoanProcessor {
  public boolean processLoan(LoanApplication loanApp) {
    if (loanApp.creditScore > 620 && loanApp.loanAmount < (loanApp.salary / 2)) {
      return true;
    } else {
      return false;
    }
  }
}
```
