# Web UI Automation Project

This project is a Web UI Test Automation framework developed as part of a technical case study.

## 🛠 Technologies Used

- **Java 21**
- **Selenium WebDriver**
- **TestNG** (parallel execution)
- **Cucumber BDD**
- **Maven**
- **Docker**
- **Selenium Grid 4**
- **Jenkins**
- **Cucumber Reports (Jenkins Plugin)**

---

## 📁 Project Structure

```text
web-ui-automation
├── docker-compose.yml
├── pom.xml
├── README.md
└── src
    └── test
        ├── java
        │   └── com
        │       └── vakifbank
        │           ├── hooks
        │           │   └── Hooks.java
        │           ├── pages
        │           │   ├── BasePage.java
        │           │   └── BookStorePage.java
        │           ├── runners
        │           │   └── TestRunner.java
        │           ├── stepdefinitions
        │           │   ├── AlertsSteps.java
        │           │   ├── InvalidNavigationSteps.java
        │           │   ├── PracticeFormSteps.java
        │           │   └── BookStoreSteps.java
        │           └── utils
        │               └── DriverManager.java
        └── resources
            └── features
                ├── alerts.feature
                ├── book_store.feature
                ├── invalid_navigation.feature
                └── practice_form.feature
```

---

## ✅ Implemented Test Scenarios

- Book Store list validation (row count & book details)
- Practice Form validation
  - Only mandatory fields
  - All fields filled
- Alert popup validations
- Invalid menu navigation (negative scenario)

Each scenario includes necessary validations as required by the case.

---

## 🧵 Parallel Execution

- Parallel execution is enabled using **TestNG**
- Each scenario runs with its own WebDriver instance via `ThreadLocal`
- Fully compatible with Selenium Grid 4

---

## 🌐 Selenium Grid 4 (Docker)

Selenium Grid 4 is executed using Docker containers:

- `selenium/hub`
- `selenium/node-chrome`
- `selenium/node-edge`

Tests are executed remotely via `RemoteWebDriver`.

Browser selection is controlled using a Maven parameter:

```bash
mvn verify -Dbrowser=chrome
mvn verify -Dbrowser=edge
```

---

## 🧪 Driver Management
- Centralized DriverManager
- Uses ThreadLocal<WebDriver> for parallel safety
- Supports Chrome and Edge
- No usage of Thread.sleep() (explicit waits only)

---

## 📸 Screenshot on Failure
- Screenshots are captured automatically for failed scenarios
- Implemented using a Cucumber @After hook
- Screenshots are attached directly to the Cucumber scenario
- Visible inside the Cucumber HTML report in Jenkins

📍 Location in report:
    Scenario → Hooks → After → Embedded image (png)

---

## 📊 Reporting
Jenkins Cucumber Report
- Jenkins Cucumber Reports Plugin is used
- Reports are generated from cucumber-report.json
- Includes:
    - Scenario status
    - Step details
    - Charts
    - Embedded screenshots for failed scenarios

---

## 🚀 Jenkins Integration
- Jenkins Freestyle Job
- Pulls latest code from GitHub repository
- Runs tests using Maven (verify phase)
- Executes tests on Selenium Grid 4
- Publishes Cucumber HTML reports automatically

---

## ▶️ How to Run Locally
- Prerequisites:
    - Java 21
    - Maven
    - Docker & Docker Compose

Start Selenium Grid

```bash
docker-compose up -d
```

Run Tests

```bash
mvn verify -Dbrowser=chrome
```

---

## 📝 Notes

- All requirements defined in the case study are fully implemented
- Framework is scalable and easily extendable
- Clean architecture using Page Object Model
- CI-ready with Jenkins and Docker-based Grid

---

## 👤 Author
Kerem Sarısen