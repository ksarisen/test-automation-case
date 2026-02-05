## CI Execution with Selenium Grid 4

This project is executed via Jenkins running inside Docker.
Tests are executed on Selenium Grid 4 using RemoteWebDriver.

### Architecture
- Jenkins (Docker)
- Selenium Grid 4 (Hub + Chrome/Edge Nodes)
- Maven + Cucumber + TestNG

### Execution Flow
1. Jenkins triggers the build
2. Maven runs test suite
3. RemoteWebDriver connects to `selenium-hub:4444`
4. Tests execute on Grid nodes

### Proof
- Jenkins build success screenshot
- Selenium Grid UI showing active sessions
