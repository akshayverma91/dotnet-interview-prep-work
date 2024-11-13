What is Polymorphism?
Polymorphism is a fundamental concept in object-oriented programming (OOP) that allows objects of different classes to be treated in the same way, even though they have different underlying implementations. It literally means "many forms" and reflects the ability of code to take on multiple forms or behaviors depending on the context.

Key Concepts:

Same Interface, Different Implementations: Polymorphism lets you use a single interface or method call to work with objects of different classes, each of which may have its own unique implementation of that interface or method.

Flexibility and Extensibility: Polymorphism makes your code more flexible and extensible. You can add new classes or modify existing ones without breaking existing code that uses them, as long as they conform to the common interface.

Code Simplification: Polymorphism can simplify your code by reducing the number of conditional statements (like if-else) needed to handle different object types.

Examples:

Method Overriding:

You have a Animal class with a MakeSound() method, and subclasses like Dog and Cat that override this method with their own specific sounds (e.g., "Woof!" and "Meow!"). You can call MakeSound() on any Animal object, and it will produce the appropriate sound based on its type.

public class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Generic animal sound");
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Woof!");
    }
}

public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Meow!");
    }
}


Interface Implementation:

You have an IDrawable interface with a Draw() method, and multiple classes like Circle, Square, and Line that implement this interface with their own specific drawing logic. You can use a single IDrawable variable to represent any of these shapes and call Draw() to render them appropriately.

public interface IDrawable
{
    void Draw();
}

public class Circle : IDrawable
{
    public void Draw()
    {
        Console.WriteLine("Drawing a circle...");
    }
}

public class Square : IDrawable
{
    public void Draw()
    {
        Console.WriteLine("Drawing a square...");
    }
}

Benefits of Polymorphism:

Maintainability: Easier to change or add new classes without breaking existing code.

Flexibility: Allows for a more dynamic and adaptable codebase.

Code Reusability: Reduces redundant code by sharing a common interface or method call.

Readability: Code can be more concise and easier to understand.

In essence, polymorphism lets you write code that works with objects of different types in a unified and consistent way, promoting flexibility, extensibility, and code reuse.

Method overloading:

Example 1: Calculating Area

public class Shape
{
    public double CalculateArea(double radius)
    {
        return Math.PI * radius * radius; // Area of a circle
    }

    public double CalculateArea(double length, double width)
    {
        return length * width; // Area of a rectangle
    }
}

class Program
{
    static void Main(string[] args)
    {
        Shape shape = new Shape();

        double circleArea = shape.CalculateArea(5.0); // Calls the CalculateArea(double) method
        Console.WriteLine($"Circle Area: {circleArea}");

        double rectangleArea = shape.CalculateArea(4.0, 6.0); // Calls the CalculateArea(double, double) method
        Console.WriteLine($"Rectangle Area: {rectangleArea}");
    }
}

Explanation:

Method Overloading: The Shape class has two CalculateArea() methods, each with a different signature (different number and types of parameters). This is method overloading.

Compiler Selection: The compiler chooses which CalculateArea() method to call based on the arguments you provide when calling it.

shape.CalculateArea(5.0) calls the method that takes a single double argument (circle area).

shape.CalculateArea(4.0, 6.0) calls the method that takes two double arguments (rectangle area).

Example 2: String Manipulation

public class StringHelper
{
    public string Concatenate(string str1, string str2)
    {
        return str1 + " " + str2;
    }

    public string Concatenate(string str1, string str2, string str3)
    {
        return str1 + " " + str2 + " " + str3;
    }
}

class Program
{
    static void Main(string[] args)
    {
        StringHelper helper = new StringHelper();

        string result1 = helper.Concatenate("Hello", "World");
        Console.WriteLine(result1); // Output: Hello World

        string result2 = helper.Concatenate("Good", "Morning", "Everyone");
        Console.WriteLine(result2); // Output: Good Morning Everyone
    }
}

Explanation:

Multiple Concatenation: The StringHelper class has two Concatenate() methods. One takes two strings and concatenates them, while the other takes three strings and concatenates them.

Parameter Matching: The compiler determines which Concatenate() method to call based on the number of arguments passed.

Key Points:

Method overloading allows you to provide different versions of a method with varying parameter lists.

The compiler chooses the appropriate method based on the number and types of arguments you pass when calling it.

Method overloading enhances code flexibility and readability by allowing you to reuse method names for different tasks.



What are possible ways to do method overriding?
1. Method Overriding with virtual and override Keywords

Base Class: In the base class, declare the method you want to be overridable using the virtual keyword:

public class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Generic animal sound");
    }
}
Derived Class: In the derived class, use the override keyword to indicate that you're specifically overriding the base class method:

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Woof!");
    }
}

2. Method Overriding with abstract Methods

Base Class: Declare the method as abstract in the base class:

public abstract class Shape
{
    public abstract double CalculateArea();
}

Derived Class: Derived classes must provide an implementation for abstract methods:

public class Circle : Shape
{
    public override double CalculateArea()
    {
        return Math.PI * radius * radius; 
    }
}

Key Points:

abstract methods cannot be implemented in the base class itself.

Any class that inherits from an abstract class must provide implementations for all abstract methods.


3. Overriding with sealed Methods (Preventing Further Overriding)

Base Class: Declare the method as sealed in the base class. This prevents any derived classes from overriding it:

public class Animal
{
    public sealed void Breathe()
    {
        Console.WriteLine("Animal breathing...");
    }
}

public class Dog : Animal // Error: Cannot override 'Breathe' because it is sealed.
{
    // public override void Breathe() { ... } // Not allowed
}

Important Considerations:

Return Type: The overriding method in the derived class must have the same return type as the base class method.

Access Modifier: The overriding method's access modifier can be the same or more accessible than the base class method (e.g., protected can be overridden with public, but not vice versa).

Parameters: The overriding method must have the same number and types of parameters as the base class method.


Example Scenario:

Imagine a base class Vehicle with a StartEngine() method. You want to create subclasses for different vehicle types (e.g., Car, Truck) that override StartEngine() to provide specific engine start behaviors.

Base Class:

public class Vehicle
{
    public virtual void StartEngine()
    {
        Console.WriteLine("Engine starting...");
    }
}

Derived Classes:

public class Car : Vehicle
{
    public override void StartEngine()
    {
        Console.WriteLine("Car engine starting with a smooth hum...");
    }
}

public class Truck : Vehicle
{
    public override void StartEngine()
    {
        Console.WriteLine("Truck engine starting with a loud roar...");
    }
}

