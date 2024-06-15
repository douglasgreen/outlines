# Design Patterns

## Introduction to Software Design Patterns

Software design patterns are a fundamental concept in software engineering, offering a high-level
solution to common design problems encountered in software development. By understanding and
applying design patterns, developers can create more efficient, maintainable, and scalable software.
Let's delve into the various aspects of software design patterns.

### Understanding Design Patterns

1. **Definition**: A software design pattern is a general, reusable solution to a commonly occurring
   problem within a given context in software design. It's not a finished design that can be
   directly transformed into code, but rather a template for how to solve a problem in various
   situations.

2. **Types of Patterns**: There are three main categories of design patterns:

    - **Creational Patterns**: These patterns deal with object creation mechanisms, trying to create
      objects in a manner suitable to the situation. Examples include Singleton, Factory, and
      Builder patterns.
    - **Structural Patterns**: These patterns are concerned with how classes and objects are
      composed to form larger structures. Examples include Adapter, Decorator, and Composite
      patterns.
    - **Behavioral Patterns**: These focus on communication between objects, how objects interact
      and distribute responsibility. Examples include Observer, Strategy, and Command patterns.

3. **Characteristics**: Design patterns are typically characterized by their simplicity and
   elegance, solving specific problems without adding unnecessary complexity. They also promote
   reusability and maintainability in software development.

### History and Evolution

1. **Origins**: The concept of design patterns in software engineering was inspired by the work in
   architecture by Christopher Alexander in the 1970s. He proposed that design patterns could
   provide solutions to common problems in urban planning.

2. **The Gang of Four (GoF)**: The term “design patterns” gained popularity with the 1994 book
   "Design Patterns: Elements of Reusable Object-Oriented Software" by Erich Gamma, Richard Helm,
   Ralph Johnson, and John Vlissides, collectively known as the Gang of Four (GoF). This book
   catalogued 23 design patterns and is considered a seminal work in the field.

3. **Evolution**: Since the publication of the GoF book, the study and application of design
   patterns have evolved. New patterns have emerged, and existing ones have been adapted to modern
   programming languages and paradigms.

### Importance in Software Development

1. **Problem Solving**: Design patterns provide proven solutions to common problems. This helps in
   preventing subtle issues that can cause major problems and improves the efficiency of the
   development process.

2. **Communication**: Patterns provide a common vocabulary for designers and developers. Discussing
   patterns by name, like mentioning the “Singleton pattern” or “Observer pattern”, simplifies
   communication and understanding among team members.

3. **Best Practices**: Applying design patterns encourages the use of best practices in software
   development. It guides developers to structure code in such a way that it is more robust,
   reusable, and maintainable.

4. **Adaptability and Scalability**: Patterns help in building software that is easy to adapt and
   scale as requirements change. This is crucial in modern software development, where applications
   often need to evolve rapidly to meet changing demands.

In conclusion, software design patterns are essential tools for developers. They not only offer
solutions to common problems but also enhance the quality and maintainability of software products.
As technology evolves, the application and understanding of design patterns continue to be a vital
aspect of efficient software development.

## Design Pattern Questions

For each design pattern presented here, we will ask the same series of questions:

-   What is the design pattern?
-   What is the purpose of the design pattern?
-   What software principles does the design pattern apply?
-   What are some helpful uses of the design pattern?
-   What are some possible drawbacks of using the design pattern?
-   What is the basic structure of objects and methods used by the design pattern?
-   What are some possible variations of this design pattern?
-   How does the design pattern relate to other design patterns?
-   What are some common criticisms of the design pattern?
-   Explain step-by-step how to implement the design pattern.
-   Give an example of the design pattern in Java.

## Creational Patterns

### Singleton Pattern

The Singleton pattern is a widely-used design pattern in software development. Let's explore it in
detail, addressing your specific questions.

#### What is the Singleton Design Pattern?

The Singleton pattern is a creational design pattern that ensures a class has only one instance and
provides a global point of access to it. This pattern restricts the instantiation of a class to a
single object.

#### Purpose of the Singleton Pattern

The primary purpose of the Singleton pattern is to control class instantiation. It is used when
there should be exactly one instance of a class, and that instance must be accessible from multiple
points in the application.

#### Software Principles Applied

The Singleton pattern applies the following principles:

-   **Encapsulation**: It encapsulates its sole instance.
-   **Control over global variables**: It offers a controlled access point rather than global
    variables scattered throughout the code.

#### Helpful Uses

1. **Global State Management**: Managing a shared resource, like a database or a file system, where
   having multiple instances could cause conflicts or consume excessive resources.
2. **Configuration Settings**: Holding application-wide settings that need to be accessed from
   various parts of an application.

#### Possible Drawbacks

1. **Global State**: Singleton can introduce a global state in an application, which can lead to
   hidden dependencies between classes, making the code harder to test and maintain.
2. **Scalability Issues**: In multithreaded applications, ensuring that a Singleton remains a single
   instance can be challenging and can lead to scalability issues.

#### Basic Structure

-   **Private Constructor**: Ensures that the class cannot be instantiated from outside.
-   **Private Static Instance**: The single instance of the class.
-   **Public Static Method**: This method returns the instance of the class. It creates the instance
    if it doesn't already exist.

#### Variations

1. **Lazy Initialization**: The instance is created when it is first needed.
2. **Eager Initialization**: The instance is created when the class is loaded.
3. **Thread-Safe Singleton**: Synchronization mechanisms are used to ensure that only one instance
   is created even in a multithreaded environment.

#### Relation to Other Patterns

Singleton often interacts with other design patterns. For example:

-   It can be used with Factory Method to control the factory instances.
-   In Abstract Factory, Builder, and Prototype, a Singleton might control created objects.

#### Common Criticisms

1. **Violates Single Responsibility Principle**: Singleton pattern can lead to a class that has the
   dual responsibility of its own core functionality and the management of its instance.
2. **Difficulties in Testing**: Singletons can carry state throughout the lifetime of an
   application, making unit testing difficult.

#### Implementing the Singleton Pattern

1. **Declare a private static variable** that holds the single instance of the class.
2. **Make the constructor private** to prevent instantiation from outside the class.
3. **Provide a public static method** that returns the instance of the class.

#### Example in Java

Here's a basic implementation of a Singleton pattern in Java:

```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {
        // private constructor
    }

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

In this Java example, `Singleton` class ensures that only one instance of itself is created and
provides a global access point to that instance. The `getInstance()` method creates a new instance
of `Singleton` if it doesn't exist and returns the existing instance if it does.

### Factory Method Pattern

The Factory Method Pattern is a creational design pattern that provides an interface for creating
objects in a superclass but allows subclasses to alter the type of objects that will be created.
Let's explore this pattern in detail.

#### What is the Factory Method Pattern?

It's a design pattern that deals with object creation while allowing subclasses to choose the type
of objects to create. It's part of the larger concept of Factory patterns in software design.

#### Purpose of the Design Pattern

The primary purpose of the Factory Method is to define an interface for creating an object but lets
the subclasses decide which class to instantiate. It lets a class defer instantiation to subclasses,
promoting loose coupling.

#### Software Principles Applied

1. **Encapsulation**: The Factory Method encapsulates the object creation process.
2. **Single Responsibility Principle**: It separates the object creation code from the business
   logic of the class.
3. **Open/Closed Principle**: The pattern is open for extension but closed for modification.

#### Helpful Uses

1. **Flexibility in Object Creation**: It's used when a class cannot anticipate the class of objects
   it needs to create.
2. **Programmatic Configuration**: Useful in scenarios where the types of objects needed are
   determined by external configurations or environments.

#### Possible Drawbacks

1. **Complexity**: Can introduce unnecessary complexity into code if used in simple scenarios.
2. **Indirect Layer**: Adds an additional layer of abstraction which can make debugging harder.

#### Basic Structure

1. **Product**: Defines the interface of objects the factory method creates.
2. **Concrete Product**: Implements the product interface.
3. **Creator**: Declares the factory method that returns a product object.
4. **Concrete Creator**: Overrides the factory method to return an instance of a concrete product.

#### Possible Variations

1. **Parameterized Factory Methods**: Methods that take parameters and create objects based on those
   parameters.
2. **Static Factory Methods**: Instead of using inheritance and instance methods, static methods can
   create and return instances.

#### Relation to Other Design Patterns

-   **Abstract Factory**: Often used with Factory Method. While Factory Method creates objects
    through inheritance, Abstract Factory does so through object composition.
-   **Prototype**: Can be used with Factory Method to return a cloned object instead of a new
    instance.

#### Common Criticisms

1. **Overuse**: Sometimes overused in situations where a simpler approach would suffice.
2. **Subclassing Requirement**: Requires the creation of a new subclass for each new product type.

#### Implementing the Factory Method Pattern

1. **Define a Product Interface**: This outlines the structure of the products the factory will
   create.
2. **Create Concrete Product Classes**: These classes implement the product interface.
3. **Create a Creator Abstract Class or Interface**: It should have the factory method.
4. **Implement Concrete Creator Classes**: These classes override the factory method to create
   specific product instances.

#### Example in Java

```java
// Product interface
interface Product {
    void use();
}

// Concrete Products
class ConcreteProductA implements Product {
    public void use() {
        System.out.println("Using ConcreteProductA");
    }
}

class ConcreteProductB implements Product {
    public void use() {
        System.out.println("Using ConcreteProductB");
    }
}

// Creator
abstract class Creator {
    public abstract Product factoryMethod();
}

// Concrete Creator
class ConcreteCreatorA extends Creator {
    public Product factoryMethod() {
        return new ConcreteProductA();
    }
}

class ConcreteCreatorB extends Creator {
    public Product factoryMethod() {
        return new ConcreteProductB();
    }
}

// Usage
public class FactoryMethodExample {
    public static void main(String[] args) {
        Creator creatorA = new ConcreteCreatorA();
        Product productA = creatorA.factoryMethod();
        productA.use();

        Creator creatorB = new ConcreteCreatorB();
        Product productB = creatorB.factoryMethod();
        productB.use();
    }
}
```

In this Java example, `ConcreteCreatorA` and `ConcreteCreatorB` are subclasses of `Creator` and
override the `factoryMethod` to return instances of `ConcreteProductA` and `ConcreteProductB`,
respectively. This allows for creating different products while the client code remains decoupled
from the concrete product classes.

### Abstract Factory Pattern

The Abstract Factory Pattern is a creational design pattern that focuses on the method of creating
families of related or dependent objects without specifying their concrete classes. Let's explore
this pattern in detail based on your queries.

#### What is the Abstract Factory Pattern?

The Abstract Factory Pattern is used to provide an interface for creating families of related or
dependent objects without specifying their concrete classes. It involves multiple factories to
create a series of related or dependent products.

#### Purpose of the Design Pattern

The purpose of the Abstract Factory pattern is to enable a system to be independent of how its
objects are created, composed, and represented. It allows one to use multiple factories, each
designed to create objects belonging to a different family of products.

#### Software Principles Applied

1. **Encapsulation**: The pattern encapsulates the concrete classes and the creation process.
2. **Open/Closed Principle**: The pattern is open for extension but closed for modification.
3. **Single Responsibility Principle**: It promotes separation of concerns – each factory class
   handles the creation of a certain type of object.

#### Helpful Uses

1. **Consistent Object Families**: Useful when a system should be configured with one of multiple
   families of products.
2. **Platform Independence**: When the system needs to be independent of how its products are
   created, composed, and represented.

#### Possible Drawbacks

1. **Complexity**: The pattern can be complex to implement, especially when adding new variants.
2. **Fixed Set of Products**: If new kinds of products need to be added, the interface may require
   changes, affecting all its concrete classes.

#### Basic Structure

1. **Abstract Factory**: An interface with methods to create different abstract products.
2. **Concrete Factory**: Implements the operations to create concrete products.
3. **Abstract Product**: Declares an interface for a type of product object.
4. **Concrete Product**: Defines a product object to be created by the corresponding concrete
   factory.
5. **Client**: Uses interfaces declared by the Abstract Factory and Abstract Product classes.

#### Possible Variations

1. **Lazy Initialization**: Factories might use lazy initialization to create objects when needed
   rather than upfront.
2. **Prototyping**: A variation might involve using a prototype pattern to clone a pre-initialized
   object.

#### Relation to Other Design Patterns

-   **Factory Method**: Often used inside an abstract factory to create the concrete objects.
-   **Singleton**: The factories themselves are often implemented as Singletons.

#### Common Criticisms

1. **Complexity**: The pattern can be overkill for simple systems.
2. **Refactoring Effort**: Introducing a new variant of a product might require substantial changes.

#### Implementing the Pattern

1. **Define Abstract Factory Interface**: Declare an interface for operations that create abstract
   products.
2. **Create Concrete Factory Classes**: Implement the abstract factory interface to create concrete
   products.
3. **Define Abstract Product Interfaces**: Each distinct product of a product family should have an
   abstract interface.
4. **Implement Concrete Product Classes**: Implement each product's interface in classes.
5. **Use the Factory**: The client code should work with factories and products only through their
   abstract interfaces.

#### Example in Java

```java
// Abstract Factory
interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}

// Concrete Factory
class WinFactory implements GUIFactory {
    public Button createButton() {
        return new WinButton();
    }

    public Checkbox createCheckbox() {
        return new WinCheckbox();
    }
}

class MacFactory implements GUIFactory {
    public Button createButton() {
        return new MacButton();
    }

    public Checkbox createCheckbox() {
        return new MacCheckbox();
    }
}

// Abstract Product
interface Button {
    void paint();
}

interface Checkbox {
    void paint();
}

// Concrete Products
class WinButton implements Button {
    public void paint() {
        System.out.println("Windows Button");
    }
}

class MacButton implements Button {
    public void paint() {
        System.out.println("Mac Button");
    }
}

class WinCheckbox implements Checkbox {
    public void paint() {
        System.out.println("Windows Checkbox");
    }
}

class MacCheckbox implements Checkbox {
    public void paint() {
        System.out.println("Mac Checkbox");
    }
}

// Client code
public class Application {
    private Button button;
    private Checkbox checkbox;

    public Application(GUIFactory factory) {
        button = factory.createButton();
        checkbox = factory.createCheckbox();
    }

    public void paint() {
        button.paint();
        checkbox.paint();
    }

