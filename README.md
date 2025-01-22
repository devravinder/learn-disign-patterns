# [Design Patterns](https://refactoring.guru/design-patterns/creational-patterns)

Note:-
- important one are highlighted with `backtics`


## Creational Design Patterns
- to create objects

- `Singleton`:-
    - to create a single instance of a class
    - to ensure that a class has only one instance
    - use case:-
        - logger

- `Factory`:-
    - to create object/objects through a common interface
        - but we can get the required type of object...based on the input or configuration
    - Defines an interface for creating objects
        - but lets subclasses alter the type of objects that will be created
    - `DAO Factory`:-
        - JPA Factory & DAO objects specific to each database

- `Abstract`:-
    - hide the complexity of creating objects from the user
        - create objects without specifying the class to create
    - `Abstract Factory`:-
        - create a `group of related objects` without specifying their concrete classes
        - use case:
            - Cross-Platform UI Elements: In applications that need to support multiple operating systems (e.g., Windows, macOS),

            - Zalaris Helpdesk Extensions:-
                - can be extended to integrate Azure Devops, SAP, Helpdesk Sonic, etc

- `Builder`:-
    - create complex objects step by step
    - Separates the creation of a complex object from its representation
        - so the same construction process can create different representations

    - use case:-
        - to separate validation logic & business logic...if validation is growing
            - Validation Builder:-
                - this class constructor takes a list of validators
                  - Validator interface...many validation classes
                - when we call validate...
                    - it calls all the validators


- `Prototype`:-
    - create objects by copying existing ones
    - When creating a new object is expensive, and a similar object already exists.
        - eg: Cloning game characters with predefined properties. (eg: war games)
            - TeamMember is interface
              - Two Teams Own & Enemy
              - to create/hire new team members
                - just clone existing team member


## Structural Design Patterns
-  composition and organization of classes and objects to form larger structures

- `Adapter`:-
    - is a structural design pattern that allows objects with `incompatible interfaces to collaborate`.
        - incompatible interfaces allows us to separate the concerns
    - it Converts the interface of one class into another interface that the client expects.
    - it act as a bridge between two incompatible systems
    - eg:
        - A card reader acting as an adapter between an SD card and a laptop.
        - `Port & Adapter pattern ( Hexagonal Architecture )`:-
            -  separation of concerns by decoupling the core business logic from external systems and technologies
            - allows for flexible interaction with various external actors, such as user interfaces, databases, and third-party services, without tightly coupling them to the core application

                - Ports:
                    - interfaces that define how the core application interacts with the outside world
                    - types:
                        - `Incoming Ports`:
                            - Interfaces that the application implements, allowing external actors to invoke operations within the application.
                        - `Outgoing Ports`:
                            - Interfaces that enables the application to communicate with external systems.

                        - eg:

                - Adapters:-
                    - These are concrete implementations of the ports.
                    - They serve as bridges between the external systems and the core application
                    - types:
                        - `Incoming Adapters`:
                            - They convert incoming requests from external sources into a format that the application can understand, invoking the appropriate incoming port.

                        - `Outgoing Adapters`:
                            - They take data from the application and format it for external systems, implementing outgoing ports.



        - eg:
           - client request -> clinetInterface(PORT - interface)
                -  clinetInterface(PORT) implented by clinetInterfaceService ( ADAPTER - implementation)

                - the clinetInterfaceService (ADAPTER) is just bridge
                   - in iteracts with other external systems ( interface/services )



