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
## 7) Applying Assertions
### Initial Setup and Testing
- Utilize **'assertNotNull'** and **'assertEquals'** for basic string comparisons in the initial test.
- Confirm the working condition of the initial unit test.
- Introduce an intentional failure by altering the expected first name to trigger an assertion failure.
- Utilize IntelliJ's comparison tool to highlight differences in strings, particularly useful for differences involving whitespace.
### Exploring Additional Assertions
- Use **'assertSame'** to confirm that two variables refer to the exact same object in memory, useful for enums where instances are inherently unique.
- Utilize **'assertNotSame'** to ensure that objects meant to be copies are not the same instance as the original.
### Testing New Features
- Focus on the ClinicCalendar class which includes a new hasAppointment method.
  - Method checks if there are appointments on a specified day, returning true if appointments exist.
- Create tests using assertTrue and assertFalse to verify the functionality of hasAppointment.
### Testing Collection-Based Features
- Demonstrate a new feature integrating today's appointments into the user interface.
- Conduct manual testing by entering and verifying appointments for today and other days.
- Implement JUnit tests to automatically verify today's appointments against manual entries.
### Advanced Collection Assertions
- Use **'assertEquals'** to compare expected appointments against all appointments, expected to fail when non-today appointments are included.
- Apply **'assertIterableEquals'** for comparing collections of objects, ensuring both equivalence and order are correct.
### Code Refactoring
- Isolate and refactor date pattern conversion logic from the addAppointment method into a new method, convertToDateFromString.
- Consider moving the new method to a utility class for broader use.
- Re-run tests to ensure no functionality was broken during refactoring.
### Conclusion and Next Steps
- Summarize the new assertions and their utility in enhancing testing capabilities.
- Highlight plans for further structuring tests, including setup and teardown processes.
## 8) Demo: Setting up and Tearing Down Tests
### Introduction to Test Setup and Teardown
- Setting up and tearing down are processes done before and after tests run.
- JUnit 5 supports these processes through specific lifecycle annotations.
### Lifecycle Annotations Explained
- **@BeforeAll:** Runs once before all test methods in the class. Must be static unless explicitly overridden.
- **@BeforeEach:** Runs before each test method.
- **@AfterEach:** Runs after each test method.
- **@AfterAll:** Runs once after all test methods are completed. Like @BeforeAll, typically needs to be static.
### Application Example: Patient Intake System
- Discuss setup for a sample patient intake system using lifecycle annotations.
### Implementation Details
- Example method initAll() runs first, before all tests due to @BeforeAll.
- init() method runs before each test method because of @BeforeEach annotation.
- tearDown() method runs after each test method due to @AfterEach.
- tearDownAll() method, annotated with @AfterAll, runs last after all tests are finished.
### Practical Usage
- Common usage is setting up before tests, such as initializing shared resources.
- Example from ClinicCalendar test:
  - Previously, each test method created a calendar instance.
  - Moved calendar instantiation to a @BeforeEach method named init to avoid redundancy.
  - Converted the calendar from a local variable in each test method to an instance field, accessible across all tests.
### Enhancements for Visibility
- Added print statements in each lifecycle method and test method to trace execution flow and order in the console.
### Considerations for Further Lifecycle Methods
- Although not required for the calendar test scenario, additional lifecycle methods (@BeforeAll, @AfterEach, and @AfterAll) were implemented to demonstrate their use.
- Mentioned the aesthetic preference for placing teardown methods at the bottom of the class but noted it's not necessary.
### Final Testing and Observations
- Executed tests to confirm the proper order of lifecycle methods and ensure the setup and teardown processes were correctly implemented.