    public static void main(String[] args) {
        GUIFactory factory = new WinFactory(); // Can be replaced with MacFactory
        Application app = new Application(factory);
        app.paint();
    }
}
```

In this Java example, the `Application` class is the client that uses the `GUIFactory` interface to
create GUI elements. Depending on the factory (Windows or Mac) passed to the application, it will
create and display either Windows or Mac styled buttons and checkboxes. This pattern allows for the
creation of platform-specific GUI elements while keeping the client code abstracted from the
concrete implementations.

### Builder Pattern

The Builder Pattern is a creational design pattern that aims to construct complex objects step by
step. Let's explore this pattern in detail, addressing your specific questions.

#### What is the Builder Pattern?

The Builder Pattern separates the construction of a complex object from its representation so that
the same construction process can create different representations. It's particularly useful for
constructing objects with numerous parameters.

#### Purpose of the Design Pattern

The primary purpose of the Builder Pattern is to provide a flexible solution to various object
creation problems in object-oriented programming. It's used to construct a complex object step by
step and allows it to be constructed in a safe manner.

#### Software Principles Applied

1. **Single Responsibility Principle**: The pattern separates the complex construction of an object
   from its representation.
2. **Open/Closed Principle**: It’s easy to introduce new types of products without affecting the
   existing client code.

#### Helpful Uses

1. **Complex Objects**: Useful for creating complex objects with multiple optional and required
   fields, especially when a constructor with many parameters would be impractical.
2. **Immutability**: Helps in building immutable objects without much complex logic in the
   constructor.

#### Possible Drawbacks

1. **Increased Complexity**: Introduces multiple new classes, which can complicate the code
   structure.
2. **Builder Overhead**: In simpler scenarios, using a builder can lead to unnecessary overhead.

#### Basic Structure

1. **Builder**: An interface that specifies methods for creating the different parts of a Product
   objects.
2. **Concrete Builder**: Implements the Builder interface, providing implementations for those
   creation methods. It keeps track of the product being created and offers a way to retrieve the
   finished object.
3. **Product**: The complex object that is being built.
4. **Director**: An optional class that defines the order in which to call construction steps, so
   you can create and reuse specific configurations of products.

#### Possible Variations

1. **Fluent Interface**: Often, each method in a builder returns the builder itself so that method
   calls can be chained.
2. **No Director Class**: In simpler implementations, the director class can be omitted.

#### Relation to Other Design Patterns

-   **Abstract Factory**: Builders can be used in Abstract Factories when the products are complex
    and require intricate configuration.
-   **Prototype**: Builders often construct objects step by step, while Prototype fully initializes
    an instance to be cloned or copied.

#### Common Criticisms

1. **Complexity for Simple Cases**: It can be considered overkill for simpler objects, where a
   builder isn't strictly necessary.
2. **Mutable Builder State**: The Builder itself is often mutable.

#### Implementing the Pattern

1. **Create the Builder Interface**: Define the steps needed to construct the product.
2. **Implement Concrete Builders**: Provide implementation for the building steps defined in the
   builder interface.
3. **Define the Product**: Create the complex object that is being built.
4. **Create a Director (Optional)**: Define a class to encapsulate the logic for constructing the
   object.

#### Example in Java

```java
// Product
class Car {
    private final String engine;
    private final int wheels;

    Car(String engine, int wheels) {
        this.engine = engine;
        this.wheels = wheels;
    }

    // getters and toString
}

// Builder Interface
interface CarBuilder {
    CarBuilder setEngine(String engine);
    CarBuilder setWheels(int wheels);
    Car build();
}

// Concrete Builder
class ConcreteCarBuilder implements CarBuilder {
    private String engine;
    private int wheels;

    public CarBuilder setEngine(String engine) {
        this.engine = engine;
        return this;
    }

    public CarBuilder setWheels(int wheels) {
        this.wheels = wheels;
        return this;
    }

    public Car build() {
        return new Car(engine, wheels);
    }
}

// Usage
public class BuilderExample {
    public static void main(String[] args) {
        CarBuilder builder = new ConcreteCarBuilder();
        Car car = builder.setEngine("V8").setWheels(4).build();
        System.out.println(car);
    }
}
```

In this Java example, `ConcreteCarBuilder` implements the `CarBuilder` interface, allowing for the
step-by-step construction of a `Car` object. The builder methods `setEngine` and `setWheels` are
used to configure the car, and `build` finalizes the construction, returning the completed `Car`
object. This pattern is especially useful when the object to be created has several parameters, some
of which may be optional.

### Prototype Pattern

The Prototype Pattern is a creational design pattern used in software development. Let's delve into
the details of this pattern, addressing your specific questions.

#### What is the Prototype Pattern?

The Prototype Pattern involves creating new objects by copying an existing object, known as the
prototype. This pattern is used when the creation of an object is more convenient or more efficient
through cloning than through traditional methods.

#### Purpose of the Design Pattern

The purpose of the Prototype Pattern is to:

-   Allow the cloning of objects without coupling to their specific classes.
-   Reduce the need for creating subclasses just to create diverse objects.

#### Software Principles Applied

1. **Encapsulation**: Encapsulates the knowledge of which classes to create.
2. **Open/Closed Principle**: New concrete classes can be introduced by cloning pre-existing classes
   without modifying the code.

#### Helpful Uses

1. **Avoiding Costly Creation**: When the cost of creating an object is more expensive (in terms of
   resources and time) than cloning.
2. **Preserving Existing State**: Useful in scenarios where an object is in a desirable state that
   needs to be duplicated.

#### Possible Drawbacks

1. **Complexity in Cloning**: Complex objects with circular references or complex relations might be
   difficult to clone.
2. **Hidden Side Effects**: Cloning can lead to issues if not all the object's fields, including
   private ones, are correctly copied.

#### Basic Structure

1. **Prototype**: An interface that declares the cloning method.
2. **Concrete Prototype**: Implements the cloning method.
3. **Client**: Creates a new object by asking a prototype to clone itself.

#### Possible Variations

1. **Deep vs Shallow Copy**: Depending on the requirement, either a deep copy (where all objects are
   duplicated) or a shallow copy (where references are copied) can be used.
2. **Registry of Prototypes**: A common variation includes a registry (or factory) that maintains a
   set of prototypes from which to clone.

#### Relation to Other Design Patterns

-   **Factory Method**: Prototype can use a factory method as a registry for creating objects.
-   **Composite and Decorator Patterns**: Can be used in conjunction with Prototype to copy complex
    structures.

#### Common Criticisms

1. **Complicated Cloning Logic**: The logic for cloning can become complicated, especially with deep
   copy cloning.
2. **Ambiguity**: It's not always clear about what is being cloned, especially when dealing with
   complex object graphs.

#### Implementing the Pattern

1. **Define the Prototype Interface**: This interface includes a method for cloning the object.
2. **Implement the Concrete Prototype**: Classes that implement the prototype interface and handle
   cloning of objects.
3. **Clone the Prototype**: The client, instead of creating objects directly, asks the prototype to
   clone itself.

#### Example in Java

```java
// Prototype
interface Prototype {
    Prototype clone();
}

// Concrete Prototype
class ConcretePrototype implements Prototype {
    private String field;

    ConcretePrototype(String field) {
        this.field = field;
    }

    // Implement the clone method
    public Prototype clone() {
        return new ConcretePrototype(this.field);
    }

    @Override
    public String toString() {
        return "Field: " + field;
    }
}

// Client code
public class PrototypeExample {
    public static void main(String[] args) {
        Prototype prototype = new ConcretePrototype("example");
        Prototype clone = prototype.clone();

        System.out.println(prototype);
        System.out.println(clone);
    }
}
```

In this Java example, the `ConcretePrototype` class implements the `Prototype` interface. The
`clone()` method creates a new `ConcretePrototype` instance by copying the existing object's field
value. The client can create new objects by cloning this prototype, reducing the need for the
subclassing and simplifying object creation in scenarios where objects are similar or require
extensive resources to create.

## Structural Patterns

### Adapter Pattern

The Adapter Pattern is a structural design pattern that allows objects with incompatible interfaces
to collaborate. Let's discuss this pattern in detail based on your questions.

#### What is the Adapter Pattern?

The Adapter Pattern acts as a bridge between two incompatible interfaces. This type of design
pattern comes under structural pattern as it combines the capability of two independent interfaces.

#### Purpose of the Design Pattern

The purpose of the Adapter Pattern is to enable communication between two existing classes that
otherwise couldn't work together due to incompatible interfaces. It's about creating an intermediary
that translates calls between the two interfaces.

#### Software Principles Applied

1. **Single Responsibility Principle**: Adapters handle the work of adapting one interface to
   another.
2. **Open/Closed Principle**: You can introduce new types of adapters into the program without
   breaking the existing client code.

#### Helpful Uses

1. **Integration of New Components**: Useful when integrating new components into existing
   infrastructure with incompatible interfaces.
2. **Legacy Code Integration**: Helps in making new code work with legacy code without modifying the
   existing code.

#### Possible Drawbacks

1. **Increased Complexity**: Can add complexity to the code by introducing additional layers.
2. **Performance Overhead**: The additional abstraction can sometimes lead to performance issues.

#### Basic Structure

1. **Target**: The domain-specific interface used by the client.
2. **Adapter**: Adapts the interface of the Adaptee to the Target interface.
3. **Adaptee**: The existing interface that needs adapting.
4. **Client**: Collaborates with objects conforming to the Target interface.

#### Possible Variations

1. **Object Adapter Pattern**: Uses composition to adapt the Adaptee interface.
2. **Class Adapter Pattern**: Uses multiple inheritance (not available in Java) to adapt one
   interface to another.

#### Relation to Other Design Patterns

-   **Bridge**: Often confused with Bridge pattern, but Bridge is more about separating an interface
    from its implementation.
-   **Decorator**: Adapters can use decorators to add new behavior while adapting interfaces.

#### Common Criticisms

1. **Not a Full-Fledged Solution**: Viewed as a patch rather than a complete solution in a
   well-designed system.
2. **Potentially Misleading**: Can make the code harder to understand due to indirect levels of
   abstraction.

#### Implementing the Pattern

1. **Identify the Target Interface**: This is what the client expects to work with.
2. **Identify the Adaptee**: The existing class that needs adapting.
3. **Create an Adapter Class**: This class implements the Target interface and contains a reference
   to an Adaptee object.
4. **Implement the Interface**: The Adapter class translates the interface of the Target into a form
   the Adaptee understands.

#### Example in Java

```java
// Target Interface
interface MediaPlayer {
    void play(String audioType, String fileName);
}

// Adaptee
class AdvancedMediaPlayer {
    void playVlc(String fileName) {
        System.out.println("Playing vlc file. Name: " + fileName);
    }
    void playMp4(String fileName) {
        System.out.println("Playing mp4 file. Name: " + fileName);
    }
}

// Adapter
class MediaAdapter implements MediaPlayer {
    AdvancedMediaPlayer advancedMusicPlayer;

    MediaAdapter(String audioType) {
        advancedMusicPlayer = new AdvancedMediaPlayer();
    }

    public void play(String audioType, String fileName) {
        if(audioType.equalsIgnoreCase("vlc")){
            advancedMusicPlayer.playVlc(fileName);
        }
        else if(audioType.equalsIgnoreCase("mp4")){
            advancedMusicPlayer.playMp4(fileName);
        }
    }
}

// Client
class AudioPlayer implements MediaPlayer {
    MediaAdapter mediaAdapter;

    public void play(String audioType, String fileName) {
        // Inbuilt support to play mp3 music files
        if(audioType.equalsIgnoreCase("mp3")){
            System.out.println("Playing mp3 file. Name: " + fileName);
        }
        // MediaAdapter is providing support to play other file formats
        else if(audioType.equalsIgnoreCase("vlc") || audioType.equalsIgnoreCase("mp4")){
            mediaAdapter = new MediaAdapter(audioType);
            mediaAdapter.play(audioType, fileName);
        }
        else{
            System.out.println("Invalid media. " + audioType + " format not supported");
        }
    }
}

// Usage
public class AdapterPatternDemo {
    public static void main(String[] args) {
        AudioPlayer audioPlayer = new AudioPlayer();
        audioPlayer.play("mp3", "beyond_the_horizon.mp3");
        audioPlayer.play("mp4", "alone.mp4");
        audioPlayer.play("vlc", "far_far_away.vlc");
        audioPlayer.play("avi", "mind_me.avi");
    }
}
```

In this Java example, the `AudioPlayer` (client) can play MP3 files by default. The `MediaAdapter`
(adapter) is used to play other types of audio formats, and it delegates the playing of those
formats to the `AdvancedMediaPlayer` (adaptee). This way, the AudioPlayer works with the MediaPlayer
interface to play various formats, using the MediaAdapter for formats other than MP3.

### Bridge Pattern

The Bridge Pattern is a structural design pattern that aims to decouple an abstraction from its
implementation so that the two can vary independently. Let's explore this pattern in more detail.

#### What is the Bridge Pattern?

The Bridge Pattern is a structural design pattern that separates the abstraction from its
implementation. It involves an interface which acts as a bridge, making the functionality of
concrete classes independent from interface implementer classes.

#### Purpose of the Design Pattern

The purpose of the Bridge Pattern is to:

-   Separate an abstraction from its implementation so that both can be modified independently.
-   Promote loose coupling between the abstraction and its implementation.

#### Software Principles Applied

1. **Decoupling**: It helps in decoupling the client code from the implementation.
2. **Open/Closed Principle**: The abstraction and implementation can be extended independently.
3. **Composition over Inheritance**: It favors composition over inheritance, leading to more
   flexible and maintainable code.

#### Helpful Uses

1. **Platform Independence**: Useful in cases where code should run on multiple platforms.
2. **Changing Implementation at Runtime**: When the implementation can be selected or switched at
   runtime.
3. **Preventing a Cartesian Product of classes**: Avoids the explosion of classes that would result
   from multiple, orthogonal abstractions.

#### Possible Drawbacks

1. **Complexity**: Can add complexity to the code, making it harder to understand.
2. **Overhead**: Introduces an extra layer of abstraction which can lead to overhead.

#### Basic Structure

1. **Abstraction**: Defines the abstraction's interface and maintains a reference to an object of
   the Implementor type.
2. **Refined Abstraction**: Extends the interface defined by Abstraction.
3. **Implementor**: Defines the interface for implementation classes.
4. **Concrete Implementor**: Implements the Implementor interface.

#### Possible Variations

1. **Multi-level Abstraction**: The pattern can be extended to multiple levels of abstraction, if
   needed.
2. **Different Implementations**: Implementations can use different approaches like inheritance,
   composition, or others.

#### Relation to Other Design Patterns

-   **Adapter vs Bridge**: Adapter is meant to make unrelated classes work together, while Bridge is
    designed up-front to let the abstraction and implementation vary independently.
-   **Strategy Pattern**: Similar to Bridge in that it promotes delegation. However, Strategy is
    about choosing an algorithm, while Bridge is about separating layers.

#### Common Criticisms

1. **Overuse for Simple Systems**: Can be overkill for systems that don't need loose coupling or
   don't have multiple varying aspects.
2. **Initial Complexity**: Introduces complexity in initial stages of design and might not be
   justified until the system needs to scale.

#### Implementing the Pattern

1. **Identify Abstraction and Implementation**: Separate out the abstraction and its implementation
   into different class hierarchies.
2. **Create the Abstraction Interface**: This should include a reference to the Implementor.
3. **Create Refined Abstractions**: If needed, extend the base abstraction to provide extra
   variants.
4. **Create the Implementor Interface**: This should declare methods that resemble those of the
   abstraction but can be implemented differently.
5. **Implement the Concrete Implementors**: Create specific classes that implement the Implementor
   interface.

#### Example in Java

```java
// Implementor
interface Color {
    void applyColor();
}

// Concrete Implementor
class RedColor implements Color {
    public void applyColor() {
        System.out.println("Red.");
    }
}

class BlueColor implements Color {
    public void applyColor() {
        System.out.println("Blue.");
    }
}

// Abstraction
abstract class Shape {
    protected Color color;

    public Shape(Color color) {
        this.color = color;
    }

    abstract public void applyColor();
}

// Refined Abstraction
class Triangle extends Shape {
    public Triangle(Color color) {
        super(color);
    }

