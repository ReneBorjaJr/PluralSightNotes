# Plural Sight Notes
## 1) The Benefits of Unit Testing
### Introduction to Unit Testing:
- A unit test is a piece of code written to test small, individual components of a larger system, usually not the whole system at once.
- The target code tested could be a Java class, a single method, or a static function.
- Sometimes, unit tests may cover several classes, known as component tests.
### Execution and Verification:
- The test code runs the target code and checks its results.
- Verification is often done using assertion methods provided by libraries like JUnit, comparing expected outcomes with actual results.
- Before the advent of unit testing libraries, this process was manual—running the program, providing input, and observing output directly.
### Benefits of Unit Testing:
- **Immediate Feedback:** Unit tests provide quick verification of whether a small unit of code performs as expected, allowing for early detection of issues.
- **Facilitates Development:** Allows testing of parts of the system as they are developed, even if the full system isn’t complete. For example, a sorting algorithm needed in a larger system can be tested independently.
- **Regression Testing:** Serve as automated regression tests to ensure all parts of the system function correctly before deployment.
- **Aids in Design:** Tests can reveal how parts of the system will interact and whether the interfaces are clear and understandable.
  - If a unit is hard to test, it might indicate underlying design issues that need attention.
- **Increases Programmer Confidence:** Having a suite of passing tests makes it safer and more appealing to refactor or improve code, knowing that any introduced errors will be caught.
- **Documentation:** Unit tests provide practical documentation of how parts of the system are intended to function, offering examples of usage and behavior.
### Conclusion:
- Unit tests are not only about detecting errors but also about improving design, facilitating development, and ensuring system reliability. They also function as useful documentation for other developers.
## 2) Demo: Setting up JUnit 5 in an IDE
### IntelliJ Setup for JUnit 5
1. Project Requirements
  - Ensure the project is set up with at least Java 8 as JUnit 5 requires Java 8 or newer.
2. Open Module Settings
  - Navigate to the module settings to confirm the project's language level is set to Java 8.
  -Verify that separate directories for application code (src) and test code (test) are set up.
3. Adding JUnit 5 Dependency
  - Go to the Dependencies tab in module settings to manage third-party libraries (JAR files).
  - Instead of manually adding JAR files, use IntelliJ's integrated feature by attempting to write a test.
  - When prompted to create a test class for a production class without existing tests, choose to create one.
  - IntelliJ will automatically detect the absence of JUnit 5 in the module dependencies and offer to fix it.
  - Select "Fix," and IntelliJ will search Maven Central for JUnit 5 JARs.
  - Choose the desired version of JUnit and confirm to add it to the project's dependencies.
4. Verification
  - Confirm the addition of necessary JUnit 5 JAR files in the project dependencies.
  - A test class is automatically created, ready for writing tests.
