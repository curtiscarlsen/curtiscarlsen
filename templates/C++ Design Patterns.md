# SOLID design principles

## Single Responsibility per class

## Open to extension, closed to change
classes should be able to extend where needed without re-coding the class

## Liskov Substition Principle
sub-classes should be directly substitutable for the base class

## Interface Segregation Principle
sub-classes should not have to define interfaces they do not use
make interface features separate classes and inherit from those classes as needed for each subclass

But this requires multiple inheritance which is not allowed at RB...

## Dependency Inversion Principle

classes should not directly depend on other classes, but abstractions (reference pointers) of those classes, so that the class being used can be substituted with a derived class.

# Design Patterns

## Strategy Pattern

move features for a class into their own classes accessed by an internal reference pointer, and the choose the right implementation subclass and supply it as a constructor argument at instanciation.

## Visitor Pattern

Dynamically abstract method calls to contained classes.  Traditional implementation for this pattern uses Accept and pointers which tends to be quite slow and complicated.  A new suggestion from 'Design Patterns and Principles' is to use std::variant as a type-safe union, allowing us to use one abstracting object to access objects of different types.  

## Adaptor Pattern

Adapts the interface of one object to another.  Implemented as a wrapper class around the original class.  If one needs to change the functionality of a class, and there are many instances of the old class, adaptor pattern can be used to wrap the old classes and make them work like new ones without changing the old class.

## Observer Pattern
Create generic classes that monitor classes of events and notifiy interested classes of changes.

has command, receiver, invoker and client objects in its design.  command object manages running the method of the receiver.  invoker calls/triggers the command. receiver implements the actual command code.  client manages the relationships between the other 3 classes.

## Curiously Recurring Template Pattern
Passing the derived class to a base class as a template parameter.  This allows the base class to access elements of the derived class.

* Can be used to implement static mixin classes.