    public void applyColor() {
        System.out.print("Triangle filled with color ");
        color.applyColor();
    }
}

class Square extends Shape {
    public Square(Color color) {
        super(color);
    }

    public void applyColor() {
        System.out.print("Square filled with color ");
        color.applyColor();
    }
}

// Client code
public class BridgePatternDemo {
    public static void main(String[] args) {
        Shape triangle = new Triangle(new RedColor());
        triangle.applyColor();

        Shape square = new Square(new BlueColor());
        square.applyColor();
    }
}
```

In this Java example, `Shape` is the abstraction, and `Color` is the implementor. The `Shape` class
doesn’t implement the color functionality but instead delegates it to the `Color` implementor. This
way, the abstraction (shape) and implementation (color) can be varied independently. For instance,
new shapes or colors can be added without affecting each other.

### Composite Pattern

The Composite Pattern is a structural design pattern that allows you to compose objects into tree
structures to represent part-whole hierarchies. Let's explore this pattern in detail based on your
questions.

#### What is the Composite Pattern?

The Composite Pattern is designed to treat individual objects and compositions of objects uniformly.
It lets clients treat individual objects and compositions of objects the same way.

#### Purpose of the Design Pattern

The purpose of the Composite Pattern is to:

-   Organize objects into tree structures to represent part-whole hierarchies.
-   Enable clients to treat individual objects and compositions of those objects uniformly.

#### Software Principles Applied

1. **Single Responsibility Principle**: Separates the responsibility of managing the hierarchy from
   the business logic of the individual objects.
2. **Open/Closed Principle**: New types of elements can be added without changing the existing code.

#### Helpful Uses

1. **Graphic Rendering Engines**: For rendering graphics in a hierarchical structure, like graphical
   user interfaces.
2. **File System Structures**: Representing and managing file systems which are inherently
   hierarchical.

#### Possible Drawbacks

1. **Overgeneralization**: Not all objects can feasibly be represented in a tree structure.
2. **Design Complexity**: Can make the design more complex by requiring all components to follow a
   similar interface.

#### Basic Structure

1. **Component**: An interface or abstract class defining the common operations for both composite
   and leaf nodes.
2. **Leaf**: Represents leaf objects in the composition. A leaf has no children.
3. **Composite**: A class that has child components (leaf or composite) and implements the component
   interface.

#### Possible Variations

1. **Transparent vs. Safe Composite**: Transparent allows clients to treat leaf and composite
   objects exactly the same. Safe composite differentiates methods for managing children.
2. **Dynamic Composition**: Components can be added/removed dynamically at runtime.

#### Relation to Other Design Patterns

-   **Decorator**: While Composite assembles objects into tree structures, Decorator adds new
    functionalities to objects.
-   **Chain of Responsibility**: Can be used with Composite to spread or handle requests over a tree
    structure.

#### Common Criticisms

1. **Overhead**: Might introduce overhead, especially for operations where leaf and composite
   objects need to be treated differently.
2. **Complexity for Simple Scenarios**: Can be too complex for simple scenarios.

#### Implementing the Pattern

1. **Define Component Interface**: Outline methods common to both simple and complex elements.
2. **Create Leaf Classes**: Implement component interface without adding child management behavior.
3. **Create Composite Classes**: Implement component interface and add storage and management of
   child components.
4. **Client Interaction**: Use component interface to interact with objects in the composite
   structure.

#### Example in Java

```java
// Component
interface Graphic {
    void draw();
}

// Leaf
class Circle implements Graphic {
    public void draw() {
        System.out.println("Drawing a circle");
    }
}

// Leaf
class Square implements Graphic {
    public void draw() {
        System.out.println("Drawing a square");
    }
}

// Composite
class CompositeGraphic implements Graphic {
    private List<Graphic> childGraphics = new ArrayList<>();

    public void add(Graphic graphic) {
        childGraphics.add(graphic);
    }

    public void draw() {
        for (Graphic graphic : childGraphics) {
            graphic.draw();
        }
    }
}

// Client code
public class CompositePatternDemo {
    public static void main(String[] args) {
        Circle circle = new Circle();
        Square square = new Square();

        CompositeGraphic graphic = new CompositeGraphic();
        graphic.add(circle);
        graphic.add(square);

        graphic.draw();
    }
}
```

In this Java example, both `Circle` and `Square` are leaf nodes, and `CompositeGraphic` is a
composite object that can contain any number of `Graphic` objects, including other
`CompositeGraphic` objects. This allows for building a nested structure of graphics that can be
treated uniformly by the client.

### Decorator Pattern

The Decorator Pattern is a structural design pattern that allows for the dynamic addition of
behaviors to individual objects without affecting the behavior of other objects from the same class.
Let's explore this pattern in detail.

#### What is the Decorator Pattern?

The Decorator Pattern is used to extend or alter the functionality of objects at runtime by wrapping
them in an object of a decorator class. This provides a flexible alternative to subclassing for
extending functionality.

#### Purpose of the Design Pattern

The purpose of the Decorator Pattern is to:

-   Add responsibilities to individual objects dynamically and transparently.
-   Offer a flexible alternative to subclassing for extending functionality.

#### Software Principles Applied

1. **Open/Closed Principle**: Objects can be extended with new functionality without modifying their
   existing code.
2. **Single Responsibility Principle**: Functionality can be divided into different classes with
   specific behaviors.

#### Helpful Uses

1. **User Interface Components**: Adding behaviors to UI components like borders or behaviors.
2. **Adding Responsibilities**: Used in scenarios where responsibilities and behaviors need to be
   added dynamically to objects.

#### Possible Drawbacks

1. **Complexity**: Can introduce a lot of small classes, which can complicate the design and
   increase complexity.
2. **Difficult Debugging**: Debugging can be harder due to multiple layers of wrapping.

#### Basic Structure

1. **Component**: Defines the interface for objects that can have responsibilities added to them
   dynamically.
2. **Concrete Component**: Defines an object to which additional responsibilities can be attached.
3. **Decorator**: Maintains a reference to a Component object and defines an interface that conforms
   to Component's interface.
4. **Concrete Decorators**: Extend the functionality of the Component by adding state or adding
   behavior.

#### Possible Variations

1. **Decorator with Additional Methods**: Decorators can add new methods in addition to implementing
   the existing ones.
2. **Multiple Decorators**: Multiple decorators can be stacked to add multiple layers of behavior.

#### Relation to Other Design Patterns

-   **Composite Pattern**: Decorator is often used with Composite. While Composite treats objects
    uniformly, Decorator adds responsibilities to individual objects.
-   **Strategy Pattern**: Both can be used to change the behavior of an object, but Strategy changes
    the entire algorithm, while Decorator adds responsibilities.

#### Common Criticisms

1. **Overuse**: Overusing Decorator can lead to complex code that is difficult to maintain.
2. **Performance Concerns**: Can introduce overhead, particularly with a large number of decorators.

#### Implementing the Pattern

1. **Define the Component Interface**: This outlines the standard functionality.
2. **Create Concrete Components**: Implement the component interface.
3. **Create an Abstract Decorator Class**: This class should implement the component interface and
   have a reference to a component.
4. **Create Concrete Decorator Classes**: Extend the functionality of components by implementing
   additional behavior.

#### Example in Java

```java
// Component
interface Coffee {
    String getDescription();
    double cost();
}

// Concrete Component
class SimpleCoffee implements Coffee {
    public String getDescription() {
        return "Simple Coffee";
    }

    public double cost() {
        return 2.0;
    }
}

// Decorator
abstract class CoffeeDecorator implements Coffee {
    protected Coffee decoratedCoffee;

    public CoffeeDecorator(Coffee coffee) {
        this.decoratedCoffee = coffee;
    }

    public String getDescription() {
        return decoratedCoffee.getDescription();
    }

    public double cost() {
        return decoratedCoffee.cost();
    }
}

// Concrete Decorators
class MilkDecorator extends CoffeeDecorator {
    public MilkDecorator(Coffee coffee) {
        super(coffee);
    }

    @Override
    public String getDescription() {
        return decoratedCoffee.getDescription() + ", Milk";
    }

    @Override
    public double cost() {
        return decoratedCoffee.cost() + 0.5;
    }
}

class SugarDecorator extends CoffeeDecorator {
    public SugarDecorator(Coffee coffee) {
        super(coffee);
    }

    @Override
    public String getDescription() {
        return decoratedCoffee.getDescription() + ", Sugar";
    }

    @Override
    public double cost() {
        return decoratedCoffee.cost() + 0.2;
    }
}

// Client code
public class DecoratorPatternDemo {
    public static void main(String[] args) {
        Coffee coffee = new SimpleCoffee();
        System.out.println(coffee.getDescription() + " Cost: $" + coffee.cost());

        Coffee milkCoffee = new MilkDecorator(coffee);
        System.out.println(milkCoffee.getDescription() + " Cost: $" + milkCoffee.cost());

        Coffee sugarMilkCoffee = new SugarDecorator(milkCoffee);
        System.out.println(sugarMilkCoffee.getDescription() + " Cost: $" + sugarMilkCoffee.cost());
    }
}
```

In this Java example, `SimpleCoffee` is the concrete component, and `MilkDecorator` and
`SugarDecorator` are concrete decorators that add additional behavior (ingredients and cost) to the
coffee. This implementation showcases how the Decorator Pattern can be used to add responsibilities
to objects dynamically.

### Facade Pattern

The Facade Pattern is a structural design pattern that provides a simplified interface to a complex
system of classes, a library, or a framework. Let's explore this pattern in detail.

#### What is the Facade Pattern?

The Facade Pattern provides a high-level interface that makes a complex subsystem easier to use. It
doesn’t encapsulate the subsystem but provides a simplified interface to it.

#### Purpose of the Design Pattern

The purpose of the Facade Pattern is to:

-   Provide a unified and simplified interface to a set of interfaces in a subsystem, making the
    subsystem easier to use.
-   Reduce dependencies of outside code on the inner workings of a subsystem.

#### Software Principles Applied

1. **Principle of Least Knowledge (Law of Demeter)**: Facade promotes loose coupling by limiting the
   knowledge of the inner workings of its subsystems.
2. **Single Responsibility Principle**: It separates the complexity of a subsystem by providing a
   simple interface.

#### Helpful Uses

1. **Simplifying Complex Systems**: Useful when working with complex libraries or APIs.
2. **Layering**: Creating distinct layers in applications (e.g., a presentation layer that interacts
   with a more complex business layer).

#### Possible Drawbacks

1. **Limited Functionality**: The facade might not expose all functionality of the complex
   subsystem, leading to restrictions.
2. **Risk of Becoming a God Object**: Might evolve into a class with too many responsibilities if
   not implemented carefully.

#### Basic Structure

1. **Facade**: A single class that provides a simplified interface to a complex subsystem.
2. **Subsystems**: The complex system or subsystems the facade provides a simplified interface for.

#### Possible Variations

1. **Multiple Facades**: A system can have multiple facades for different client needs.
2. **Facade as Singleton**: The facade can be implemented as a Singleton if only one facade instance
   is needed.

#### Relation to Other Design Patterns

-   **Abstract Factory**: Can be used with Facade to provide a simple interface for creating complex
    objects.
-   **Adapter vs Facade**: Adapter changes the interface of one or more classes, while Facade
    provides a simple interface to a complex subsystem.

#### Common Criticisms

1. **Not a Full Encapsulation**: It doesn't encapsulate the subsystems but just provides a
   simplified interface.
2. **Possibility of Over-Simplification**: May oversimplify the system, making it difficult to
   leverage all its functionalities.

#### Implementing the Pattern

1. **Identify the Complex Subsystem**: Determine the complex parts of the system that need
   simplification.
2. **Create a Facade Interface**: Design an interface that simplifies and unifies the complex
   subsystem operations.
3. **Implement the Facade**: Implement the methods of the facade interface to delegate client calls
   to the appropriate subsystem operations.
4. **Client Interaction**: Use the facade to interact with the complex subsystems.

#### Example in Java

```java
// Complex subsystem parts
class SubsystemA {
    void operationA() {
        System.out.println("Subsystem A operation");
    }
}

class SubsystemB {
    void operationB() {
        System.out.println("Subsystem B operation");
    }
}

// Facade
class Facade {
    private SubsystemA subsystemA;
    private SubsystemB subsystemB;

    Facade() {
        subsystemA = new SubsystemA();
        subsystemB = new SubsystemB();
    }

    void operation() {
        subsystemA.operationA();
        subsystemB.operationB();
    }
}

// Client code
public class FacadePatternDemo {
    public static void main(String[] args) {
        Facade facade = new Facade();
        facade.operation();
    }
}
```

In this Java example, the `Facade` class provides a simple interface (`operation()`) to the complex
operations of `SubsystemA` and `SubsystemB`. The client interacts with the subsystems through the
facade, which simplifies the usage of the subsystems by hiding their complexities.

### Flyweight Pattern

The Flyweight Pattern is a structural design pattern focused on efficient data sharing through
fine-grained objects. Let's explore this pattern in detail.

#### What is the Flyweight Pattern?

The Flyweight Pattern is used to minimize memory usage or computational expenses by sharing as much
data as possible with similar objects. It's about sharing state among a large number of fine-grained
objects for efficiency.

#### Purpose of the Design Pattern

The purpose of the Flyweight Pattern is to:

-   Reduce the memory footprint of large numbers of similar objects.
-   Share common parts of state among multiple objects instead of keeping all the data in each
    object.

#### Software Principles Applied

1. **Single Responsibility Principle**: Flyweights are focused solely on intrinsic state, separating
   extrinsic state to be managed elsewhere.
2. **Principle of Least Knowledge**: Objects minimize their knowledge about other parts of the
   system, focusing only on their intrinsic state.

#### Helpful Uses

1. **Graphical Representations**: Useful in graphic-intensive applications like gaming where
   numerous objects share similar properties.
2. **Text Formatting**: Managing formatting data of characters in a text editor.

#### Possible Drawbacks

1. **Complexity**: The pattern can make the code more complex by introducing several additional
   classes.
2. **Premature Optimization**: It may lead to premature optimization if used in scenarios that don't
   necessarily require such fine-grained objects.

#### Basic Structure

1. **Flyweight**: An interface through which flyweights can receive and act on extrinsic state.
2. **Concrete Flyweight**: Implements the Flyweight interface and stores intrinsic state. The same
   instance can be shared among contexts.
3. **Flyweight Factory**: Creates and manages flyweight objects. It ensures that flyweights are
   shared correctly.

#### Possible Variations

1. **Unshared Concrete Flyweight**: Not all flyweight objects need to be shared, especially if their
   state is frequently changing.
2. **Composite Flyweight**: A flyweight that is composed of other flyweights.

#### Relation to Other Design Patterns

-   **Composite Pattern**: Flyweight can be used with Composite to represent hierarchical structures
    of shared flyweights.
-   **Singleton**: The Flyweight Factory is often implemented as a Singleton.

#### Common Criticisms

1. **Overhead in Shared State Management**: The pattern can introduce overhead in managing shared
   and unshared states.
2. **Complexity vs Benefit**: It might not offer a significant benefit in scenarios where the number
   of objects isn't actually high enough to justify the complexity.

#### Implementing the Pattern

1. **Identify Intrinsic and Extrinsic State**: Separate the state of objects into intrinsic (shared)
   and extrinsic (unique to each object) states.
2. **Create Flyweight Interface**: This defines methods that pass extrinsic state.
3. **Implement Concrete Flyweight Classes**: These classes include an implementation of the
   flyweight interface for shared state.
4. **Create Flyweight Factory**: To manage flyweight objects and ensure they are shared properly.

#### Example in Java

```java
// Flyweight
interface CoffeeOrder {
    void serveCoffee(CoffeeOrderContext context);
}

