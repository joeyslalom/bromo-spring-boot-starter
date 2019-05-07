
# Java Coding Standards

_These coding standards are goals, not a list of rules to be followed rigidly when delivering or reviewing code. Read them over once in a while, get a feel for what the goals are, and be a conscientious software engineer._

A reasonable coding style can be found at the [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)

The `google_checks.xml` file in this repository comes from the [Checkstyle git repository](https://github.com/checkstyle/checkstyle/blob/master/src/main/resources/google_checks.xml).

## General
* Favor immutability!
* Strive for simplicity as complexity is often costly and frail
* Strive for quality and supportability as these distinguish good code from bad code and are most often achieved via simplicity
* Remember the purpose of code is to communicate between systems but also to other developers
* Projects must be IDE-agnostic
* Use the latest version of JDK 8

## OO Constructs
* Avoid inheritance, favor composition
* Avoid deep levels of inheritance and mixing of classes and interfaces
* Favor immutable value objects initialized at construction
* Use the Builder pattern instead of public setters for complex construction scenarios
* Prefer instance properties marked private and final

## Functional Constructs
* Use Optional instead of null for return types
* Use functional interfaces and lambdas where it simplifies the code; consider refactoring towards a more functional style if necessary

## Dependency Injection
* Use constructor injection for container-managed objects; instances should be immutable
* Every class for container-managed objects should implement an interface; abstractions help with refactoring and testing
* Configuration values can be injected into Spring Beans, also leverage Spring profiles

## Testing
* Mocking at the boundaries of the service is a best practice to deal with error states and the unexpected
  * mocking enables large testing coverage at the unit/functional levels of a service driving increased quality as branch and statement coverage is considered and tested in-depth by the developer.
  * mocking increases overall speed of delivery as the code/test/fix cycle is fast when done by development
  * mocking enables error/exception injection and testing scenarios that would be difficult if not impossible with concrete dependencies
  * mocking can enable performance evaluations of individual services at early stages in development
* Mocking code should be reviewed and written with care as a bug the mock could result in a defect to slip through to later testing stages
* Mocking is not a substitution for later testing stages (integration, performance/concurrency) but greatly can reduce the time, effort, and cost of those stages  
* Write unit tests, but unit tests should not require a container! See: [Spring Framework Unit Testing](https://docs.spring.io/spring/docs/current/spring-framework-reference/testing.html#unit-testing)
* In contrast, Spring Boot Tests - which start the application context - are also useful in finding runtime issues.
* Finally, Smoke Tests are helpful for asserting basic functionality is working
* A project with all three styles of tests (unit tests, spring boot tests, and smoke tests) provides greater assurance
the service is functioning properly.

## Documentation
* Prefer language-neutral files for interfaces, e.g., swagger or protobuf
* Every public method whose purpose isn't fully documented by its name must have at least a 1-line descriptive JavaDoc
* Write a README for the repository that explains the project's purpose, its data-flow, how to set it up, how to deploy it, how to test it

## Libraries
* Libraries needed only for testing should be given "test" scope in the building tool
* Use the latest versions of open source libraries and stay up-to-date with its releases.

## GitHub

* Ensure `master` branch is protected, so commits to those branches must first go through the validation
and PR approval process.
* Use a CODEOWNERS so the team is aware of pull requests, and use a GitHub team.  https://help.github.com/categories/setting-up-and-managing-organizations-and-teams/
* Ensure the GitHub repo is also part of the GitHub team.

## Builds

* Use the Gradle Wrapper when creating a project and running the build.  The wrapper should also be included in version
 control.  https://docs.gradle.org/current/userguide/gradle_wrapper.html
* Google's Error Prone compiler provides code analysis to find common mistakes.  https://errorprone.info/
* Checkstyle enforces a consistent coding standard.
* Use jacaceo for code coverage, which has native Gradle support.  https://docs.gradle.org/current/userguide/jacoco_plugin.html
* All tests are written using JUnit 5.  Smoke tests can also use JUnit5 with the `Junit5Runner` included in the starter.
 https://junit.org/junit5/docs/current/user-guide/


### Value objects
* Use a tool such as Google's AutoValue to create value objects.  https://github.com/google/auto/tree/master/value
* Keep value objects in their own module in the multi-module build so the tool's implementation remains encapsulated.


### Spring Profiles and Properties
* Configuration should be externalized using Spring's application.properties.
* This allows values to be overridden by environment variables or by profiles.
* Spring Boot projects commonly use a `local` profile for development.
* https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-external-config.html


### Swagger
* When working with REST endpoints, Swagger provides a helpful standard to document the interface and generate the model
and API classes.
* Keep Swagger objects in their own module in the multi-module build so the tool's implementation remains encapsulated.
