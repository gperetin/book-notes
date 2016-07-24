# Chapter 2: Test Driven Development with Objects

* OO design focuses on the communication between objects, more than on the
  objects themselves
* values and objects
  * objects also known as entities
  * values are immutable instances that model fixed quantities
  * objects use mutable state to model their behavior over time
  * system is split into 2 worlds: values (which are treated functionally),
    and objects (which implement stateful behavior of the system)
* **communication patterns** - set of rules that govern how a group of objects
  communicate, eg. the roles they play and the messages they can send
* **domain model** is in the communication patterns!
* **tell don't ask**
  * calling object should describe what it wants in terms of the role that its
    neighbor plays, and let the called object decide how to make that happen
  * this makes it easier to swap objects that play the same role
* we sometimes ask, when getting information from values objects and
  collections, or when using a factory to create objects
* since we want to have as few getters on objects as possible, doesn't that
  make testing hard?
  * we use substitutes, or mock objects, to replace target object's neighbors