// Concrete Flyweight
class CoffeeFlavor implements CoffeeOrder {
    private final String flavor;

    CoffeeFlavor(String newFlavor) {
        this.flavor = newFlavor;
    }

    public void serveCoffee(CoffeeOrderContext context) {
        System.out.println("Serving Coffee flavor " + flavor + " to table number " + context.getTable());
    }
}

// Context
class CoffeeOrderContext {
    private final int tableNumber;

    CoffeeOrderContext(int tableNumber) {
        this.tableNumber = tableNumber;
    }

    int getTable() {
        return this.tableNumber;
    }
}

// Flyweight Factory
class CoffeeFlavorFactory {
    private final Map<String, CoffeeFlavor> flavors = new HashMap<>();

    CoffeeFlavor getCoffeeFlavor(String flavorName) {
        CoffeeFlavor flavor = flavors.get(flavorName);
        if (flavor == null) {
            flavor = new CoffeeFlavor(flavorName);
            flavors.put(flavorName, flavor);
        }
        return flavor;
    }

    int getTotalCoffeeFlavorsMade() {
        return flavors.size();
    }
}

// Client code
public class FlyweightPatternDemo {
    private final CoffeeFlavorFactory flavorFactory = new CoffeeFlavorFactory();

    void takeOrders(String flavorIn, int table) {
        CoffeeFlavor flavor = flavorFactory.getCoffeeFlavor(flavorIn);
        flavor.serveCoffee(new CoffeeOrderContext(table));
    }

    public static void main(String[] args) {
        FlyweightPatternDemo shop = new FlyweightPatternDemo();

        shop.takeOrders("Cappuccino", 2);
        shop.takeOrders("Frappe", 1);
        shop.takeOrders("Espresso", 1);
        shop.takeOrders("Frappe", 897);
        shop.takeOrders("Cappuccino", 97);
        shop.takeOrders("Espresso",

3);
        shop.takeOrders("Frappe", 3);
        shop.takeOrders("Espresso", 3);
        shop.takeOrders("Cappuccino", 3);
        shop.takeOrders("Espresso", 96);
        shop.takeOrders("Frappe", 552);
        shop.takeOrders("Cappuccino", 121);
        shop.takeOrders("Espresso", 121);

        System.out.println("Total CoffeeFlavor objects made: " + shop.flavorFactory.getTotalCoffeeFlavorsMade());
    }
}
```

In this Java example, `CoffeeFlavor` represents a Flyweight that stores intrinsic state (flavor),
and `CoffeeOrderContext` represents extrinsic state (table number). The `CoffeeFlavorFactory`
manages the creation and sharing of `CoffeeFlavor` objects. This implementation demonstrates how the
Flyweight Pattern can effectively manage similar objects with shared data to optimize memory and
resource usage.

### Proxy Pattern

The Proxy Pattern is a structural design pattern that provides a surrogate or placeholder for
another object to control access to it. Let's explore this pattern in detail.

#### What is the Proxy Pattern?

The Proxy Pattern involves using a separate object (a proxy) to represent and control access to
another object. This pattern creates a proxy object that serves as an intermediary for the actual
object and can control access to it.

#### Purpose of the Design Pattern

The purpose of the Proxy Pattern is to:

-   Control access to an object.
-   Delay the full cost of creating and utilizing the object until it's actually needed.
-   Provide a surrogate or placeholder for an object to control its creation, lifecycle, or access.

#### Software Principles Applied

1. **Single Responsibility Principle**: Proxies take on one responsibility (such as access control,
   lazy initialization, logging, etc.), and hence, adhere to this principle.
2. **Open/Closed Principle**: Proxies allow for new functionalities to be introduced without
   changing the object's code.

#### Helpful Uses

1. **Lazy Initialization**: Delaying the creation of a large or resource-intensive object until it's
   actually needed.
2. **Access Control**: Controlling the access to an object, for example, in the case of sensitive
   information.
3. **Logging and Monitoring**: Keeping track of operations and method calls on an object.

#### Possible Drawbacks

1. **Performance Issues**: Can introduce latency, especially if the proxy does significant extra
   work.
2. **Complexity**: Increases the complexity of code, sometimes making it difficult to maintain.

#### Basic Structure

1. **Subject**: An interface common to both the real object and the proxy, defining operations that
   can be performed on the real object.
2. **Real Subject**: The real object that the proxy represents.
3. **Proxy**: Maintains a reference to the real subject, controls access to it, and may be
   responsible for its creation and deletion.

#### Possible Variations

1. **Virtual Proxy**: Delays the creation and initialization of expensive objects.
2. **Protection Proxy**: Controls access to the original object, useful for different access rights.
3. **Remote Proxy**: Represents an object in a different space (e.g., network).

#### Relation to Other Design Patterns

-   **Decorator Pattern**: While both add functionality, Decorator adds functionality to an object,
    whereas Proxy controls access to it.
-   **Adapter vs Proxy**: Adapter provides a different interface to its subject, Proxy provides the
    same interface.

#### Common Criticisms

1. **Overuse and Misuse**: Sometimes used inappropriately, adding unnecessary layers of abstraction.
2. **Complexity vs Benefits**: The benefits of using a proxy must be weighed against the added
   complexity.

#### Implementing the Pattern

1. **Define the Subject Interface**: This interface should declare common methods for both the real
   subject and the proxy.
2. **Implement the Real Subject**: Create the real object that the proxy is supposed to represent.
3. **Create the Proxy Class**: Implement the same interface and add a reference field to the real
   subject object. The proxy controls access to the real subject.

#### Example in Java

```java
// Subject Interface
interface Image {
    void display();
}

// Real Subject
class RealImage implements Image {
    private String fileName;

    public RealImage(String fileName) {
        this.fileName = fileName;
        loadFromDisk(fileName);
    }

    private void loadFromDisk(String fileName) {
        System.out.println("Loading " + fileName);
    }

    public void display() {
        System.out.println("Displaying " + fileName);
    }
}

// Proxy
class ProxyImage implements Image {
    private RealImage realImage;
    private String fileName;

    public ProxyImage(String fileName) {
        this.fileName = fileName;
    }

    public void display() {
        if (realImage == null) {
            realImage = new RealImage(fileName);
        }
        realImage.display();
    }
}

// Client code
public class ProxyPatternDemo {
    public static void main(String[] args) {
        Image image = new ProxyImage("test_image.jpg");

        // Image will be loaded from disk
        image.display();
        // Image will not be loaded from disk
        image.display();
    }
}
```

In this Java example, `ProxyImage` serves as a proxy for `RealImage`. It controls access to
`RealImage` and handles lazy loading. When `display()` is called for the first time, `ProxyImage`
will create a `RealImage` object and load the image. Subsequent calls to `display()` will just
delegate to the `RealImage` object without reloading the image. This pattern is particularly useful
for resources-intensive operations such as loading an image from disk.

## Behavioral Patterns

### Chain of Responsibility Pattern

The Chain of Responsibility Pattern is a behavioral design pattern that passes requests along a
chain of handlers. Let's delve into the details of this pattern.

#### What is the Chain of Responsibility Pattern?

The Chain of Responsibility Pattern allows an object to send a command or request without needing to
know which object will handle the command. Requests are passed along a chain of handlers until one
of them handles it.

#### Purpose of the Design Pattern

The purpose of the Chain of Responsibility Pattern is to:

-   Decouple the sender and receiver of a request.
-   Allow multiple objects an opportunity to handle the request.

#### Software Principles Applied

1. **Single Responsibility Principle**: Each handler in the chain handles only specific requests,
   following the principle.
2. **Open/Closed Principle**: It's easy to add new handlers to the system without modifying the
   existing code.

#### Helpful Uses

1. **Event Handling Systems**: In GUI frameworks where an event can be handled at multiple stages.
2. **Processing Pipelines**: Such as in logging frameworks where a message might be processed at
   multiple levels.

#### Possible Drawbacks

1. **Performance**: Can impact performance as the request might go through multiple handlers.
2. **Debugging Difficulty**: Tracing through the chain can be difficult, especially with complex
   chains.

#### Basic Structure

1. **Handler Interface**: An interface for handling requests and optionally implementing the
   successor chain.
2. **Concrete Handlers**: Implement the handler interface and handle the request or pass it to the
   next handler in the chain.
3. **Client**: Initiates the request to a chain of handler objects.

#### Possible Variations

1. **Mutable Chains**: The chain of responsibility can be modified dynamically at runtime.
2. **Asynchronous Processing**: Handlers can process the requests asynchronously.

#### Relation to Other Design Patterns

-   **Composite Pattern**: Handlers in Chain of Responsibility can be composed into a tree
    structure.
-   **Command Pattern**: Often used with Chain of Responsibility, where a command traverses a chain
    of handlers.

#### Common Criticisms

1. **Lack of Clarity**: It can be unclear which part of the chain will handle the request.
2. **Overhead**: Introduces additional overhead, especially if the chain is long or complex.

#### Implementing the Pattern

1. **Define Handler Interface**: Create an interface or abstract class defining how requests are
   handled.
2. **Implement Concrete Handlers**: Create classes that extend the handler interface and implement
   specific request handling.
3. **Link Handlers**: Chain the handlers together.
4. **Client Request Handling**: The client sends the request which travels along the chain until
   handled.

#### Example in Java

```java
// Handler Interface
abstract class Handler {
    protected Handler successor;

    public void setSuccessor(Handler successor) {
        this.successor = successor;
    }

    public abstract void handleRequest(Request request);
}

// Concrete Handlers
class ConcreteHandler1 extends Handler {
    public void handleRequest(Request request) {
        if (request.getType() == RequestType.TYPE1) {
            System.out.println("ConcreteHandler1 handling request of TYPE1");
        } else if (successor != null) {
            successor.handleRequest(request);
        }
    }
}

class ConcreteHandler2 extends Handler {
    public void handleRequest(Request request) {
        if (request.getType() == RequestType.TYPE2) {
            System.out.println("ConcreteHandler2 handling request of TYPE2");
        } else if (successor != null) {
            successor.handleRequest(request);
        }
    }
}

// Request Types
enum RequestType {
    TYPE1, TYPE2
}

class Request {
    private RequestType type;

    public Request(RequestType type) {
        this.type = type;
    }

    public RequestType getType() {
        return type;
    }
}

// Client code
public class ChainOfResponsibilityDemo {
    public static void main(String[] args) {
        Handler h1 = new ConcreteHandler1();
        Handler h2 = new ConcreteHandler2();

        h1.setSuccessor(h2);

        h1.handleRequest(new Request(RequestType.TYPE1));
        h1.handleRequest(new Request(RequestType.TYPE2));
    }
}
```

In this Java example, `ConcreteHandler1` and `ConcreteHandler2` are handlers that process requests
of specific types (`TYPE1` and `TYPE2`). If a handler cannot handle a request, it passes the request
along to its successor in the chain. This pattern is especially useful for creating processing
pipelines where a request needs to be processed by multiple handlers.

### Command Pattern

The Command Pattern is a behavioral design pattern that turns a request into a stand-alone object
that contains all information about the request. Let's explore this pattern in detail.

#### What is the Command Pattern?

The Command Pattern encapsulates a request as an object, thereby allowing for parameterization of
clients with queues, requests, and operations. It also allows for the support of undoable
operations.

#### Purpose of the Design Pattern

The purpose of the Command Pattern is to:

-   Decouple the object that invokes the operation from the one that knows how to perform it.
-   To turn a request into an object, which contains all the information about the request.

#### Software Principles Applied

1. **Single Responsibility Principle**: Command pattern separates concerns by isolating the command
   logic and the object that invokes the command.
2. **Open/Closed Principle**: New commands can be added without changing existing code.

#### Helpful Uses

1. **Parameterizing Objects**: Objects can be parameterized with commands.
2. **Queueing and Logging Operations**: Commands can be queued and logged as they are applied.
3. **Supporting Undo/Redo**: Commands can support undoing and redoing of operations.

#### Possible Drawbacks

1. **Complexity**: Can overcomplicate the application if simple operations are encapsulated in
   commands.
2. **Number of Classes**: Increases the number of classes for each individual command.

#### Basic Structure

1. **Command**: An interface with a method signature like `execute()` or `undo()`.
2. **Concrete Command**: Implements the Command interface and defines the binding between a Receiver
   and an action.
3. **Invoker**: Asks the command to carry out the request.
4. **Receiver**: Knows how to perform the operations associated with carrying out a request.
5. **Client**: Creates a ConcreteCommand object and sets its receiver.

#### Possible Variations

1. **Composite Command**: A command that is made up of multiple commands.
2. **Undoable Commands**: Commands that can undo their effects.

#### Relation to Other Design Patterns

-   **Memento Pattern**: Can be used to keep the state so that it can be restored by an undo
    command.
-   **Composite Pattern**: Can be used to implement Composite Commands.

#### Common Criticisms

1. **Overhead**: Introduces an extra layer of abstraction, which can be seen as an overhead for
   simple scenarios.
2. **Complexity**: The pattern can lead to a proliferation of classes and objects, increasing
   complexity.

#### Implementing the Pattern

1. **Define the Command Interface**: Create a command interface with an `execute()` method.
2. **Create Concrete Commands**: Implement the command interface for specific actions.
3. **Define the Receiver**: Create the class that will perform the actual action.
4. **Create the Invoker**: Design the invoker class that will use the command.
5. **Client Setup**: The client creates instances of Concrete Commands and sets their receiver.

#### Example in Java

```java
// Command
interface Command {
    void execute();
}

// Receiver
class Light {
    public void turnOn() {
        System.out.println("The light is on");
    }

    public void turnOff() {
        System.out.println("The light is off");
    }
}

// Concrete Commands
class TurnOnLightCommand implements Command {
    private Light light;

    public TurnOnLightCommand(Light light) {
        this.light = light;
    }

    public void execute() {
        light.turnOn();
    }
}

class TurnOffLightCommand implements Command {
    private Light light;

    public TurnOffLightCommand(Light light) {
        this.light = light;
    }

    public void execute() {
        light.turnOff();
    }
}

// Invoker
class RemoteControl {
    private Command command;

    public void setCommand(Command command) {
        this.command = command;
    }

    public void pressButton() {
        command.execute();
    }
}

