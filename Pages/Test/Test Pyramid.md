# Test Pyramid

The test pyramid consists of three main levels:

1. **Unit Tests:** These are low-level tests that focus on testing individual units of code, such as functions or methods, in isolation. Unit tests are the foundation of the test pyramid and should make up the majority of tests in a codebase. They are fast to execute, easy to write and maintain, and provide rapid feedback during the development cycle.
2. **Integration Tests:** Integration tests verify the correct interaction and communication between different components or modules of the system. They test the integration points between units and ensure that the system works as expected when multiple units are combined. Integration tests are more complex and time-consuming than unit tests but still faster than end-to-end tests.
3. **End-to-End (E2E) Tests:** E2E tests simulate real-world scenarios by testing the entire application from start to finish, including all components and external dependencies. These tests ensure that the system behaves correctly from the user's perspective and validate the overall system functionality. E2E tests are the most comprehensive but also the slowest and most expensive to execute.

The test pyramid emphasizes having a larger number of unit tests at the base, followed by fewer integration tests, and even fewer end-to-end tests at the top. This distribution ensures that the majority of testing efforts are focused on low-level, fast, and isolated tests, while still providing adequate coverage for higher-level system behaviors.
