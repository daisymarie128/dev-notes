## Testing
There are 3 different types of tests, all with different purposes but all should usually always be used in your project. It's better to split these tests up and organise and run them separately.

#### Testing Types:
**Unit tests** <br>
These tests ensure that individual components of the app work as expected. Assertions test the component API.

**Integration tests** <br>
Integration tests ensure that component collaborations work as expected. Assertions may test component API, UI, or side-effects (such as database I/O, logging, etc…)

**Functional tests** <br>
Functional tests ensure that the app works as expected from the user’s perspective. Assertions primarily test the user interface.

Tests are usually used at different stages of the project and supply different benefits.<br>
**Development stage**<br>
When writing tests during development help with developer feedback and also aid in writing cleaner code. Usually different tests will be run separately at this stage.

**Staging environment**
Running tests in staging detects bugs and problems and can stop the deploy process if something goes wrong. At the stage all tests would be run together to check the whole app is working as expected.

**Production**
Testing in production also referred to as smoke tests help run ensure that none of the critical functionality was broken during the deploy process. – personally I don't quite understand how this is useful? Shouldn't the tests run in staging have already picked up any problems and stopped the deploy process? Would love for someone to clarify this.

Specific tests all have different jobs to do and usually fall into 1 of the 3 categories:
- User experience tests (end user experience)
- Developer API tests (developer experience)
- Infrastructure tests (load tests, network integration tests, etc…)