// Client code
public class CommandPatternDemo {
    public static void main(String[] args) {
        Light light = new Light();
        Command turnOn = new TurnOnLightCommand(light);
        Command turnOff = new TurnOffLightCommand(light);

        RemoteControl remote = new RemoteControl();
        remote.setCommand(turnOn);
        remote.pressButton();
        remote.setCommand(turnOff);
        remote.pressButton();
    }
}
```

In this Java example, `Light` is the Receiver, `TurnOnLightCommand` and `TurnOffLightCommand` are
Concrete Commands, and `RemoteControl` is the Invoker. The client (in this case, the
`CommandPatternDemo` class) creates the commands and associates them with the receiver. The invoker
then executes these commands. This pattern allows the client to switch commands and receivers
dynamically.

### Interpreter Pattern

The Interpreter Pattern is a behavioral design pattern that defines a grammatical representation for
a language and provides an interpreter to deal with this grammar. Let's explore this pattern in
detail.

#### What is the Interpreter Pattern?

The Interpreter Pattern is used to define a representation of a language's grammar and provides an
interpreter that uses this representation to interpret sentences in the language.

#### Purpose of the Design Pattern

The purpose of the Interpreter Pattern is to:

-   Provide a way to evaluate language grammar or expression.
-   Allow for easy interpretation of a language or a grammar.

#### Software Principles Applied

1. **Open/Closed Principle**: New expressions can be added without changing the existing
   interpretive code.
2. **Single Responsibility Principle**: Each node in the expression tree handles its specific
   processing.

#### Helpful Uses

1. **Programming Language Interpreters and Compilers**: Useful in scenarios where the language can
   be represented as abstract syntax trees.
2. **Regular Expressions**: Implementing interpreters for regular expressions.

#### Possible Drawbacks

1. **Complexity**: Can become very complex for large grammars.
2. **Performance**: May not be as efficient as hard-coded expressions, especially for complex
   interpretations.

#### Basic Structure

1. **Abstract Expression**: Declares an interface for executing a particular operation.
2. **Terminal Expression**: Implements the interface for terminal symbols in the grammar.
3. **Nonterminal Expression**: One or more terminal expressions to represent sequence or choices in
   the grammar.
4. **Context**: Contains information global to the interpreter.
5. **Client**: Builds (or is given) the abstract syntax tree of the specific language and then
   invokes the interpret operation.

#### Possible Variations

1. **Abstract Syntax Tree**: Building and interpreting abstract syntax trees.
2. **Different Kinds of Expressions**: Adding new expressions without changing existing classes.

#### Relation to Other Design Patterns

-   **Composite Pattern**: Often used with the Interpreter pattern to build the abstract syntax
    trees.
-   **Flyweight**: Used for sharing terminal symbols within the interpreter's context.

#### Common Criticisms

1. **Scalability**: It can be cumbersome and impractical for large grammars.
2. **Complexity**: Implementing the pattern can become complex and difficult to maintain.

#### Implementing the Pattern

1. **Define the Grammar**: Define a simple grammar for the language.
2. **Create Abstract Expression Class**: An interface or abstract class to interpret operations.
3. **Implement Terminal Expressions**: Implement classes for each symbol of the grammar.
4. **Implement Nonterminal Expressions**: Implement classes for grammar rules that combine symbols.
5. **Create the Context Class**: Context information required during interpretation.
6. **Build the Abstract Syntax Tree**: The client builds the syntax tree representing a particular
   sentence in the language.
7. **Interpret**: The client invokes the interpretation operation.

#### Example in Java

```java
// Abstract Expression
interface Expression {
    boolean interpret(String context);
}

// Terminal Expression
class TerminalExpression implements Expression {
    private String data;

    TerminalExpression(String data) {
        this.data = data;
    }

    public boolean interpret(String context) {
        return context.contains(data);
    }
}

// Nonterminal Expression
class OrExpression implements Expression {
    private Expression expr1;
    private Expression expr2;

    OrExpression(Expression expr1, Expression expr2) {
        this.expr1 = expr1;
        this.expr2 = expr2;
    }

    public boolean interpret(String context) {
        return expr1.interpret(context) || expr2.interpret(context);
    }
}

class AndExpression implements Expression {
    private Expression expr1;
    private Expression expr2;

    AndExpression(Expression expr1, Expression expr2) {
        this.expr1 = expr1;
        this.expr2 = expr2;
    }

    public boolean interpret(String context) {
        return expr1.interpret(context) && expr2.interpret(context);
    }
}

// Client code
public class InterpreterPatternDemo {
    public static void main(String[] args) {
        Expression isJava = new TerminalExpression("Java");
        Expression isJavaEE = new TerminalExpression("Java EE");
        Expression isJavaOrJavaEE = new OrExpression(isJava, isJavaEE);

        System.out.println("Does the context contain Java or Java EE? " +
                           isJavaOrJavaEE.interpret("Java SE"));
    }
}
```

In this Java example, `TerminalExpression` implements individual elements of the language. The
`OrExpression` and `AndExpression` classes implement compound expressions. The client
(`InterpreterPatternDemo`) creates an abstract syntax tree representing the expression and then
evaluates it. This pattern is particularly useful for interpreting languages and expressions.

### Iterator Pattern

The Iterator Pattern is a behavioral design pattern that provides a way to access the elements of an
aggregate object sequentially without exposing its underlying representation.

#### What is the Iterator Pattern?

The Iterator Pattern is used to provide a standard way to traverse through a collection of objects
without needing to understand the underlying structure of the collection.

#### Purpose of the Design Pattern

The purpose of the Iterator Pattern is to:

-   Provide a way to access elements of a collection object in sequential order.
-   Decouple the collection objects from the algorithms that operate on them.

#### Software Principles Applied

1. **Single Responsibility Principle**: It separates the responsibilities by keeping the iteration
   logic out of the collection.
2. **Open/Closed Principle**: New types of collections and iterators can be added without modifying
   the existing code.

#### Helpful Uses

1. **Navigating Complex Data Structures**: Useful for collections with complex data structures where
   the traversal isn’t straightforward.
2. **Multiple Simultaneous Traversals**: Allows multiple traversals on the same collection
   independently.

#### Possible Drawbacks

1. **Overhead**: For simple collections, using an iterator can add unnecessary overhead.
2. **Complexity**: Can introduce complexity and additional classes or interfaces.

#### Basic Structure

1. **Iterator**: An interface for accessing and traversing elements.
2. **Concrete Iterator**: Implements the iterator interface and is responsible for managing the
   current position of the iterator.
3. **Aggregate**: An interface that declares one or more methods for getting iterators compatible
   with the collection.
4. **Concrete Aggregate**: Implements the Aggregate interface and returns an instance of the
   corresponding Concrete Iterator.

#### Possible Variations

1. **Bidirectional Iterators**: Allows traversing the collection in both directions.
2. **Mutable Iterators**: Provides methods to modify the collection while traversing.

#### Relation to Other Design Patterns

-   **Composite Pattern**: Often used with Iterator to traverse composite objects.
-   **Factory Method**: Can be used to create the appropriate iterator for a collection.

#### Common Criticisms

1. **Redundancy**: Modern programming languages often provide built-in iterators making the explicit
   use of the pattern less necessary.
2. **Complexity for Simple Collections**: Can be seen as an overkill for collections with simple
   internal structures.

#### Implementing the Pattern

1. **Create the Iterator Interface**: Define methods for accessing and traversing elements.
2. **Implement Concrete Iterators**: Create classes that implement the iterator interface for
   specific collections.
3. **Define the Aggregate Interface**: This interface should have a method to create and return an
   iterator.
4. **Implement Concrete Aggregates**: Implement the aggregate interface in collection classes.

#### Example in Java

```java
// Iterator Interface
interface Iterator {
    boolean hasNext();
    Object next();
}

// Aggregate Interface
interface Container {
    Iterator getIterator();
}

// Concrete Iterator
class NameIterator implements Iterator {
    private String[] names;
    private int index;

    public NameIterator(String[] names) {
        this.names = names;
    }

    @Override
    public boolean hasNext() {
        return index < names.length;
    }

    @Override
    public Object next() {
        if (this.hasNext()) {
            return names[index++];
        }
        return null;
    }
}

// Concrete Aggregate
class NameRepository implements Container {
    private String[] names = {"John", "Doe", "Jane", "Doe"};

    @Override
    public Iterator getIterator() {
        return new NameIterator(names);
    }
}

// Client code
public class IteratorPatternDemo {
    public static void main(String[] args) {
        NameRepository namesRepository = new NameRepository();

        for (Iterator iter = namesRepository.getIterator(); iter.hasNext();) {
            String name = (String)iter.next();
            System.out.println("Name : " + name);
        }
    }
}
```

In this Java example, `NameRepository` is a concrete aggregate that implements the `Container`
interface. It returns a `NameIterator`, which is a concrete iterator for traversing the `names`
array. The client (`IteratorPatternDemo`) uses the iterator to traverse the `NameRepository`
sequentially. This pattern is particularly useful in cases where the collection's internal structure
is complex, and you want to provide a simple way to access its elements.

### Mediator Pattern

The Mediator Pattern is a behavioral design pattern that provides a centralized communication medium
between different objects in a system.

#### What is the Mediator Pattern?

The Mediator Pattern is designed to reduce the direct communication between classes and move it to a
mediator object. This pattern helps in reducing the coupling between classes by providing a central
place where interactions can be managed and orchestrated.

#### Purpose of the Design Pattern

The purpose of the Mediator Pattern is to:

-   Reduce the direct communication between objects, thereby reducing the coupling and dependencies
    between them.
-   Centralize complex communications and control logic between objects in a single mediator object.

#### Software Principles Applied

1. **Single Responsibility Principle**: The mediator object centralizes complex logic that would
   otherwise be distributed across several objects.
2. **Open/Closed Principle**: New mediator classes can be added without changing existing code.

#### Helpful Uses

1. **Complex Form Interactions**: In UI development, for managing complex form controls and
   interactions.
2. **Chat Rooms**: As a centralized system to manage communication between multiple users.

#### Possible Drawbacks

1. **God Object**: The mediator can become overly complex, turning into a "god object" that's hard
   to maintain.
2. **Performance**: If not well-implemented, the mediator can become a performance bottleneck.

#### Basic Structure

1. **Mediator Interface**: An interface that defines the communication protocol between various
   objects.
2. **Concrete Mediator**: Implements the mediator interface and coordinates the interaction between
   different objects.
3. **Colleague Classes**: A set of classes that communicate with each other through the mediator.

#### Possible Variations

1. **Event-Driven Mediators**: Mediators that use events or messages to communicate between
   colleagues.
2. **Decentralized Mediation**: Where the mediation logic is distributed and not centralized in a
   single mediator object.

#### Relation to Other Design Patterns

-   **Observer Pattern**: Often used together, where the mediator may observe and react to events
    from its colleagues.
-   **Command Pattern**: Commands can be used to encapsulate a request as an object, which then are
    handled by the mediator.

#### Common Criticisms

1. **Complexity**: Can become complex and hard to maintain as the number of interactions grows.
2. **Overuse**: It might be overused for problems that can be solved in simpler ways.

#### Implementing the Pattern

1. **Define Mediator Interface**: Create an interface for the mediator, defining the methods for
   communication.
2. **Implement Concrete Mediator**: Develop a concrete mediator class that implements the mediator
   interface.
3. **Create Colleague Classes**: Develop classes that use the mediator for communication.
4. **Implement Communication**: Implement the communication between colleagues through the mediator.

#### Example in Java

```java
// Mediator Interface
interface ChatMediator {
    void sendMessage(String msg, User user);
    void addUser(User user);
}

// Concrete Mediator
class ChatRoom implements ChatMediator {
    private List<User> users;

    public ChatRoom() {
        this.users = new ArrayList<>();
    }

    @Override
    public void addUser(User user) {
        this.users.add(user);
    }

    @Override
    public void sendMessage(String msg, User user) {
        for (User u : users) {
            // message should not be received by the user sending it
            if (u != user) {
                u.receive(msg);
            }
        }
    }
}

// Colleague
abstract class User {
    protected ChatMediator mediator;
    protected String name;

    public User(ChatMediator med, String name){
        this.mediator = med;
        this.name = name;
    }

    public abstract void send(String msg);
    public abstract void receive(String msg);
}

// Concrete Colleague
class UserImpl extends User {

    public UserImpl(ChatMediator med, String name) {
        super(med, name);
    }

    @Override
    public void send(String msg){
        System.out.println(this.name+": Sending Message="+msg);
        mediator.sendMessage(msg, this);
    }
    @Override
    public void receive(String msg) {
        System.out.println(this.name+": Received Message:"+msg);
    }
}

// Client code
public class MediatorPatternDemo {
    public static void main(String[] args) {
        ChatMediator mediator = new ChatRoom();

        User user1 = new UserImpl(mediator, "John");
        User user2 = new UserImpl(mediator, "Doe");
        User user3 = new UserImpl(mediator, "Smith");
        User user4 = new UserImpl(mediator, "Jane");

        mediator.addUser(user1);
        mediator.addUser(user2);
        mediator.addUser(user3);
        mediator.addUser(user4);

        user1.send("Hi All");
    }
}
```

In this Java example, `ChatRoom` acts as a concrete mediator for the chat application. `User` is an
abstract class that represents colleagues in the mediator pattern. Concrete implementations of
`User` (like `UserImpl`) use the `ChatMediator` to send and receive messages. This pattern is
beneficial in scenarios like chat applications where multiple users interact with each other, but
the complexity of communication logic is encapsulated within the mediator (`ChatRoom`).

### Memento Pattern

The Memento Pattern is a behavioral design pattern that allows capturing and externalizing an
object's internal state so that the object can be restored to this state later.

#### What is the Memento Pattern?

The Memento Pattern provides the ability to restore an object to its previous state (undo via
rollback). It involves capturing and storing the current state of an object in a manner that it can
be restored at a later time without breaking the rules of encapsulation.

#### Purpose of the Design Pattern

The purpose of the Memento Pattern is to:

-   Preserve the internal state of an object.
-   Provide a mechanism for undoing actions without revealing details of the implementation.

#### Software Principles Applied

1. **Single Responsibility Principle**: The pattern keeps the object's state handling separate from
   its business logic.
2. **Open/Closed Principle**: It's easy to add new states and mementos without changing existing
   code.

#### Helpful Uses

1. **Undo Functionality**: Commonly used in applications with undo/redo functionality, like text
   editors or graphic editors.
2. **Snapshots**: Taking snapshots of an object's state to revert to them if necessary.

#### Possible Drawbacks

1. **Memory Usage**: Storing copies of the object's state can consume significant memory.
2. **Complexity**: Implementing the pattern can complicate the code, especially in cases where the
   object's state is complex.

#### Basic Structure

1. **Originator**: The object whose state is to be saved. It creates a memento containing a snapshot
   of its current internal state.
2. **Memento**: A class that stores the internal state of the Originator. It's only accessible by
   the Originator.
3. **Caretaker**: It is responsible for the memento's safekeeping but does not modify or examine the
   contents of the memento.

#### Possible Variations

1. **Multiple States**: Storing multiple states in the memento.
2. **State Compression**: Compressing the state in the memento to save space.

#### Relation to Other Design Patterns

-   **Command Pattern**: Often used with Memento to maintain the state required for undo
    functionality.
-   **Iterator Pattern**: Memento can be used to capture the state of an iteration.

#### Common Criticisms

1. **Overhead**: The pattern can introduce memory and performance overhead.
2. **Complexity**: Managing mementos can be complex in large applications.

#### Implementing the Pattern

1. **Create the Memento Class**: Design a memento class that will store the internal state of the
   Originator.
2. **Originator Implementation**: Implement the Originator class that creates and uses mementos to
   save and restore its state.
3. **Caretaker Implementation**: Implement the Caretaker class that keeps track of the mementos
   without modifying them.

#### Example in Java

```java
// Memento
class Memento {
    private String state;

