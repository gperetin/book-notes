# Chapter 6: Object-Oriented Style

* 2 main heuristics to guide the structuring of the program:
  * **separation of concenrns**
    * gather together code that changes for the same reason
  * **higher level of abstractions**
    * avoid complexity by working on a higher level of abstraction
* using these 2 will push the design towards something like ports and adapters
  architecture (http://alistair.cockburn.us/Hexagonal+architecture)
  * code for the business domain is isolated from its dependencies (eg.
    databases or user interface)
* we implement bridges to map between the application core and each technical
  domain (adapters in Hexagonal architecture)
  * for example, a bridge might map an order book object to SQL statements
    that persist those in a database
* **encapsulation**
  * ensures that the behavior of an object can only be affected through its
    API
* **information hiding**
  * conceals how object implements its functionality behind the abstraction of
    the API
* **object peer stereotypes**
  * dependencies - services that the object requires from its peers so it can
    perform its responsibilities; object cannot function without these
  * notifications - peers that need to be kept up to date with object's
    activity; notifications decouple objects from each other
  * adjustments - peers that adjust object's behavior to the wider needs of
    the system
* **context-independence**
  * system is easier to change if its objects are context-independent; each
    object should have no built-in knowledge about the system in which it
    executes
  * whatever an object needs to know about the larger environment it's running
    in must be passed in