- Bridge:-
    - Decouples an abstraction from its implementation, allowing both to vary independently.
    - moving from inheritance to composition
    - [refer](https://refactoring.guru/design-patterns/bridge)


- `Composite`:-
    - is a structural design pattern that allows you to compose objects into a tree structure to represent part-whole hierarchies.
    - Clients can treat individual objects and compositions uniformly.

    - Eg:-
        - Organization:-
            - Employee
                - Developers
                - Manager
            - Team
            - Project


- `Decorator`:-
    - Adds new behavior to an object dynamically without altering its structure or class definition
        - by wrapping with new interface/classes

    - Eg:-
        - Streams
            - InputStream
                - BufferedInputStream
                    - BufferedFileInputStream


- `Facade`:-
    - Provides a `simplified` interface to a larger and more complex subsystem.
    - Eg:
        - A HotelBookingFacade that combines room booking, meal selection, and transportation into a single interface.

- `Proxy`:-
    - design pattern that lets you provide a substitute or placeholder for another object
    - Use case:-
        - When you want to control access to an object for various reasons
            - e.g., security, logging, lazy initialization

    - eg:-
        - A virtual proxy loading an image only when it is displayed.
        - A proxy for a remote database that caches data locally.
        - Spring AOP (Aspect Oriented Programming)
            - separation of concerns with reflection ( proxy object )

        - Redux-toolkit
            - Immutable.Js
                - to give brand new object on modification
                - so react can re-render



- Flyweight:-
    - to Reduces memory/storage usage by sharing as much data as possible between similar objects
        - typically for objects that are immutable

    - `seperate common parts`
    - `to reduce memory/storage usage`

    - Use Case:-
        - When many similar objects exist, and storing all of them individually would consume too much memory

    - eg:-
        - database normalization rules
            - separating tables



## Behavioral Design Patterns

- `Chain of Responsibility`:-
    - Pass a request along a chain of handlers
    - Use case:
        - Multiple handlers for a single request	& Security filters
    - eg:
        - Logging levels - (INFO → DEBUG → ERROR).
        - `SecurityFilterChain`
        - ValidationBuilder
            - internally uses chain of validations

- `Command`:-
    - is a behavioral design pattern that turns a request into a stand-alone object
        -  that contains all information about the request.
    - This transformation lets you pass requests as
        - a method arguments, delay or queue a request’s execution, and support undoable operations.

    - Use Case:-
        - When you want to decouple the sender of a request from its receiver.

    - eg:
        - TipTop Editor ( React )
            - Undo & Redo
            - Copy & Paste
                - Paste
                    - it will send to TextColor, BackgroundColor, FontSize, FontFamily



- Interpreter:-
    - Defines a language's grammar and provides an interpreter to process sentences in that language
    - Use Case:-
        - When you need to evaluate expressions in a domain-specific language

    - eg:
        - Parsing mathematical expressions or queries



- `Iterator`:-
    - is a behavioral design pattern that lets you traverse elements of a collection
        - without exposing its underlying representation
            - eg: Collection (list, stack, tree, etc.).

- `Mediator`:-
    - is a behavioral design pattern that lets you reduce chaotic dependencies between objects.
    - The pattern restricts direct communications between the objects and forces them to collaborate only via a mediator object
    - eg:-
        - in our Insta-Cred app
            - when LoanRequest is created
                - LoanRequestEvent is created through LoanRequestEventCreator(mediator)
                - direct creation
                - out-box-pattern

- `Memento`:-
    - is a behavioral design pattern that lets you save and restore the previous state of an object without revealing the details of its implementation.

    - Use case:-
        - When you need to implement undo/redo or rollback functionality
        - history

    - eg:-
        - Chess game history
        - undo & redo text editor



- Observer:-
    - Defines a one-to-many dependency between objects
        - so when one object changes state, all its dependents are notified.
    - a subscription mechanism to notify multiple objects

    - eg:-
        - State-management:-
            - Redux toolkit
            - store.subscribe & listener

- `State`:-
    - design pattern that lets an object alter its behavior when its internal state changes
    - It appears as if the object changed its class.

    - Use case:-
        - When an object’s behavior depends on its state, and it needs to change dynamically.
    - eg:
        - A vending machine transitioning between states
            - idle, has money, dispensing

- `Strategy`:-
    - design pattern that lets you define a family of algorithms,
        - put each of them into a separate class, and make their objects interchangeable.


- Use case:-
    - When you need to choose an algorithm at runtime without altering the client code.
    - eg:
        - Sorting algorithms (bubble sort, merge sort).
        - Payment systems offering different payment methods (credit card, PayPal, bank transfer).

- `Template Method`:-
    - defines the skeleton of an algorithm in parent, letting subclasses override specific steps
        - without changing its structure

    - Use case:-
        - When you want to define the structure of an algorithm but allow customization in specific steps
        - eg:
            - Preparing different types of beverages (coffee, tea)
            - Spring Boot starter templates
                - eg: data-jpa

- `Visitor`:-
    - design pattern that lets you separate algorithms from the objects on which they operate
    - adding new operations to existing object structures without modifying their classes
    - widely used in inheritance with overriding & overloading

  eg:-
    - Veterinary Doctor treats animals
        - in treat
            - eat
            - move ( based on object )
                - walk
                - fly
        - Animal
            - Dog
            - Duck
            - Cow
   