    public Memento(String state) {
        this.state = state;
    }

    public String getState() {
        return state;
    }
}

// Originator
class Originator {
    private String state;

    public void setState(String state) {
        this.state = state;
    }

    public String getState() {
        return state;
    }

    public Memento saveStateToMemento() {
        return new Memento(state);
    }

    public void getStateFromMemento(Memento memento) {
        state = memento.getState();
    }
}

// Caretaker
class Caretaker {
    private List<Memento> mementoList = new ArrayList<>();

    public void add(Memento state) {
        mementoList.add(state);
    }

    public Memento get(int index) {
        return mementoList.get(index);
    }
}

// Client code
public class MementoPatternDemo {
    public static void main(String[] args) {
        Originator originator = new Originator();
        Caretaker caretaker = new Caretaker();

        originator.setState("State #1");
        originator.setState("State #2");
        caretaker.add(originator.saveStateToMemento());

        originator.setState("State #3");
        caretaker.add(originator.saveStateToMemento());

        originator.setState("State #4");
        System.out.println("Current State: " + originator.getState());

        originator.getStateFromMemento(caretaker.get(0));
        System.out.println("First saved State: " + originator.getState());
        originator.getStateFromMemento(caretaker.get(1));
        System.out.println("Second saved State: " + originator.getState());
    }
}
```

In this Java example, the `Originator` class creates a `Memento` object to capture its current
state. The `Caretaker` class is responsible for storing the `Memento` objects. This pattern is
particularly useful in scenarios where we need to maintain a history of an object's states and
provide undo or rollback functionalities.

### Observer Pattern

The Observer Pattern is a behavioral design pattern that defines a one-to-many dependency between
objects so that when one object changes state, all its dependents are notified and updated
automatically.

#### What is the Observer Pattern?

The Observer Pattern involves an object, known as the subject, maintaining a list of its dependents,
called observers, and notifying them automatically of any state changes, usually by calling one of
their methods.

#### Purpose of the Design Pattern

The purpose of the Observer Pattern is to:

-   Create a mechanism for an object to publish changes to its state.
-   Allow other objects to subscribe and react to these changes.

#### Software Principles Applied

1. **Loose Coupling**: The subject and observers are loosely coupled. The subject knows nothing
   about the observer other than it implements a certain interface.
2. **Single Responsibility Principle**: The pattern helps in separating concerns – the subject
   focuses on the core logic, while observers handle their specific reactions.

#### Helpful Uses

1. **Event Handling Systems**: Particularly in graphical user interfaces.
2. **Model-View-Controller (MVC) Architecture**: The model notifies views when its data changes.
3. **Publish-Subscribe Systems**: Like in message queues and event bus systems.

#### Possible Drawbacks

1. **Memory Leaks**: In languages without automatic garbage collection, if observers are not
   unregistered, it can lead to memory leaks.
2. **Unexpected Updates**: If not properly managed, a change in the subject may lead to a cascade of
   updates in observers.
3. **Complexity**: Can make the design of an application more complex due to the dynamic
   relationships.

#### Basic Structure

1. **Subject**: An interface that defines methods for attaching, detaching, and notifying observers.
2. **Concrete Subject**: Implements the subject interface. When its state changes, it notifies the
   attached observers.
3. **Observer**: An interface with a method that is called by the subject when a change occurs.
4. **Concrete Observer**: Implements the observer interface and registers with a concrete subject to
   receive updates.

#### Possible Variations

1. **Event/Listener**: A variation where observers are notified through event handlers.
2. **Change Management**: Managing changes to prevent observers from reacting to irrelevant updates.

#### Relation to Other Design Patterns

-   **Mediator Pattern**: Sometimes used with Observer to allow objects to communicate without being
    tightly coupled.
-   **Singleton**: Can be used to implement a central registry of observers.

#### Common Criticisms

1. **Debugging Difficulty**: It can be challenging to debug due to the indirect nature of
   communication.
2. **Performance Concerns**: A large number of observers, or complex observer logic, can impact
   performance.

#### Implementing the Pattern

1. **Define Observer and Subject Interfaces**: Create interfaces for both subjects and observers.
2. **Implement Concrete Subject**: Implement the subject interface with mechanisms to track and
   notify observers.
3. **Implement Concrete Observers**: Implement the observer interface in classes that need to react
   to the subject's changes.
4. **Subject-Observer Interaction**: Allow observers to register with and receive updates from the
   subject.

#### Example in Java

```java
import java.util.ArrayList;
import java.util.List;

// Observer Interface
interface Observer {
    void update(String message);
}

// Subject Interface
interface Subject {
    void attach(Observer o);
    void detach(Observer o);
    void notifyUpdate(String message);
}

// Concrete Subject
class NewsAgency implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private String news;

    public void setNews(String news) {
        this.news = news;
        notifyUpdate(news);
    }

    @Override
    public void attach(Observer o) {
        observers.add(o);
    }

    @Override
    public void detach(Observer o) {
        observers.remove(o);
    }

    @Override
    public void notifyUpdate(String message) {
        for(Observer o: observers) {
            o.update(message);
        }
    }
}

// Concrete Observer
class NewsChannel implements Observer {
    private String news;

    @Override
    public void update(String news) {
        this.news = news;
        System.out.println("NewsChannel received news: " + news);
    }
}

// Client code
public class ObserverPatternDemo {
    public static void main(String[] args) {
        NewsAgency observable = new NewsAgency();
        NewsChannel observer = new NewsChannel();

        observable.attach(observer);
        observable.setNews("Breaking News: New design pattern tutorial released!");
    }
}
```

In this Java example, `NewsAgency` is the Concrete Subject, and `NewsChannel` is the Concrete
Observer. When the `NewsAgency` receives new news, it notifies all registered `NewsChannel`
instances by calling their `update` method with the new news. This pattern allows the `NewsChannel`
to react to changes in the `NewsAgency` without being tightly coupled to it.

### State Pattern

The State Pattern is a behavioral design pattern that allows an object to change its behavior when
its internal state changes. This pattern is used to encapsulate varying behavior for the same
routine based on an object's state object.

#### What is the State Pattern?

The State Pattern allows objects to behave differently depending on their internal state.
Essentially, it encapsulates the state-specific behavior into separate classes and delegates
behavior to the current state object.

#### Purpose of the Design Pattern

The purpose of the State Pattern is to:

-   Manage state-specific behavior dynamically.
-   Remove complex conditional logic and improve maintainability and scalability.

#### Software Principles Applied

1. **Open/Closed Principle**: It's easy to add new states without changing the existing states or
   the context.
2. **Single Responsibility Principle**: Each state class encapsulates all behavior associated with a
   particular state.

#### Helpful Uses

1. **Workflow Management**: Managing complex state transitions in business processes.
2. **UI Tool States**: Different behaviors of UI tools, like different modes in a drawing
   application.

#### Possible Drawbacks

1. **Overhead**: Introducing many small classes can make a system more complex to understand and
   maintain.
2. **Number of Classes**: Can lead to an explosion of classes, one for each state.

#### Basic Structure

1. **Context**: Maintains a reference to the current state and delegates state-specific behavior to
   it.
2. **State Interface**: Defines an interface for encapsulating the behavior associated with a
   particular state.
3. **Concrete States**: Implement the State interface and provide the behavior for their state.

#### Possible Variations

1. **State Transition Control**: Controlling how and when state transitions occur.
2. **State History**: Keeping a history of states for undo functionality.

#### Relation to Other Design Patterns

-   **Strategy Pattern**: Similar to State, but Strategy is more about choosing an algorithm,
    whereas State is about changing behavior based on internal state.
-   **Singleton**: Sometimes, states are implemented as singletons if they don't maintain state.

#### Common Criticisms

1. **Complexity**: Can unnecessarily complicate the design for simple state changes.
2. **State Explosion**: The number of classes can grow quickly with more states.

#### Implementing the Pattern

1. **Define the State Interface**: Create an interface or abstract class defining methods for
   state-specific behavior.
2. **Implement Concrete States**: Create classes for each specific state, implementing the state
   interface.
3. **Create the Context**: Develop a class that maintains a current state and delegates the
   state-specific work to the current state object.
4. **Changing States**: Allow the context to change its current state object based on conditions.

#### Example in Java

```java
// State Interface
interface State {
    void handle(Context context);
}

// Concrete States
class StartState implements State {
    public void handle(Context context) {
        System.out.println("In start state");
        context.setState(this);
    }

    public String toString(){
        return "Start State";
    }
}

class StopState implements State {
    public void handle(Context context) {
        System.out.println("In stop state");
        context.setState(this);
    }

    public String toString(){
        return "Stop State";
    }
}

// Context
class Context {
    private State state;

    public Context() {
        state = null;
    }

    public void setState(State state) {
        this.state = state;
    }

    public State getState() {
        return state;
    }
}

// Client code
public class StatePatternDemo {
    public static void main(String[] args) {
        Context context = new Context();

        StartState startState = new StartState();
        startState.handle(context);

        System.out.println(context.getState().toString());

        StopState stopState = new StopState();
        stopState.handle(context);

        System.out.println(context.getState().toString());
    }
}
```

In this Java example, `StartState` and `StopState` are concrete states implementing the `State`
interface. `Context` maintains a reference to the current state and delegates state-specific
behavior to it. This pattern allows the `Context` to change its behavior by transitioning from one
state to another, making it easier to manage complex state logic and transitions.

### Strategy Pattern

The Strategy Pattern is a behavioral design pattern that enables selecting an algorithm's behavior
at runtime. It defines a family of algorithms, encapsulates each one, and makes them
interchangeable.

#### What is the Strategy Pattern?

The Strategy Pattern involves defining a set of algorithms, encapsulating each one into separate
classes, and making them interchangeable. This pattern lets the algorithm vary independently from
clients that use it.

#### Purpose of the Design Pattern

The purpose of the Strategy Pattern is to:

-   Enable the selection of algorithms at runtime.
-   Provide a means to replace inheritance with delegation to achieve the desired behavior.

#### Software Principles Applied

1. **Open/Closed Principle**: New strategies can be introduced without changing the context.
2. **Single Responsibility Principle**: Each strategy encapsulates its own algorithm or behavior.

#### Helpful Uses

1. **Dynamic Behavior Change**: Useful when you need to dynamically change the behavior of an
   object.
2. **Algorithm Decoupling**: Allows separating algorithm implementation from the code that uses the
   algorithm.

#### Possible Drawbacks

1. **Increased Number of Objects**: Can lead to a proliferation of classes, as each strategy is
   implemented as its own class.
2. **Client Awareness**: Clients must be aware of the differences between strategies to select the
   appropriate one.

#### Basic Structure

1. **Strategy Interface**: An interface common to all supported algorithms.
2. **Concrete Strategies**: Implementations of the strategy interface, each encapsulating a specific
   algorithm.
3. **Context**: Holds a reference to a strategy and delegates it executing the behavior.

#### Possible Variations

1. **State vs. Strategy**: Although similar, the Strategy pattern is about changing behavior, while
   the State pattern is more about changing object state.
2. **Immutable Strategies**: Making strategy objects immutable and stateless.

#### Relation to Other Design Patterns

-   **State Pattern**: Often confused with the Strategy pattern, but while Strategy changes the guts
    of the object, State changes the entire behavior.
-   **Factory Method**: Can be used to instantiate strategies.

#### Common Criticisms

1. **Complexity**: Introduces complexity into the code, particularly in cases where there are
   multiple strategies.
2. **Overhead for Simple Choices**: Might be overkill for situations where a simple conditional
   would suffice.

#### Implementing the Pattern

1. **Define Strategy Interface**: Create an interface for the strategies with a method signature
   that all concrete strategies must implement.
2. **Implement Concrete Strategies**: Develop classes that implement the strategy interface, each
   providing a different behavior.
3. **Context Class**: Create a class with a method that calls the strategy interface method. It
   allows changing the strategy object at runtime.

#### Example in Java

```java
// Strategy Interface
interface SortingStrategy {
    void sort(int[] array);
}

// Concrete Strategies
class BubbleSortStrategy implements SortingStrategy {
    public void sort(int[] array) {
        System.out.println("Sorting using bubble sort");
        // Implement sorting logic
    }
}

class QuickSortStrategy implements SortingStrategy {
    public void sort(int[] array) {
        System.out.println("Sorting using quick sort");
        // Implement sorting logic
    }
}

// Context
class SortedList {
    private SortingStrategy strategy;

    public void setSortingStrategy(SortingStrategy strategy) {
        this.strategy = strategy;
    }

    public void sort(int[] array) {
        strategy.sort(array);
    }
}

// Client code
public class StrategyPatternDemo {
    public static void main(String[] args) {
        SortedList list = new SortedList();

        list.setSortingStrategy(new BubbleSortStrategy());
        list.sort(new int[]{2, 1, 3});

        list.setSortingStrategy(new QuickSortStrategy());
        list.sort(new int[]{2, 1, 3});
    }
}
```

In this Java example, `BubbleSortStrategy` and `QuickSortStrategy` are concrete strategies that
implement the `SortingStrategy` interface. `SortedList` is the context that uses a sorting strategy.
The client (`StrategyPatternDemo`) can change the sorting algorithm at runtime by changing the
strategy in the `SortedList`. This pattern allows for changing the sorting behavior of `SortedList`
without modifying its code, demonstrating the flexibility and dynamic behavior change facilitated by
the Strategy pattern.

### Template Method Pattern

The Template Method Pattern is a behavioral design pattern that defines the skeleton of an algorithm
in a method, deferring some steps to subclasses. It allows subclasses to redefine certain steps of
an algorithm without changing the algorithm's structure.

#### What is the Template Method Pattern?

The Template Method Pattern involves an abstract class that defines a template method setting the
blueprint of an algorithm. The steps of this algorithm are defined as abstract methods, which are
then implemented by subclasses.

#### Purpose of the Design Pattern

The purpose of the Template Method Pattern is to:

-   Define the program skeleton of an algorithm in an operation, deferring some steps to client
    subclasses.
-   Allow subclasses to redefine certain steps of an algorithm without changing its structure.

#### Software Principles Applied

1. **Don't Repeat Yourself (DRY)**: The pattern allows avoiding code duplication by extracting
   common code into a single place.
2. **Open/Closed Principle**: The algorithm can be extended without modifying the existing code.

#### Helpful Uses

1. **Workflow Management**: Useful in workflows where the sequence of processes is fixed, but the
   details of each process vary.
2. **Data Processing**: Common in data processing applications where the steps are the same but the
   data handling differs.

#### Possible Drawbacks

1. **Limited Flexibility**: Subclasses have limited control over the algorithm. They can only change
   the steps that are specifically designed to be overridden.
2. **Complexity**: Can make the code more complex and harder to understand.

#### Basic Structure

1. **Abstract Class**: Defines abstract methods and a template method.
2. **Template Method**: A method in the abstract class that defines the algorithm's skeleton.
3. **Concrete Class**: Implements the abstract methods of the abstract class.

#### Possible Variations

1. **Hooks**: Optional steps in the algorithm that have a default implementation but can be
   overridden.
2. **Strategies as Parameters**: Combining with the Strategy Pattern to pass specific behaviors as
   parameters.

#### Relation to Other Design Patterns

-   **Factory Method**: Often used as a step in the Template Method.
-   **Strategy Pattern**: Similar in concept but differs in the granularity of the behavior that can
    be changed.

#### Common Criticisms

1. **Overuse**: Sometimes overused for problems that can be solved in simpler ways.
2. **Inflexibility**: The rigid structure may not fit all use cases.

#### Implementing the Pattern

1. **Define Abstract Class**: Create an abstract class that declares abstract methods and a template
   method.
2. **Implement Template Method**: Define the template method in the abstract class. This method
   calls the abstract methods in a specific order.
3. **Create Concrete Classes**: Implement the abstract methods in concrete subclasses.

#### Example in Java

```java
// Abstract Class
abstract class Game {
    abstract void initialize();
    abstract void startPlay();
    abstract void endPlay();

