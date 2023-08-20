# SOLID design principles

## Single Responsibility per class

## Open to extension, closed to change
classes should be able to extend where needed without recoding the class

## Liskov Substitition Principle
subclasses should be directly substitutable for the base class

## Interface Segregation Principle
sub-classes should not have to define interfaces they do not use
make interface features separate classes and inherit from those classes as needed for each subclass

But this requires multiple inheritance which is not allowed at RB...

## Dependancy Inversion Principle

classes should not directly depend on other classes, but abstractions (reference pointers) of those classes, so that the class being used can be substituted with a derived class.

