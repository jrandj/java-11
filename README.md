# Java 11

## Java SE 11 Programmer I

- [Creating a Simple Java Program](#Creating-a-Simple-Java-Program)
- [Working With Java Primitive Data Types and String APIs](#Working-With-Java-Primitive-Data-Types-and-String-APIs)
- [Using Operators and Decision Constructs](#Using-Operators-and-Decision-Constructs)
- [Working with Java Arrays](#Working-with-Java-Arrays)
- [Describing and Using Objects and Classes](#Describing-and-Using-Objects-and-Classes)
- [Creating and Using Methods](#Creating-and-Using-Methods) 
- [Applying Encapsulation](#Applying-Encapsulation) 
- [Reusing Implementations Through Inheritance](#Reusing-Implementations-Through-Inheritance) 
- [Programming Abstractly Through Interfaces](#Programming-Abstractly-Through-Interfaces) 
- [Handling Exception](#Handling-Exception) 
- [Understanding Modules](#Creating-and-Using-Methods)
- [Understanding Java Technology and environment](#Understanding-Java-Technology-and-environment)

### Creating a Simple Java Program

1. A Java class is compiled using the **javac** program. Compilation results in one or more class files depending on the contents of the Java source file. An example is shown below:

    ```java
    javac TestClass.java
    ```

1. A Java class is executed using the **java** program. An example is shown below:

    ```java
    java TestClass a b c
    ```

1. The **Java Virtual Machine (JVM)** is an executable. When the JVM runs, it loads the given class and looks for the main method of that class to run. The executable for the JVM is named java.

1. Every Java class belongs a package. There can be at most one package statement in the source file, and it must be the first statement in the file. If there is no package statement, then the classes defined in that file belong to an unnamed package which is known as the default package. Classes from other packages can be imported so that they can be referrred to without using hte Fully Qualified Class Name (FQCN).

1. The stack is used for storing local variables, functional calls, and references to objects. The heap is used for storing objects.

### Working With Java Primitive Data Types and String APIs

1. Java is a statically typed language. This means that the data type of a variable is defined at compile time and cannot change during run time.

1. Java has primitive and reference variables. The Java compiler and JVM inherently know what primitive types mean, while reference data types are built by combining primitive data types and other reference data types.

1. Primitive data types below:

    | Date Type | Size    | Description                                                             | Sample                  |
    |-----------|---------|-------------------------------------------------------------------------|-------------------------|
    | byte      | 1 byte  | -128 to 127                                                             | -1, 0, 1                |
    | short     | 2 bytes | -32,768 to 32,767                                                       | -1, 0, 1                |
    | int       | 4 bytes | -2,147,483,648 to 2,147,483,647                                         | -1, 0, 1                |
    | long      | 8 bytes | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807                 | -1, 0, 1                |
    | float     | 4 bytes | Stores fractional numbers. Sufficient for storing 6 to 7 decimal digits | 1.1f, 2.0f              |
    | double    | 8 bytes | Stores fractional numbers. Sufficient for storing 15 decimal digits     | 1.1d, 2.0d              |
    | boolean   | 1 bit   | Stores true or false values                                             | true, false             |
    | char      | 2 bytes | Stores a single character                                               | '\u0000', 'a'           |

    Wrapper classes exist for Byte, Short, Integer, Long, Float and Double.

1. Reference types include:
    * Classes
    * Interfaces
    * Enums
    
1. A variable contains a raw number, and assigning one variable to another simply copies that number from one variable to another. Java uses **pass by value** semantics.

1. Java initialises all static and instance variables of a class automatically if you don't initialise them explicitly. You must initalise local variables explicitly before they are used.

1. Assigning a smaller type to a larger type is known as **implicit widening conversion** as no cast is required. To assign a larger type to a smaller type, for a compile time constant (i.e. final) the compiler will automatically narrow the value. If the source variable is not a constant then a cast is required, this is known as **explicit narrowing**. Determining the value that will actually be assigned when doing an explicit can be complicated.

1. A string is an object of class java.lang.String. String is a final class and implements java.lang.CharSequence. String is immutable so the value cannot be changed after instatiation.

1. A string can be instantiated using:
    ```java
    String myString = new String();
    String myString = new String("example");
    String myString = "example";
    String myString = new String(StringBuilder sb);
    String myString = new String(byte[] bytes);
    String myString = new String(char[] value);
    String myString = s1 + "add";
    ``` 

1. String concatenation can occur with the += operator if one of the operands is a String.

1. Strings created without using the new keyword are kept in the **string pool**. If a String is created without the new keyword and the same string already exists in the string pool, then a reference to the existing String will be returned.

1. Useful String methods include:
    ```java
    int length();
    char charAt(int index);
    int indexOf(int ch);
    String substring(int beginIndex, int endIndex);
    String substring(int beginIndex);
    String concat(String str);
    String toLowerCase();
    String toUpperCase();
    String replace(char oldChar, char newChar);
    String strip();
    String stripLeading();
    String stripTrailing();
    String trim();
    ```

1. Note that in the substring methods the ending index is exclusive, and the starting index is inclusive.

1. Useful methods for inspecting a String include:
    ```java
    boolean isBlank();
    boolean isEmpty();
    boolean startsWith(String prefix);
    boolean endsWith(String suffix);
    boolean contains(CharSequence s);
    boolean equals(Object anObject);
    boolean equalsIgnoreCase(String anotherString);
    ```

1. java.lang.StringBuilder is the mutable twin of java.lang.String. StringBuilder is also a final class and implements java.lang.CharSequence. StringBuilder is better suited for creating temporary strings that have no use once a method ends.

1. Stringbuilder provides several constructors:
    ```java
    StringBuilder();
    StringBuilder(CharSequence seq);
    StringBuilder(int capacity);
    StringBuilder(String str);
    ```

1. Note that the default size for the no argument constructor is 16 characters.

1. Useful StringBuilder methods include:
    ```java
    insert(int position, <X> value);
    append(<X> value);
    reverse();
    delete(int start, int end);
    deleteCharAt(int index);
    replace(int start, int end, String replacement);
    int capacity();
    char charAt(int index);
    int length();
    int indexOf(String str);
    int indexOf(String str, int startIndex);
    void setLength(int len);
    String substring(int start);
    String substring(int start, int end);
    String toString();
    ```
1. The value to append is typically determined by String.valueOf().


### Using Operators and Decision Constructs

1. Arithmetic operators are used to perform standard mathematical operations on all primitive variables (and wrapper objects for numeric types) except boolean.

1. Operators and their precedence shown below:

    | Operator Type | Category             | Precadence                              |
    |---------------|----------------------|-----------------------------------------|
    | Unary         | postfix              | expr++ expr--                           |
    | Unary         | prefix               | ++expr --expr +expr -expr ~ !           |
    | Arithmetic    | multiplicative       | * / %                                   |
    | Arithmetic    | additive             | + -                                     |
    | Shift         | shift                | << >> >>>                               |
    | Relational    | comparison           | < > <= >= instanceof                    |
    | Relational    | equality             | == !=                                   |
    | Bitwise       | bitwise AND          | &                                       |
    | Bitwise       | bitwise exclusive OR | ^                                       |
    | Bitwise       | bitwise inclusive OR | \|                                      |
    | Logical       | logical AND          | &&                                      |
    | Logical       | logical OR           | \|\|                                    |
    | Ternary       | ternary              | ? :                                     |
    | Assignment    | assignment           | = += -= *= /= %= &= ^= \|= <<= >>= >>>= |

1. Java applies the rules of **numeric promotion** while working with operators that deal with numeric values. **Unary numeric promotion** occurs if an operand is smaller than int, and causes the operand to be automatically promoted to int. **Binary numeric promotion** occurs if one of the promoted operands is larger than int, and causes both operands to be promoted to the larger operand.

1. In the case of a Dangling Else statement, the Else is associated to the nearest if statement.

1. In a switch statement the expression must be:
    * Integral types (byte, char, short, int) and their wrapper classes. Note that this excludes long.
    * enum type.
    * A String.

1. In a switch statement case labels are optional, but if provided they must be compile time constants.

1. In a switch statement the default block is optional, but if provided there can only be 1.

### Working with Java Arrays

1. Examples for array instantiation:
    ```java
    int[] ia = new int[10];
    int[] ia = {0, 1, 2, 3, 4, 5};
    int[][] iaa = new int[2][3];
    int[][] iaa = new int[3][];
    int[][] iaa = new int[][]{new int[]{1,2}};
    int[][] iaa = {{1,2}};
    ``` 

1. Members of an array object include:
    * length
    * clone

1. Arrays have two interesting runtime properties:
    * They are reified meaning that type checking is done at runtime by the JVM and not the compiler.
    * They are covariant meaning that a subclass object can be stored in  an array that is declared to be the type of its superclass (i.e. you can store an integer in a number array).

1. The compare method compares 2 int arrays and returns 0 if they are equal, a value less than 0 if the first array is lexicographically less than the second array, and a value greater than 0 if the first array is lexicographically greather than the second array.

1. The mismatch method takes two int arrays and returns the index of the first mismatch, otherwise it returns -1 if no mismatch is found.

### Describing and Using Objects and Classes

1. When an object is instantiated the JVM allocates the necessary heap space to contain the various fields defined in the class. An example of instantiation is shown below:

    ```java
    new java.lang.Object();
    ``` 

1. In Java if you don't specify any reference variable explicitly within any instance method, the JVM assumes that you mean to access the same object for which the method has been invoked. You can make this explicit with the **this** keyword.

1. The structure of a Java source file is:
    * At most one package statement.
    * Zero or more import statements.
    * One or more reference type (i.e. class, interface, or enum) definitions.

1. Members of a class definition incldue field declarations, methods, constructors, and initialisers. Members can be static or non-static.

1. The code for a top level public reference type must be written inside a Java file with the same name. 

1. Java has three **visibility scopes** for variables - class, method, and block. Java has five **lifespan scopes** for variables - class, instance, method, for loop, and block.

1. From Java 10 you can use a **var declaration** to infer types in a local method. An example is shown below:

    ```java
    var str = "Java 11";
    ```

1. If there are no more references to an Object, the JVM concludes that the object is not required anymore and is marked as **garbage**. The object is then removed using **garbage collection**.

### Creating and Using Methods

1. The basic structure of a method is shown below:

    ```java
    returnType methodName(parameters){
        methodBody
    ```

1. The method must return a value of the type specified, with the following exceptions:
    * If the type is numeric then the return value can be one of any other numeric type as long as the type of the return value is smaller than the declared type.
    * Wrapper classes and primitives are interchangable.
    * A subtype of the declared type can be returned (referred to as **covariant return**).

1. The method signature includes the method name and its ordered list of parameter types. Where multiple methods exist with the same name but different parameter types, it is said that the class has **overloaded** the method name.

1. If the type but not exact number of parameters is known, the varargs syntax can be used. This is represented by 3 dots after a data type. Restrictions on the usage of varargs are:
    * A method cannot have more than 1 varargs parameter.
    * The varargs parameter must be the last parameter in the parameter list.

1. The following rules used by the compiler to disambiguate method calls to overloaded methods:
    * A compilation error will occur if the compiler is not able to successfully disambiguate a particular method call.
    * If the compiler finds a method whose parameter list is an exact match to the argument list of the method call, that method is selected.
    * If more than one method is capable of accepting a method call and none of them are an exact match, the one that is most specific is chosen by the compiler.
    * Higher priority is given to primitive versions if the argument can be widened to the method parameter type, this occurs before autoboxing is considered.
    * Autoboxing is considered before varargs.

1. When a new instance of a class is created, the JVM does four things:
    * Checks if the class has been initialised, if not, loads and initialises the class.
    * Allocates the memory to hold the instance variables of the class in the heap space.
    * Initialises the instance variables to their default values.
    * Gives the instance an opportunity to set the values of the instance variables as per the instance initialisers and constructors.

1. An instance initialiser is shown below:

    ```java
    class TestClass{
        {
            System.out.println("In instance initialiser");
        }
    }

    ```

1. An instance variable is not allowed to use the value of a variable if that variable is declared below the initialiser. It can assign a value to such a variable. An instance initialiser is not expected to throw any exceptions. Instance initialisers should generally be avoided, and a well designed class should not need to use them.

1. A constructor is a method that always has the same name as the class, and does not have a return type.

1. A no argument constructor is defined by default only if no constructors are provided explicitly.

1. Constructors can be overloaded through **constructor overloading**. When a constructor calls another constructor of the same class, this is done with the **this** keyword and is called **constructor chaining**. The call to another constructor must be the first line of code in a constructor.

1. Java forces the programmer to assign a value to a final variable explicitly. A static variable can be used by other classes only after the class is loaded made ready to use. You can assign a value to a final static variable at the time of declaration or in any one of the **static initialisers**.

1. Access to static members is decided by the compiler at compile time by checking the declared type of the variable. This is referred to as **static binding**. Static binding uses type information to bind a method to a method call, as opposed to **dynamic binding** which takes into account the actual object.

1. The first step in creating an instance of a class is to initialise the class itself. Whenever the JVM encounters the usage of a class for the first time, it allocates and initialises space for the static fields of that class. The rules for static blocks:
    * A class can have any number of static blocks. They are executed in the order that they appear in the class.
    * A static block can access all static variables and static methods of the class. However, if the declaration of a static variable appears after the static block, then only the value can be set.
    * If the class has a superclass, and the superclass hasn't been initialised already, the JVM will initialise the superclass first.
    * There is no way to access or refer to a static block. It can only be invoked by the JVM, and only once.


### Applying Encapsulation

1. Encapsulation, Inheritance and Polymorphism are the three pillars of Object-Orientated Programming.

1. Encapsulation is about restricting direct access to an objects data fields. This is achieved through the use of access modifiers. Access modifiers and their impact on accessibility are shown below:

    | Modifier    | Class | Package | Subclass | World |
    |-------------|-------|---------|----------|-------|
    | public      | Y     | Y       | Y        | Y     |
    | protected   | Y     | Y       | Y        | N     |
    | no modifier | Y     | Y       | N        | N     |
    | private     | Y     | N       | N        | N     |

1. A top level class, interface or enum can only have a public or default access modifier.

1. Members of an interface are always public, even if not declared that way. The compiler will generate an error if you define them as private or protected. From Java 9 an interface can have private methods.

1. Enum constants are always public, even if not declared that way. The compiler will generate an error if you define them as private or protected. Enum constructors are always private.

1. Encapsulation encourages loose coupling between classes. If the functionality of a class is exposed through methods, there are two advantages:
    * The implementation can be modified without users being aware (i.e. the implementation details of the functionality are hidden from the users).
    * The value of a variable can be ensured to be consistant with the business logic of the class. For example you could restrict setting the age of a Person class instance from being a negative number.

### Reusing Implementations Through Inheritance

1. A class defines a type, and contains a state (the instance fields) and the implementation (the methods). Thus, inheritance could be of state, implementation or type.

1. Java restricts a class from extending more than one class, so it is said that Java does not support multiple inheritance of state. A class can inherit implementation by extending a class and/or by implementating interfaces. As a class can implement multiple interfaces, Java supports multiple implementation inheritance. Java also supports multiple inheritance of type as an object can have multiple types: the type of its own class and the types of all the interfaces that the class implements. 

1. To inherit features from another class, that class is extended using the extends keyword. Constructors, static and instance initialisers of a class are not considered members of a class so are not inherited by a subclass. Only class members that are visible to another class as per the rules of access modifiers are inherited in a subclass.

1. Note that when the JVM initialises a class, memory is allocated for all instance variables irrespective of whether they will be accessible.

1. A subclass cannot be initialised before its parent. A call to super() is automatically inserted by the compiler in the first line of the constructor if no other call is provided.

1. The order of initialisation for loading a class is summarised below:
    * If there is a super class, initialise static fields and execute static initialisers of the super class in the order of their appearance.
    * Initialise static fields and execute static initialisers of the class in the order of their appearance.
    * If there is a super class, initialise the instance fields and execute instance initialisers of the super class in the order of their appearance.
    * Execute the super class's constructor.
    * Initialise the instance fields and execute instance initialisers of the class in the order of their appearance.
    * Execute class constructor.

1. An abstract class is used to capture common features of multiple related object types while knowing that no object that exhibits only the feature captured in the abstract class can actually exist.

1. An abstract method allows you to capture declaration without providing implementation.

1. A summary of the application of access modifiers, final, abstract and static keywords is shown below:
    * An abstract class doesn't have to have an abstract method but if a class has an abstract method, it must be declared abstract. In other words, a concrete class cannot have an abstract method.
    * An abstract class cannot be instantiated irrespective of whether it has an abstract method or not.
    * A final class or a final method cannot be abstract.
    * A final class cannot contain an abstract method but an abstract class may contain a final method.
    * A private method is always final.
    * A private method can never be abstract.
    * A static method can be final but can never be abstract.

1. The conventional sequence of modifiers in a method declaration are shown below:

    ```java
    <access modifier> <static> <final or abstract> <return type> methodName(<parameter list>)

    ```

1. **Polymorphism** refers to the ability of an object to exhibit behaviour associated with different types. The objective of polymorphism is to enable classes to become standardised components that can be easily exchanged without any impact on other components.

1. Polymorphism works because of **dynamic binding** of method calls. When you invoke an instance method using a reference variable, it is not the compiler but the JVM that determines which code to execute based on the class of the actual object referenced by the variable. In Java, calls to non-private and non-final instance methods are dynamically bound. Everything else is **statically bound** at compile time by the compiler.

1. Static methods, static variables, and instance variables are accessed as per the declared type of the variable through which they are accessed and not according to the actual type of the object to which the variable refers. Contrast this with methods, where the actual type of the object determines which instance method is used.

1. A class is allowed to completely replace the behaviour of an instance method that it inherited by providing its own implementation of that method. This is known as **overriding**. The rules for overriding a method are shown below:
    * An overriding method must not be less accessible than the overriden method.
    * The return type of the overriding method must be a covariant return of the overridden method.
    * The types and order of the parameter list must be exactly the same.
    * An overriding method cannot put a wider exception in its throws clause than the ones present in the throws clause of the overriden method.

1. A class can **hide** static methods and variables and instance variables. Basically, static methods are hidden, non-static methods are overriden.

1. The purpose of casting is to provide the compiler with the type information of the actual object to which a variable will be pointing at run time. When you cast a reference to another type, you are basically saying that the program does something that is not evident from the code itself. Ideally, you should never need to use casting.

1. The instanceof operator can be used to check if an object is an instance of a particular reference type. An example is shown below:

    ```java
    if(f instanceof Mango){
    }
    ```

### Programming Abstractly Through Interfaces

1. An **interface** is used to describe behaviour as captured by a group of objects. An example is shown below:

    ```java
    interface Movable{
        void move(int x);
    }
    ```

1. From an OOP perspective an interface should not contain any implementation. It should only contain method declarations. However, Java allows interfaces to contain static fields as well as default, static and private methods.

1. Key rules for interfaces are shown below:
    * Members of an interface are always public, even if not declared that way. The compiler will generate an error if you define them as private or protected. From Java 9 an interface can have private methods.
    * An interface is always abstract.
    * All variables are implicitly public, static and final.

1. Methods that interfaces can contain are shown below:
    * Abstract methods. Contain only declarations. An example is shown below:

        ```java
        interface Movable{
            void move(int x); // implicitly abstract
            abstract void move2(int x); // explicitly abstract
        }
        ```

    * Default methods. Opposite of abstract, cannot have a method that is both default and abstract. An example is shown below:

        ```java
        interface Movable{
            default move(int x){
                System.out.println("Moving by "+x+" points");  
            }
        }
        ```

    * Static methods. Can be public or private but not protected or default. If no access modifier is specified, they are implicitly public. An example is shown below:
 
        ```java
        interface Movable{
            static void sayHello(){
                System.out.println("Hello!");  
            }
        }
        ```

    * Private methods. Helpful when methods get too big and need to be refactored into smaller internal methods. An example is shown below:
    
        ```java
        interface Movable{
            private void moveInternal(){
                System.out.println("in moveInternal");  
            }
            default void move(int n){
                while(n-->0) moveInternal();
            }
        }
        ```

1. An empty interface is known as a **marker interface**. The most common marker interface used in Java is java.io.Serializable. It signifies to the JVM that objects of classes implementing this interface can be serialised and deserialised.

1. A class can implement any number of interfaces. Once a class declares that it implements an interface, it must have an implementation for all of the abstract methods declared in that interface. Implementation could be inherited from an ancestor class. If the class does not have implementation for even one of the methods, the class must be declared abstract. An example is shown below:

    ```java
    interface Movable{
        void Move();
    }

    interface Readable{
        void read();
    }

    class Price implements Movable, Readable{
        public void move(){
            System.out.println("Moving...");
        }
        public void read(){
            System.out.println("Reading...");
        }
    }
    ```

1. Unlike the static methods of a class, the static methods of an interface cannot be inherited. Multiple fields with the same name can be inherited as long as they are not used ambiguously.

1. An interface can extend any number of interfaces. The extending interface inherits all members except static methods of each of the extended interfaces.

1. An interface defines behaviour. An interface tells you nothing about the actual object other than how it behaves. An abstract class defines an object which in turn drives the behaviour.

1. An ArrayList is a class that implements java.util.List, which in turn extends java.util.Collection.

1. A **parametrised** class uses a type parameter instead of the data type. An example is shown below:

    ```java
    public class DataHolder<E>{
        E data;
        public E getData() { return data; }
        public void setData(E e){ data = e; }
    }

    public class SomeClass<E>{
        public static void consumeData(DataHolder<String> stringData){
            String s = stringData.getData(); // no cast required
        }
    }
    ```

1. This allows a class to be written in a generic fashion, without hardcoding it to any particular type. This also allows that class to be typed to any type as per the requirement at the time of use.

1. A parametrised method is similar to a parametrised class. The only difference is that the type parameter is valid only for that method instead of the whole class.

1. All generic information is stripped at run time, this is known as **type erasure**. This means that the presence of generics can throw up complicated situations with respect to Overloading and Overriding.

1. The java.util.Collection interface is the root interface in the collection heirarchy. java.util.List defines the behaviour of collections that keep objects in an order. The functionality is implemented by classes such as ArrayList and LinkedList.

1. Useful List methods are shown below:
    ```java
    E get(int index);
    E set(int index, E e);
    boolean add(E e);
    void add(int index, E e);
    boolean addAll(Collection<? extends E> c);
    void addAll(int index, Collection<? extends E> c);
    E remove(int index);
    boolean remove(Object obj);
    boolean removeAll(Collection<?> c);
    boolean retainAll(Collection c);
    void clear();
    int size();
    default void forEach(Consume<? super T> action);
    boolean isEmpty();
    boolean contains(Object o);
    boolean containsAll(Collection c);
    List subList(int fromIndex, int toIndex);
    int indexOf(Object o);
    int lastIndexOf(Object o);
    Object[] toArray();
    <T> T[] toArray(T[] a);
    ```

1. The of and copyOf methods take 0 to 10 parameters and return an unmodifiable list.

1. ArrayList constructors are shown below:
    ```java
    ArrayList();
    ArrayList(Collection c);
    ArrayList(int initialCapacity);
    ```

1. Advantages of ArrayList over an array include dynamic sizing, type safety, and readymade features. Disadvantages of ArrayList over an array include higher memory usage, no type safety, and no support for primitive values.

1. The java.util.HashMap class implements the java.util.Map interface. Map does not extend the Collection interface. Useful Map methods are shown below:

    ```java
    V get(Object key);
    V put(K key, V value);
    V remove(Object key);
    Set<K> keySet();
    Collection<V> values();
    void clear();
    int size();
    default void forEach(BiConsumer<? super K, ? super V> action);
    ```

1. A lambda expression is a shortcut for the compiler that defines a class with a method and instantiates that class. The below is an example of a class that implements a car shop:

    ```java
    class Car {
      String company;
      int year;
      double price;
      String type;
    
      Car(String c, int y, double p, String t) {
        this.company = c;
        this.year = y;
        this.price = p;
        this.type = t;
      }
    
      public String toString() {
        return "(" + company + "" + year + ")";
      }
    }
    
    class CarMall {
      List<Car> cars = new ArrayList<>();
    
      CarMall() {
        cars.add(new Car("Honda", 2012, 9000.0, "HATCH"));
        cars.add(new Car("Honda", 2018, 17000.0, "SEDAN"));
        cars.add(new Car("Toyota", 2014, 19000.0, "SUV"));
        cars.add(new Car("Ford", 2014, 13000.0, "SPORTS"));
        cars.add(new Car("Nissan", 2017, 8000.0, "SUV"));
      }
    
      List<Car> showCars(CarFilter cf) {
        ArrayList<Car> carsToShow = new ArrayList<>();
        for (Car c : cars) {
          if (cf.showCar(c))
            carsToShow.add(c);
        }
        return carsToShow;
      }
    }
    
    interface CarFilter {
      boolean showCar(Car c);
    }
    ```
1. The showCars method returns a list of cars based on any given criteria. By accepting an interface as an argument, the showCars method lets the caller decide the criteria for the search. TestClass below represents a third party class that uses CarMall: 

    ```java
    public class TestClass {
        public static void main(String[] args) {
        CarMall cm = new CarMall();
        CarFilter cf = new CompanyFilter("Honda");
        List<Car> carsByCompany = cm.showCars(cf);
        System.out.println(carsByCompany);
        }
    }

    class CompanyFilter implements CarFilter {
      private String company;
    
      public CompanyFilter(String c) {
        this.company = c;
      }
    
      public boolean showCar(Car c) {
        return company.contentEquals(c.company);
      }
    }
    ```

1. Observe that the above implementation can be replaced with the below:

    ```java
    public class TestClass {
        public static void main(String[] args) {
            CarMall cm = new CarMall();
            List<Car> carsByCompany = cm.showCars(c -> c.company.contentEquals("Honda"));
            System.out.println(carsByCompany);
        }
    }
    ```
1. The compiler knows that the showCars method must pass an object of a class that implements CarFilter. As a result it is easy to generate the below:

    ```java
    class XYZ implements CarFilter{
        public boolean showCar(Car <<parameterName>>){
            return <<an expression that returns a boolean>>;
    }
    ```

1. The parameterName and expression are contained wtihin the lambda expression.

1. A lambda expression can be written only where the target type is an interface with exactly one abstract method. Such an interface is known as a **functional interface**.

1. The syntax for a lambda expression is the variable declarations on the left side of the arrow operator and the right side for the code that you want execution.

1. Multiple lines of code must be written within curly braces. Parameter options are shown below:

    ```java
    () -> true // no parameter
    a -> a*a // 1 parameter
    (a) -> a*a // 1 parameter
    (int a) -> a*a // 1 parameter
    (a, b, c) -> a + b + c // multiple parameters
    (var a) -> a*a // var also allowed
    ```

1. Filtering a list of objects is so common that Java provides a generic interface java.util.function.Predicate for this purpose. This is shown below:

    ```java
    interface Predicate<T>{
        boolean test(T t);
    }
    ```

1. This allows us to remove the CarFilter interface in the above example:

    ```java
    List<Car> showCars(Predicate<Car> cp) {
      ArrayList<Car> carsToShow = new ArrayList<>();
      for (Car c : cars) {
        if (cp.test(c)){
          carsToShow.add(c);
        }
      }
      return carsToShow;
    }
    ```
1. Other methods for the Predicate interface are shown below:

    ```java
    default Predicate<T> and(Predicate<? super T> other);
    default Predicate<T> negate();
    default Predicate<T> or(Predicate<? super T> other);
    static <T> Predicate<T> isEqual(Object targetRef);   
    ```
1. The Predicate interface is an example of a functional interface. They are called functional interfaces because they represent a single function and are for doing exactly one thing.

### Handling Exceptions

1. Java exceptions are designed to help you write code that covers all possible execution paths. This includes normal operations, exceptional situtaions and unknown exceptional situations. This is shown below:

    ```java
    try{    
        // code for normal course of action
    } catch(SecurityException se) {
        // code for known exceptional situation
        System.out.println("No permission!");
    }
    catch(Throwable t) {
        // code for unknown exceptional situations
        System.out.println("Some problem in copying: "+t.getMessage());
        t.printStackTrace();
    }
    ```

1. When developing code there is always the provider and the client. Exceptions are a means for the provider to let the client know about any exceptional events, and allow the client to determine how they want to deal with them. The mechanism to let the client know is to **throw** an exception. An example is shown below:

    ```java
    public void copyFile(String inputPath, String outputPath) throws IOException {
        // code to copy file
    }
    ```

1. If the client can resolve the situation a **catch** statement can be used. If the client cannot handle the exceptional situation either, the exception can be propogated to the client's client. An exception is considered handled when it is caught in a catch block.

1. The throw statement is used to explicitly throw an exception. Throwing an exception implies that the code has encountered an unexpected situation with which it does not want to deal. Java requires that you list the exceptions that a method might throw in the throws clause of that method. This is shown below:

    ```java
    public double computeSimpleInterest (double p, double r, double t) throws Exception{
        if(t<0) {
            throw new IllegalArgumentException("time is less than 0");
        }
        // other code
    }
    ```

1. A **try statement** provides an opportunity to recover from an exceptional situation that arises while executing a block of code.

    ```java
    try {
        // code that might throw exceptions
    } catch(<ExceptionClass1> e1){
        // code to execute if code in try throws exception 1
    } catch(<ExceptionClass2> e2){
        // code to execute if code in try throws exception 2
    } catch(<ExceptionClassN> en){
        // code to execute if code in try throws exception N
    } finally{
        // code to execute after try and catch blocks finish execution
 
    }
    ```

1. The java.lang.Throwable class is the root of all exceptions.   A Throwable object includes the chain of the method calls that led to the exception (known as the "stack trace") and any informational message specified by the programmer.

1. The Throwable heirarchy is shown below:

    ![heirarchy](https://i.ibb.co/58YTzkb/heirarchy.png)

1. Generally **checked exceptions** are those that extend java.lang.Throwable but do not extend java.lang.RuntimeException or java.lang.Error. The remaining exceptionsare **checked exceptions**. Checked exceptions must be declared in the throws clause of the method.

### Understanding Modules

1. Jar files are used to package multiple classes into a file and deliver the file as an application to users. However, packaging classes into a jar file without a well thought out plan can give rise to unwieldy applications that are difficult to update and/or reuse. Jar files also make it difficult to use part of an application without having the whole set of jar files. Various Java community projects such as Ant, Maven, and Graven have attempted to provide a way of managing these issues.

1. In Java 9 the Java Module System was introduced to assist with these problems. The idea of Modules is that classes are mixed and matched at run time to form an application. 

1. A module is declared using the module-info.java file. By convention, this file is placed in a folder with the same name as the module name. An example of the contents of this file is shown below:

    ```java
    module simpleinterest{
    }
    ```

1. An example of the file structure for a module shown below:

    ![heirarchy](https://i.ibb.co/BwYqxWM/moduleinfo.jpg)

1. The module is compiled using the below:

    ```java
    javac -d out --module-source-path src --module simpleinterest
    ```

1. The above command used 3 switches. The -d switch directed the output to a particular directory, the --module-source-path switch provided the location of the source module definition, and the --module switch specified the name of the module to compile.

1. The file structure after compilation is shown below:

    ![heirarchy](https://i.ibb.co/kBDmvhG/moduleinfofull.jpg)

1. The module can be run using the below: 

    ```java
    java --module-path out --module simpleinterest/simpleinterest.SimpleInterestCalculator
    ```

1. Note that the format of the --module switch argument is \<module name>/\<main class name>.

1. The module is compiled into a jar using the below:

    ```java
    jar --create --file simpleinterest.jar --main-class simpleinterest.SimpleInterestCalculator -C out\simpleinterest
    ```

1. The above command used 4 switches. The --create switch tells the jar tool to create, the --file switch specifies the name of the file, the --main-class switch adds a Main-Class entry in the jar file manifest, and the -C switch makes the jar tool change working directories so that the structure inside the jar file is the same as the structure inside out\simpleinterest. 

1. The module can now be run using the below:

    ```java
    java --module-path . --module simpleinterest
    ```

1. It is a good design practise to define functionality in the form of an interface and let the actual implementation implement that interface. Seperating the interface and the implementation into separate modules allows us to build an application by mixing and matching modules without the need to bundle classes that are not required for the application. An interface is added as shown below:

    ```java
    package calculators;
	public interface InterestCalculator{
		public double calculate(double principle, double rate, double time);
	}
    ```

1. The exports clause allows the public types within a package be eligible to be accessible by other modules. The contents of module-info.java for the calculators module is shown below:

    ```java
    module calculators{
		exports calculators;
	}
    ```

1. The requires clause is the counterpart of the exports clause. The purpose of having a requires class is to make the dependencies of a module explicitly clear to the users. The contents of module-info.java for the simpleinterest module is shown below:

    ```java
    module simpleinterest{
		requires calculators;
	}
    ```

1. A simplified SimpleInterestCalculator.java is shown below:

    ```java
    package simpleinterest;
	import calculators.InterestCalculator;
	public class SimpleInterestCalculator implements InterestCalculator{
		public double calculate(double principle, double rate, double time){
			return principle*rate*time;
		}
		public static void main(String[] args){
			InterestCalculator ic = new SimpleInterestCalculator();
			System.out.println(ic.calculate(100, .05, 2));
		}
	}
    ```

1. The directory structure after compilation is shown below:

	![heirarchy](https://i.ibb.co/C0zF5rk/moduleexport-JPG.jpg)

1. The exports clause allows any other module to require it. The Java module systems allows you to fine tune access to a module only to specific modules using a variation of the exports clause. This is shown below:

    ```java
    module <modulename>{
		exports <packagename> to <modulename(s)>;
	}
    ```

1. If a module A reads another module B, and module B reads another module C, module A does not read module C. That is to say that dependencies are not transitive. An example is shown below:

    ```java
    module ui{
		requires hr;
	}

    module hr{
		requires valueobjects;
		exports hrservice;
	}

	// code appearing in a class in the ui module
	HRService hrService = new HRService(); // HRService is defined in hr module
	Employee e = hrService.getEmployee(employeeId); // Employee is defined in valueObjects module
    ```

1. In this case the ui module does not have a requires valueobjects, so the ui module cannot access the Employee class from the valueobjects module. This code will fail to compile. A requires valueobjects could be added to the ui module, but there could be many requires clauses in the hr module. Only multiple compilation failures can make this information known to the ui module.

1. A **requires transitive** clause allows you to specify that if a module depends on another module, any module that depends on it should also depend on the other module. An example is shown below

    ```java
    module hr{
		requires transitive valueobjects;
		exports hrservice;
	}
    ```

1. This has the added advantage of not requiring a requires valueobjects clause in the ui module. The requires hr clause in the ui module automatically makes all of the modules transitively required by the hr module, readable to the ui module. This is called implied readability.

1. A modular jar file can be ran using the -classpath or -jar options, however the JVM will not enforce the access rules specified in the module descriptor.

1. A common use case is wanting to develop a module that depends on a third party non-modular jar. If you put a non-modular jar on the module-path, Java will consider the non-modular jar to be a module. Such a module is known as an **automatic module** or a **named module** and the name of the module is created automatically using the name of the jar file.

1. As there is no module-info.class in a non-modular jar, an automatic module exports all its packages and is allowed to read all exported packages of modules on the module-path and classes vailable on the classpath.

1. If a module depends on a non-modular third party jar, you need to add a requires clause in module-info and put the third party jar in the --module-path. If additionally the automatic module requires a class from another non-modular jar, that jar needs to be included on the classpath.

### Understanding Java Technology and environment

1. Java code is compiled into **Java bytecode**, which is interpreted by the JVM. A class file produced on one platform will run on any platform that has a JVM.

1. Java is a seperate application installed on top of an Operating System.

1. The **Java Runtime Environment (JRE)** includes the class libraries and executables that are required to run a Java program while the **Java Development Kit (JDK)** includes tools such as the Java compiler and the Java debugger. 

## Java SE 11 Programmer II

- [Java Fundamentals](#Java-Fundamentals)
- [Annotations](#Annotations)
- [Generics and Collections](#Generics-and-Collections)
- [Functional Programming](#Functional-Programming)
- [Exceptions, Assertions, and Localization](#Exceptions,-Assertions,-and-Localization)
- [Modular Applications](#Modular-Applications) 
- [Concurrency](#Concurrency) 
- [I/O](#I/O) 
- [NIO.2](#NIO.2) 
- [JDBC](#JDBC) 
- [Security](#Security)

### Java Fundamentals

1. A final variable does not need to be assigned when it is declared, only before it is used. A variable reference being marked as final does not mean the associated object cannot be modified. If an instance variable is final, then it must be assigned a value when it is declared or when the object is instantiated. Similiarly, static variables must be assigned a value when declared or in a static initialiser.

1. Methods marked final cannot be overriden by a subclass. This essentially prevents any polymorphic behaviour on the method call and ensures that a specific version of the method is always called. The opposite of a final method is an abstract method as an abstract method must be implemented.