    // Template method
    public final void play() {
        initialize();
        startPlay();
        endPlay();
    }
}

// Concrete Class
class Cricket extends Game {
    @Override
    void initialize() {
        System.out.println("Cricket Game Initialized!");
    }

    @Override
    void startPlay() {
        System.out.println("Cricket Game Started. Enjoy the game!");
    }

    @Override
    void endPlay() {
        System.out.println("Cricket Game Finished!");
    }
}

// Client code
public class TemplateMethodPatternDemo {
    public static void main(String[] args) {
        Game game = new Cricket();
        game.play();
    }
}
```

In this Java example, `Game` is an abstract class that defines the template method `play`. The steps
of the game (initialize, startPlay, endPlay) are defined as abstract methods. The `Cricket` class
extends `Game` and provides specific implementations for these steps. The template method `play`
ensures that the steps are executed in a specific order. This pattern encapsulates the invariant
parts of the algorithm, allowing subclasses to implement the variable parts.

### Visitor Pattern

The description you've provided actually corresponds to the Template Method Pattern, not the Visitor
Pattern. Let me clarify the Visitor Pattern for you:

#### What is the Visitor Pattern?

The Visitor Pattern is a behavioral design pattern that lets you separate algorithms from the
objects on which they operate. It allows adding new operations to existing object structures without
modifying those structures.

#### Purpose of the Design Pattern

The purpose of the Visitor Pattern is to:

-   Add new operations or functionalities to a set of objects without altering their structure.
-   Separate an algorithm from the object structure on which it operates.

#### Software Principles Applied

1. **Open/Closed Principle**: New operations can be added to objects without modifying their
   classes.
2. **Single Responsibility Principle**: Visitor pattern separates the related operations into a
   single class.

#### Helpful Uses

1. **Performing Operations Across a Set of Objects**: Useful when operations need to be performed on
   a group of different kinds of objects.
2. **Adding Additional Operations**: Particularly useful when new operations are frequently added to
   a complex object structure.

#### Possible Drawbacks

1. **Complexity**: Can make the code more complex and harder to understand.
2. **Intrusiveness**: Requires changing the classes of objects to accommodate visitors, which can be
   intrusive.
3. **Lack of Encapsulation**: Exposes the object's internal details to the visitor.

#### Basic Structure

1. **Visitor Interface**: An interface that declares a set of visiting methods for each class of the
   object structure.
2. **Concrete Visitor**: Implements each visiting method defined by the visitor interface,
   encapsulating the algorithm or operation to be performed.
3. **Visitable Interface**: An interface declaring an accept method that takes a visitor object.
4. **Concrete Visitable Classes**: Implement the visitable interface and define the accept method.

#### Possible Variations

1. **Composite Visitors**: Visitors that work with composite objects.
2. **Accumulating Visitors**: Visitors that accumulate information while traversing the object
   structure.

#### Relation to Other Design Patterns

-   **Composite Pattern**: Often used together where the Visitor allows performing operations over
    Composite structures.
-   **Iterator Pattern**: Can be combined to traverse a complex structure and apply a visitor to
    each element.

#### Common Criticisms

1. **Difficulty in Understanding**: The pattern can be difficult to understand and implement
   correctly.
2. **Potential to Violate Encapsulation**: Visitors have access to the internal details of the
   elements they visit.

#### Implementing the Pattern

1. **Define Visitor Interface**: Create a visitor interface with a visit method for each type of
   element.
2. **Implement Concrete Visitors**: Create concrete visitor classes that implement the visitor
   interface methods.
3. **Create Visitable Interface**: Define an interface for elements that can be visited.
4. **Implement Concrete Visitable Classes**: These classes implement the visitable interface and
   define the accept method.

#### Example in Java

```java
// Visitor Interface
interface ComputerPartVisitor {
    void visit(Computer computer);
    void visit(Mouse mouse);
    void visit(Keyboard keyboard);
    void visit(Monitor monitor);
}

// Visitable Interface
interface ComputerPart {
    void accept(ComputerPartVisitor computerPartVisitor);
}

// Concrete Visitable Classes
class Keyboard implements ComputerPart {
    public void accept(ComputerPartVisitor computerPartVisitor) {
        computerPartVisitor.visit(this);
    }
}

class Monitor implements ComputerPart {
    public void accept(ComputerPartVisitor computerPartVisitor) {
        computerPartVisitor.visit(this);
    }
}

// ... Mouse and Computer classes similar to Keyboard and Monitor

// Concrete Visitor
class ComputerPartDisplayVisitor implements ComputerPartVisitor {
    public void visit(Computer computer) {
        System.out.println("Displaying Computer.");
    }

    public void visit(Mouse mouse) {
        System.out.println("Displaying Mouse.");
    }

    public void visit(Keyboard keyboard) {
        System.out.println("Displaying Keyboard.");
    }

    public void visit(Monitor monitor) {
        System.out.println("Displaying Monitor.");
    }
}

// Client code
public class VisitorPatternDemo {
    public static void main(String[] args) {
        ComputerPart computer = new Computer();
        computer.accept(new ComputerPartDisplayVisitor());
    }
}
```

In this Java example, `ComputerPart` is the Visitable interface, and `ComputerPartVisitor` is the
Visitor interface. Concrete classes like `Keyboard`, `Monitor`, `Mouse`, and `Computer` implement
`ComputerPart`. The `ComputerPartDisplayVisitor` class is a concrete visitor implementing
`ComputerPartVisitor`. This design allows adding new operations (visitors) without changing the
structure of `ComputerPart` objects.

## Concurrency Patterns

### Thread Pool Pattern

The Thread Pool Pattern is a concurrency design pattern used to manage and optimize the execution of
multiple threads in a multithreaded application. It's not part of the traditional GoF design
patterns, but it's widely used in software development.

#### What is the Thread Pool Pattern?

The Thread Pool Pattern involves creating a number of threads at the start (a "pool") and reusing
these threads for executing tasks, rather than creating a new thread for each task.

#### Purpose of the Design Pattern

The purpose of the Thread Pool Pattern is to:

-   Improve the performance of executing multiple tasks in a multithreaded environment.
-   Reduce the overhead of thread creation and destruction.
-   Limit the number of threads running in parallel and manage resource usage effectively.

#### Software Principles Applied

1. **Efficiency and Resource Management**: Helps in efficiently managing resources, particularly in
   systems with a large number of concurrent tasks.
2. **Control over Concurrency**: Provides better control over how tasks are executed concurrently.

#### Helpful Uses

1. **Web Servers**: Handling requests in web servers where each request can be processed by a thread
   from the pool.
2. **Parallel Task Processing**: In applications requiring parallel processing of tasks, such as
   data processing systems.

#### Possible Drawbacks

1. **Complexity**: Managing a thread pool adds complexity to the system.
2. **Resource Limitation**: The fixed size of the pool might lead to resource underutilization or
   bottlenecks.

#### Basic Structure

1. **Thread Pool**: A pool of pre-instantiated reusable threads.
2. **Worker Threads**: Threads in the thread pool that execute tasks.
3. **Task Queue**: A queue holding tasks to be executed, which worker threads retrieve from.

#### Possible Variations

1. **Dynamic Thread Pool**: Adjusting the number of threads in the pool based on demand.
2. **Priority-based Task Execution**: Assigning priorities to tasks and executing them accordingly.

#### Relation to Other Design Patterns

-   **Producer-Consumer Pattern**: Often used together, where the thread pool pattern can be seen as
    a consumer of tasks.

#### Common Criticisms

1. **Overhead in Fine-Grained Task**: Not suitable for tasks that are too small, as the overhead of
   task management might outweigh the benefits.
2. **Complex Task Management**: Complexity in managing tasks, especially when tasks have
   dependencies or require synchronization.

#### Implementing the Pattern

1. **Create a Task Interface**: Define an interface or abstract class for tasks that the threads
   will execute.
2. **Implement the Thread Pool**: Develop a pool class that creates and manages a fixed number of
   threads.
3. **Task Queue Management**: Implement a task queue where tasks are stored and retrieved by worker
   threads.
4. **Worker Threads Implementation**: Create worker threads that continuously look for tasks in the
   queue and execute them.

#### Example in Java

Java's `java.util.concurrent` package provides built-in support for the thread pool pattern via
`ExecutorService` and other related classes. Here's a simple implementation:

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class ThreadPoolDemo {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(5);

        for (int i = 0; i < 10; i++) {
            Runnable worker = new WorkerThread("" + i);
            executor.execute(worker);
        }

        executor.shutdown();
        while (!executor.isTerminated()) {
        }

        System.out.println("Finished all threads");
    }
}

class WorkerThread implements Runnable {
    private String command;

    public WorkerThread(String s) {
        this.command = s;
    }

    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName() + " Start. Command = " + command);
        processCommand();
        System.out.println(Thread.currentThread().getName() + " End.");
    }

    private void processCommand() {
        try {
            Thread.sleep(500);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

In this Java example, `ExecutorService` creates a thread pool with 5 threads. `WorkerThread` is the
task class. Each task is executed by a thread from the thread pool, demonstrating how the Thread
Pool Pattern manages multiple threads to efficiently execute multiple tasks.

### Reactor Pattern

The Reactor Pattern is a concurrent design pattern used for handling service requests delivered
concurrently to a service handler by one or more inputs. The pattern is particularly useful in
scenarios where an application needs to handle multiple concurrent input streams and to service
these streams in a non-blocking way.

#### What is the Reactor Pattern?

The Reactor Pattern is a design pattern that efficiently manages synchronous I/O in a non-blocking,
event-driven manner. It decouples application-specific software from I/O handling, using a handler
that dispatches I/O events to appropriate request handlers.

#### Purpose of the Design Pattern

The purpose of the Reactor Pattern is to:

-   Enable handling multiple concurrent I/O requests using non-blocking operations.
-   Efficiently manage and dispatch service requests that are delivered concurrently to an
    application.

#### Software Principles Applied

1. **Single Responsibility Principle**: Separates concerns by delegating the responsibilities to
   different classes (e.g., dispatching, I/O handling, request processing).
2. **Open/Closed Principle**: New handlers and services can be added without modifying the core
   reactor logic.

#### Helpful Uses

1. **Web Servers and Application Servers**: Handling incoming HTTP requests in a non-blocking
   fashion.
2. **Network Applications**: Efficiently managing concurrent network connections and data.

#### Possible Drawbacks

1. **Complexity**: Implementing the reactor pattern can be complex and difficult to understand.
2. **Scalability Limitations**: The single-threaded nature of the basic reactor can be a bottleneck.
3. **Handling Long-Running Tasks**: Not suitable for long-running tasks which can block the reactor
   loop.

#### Basic Structure

1. **Reactor**: An object that provides an interface to register, deregister, and dispatch I/O
   events to the appropriate handlers.
2. **Handlers**: Implementations that handle specific I/O events.
3. **Synchronous Event Demultiplexer**: A system call that blocks while waiting for events to occur
   on a set of I/O handles.
4. **Event Handler Interface**: An interface for handling various I/O events.
5. **Concrete Event Handlers**: Implement the Event Handler interface to handle specific events.

#### Possible Variations

1. **Single-Threaded Reactor**: Handles all events in a single thread, best for applications with
   small loads.
2. **Multi-Threaded Reactor**: Uses multiple threads to handle events, suitable for high-load
   applications.

#### Relation to Other Design Patterns

-   **Observer Pattern**: The Reactor pattern is similar to the Observer pattern but specifically
    tailored to synchronous I/O handling.
-   **Command Pattern**: Handlers in the reactor pattern often implement the Command pattern to
    encapsulate a request as an object.

#### Common Criticisms

1. **Complexity in Understanding and Implementation**: The reactor pattern can be complex to
   understand and implement correctly.
2. **Not Suitable for CPU-bound Tasks**: More suitable for I/O-bound tasks; not efficient for
   CPU-intensive operations.

#### Implementing the Pattern

1. **Create the Reactor Interface**: Define methods for registering, deregistering, and dispatching
   events.
2. **Implement the Synchronous Event Demultiplexer**: Use system calls to wait for events on I/O
   handles.
3. **Define the Event Handler Interface**: Create an interface for handling different types of
   events.
4. **Implement Concrete Event Handlers**: Develop classes that handle specific types of events.
5. **Build the Reactor**: Implement the reactor to manage and dispatch events to the appropriate
   handlers.

#### Example in Java

In Java, this pattern can be implemented using the `java.nio` package, specifically the `Selector`
and `Channel` classes. Here is a high-level outline:

```java
import java.nio.channels.Selector;
import java.nio.channels.SocketChannel;
import java.nio.channels.SelectionKey;
import java.nio.ByteBuffer;

// Reactor (Simplified)
class Reactor {
    private Selector selector;

    Reactor() throws IOException {
        this.selector = Selector.open();
    }

    void run() {
        while (!Thread.interrupted()) {
            // Wait for events
            selector.select();
            for (SelectionKey key : selector.selectedKeys()) {
                // Dispatch event
                if (key.isAcceptable()) {
                    // Handle accept event
                } else if (key.isReadable()) {
                    // Handle read event
                }
                // ... handle other events
            }
        }
    }

    // Method to register channel with selector
    void registerChannel(SocketChannel channel, int ops) throws IOException {
        channel.configureBlocking(false);
        channel.register(selector, ops);
    }
}

