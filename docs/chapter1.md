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
