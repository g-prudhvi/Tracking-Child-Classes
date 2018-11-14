# Tracking-Child-Classes

This recipe allows a base class to keep track of the child classes that inherit from it using a metaclass.
Every new-style Python class keeps track of its immediate child classes through the __subclass__ method. However, in most cases we also want to know about the grandchildren etc. This is an example of how that can be achieved using metaclasses. An alternative approach could be to walk through the items returned by __subclasses__().

The base class is given the meta class, and the meta class extends the baseclass with a variable 'child_classes'. This variable is a dictionary containing name:class pairs.

A nice feature is that this also works if the child class is located in a different module than the base, unlike some other ways I have seen of finding child classes. However, it can not handle two classes with the same names but in different modules.

It works also during runtime: every time a new child is created, it is added.
