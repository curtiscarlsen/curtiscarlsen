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

Abstract method calls for classes.  Traditional implementation for this pattern uses Accept and pointers which tends to be quite slow and complicated.  A new suggestion from 'Design Patterns and Principles' is to use std::variant as a type-safe union, allowing us to use one abstracting object to access objects of different types.  

## Adaptor Pattern

Adapts the interface of one object to another.  Implemented as a wrapper class around the original class.