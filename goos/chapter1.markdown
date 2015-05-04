# Chapter 1

* everyone involved in a software project has to learn as it progresses
* it's critical to deploy work after each dev cycle to get complete feedback
* benefits of TDD (writing tests before the code)
  * forces us to clarify the acceptance criteria
  * encourages writing losely coupled components
  * adds an executable description of what the code does
  * adds to complete regression suite

* start a new feature by writing an acceptance test
* whenever possible, acceptance test should exercise the system end to end, without
    calling internal code

* levels of testing:
  * Acceptance: Does the whole system work?
  * Integration: Does our code work against the code we can't change?
  * Unit: Do our objects do the right thing, are the easy to work with?

* integration tests make sure that abstractions we build over 3rd party code
  work as expected
