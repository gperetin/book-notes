# Chapter 5: Maintaining the Test-Driven Cycle

* start each feature with an acceptance test!
* acceptance test is written in a the language of the domain (not the
  underlying technology)
* unit and integration tests support the development team, should run quickly,
  and should always pass
* start testing with the simples success case
* always watch the test fail first, with an expected message
* develop from the inputs to the outputs
  * when starting a new feature, consider the event coming into the system
  that will trigger this new behavior
  * we work our way through the system - from the object that receives the
  external event, through the intermediate layers, to the central domain model
* **unit-test behavior, not methods**
  * focus on the features that the object under test provides