### Test Setup and Annotation:
- Test methods are annotated with **@Test**, indicating their role in the testing framework.
### Additional Resources
1. JUnit 5 Official Documentation
- Visit the JUnit 5 website at [junit.org/junit5](junit.org/junit5) for comprehensive guides and documentation.
- Explore sections on IDE support and the Console Launcher for alternative ways to run JUnit tests.
2. Maven Central
- JUnit JARs can be downloaded from Maven Central at [mvnrepository.com](mvnrepository.com) under the artifact **'org.junit'**.
## 3) Your Sample System
### No notes for this
## 4) Demo: Writing Your First JUnit 5 Test
### Steps to Create the Test
1. **Integration of JUnit 5:**
- Verify JUnit 5 is included in the project dependencies.
2. **Creating a Test Class in IntelliJ:**
- Use IntelliJ's testing feature to automatically generate a test class for the targeted business logic class.
3. **Annotating Test Methods:**
- Mark methods with the **'@Test'** annotation to designate them as test methods.
4. **Structure of a Test Method:**
- **Instantiate necessary classes:** Begin by creating instances of the class under test.
- **Perform actions:** Use methods of the class to simulate typical usage scenarios.
- **Retrieve and store results:** Capture outputs or changes in state resulting from the above actions.
5. **Assertions to Verify Outcomes:**
- **Check for non-null values:** Ensure important objects or results are not null using assertNotNull.
- **Validate expected results:** Use **'assertEquals'** to compare expected outcomes with actual results.
### Understanding Annotations
- **Purpose of Annotations:** Provide metadata about the methods; they don't change execution flow but guide the testing framework.
### General Testing Pattern
- **Setup:** Prepare any necessary objects and state before the main actions.
- **Execute:** Run the functions or methods that are the focus of the test.
- **Verify:** Apply assertions to confirm that the outcome matches expectations.
### Execution and Review
- **Run the Test:** Execute the test using IntelliJ's built-in test running capabilities to check for passes or failures.
- **Evaluate Results:** Analyze the outcomes and refine the tests or the underlying code as necessary.
## 5) Demo: Executing Your Test and Interpreting Results
### Introduction to Test Execution and Initial Run
- Initiate the test execution through the IDE by using the context menu on the test method.
- A results panel will display with a list of executed tests and console outputs, showing whether the tests passed or failed.
### Expanding the Test
- Incorporate additional assertions to confirm the consistency and correctness of the data.
- Utilize appropriate data formatting tools to validate data formats.
- Adjust the access level of the test method as necessary based on its package alignment with the class being tested.
### Observing Test Success
- Re-run the test after enhancing it with new assertions to verify continued success.
### Introducing a Test Failure
- Modify the test by removing or altering a critical operation to simulate a test failure.
### Benefits of Early Problem Detection Through Unit Tests
- unit tests can identify issues early, reducing the need for more time-consuming troubleshooting methods.
### Immediate Feedback from Unit Tests
- Unit tests provide rapid feedback through error messages and stack traces, allowing for quick navigation to problem areas.
### Efficient Problem Resolution
- Make iterative adjustments directly in the test code to quickly verify fixes without extensive manual testing.
### Future Improvements to the Test
- Plan to revisit and refine the test to ensure thorough coverage and robustness.

## 6) Applying Assertions

## Assertions Used
- **assertNotNull and assertEquals**: Used for basic value comparisons.
- **assertSame and assertNotSame**: Checks if two references point to the same or different objects, ideal for validating instance uniqueness.
- **assertTrue and assertFalse**: Used for validating boolean conditions.

## Testing Features
- **Feature Testing**: Involves testing methods that check for specific conditions, such as the presence of scheduled appointments.

## Assertion Techniques
- **assertEquals on Collections**: Used for comparing two collections to see if they contain equivalent elements in the same order.
- **assertIterableEquals**: Compares the contents of different collection types that can be iterated over.

## Workflow Enhancements
- **Refactoring**: Focus on simplifying methods by extracting repetitive logic into separate methods for better maintainability and readability.

## 7) Demo: Setting up and Tearing Down Tests
## Overview
- JUnit 5 supports setting up and tearing down tests using lifecycle annotations.
- These operations prepare the testing environment before tests run and clean up after tests.

## Lifecycle Annotations
- **@BeforeAll**: Executes once before all test methods in the class; usually static.
- **@BeforeEach**: Executes before each test method.
- **@AfterEach**: Executes after each test method.
- **@AfterAll**: Executes once after all test methods in the class have completed; usually static.

## Usage Context
- Lifecycle methods can be named arbitrarily as long as the correct annotations are used.
- Commonly, setup activities are needed before test methods to initialize necessary objects or state.

## Practical Application
- For a patient intake system, repeated instantiation of objects like calendars can be moved from test methods to a setup method.
- **@BeforeEach** can be used to initialize such objects, reducing redundancy across test methods.
- Instance fields (e.g., a calendar object) should be used for objects needed across multiple test methods.
- Cleanup and reset operations are vital for ensuring a clean state for each test, especially when tests have side effects (like altering a database).

## Example Flow
- Initialize global resources in a method annotated with **@BeforeAll**.
- For each test, initialize specific resources with **@BeforeEach**, run the test, then clean up with **@AfterEach**.
- After all tests, release global resources with **@AfterAll**.

## Running Tests
- Run tests to ensure that the setup and teardown processes do not interfere with the expected outcomes.
- Utilize console outputs (e.g., `println`) in lifecycle methods to trace the execution flow during test runs.

## Conclusion
- Setting up and tearing down are essential for managing test environments, especially to handle side effects and ensure reliable test outcomes.
- Customizing lifecycle methods according to the test needs can greatly enhance the efficiency and clarity of the testing process.