// Usage in an application
public class ReactorPatternDemo {
    public static void main(String[] args) throws IOException {
        Reactor reactor = new Reactor();
        // Set up channels and register them with the reactor
        // ...
        reactor.run();
    }
}
```

This example provides a basic structure for the Reactor pattern. In a practical application, you
would have concrete event handlers for different types of events (accept, read, write, etc.) and a
more comprehensive setup for the channels and their registration with the reactor. The `java.nio`
package's `Selector` class serves as a demultiplexer, allowing the reactor to wait for events on
multiple channels and process them as they occur.

## Architectural Patterns

Architectural patterns are high-level strategies that concern large-scale components, the global
properties and mechanisms of a system. They provide a template for the overall layout of
applications or systems.

### What are Architectural Patterns?

Architectural patterns are a category of patterns that address concerns at the architectural level
of a software system. They provide a blueprint for deciding the structural organization of a system
and are often related to the system's non-functional requirements, like scalability, performance,
maintainability, or reliability. These patterns help in defining the structural layout,
communication, data flow, and overall guiding principles of an application or system.

### Difference Between Architectural and Design Patterns

-   **Scope**: Architectural patterns are concerned with the overall structure of a system,
    encompassing multiple components and how they interact. Design patterns are more focused on
    solving specific problems within a component or between a small group of components at a more
    detailed level.
-   **Granularity**: Architectural patterns operate at a higher level of abstraction compared to
    design patterns. They influence the architecture of an entire system, while design patterns are
    applied to specific parts of a software application.
-   **Focus**: Architectural patterns often address broad-scale issues like system organization and
    global data flow. Design patterns typically address more localized issues, such as object
    creation, class structure, and communication between objects.

### Examples of Architectural Patterns

1. **Model-View-Controller (MVC)**: Separates the application into three interconnected components:
   the model (data), the view (user interface), and the controller (business logic). This is often
   used in web applications to separate internal representations of information from the ways
   information is presented and accepted from the user.

2. **Microservices Architecture**: Structures an application as a collection of loosely coupled
   services. Each service is self-contained and implements a specific business capability.

3. **Layered Architecture (n-tier Architecture)**: Organizes the system into layers with each layer
   performing a specific role within the application (like presentation layer, business logic layer,
   data access layer). This is common in traditional enterprise applications.

4. **Event-Driven Architecture**: Centers around the production, detection, and reaction to events.
   This architecture is effective for designing systems with asynchronous processing and where
   components need to react to state changes.

5. **Service-Oriented Architecture (SOA)**: Focuses on providing services to other components via a
   communication protocol over a network. SOA is beneficial for integrating diverse systems.

6. **Client-Server Architecture**: Involves a server providing services and a client using these
   services. The server hosts resources and services that are consumed by the client.

7. **Peer-to-Peer Architecture**: Distributes tasks or workloads among peers, which are equally
   privileged participants in the application. This is commonly used in file sharing networks.

These architectural patterns serve as guidelines for structuring software systems, making them more
efficient, scalable, maintainable, and ensuring they meet their functional and non-functional
requirements.

## Anti-Patterns and Pitfalls

### Understanding Anti-Patterns

Anti-patterns are common responses to a recurring problem that are ineffective and highly
counterproductive. They are the "bad practices" that can occur in software development and other
organizational processes. The concept of an anti-pattern is akin to a "lesson learned" in that it
represents a commonly reinvented bad wheel.

#### Key Characteristics of Anti-Patterns:

1. **Repetitive Use**: Anti-patterns are typically repeated in more than one project, indicating a
   systemic issue in the approach.
2. **Inherently Counterproductive**: They generally result in negative consequences that outweigh
   any short-term benefits.
3. **Commonly Accepted Solution**: Often, anti-patterns are initially appealing and widely used
   solutions that turn out to be ineffective or problematic.
4. **Refactored Solution**: Anti-patterns can usually be refactored or replaced with more effective
   patterns.

### Common Pitfalls in Using Design Patterns

1. **Overuse and Misuse**: One of the most common pitfalls is overusing design patterns or using a
   pattern where it is not needed or beneficial. This can lead to overly complex, hard-to-read, and
   maintainable code.

2. **Forcing a Pattern**: Trying to force the application of a design pattern to a problem it's not
   suited for can lead to awkward and inefficient solutions.

3. **Not Understanding the Pattern Fully**: Implementing a pattern without fully understanding its
   purpose, use cases, and implications can lead to incorrect application and inefficiencies.

4. **Ignoring Context**: Patterns need to be applied in the right context. Ignoring the specific
   requirements or constraints of your project when applying a pattern can cause problems.

5. **Underestimating the Impact of Change**: When a design pattern is applied, it may introduce new
   abstractions or dependencies. The impact of these changes on the overall system architecture
   should not be underestimated.

6. **Neglecting Performance Implications**: Some patterns, while providing cleaner code or other
   benefits, may introduce performance overheads. These implications must be considered, especially
   in performance-critical applications.

7. **Scalability and Maintenance Issues**: Some patterns may not scale well as the application grows
   or might make the system harder to maintain due to added complexity.

8. **Rigid Adherence**: Strictly adhering to a pattern without adapting it to the specific needs of
   your application can lead to suboptimal solutions.

### Best Practices

-   **Understand the Problem**: Before applying a design pattern, make sure you thoroughly
    understand the problem and consider whether a pattern is necessary.
-   **Know Your Patterns**: Invest time in learning not just how to implement design patterns, but
    also when and why to use them.
-   **Context Is Key**: Always consider the specific context and requirements of your project when
    applying a pattern.
-   **Balance**: Strive for a balance between code clarity, performance, and maintainability.
-   **Refactoring**: Be open to refactoring your use of patterns as the needs of your application
    evolve.

Understanding anti-patterns and being aware of the pitfalls in using design patterns can help
developers make more informed decisions, leading to cleaner, more efficient, and maintainable code.

## Design Pattern Best Practices

Design patterns are crucial tools in software development, offering standardized solutions to common
problems. However, their effectiveness depends on how they are implemented and chosen. Here are some
best practices for implementing and choosing design patterns, as well as maintaining a balance
between pattern use, simplicity, and maintainability.

### Best Practices for Implementing and Choosing Design Patterns

1. **Understand the Problem**: Before choosing a design pattern, thoroughly understand the problem
   or requirement. Ensure that the pattern fits the problem context.

2. **Know the Patterns Well**: Familiarize yourself with various design patterns. Understanding the
   intent, applicability, consequences, and implementation of different patterns is crucial for
   their effective use.

3. **Consider Maintainability and Readability**: Choose patterns that improve code readability and
   maintainability. Avoid using complex patterns for simple problems.

4. **Start with Simplicity**: Start with the simplest solution. Opt for a design pattern only if the
   simple solution doesn’t meet your needs (e.g., scalability, performance).

5. **Avoid Overusing Patterns**: Overusing design patterns can lead to unnecessary complexity. Use
   patterns only when they provide a clear advantage.

6. **Evaluate Pattern Applicability**: Assess if the chosen pattern is suitable for your use case.
   Consider factors like project size, performance requirements, and future maintenance.

7. **Refactor as Needed**: Be open to refactoring existing code to implement a design pattern if it
   leads to better code organization and maintainability.

8. **Pattern Combinations**: Sometimes combining multiple patterns can provide a more effective
   solution than using a single pattern.

9. **Document the Use of Patterns**: Documenting where and why a pattern was used helps future
   maintainers understand the design decisions.

### Balancing Pattern Use with Simplicity and Maintainability

1. **Avoid Premature Optimization**: Do not use a design pattern solely for anticipated future
   needs. Over-engineering can lead to complex and hard-to-maintain code.

2. **Focus on the Problem, Not the Pattern**: The primary goal is to solve a problem effectively,
   not to use a pattern. Patterns are means to an end, not an end in themselves.

3. **Assess the Impact on Performance**: Understand the performance implications of a pattern. Some
   patterns, while structurally sound, might introduce performance overhead.

4. **Prioritize Code Clarity**: The use of design patterns should make the code more understandable.
   If a pattern makes the code harder to understand, reconsider its use.

5. **Training and Skill Level**: Consider the skill level of the team. Complex patterns might be
   counterproductive if the team is not familiar with them.

6. **Refactor When Needed**: If a previously used pattern is complicating enhancements or bug fixes,
   consider refactoring to a more suitable pattern or a simpler solution.

7. **Review and Feedback**: Regularly review the use of design patterns in code reviews and take
   feedback from peers to ensure that the use of patterns is beneficial.

### Conclusion

Design patterns are powerful, but their benefits are realized only when used judiciously and
appropriately. Balancing the use of design patterns with the need for simplicity and maintainability
is key to a successful software design. Always start with the simplest solution and evolve your
design as needed, considering the maintainability and future scalability of your application.

## Future of Design Patterns

The future of design patterns in software development is influenced by emerging trends and the
evolving landscape of technology. While the fundamental principles behind design patterns remain
relevant, their application and significance continue to adapt with the changing times.

### Emerging Trends and the Future of Design Patterns

1. **Cloud Computing and Microservices**: The rise of cloud computing and microservices architecture
   has led to the emergence of new patterns focused on distributed systems. Patterns related to
   resilience, scalability, and cloud-native applications are gaining prominence.

2. **Containerization and Orchestration**: With technologies like Docker and Kubernetes, patterns
   around container management, service discovery, and continuous deployment are increasingly
   important.

3. **Reactive and Asynchronous Programming**: As applications become more responsive and real-time,
   reactive programming patterns are becoming essential. Patterns that deal with asynchronous data
   streams and non-blocking operations are in focus.

4. **AI and Machine Learning**: The integration of AI and ML into software systems is leading to the
   development of patterns that cater to data processing, model training, and inference efficiency.

5. **DevOps and Continuous Integration/Continuous Deployment (CI/CD)**: DevOps practices are
   influencing patterns around automation, monitoring, and rapid deployment.

6. **Front-End Frameworks and SPA**: Modern front-end frameworks (React, Angular, Vue.js) and Single
   Page Applications (SPAs) bring patterns related to state management, component lifecycle, and
   virtual DOM.

7. **Functional Programming**: With the rising popularity of functional programming languages and
   paradigms, patterns that emphasize immutability, statelessness, and function composition are
   becoming more prevalent.

8. **Security and Privacy**: As cybersecurity threats evolve, design patterns that emphasize secure
   design, data privacy, and secure communication are becoming increasingly critical.

### Wrap-Up and Final Thoughts

Design patterns are not static; they evolve with technology trends and industry demands. The core
principle of design patterns, which is to provide reusable solutions to common problems, remains
unchanged. However, the nature of these problems evolves as new technologies emerge.

In the future, we can expect to see a continued adaptation and evolution of design patterns. As
fields like cloud computing, AI, and reactive programming mature, they will inevitably give rise to
new patterns and best practices. Furthermore, the integration of design patterns with modern
development methodologies like Agile and DevOps will continue to shape their application in software
development.

The key for developers and software architects is to stay informed about these changes and continue
learning. Embracing new patterns and practices, while understanding their underlying principles,
will be essential for building efficient, scalable, and robust software systems in the future.

In summary, design patterns will continue to play a vital role in software development, adapting to
new technologies and methodologies, and providing time-tested solutions to emerging challenges in
software design and architecture.

## Glossary of Terms

**Singleton**: Ensures a class has only one instance and provides a global point of access to it.

**Factory Method**: Defines an interface for creating an object but lets subclasses decide which
class to instantiate.

**Abstract Factory**: Provides an interface for creating families of related or dependent objects
without specifying their concrete classes.

**Builder**: Separates the construction of a complex object from its representation, allowing the
same construction process to create different representations.

**Prototype**: Creates new objects by copying an existing object, known as the prototype.

**Adapter**: Allows incompatible interfaces to work together. It involves a wrapper that converts
one interface to another.

**Decorator**: Dynamically adds responsibility to an object in a transparent manner without
affecting other objects.

**Proxy**: Provides a surrogate or placeholder for another object to control access to it.

**Composite**: Composes objects into tree structures to represent part-whole hierarchies, allowing
clients to treat individual objects and compositions uniformly.

**Observer**: Defines a one-to-many dependency between objects so that when one object changes
state, all its dependents are notified and updated automatically.

**Strategy**: Defines a family of algorithms, encapsulates each one, and makes them interchangeable.
Strategy lets the algorithm vary independently from clients that use it.

**Command**: Encapsulates a request as an object, thereby allowing for parameterization of clients
with different requests, queue or log requests, and support undoable operations.

**State**: Allows an object to alter its behavior when its internal state changes. The object will
appear to change its class.

**Chain of Responsibility**: Passes a request along a chain of handlers. Upon receiving a request,
each handler decides either to process the request or to pass it to the next handler in the chain.

**Memento**: Without violating encapsulation, captures and externalizes an object's internal state
so that the object can be restored to this state later.

**Template Method**: Defines the skeleton of an algorithm in an operation, deferring some steps to
subclasses. Template Method lets subclasses redefine certain steps of an algorithm without changing
the algorithm's structure.

**Visitor**: Represents an operation to be performed on the elements of an object structure. Visitor
lets you define a new operation without changing the classes of the elements on which it operates.

**Mediator**: Defines an object that encapsulates how a set of objects interact. Mediator promotes
loose coupling by keeping objects from referring to each other explicitly, and it lets you vary
their interaction independently.

**Flyweight**: Uses sharing to support large numbers of fine-grained objects efficiently.

**Bridge**: Decouples an abstraction from its implementation so that the two can vary independently.

## Frequently Asked Questions

1. **What are software design patterns?**

    - Design patterns are standard solutions to common problems in software design. They are
      templates or guidelines used to solve issues that are encountered frequently during software
      development.

2. **Why are design patterns important?**

    - Design patterns provide a proven solution to common problems, promote code reusability,
      improve readability, and enhance maintainability.

3. **Can you give examples of some common design patterns?**

    - Common examples include Singleton, Factory, Observer, Strategy, and Decorator patterns.

4. **What is the Singleton pattern?**

    - The Singleton pattern ensures a class has only one instance and provides a global point of
      access to it.

5. **What is the Factory pattern?**

    - The Factory pattern creates objects without specifying the exact class of object that will be
      created.

6. **How is the Strategy pattern used?**

    - The Strategy pattern is used to create a family of algorithms, encapsulate each one, and make
      them interchangeable.

7. **What is the Observer pattern?**

    - The Observer pattern defines a one-to-many dependency between objects so that when one object
      changes state, all its dependents are notified and updated automatically.

8. **What is the Decorator pattern?**

    - The Decorator pattern allows behavior to be added to an individual object, either statically
      or dynamically, without affecting the behavior of other objects from the same class.

9. **What is the difference between Creational, Structural, and Behavioral patterns?**

    - Creational patterns deal with object creation, Structural patterns deal with object
      composition, and Behavioral patterns characterize the ways in which objects interact and
      distribute responsibility.

10. **Can design patterns be combined?**

    - Yes, design patterns can be combined to solve complex problems.

11. **How do design patterns improve code maintainability?**

    - By using standardized solutions, design patterns make code more organized and understandable,
      thereby easing maintenance.

12. **Are design patterns language-specific?**

    - No, design patterns are not specific to any programming language. They are concepts that can
      be implemented in any language.

13. **What is the Model-View-Controller (MVC) pattern?**

    - MVC is a design pattern used to separate application's concerns into three parts: the model
      (data), the view (user interface), and the controller (business logic).

14. **What is the Adapter pattern?**

    - The Adapter pattern allows the interface of an existing class to be used as another interface.

15. **How does the Builder pattern work?**

    - The Builder pattern separates the construction of a complex object from its representation,
      allowing the same construction process to create different representations.

16. **What is the Prototype pattern?**

    - The Prototype pattern is used to create duplicate objects while keeping performance in mind.
      It involves copying existing objects.

17. **How do design patterns differ from frameworks or libraries?**

    - Design patterns are guidelines for solving common problems, while frameworks and libraries are
      concrete implementations that you can directly use in your code.

18. **Are design patterns only useful for object-oriented programming?**

    - While they are most commonly used in object-oriented programming, some patterns can be
      applicable in other programming paradigms as well.

19. **Can design patterns be harmful if misused?**

    - Yes, inappropriate use of design patterns can lead to overly complex code and can degrade
      performance.

20. **How should one choose an appropriate design pattern?**
    - The choice should be based on the specific problem being solved, considering factors like the
      application’s design, maintainability, and performance requirements.
