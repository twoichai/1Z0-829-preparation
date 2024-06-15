# Chapter 1: Building Blocks
**Topics:**
- Handling date, time, text, numeric and boolean values
--primitives and wrapper classes
- OOP
--nected class objects
--life-cycle
--garbage collection
---
### Components of Java
JDK:

`javac`: Converts .java src files into .class bytecode
`java`: Executes the Program
`jar`: Packages files together
`javadoc`: Generates documentation

**HINT**: java launches HVM and runs the bytecode

---
### Class Structure
- Object = Class
- Class contains fields (attributes) and methods

Example

    public class Animal {
	    String name;
	    public void setName(String newName){
		    name = newName;
	    }
    }

> void - no value at all returned
> smart to use when just changing the state of the object
---
### Classes and Source Files
**Top Level class** is often public --> any code can call it
**Java does not requiere that the type is public**

    class Animal {
    }
it is possible to have two types in the same file

    public class Animal {
    }
    class Animal2{}
**HINT**: if you have public type, it needs to match the filename

> public class Animal2{} -> will not compile in a file Animal.java

---
### Writing a *main ()* Method
**main function:** lets JVM call our code
also called ***entry point into the program***

    
    public class Zoo {
	    public static void main(String[] args) {
	     System.out.println("Hello World"); 
	    } 
    }

`javac Zoo.java`: convert the file into binary class file
`java Zoo`: executes the class file
 
 **Java Class Rules:**
 - each file contains only one public class
 - filename must match class name & `.java` extension

other things:
`static`: bind a method to its class so it can be called by just the class name --> no object creation needed

---
### Understanding Package Declarations and Imports

HINT:

    public static void main(String[] args) { 
    	Random r = new Random();
    	System.out.println(r.nextInt(10)); 
   	}
Prints numbers from 0-9

- Package names are hierarchical
- including many imports does not slows down the execution of program
- **java.lang is automatically imported**
- packages allow to have classes with same names

Some typical errors:

    import java.nio.*; // NO GOOD - a wildcard only matches // class names, not "file.Files" 
    import java.nio.*.*; // NO GOOD - you can only have one wildcard // and it must be at the end 
    import java.nio.file.Paths.*; // NO GOOD - you cannot import methods // only class names
### What happens if you need to use two classes with the same name?

    public class Conflicts { 
	    java.util.Date date; 
	    java.sql.Date sqlDate; 
    }
### Hierarchy in Java Class
- P - Package
- I - Imports
- C - Class
---
### Creating Objects
to create an instance of a class `new` is needed:

    Park p = new Park();
1. Declare the type `Park`
2. Give a variable for storage `p`
3. `Park()` is the constructor which creates a new object

**Custom constructor:**

    public class Chick { 
	    public Chick() { 
		    System.out.println("in constructor"); 
	    } 
    }
**HINT:**
- there is no return type, but `void` is not good
- constructor is named after the class
- purpose of constructor : initialize fields

**Example:**

    public class Chicken { 
	    int numEggs = 12; 
	    String name;
	    public Chicken() { 
		    name = "Duke"; // initialize in constructor 
	    } 
    }
---
### Member and Writing Member Fields

    public class Swan { 
	    int numberEggs; // instance variable 
	    public static void main(String[] args) { 
		    Swan mother = new Swan(); 
		    mother.numberEggs = 1; // set variable 
		    System.out.println(mother.numberEggs); // read variable 
    	} 
    }

---
- Fields and instance initialize blocks are run in the order in which they appear in the file
- Constructor runs after all fields and instance initializer blocks have run

---
### Understanding the Data Types
#### Primitives:

- int values without decimal points: `byte, short, int, long` 
- `float` & `long` requires L/F at the end of the number: `123L, 123.45f`
- what is the size of `boolean`? depends on the JVM

#### Difference between `short` and `char`:
`short` is *signed*, `char` is *unsigned*
**means**: 
`short`: range of short is **-infinity** to **+infinity**
`char`: **0** and **+values**
#### Writing Literals:
numbers are present in code called *literals*
if don't add `L` 

    double notAtStart = _1000.00; // DOES NOT COMPILE 
    double notAtEnd = 1000.00_; // DOES NOT COMPILE 
    double notByDecimal = 1000_.00; // DOES NOT COMPILE 
    double annoyingButLegal = 1_00_0.0_0; // Ugly, but compiles 
    double reallyUgly = 1_______2; // Also compiles
---
### Reference Types
Each primitive type has a wrapper class, which corresponds to the primitive
It is an option to convert 

    int primitive = Integer.parseInt("123);
    Integer wrapper = Integer.valueOf("123");
1. converts a String to an int primitive
2. converts a String to an Integer wrapper class

we also can return different number types with methods from `Number` class:

    Double apple = Double.valueOf("200.99");
    System.out.println(apple.byteValue()); // -56 
    System.out.println(apple.intValue()); // 200 
    System.out.println(apple.doubleValue()); // 200.99
`Integer` also has additional methods:

`max(int num1, int num2)` returns the largest of the two numbers
`min(int num1, int num2)` returns the smallest of the two numbers
`sum(int num1, int num2)` adds the two numbers

---
### Defining Text Blocks
**Escape characters:**
`\"` --> "
`\n` --> new line
### Declaring Variables
variable is a name for a piece of memory that stores data --> initializing a variable

    String zooName = "Best Zoo";

- it's not allowed to name identifiers with reserved words
- single underscore is not allowed
- identifier can't start with a number
- identifiers must begin with a letter, currency symbol or a `_` symbol

Examples of ilegal identifiers:

    int 3DPointClass; // identifiers cannot begin with a number byte hollywood@vine; // @ is not a letter, digit, $ or _ 
    String *$coffee; // * is not a letter, digit, $ or _ 
    double public; // public is a reserved word 
    short _;
### Declaring Multiple Variables

    void sandFence() { 
	    String s1, s2; 
	    String s3 = "yes", s4 = "no"; 
    }
***declared*** means that memory was allocated
***initialized*** means that a variable got a value
`int num, String value;` will not compile because of different types

### Final Local Variables
`final` is applied to local variables

    final int y = 10;
    int x = 20;
    y = x +10; // INVALID since final can't be modified
- local variables have no default value --> need to be initialized before use
---
### Var
- should be used localy --> inside a method
- it should be initialized else it will not compile
- methods params can't be vars 

**Scope of Variables**
- `Local variables`: in scope from declaration to the end of the block
- `Method parameters`: in scope for the duration of the method
- `instance variables`: in scope from declaration till object is eligible for garbage collection
- class variables: in scope till the program ends

---
### Garbage Collection
process of automatically freeing memory on the heap by deleting objects that are no longer reachable in your program
 

    System.gc();
    
In Java, there are no guarantees about when garbage collection will run. The JVM is free to ignore calls to System.gc()

---
### Summary
- Java begins program execution with a `main()` method
- Java code is organized into packages, `import` statement is used to reference classes in other packages
- Primitive types are the basic building blocks of Java
- Primitive types assemble into reference types
- 
