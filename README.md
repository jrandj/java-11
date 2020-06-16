# Java 11

## Java SE 11 Programmer I

- [Understanding Java Technology and environment](#Understanding-Java-Technology-and-environment)
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

### Understanding Java Technology and environment

### Creating a Simple Java Program

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

### Handling Exception

### Understanding Modules

## Java SE 11 Programmer II
