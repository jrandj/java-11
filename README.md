# Java 11

## Understanding Java Technology and environment

## Creating a Simple Java Program

## Working With Java Primitive Data Types and String APIs

1. Java is a statically typed language. This means that the data type of a variable is defined at compile time and cannot change during run time. 
2. Java has primitive and reference variables. The Java compiler and JVM inherently know what primitive types mean, while reference data types are built by combining primitive data types and other reference data types.
3. Primitive data types below:

| Date Type | Size    | Description                                                             | Sample                  |
|-----------|---------|-------------------------------------------------------------------------|-------------------------|
| byte      | 1 byte  | -128 to 127                                                             | -1, 0, 1                |
| short     | 2 bytes | -32,768 to 32,767                                                       | 0, 1, 2, 'a', '\u00061' |
| int       | 4 bytes | -2,147,483,648 to 2,147,483,647                                         | -1, 2, 3                |
| long      | 8 bytes | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807                 | -1, 2, 3                |
| float     | 4 bytes | Stores fractional numbers. Sufficient for storing 6 to 7 decimal digits | -1, 2, 3                |
| double    | 8 bytes | Stores fractional numbers. Sufficient for storing 15 decimal digits     | 1.1f, 2.0f              |
| boolean   | 1 bit   | Stores true or false values                                             | 1.1, 2.0                |
| char      | 2 bytes | Stores a single character                                               | true, false             |

Wrapper classes exist for Byte, Short, Integer, Long, Float and Double.

4. Reference types include:
⋅⋅* Classes
⋅⋅*  Interfaces
⋅⋅*  Enums
5. A variable contains a raw number, and assigning one variable to another simply copies that number from one variable to another. Java uses **pass by value** semantics.
6. Java initialises all static and instance variables of a class automatically if you don't initialise them explicitly. You must initalise local variables explicitly before they are used.
7. Assigning a smaller type to a larger type is known as **implicit widening conversion** as no cast is required. To assign a larger type to a smaller type, for a compile time constant (i.e. final) the compiler will automatically narrow the value. If the source variable is not a constant then a cast is required, this is known as **explicit narrowing**. Determining the value that will actually be assigned when doing an explicit can be complicated.

## Using Operators and Decision Constructs

## Working with Java Arrays

## Describing and Using Objects and Classes

## Creating and Using Methods

## Applying Encapsulation

## Reusing Implementations Through Inheritance

## Programming Abstractly Through Interfaces

## Handling Exception

## Understanding Modules

1. Linked Lists
2. Trees
3. Tries
4. Graphs
5. Stacks
6. Queues
7. Heaps
8. Vectors
9. ArrayLists
10. Hash Tables