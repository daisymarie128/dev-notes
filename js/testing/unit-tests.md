## Unit Testing
Unit tests ensure that individual components work in isolation from each other. Units are typically modules, functions, classes etc…<br>
Unity tests should deliver realtime developer feedback. This is a key concept of what a unit test should be because the tests should be run lightning fast. Asynchronous operations such as network and file I/O should be avoided in unit tests.

An example of a unit test would be if your app needed to handle different routes, you would right a unit test to check the URL and make sure that the relevant handle is being sent.

However if you wanted to check if something was posted to a specific URL and then check a database for a change that would not be a unit test.. Instead this would be and integration test

Your unit tests should be:
- Dead simple.
- Lightning fast.
- A good bug report.

When tests fail you want to be able to quickly see these key things:<br>
- Which component is being tested? – displayed in console
- What should this component do? – displayed in console
- What was the actual result? – displayed in console
- What is the expected result? – displayed in console
- How is the behaviour reproduced? – This doesn't need to be seen in the console, but instead your test should be written clearly to explain this.
