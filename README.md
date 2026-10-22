# Jenkins CI/CD Pipeline Project

## 1. Project Overview

This project demonstrates the implementation of a Continuous Integration and Continuous Delivery (CI/CD) pipeline using Jenkins. The objective is to automate source code validation, dependency installation, automated testing, and application packaging.

The project uses a simple Python application to demonstrate how Jenkins can automate repetitive software development tasks and help identify errors early in the development lifecycle.

## 2. Development Environment

The project was prepared in an Ubuntu environment running under Windows Subsystem for Linux (WSL2).

| Tool | Version / Configuration |
|---|---|
| Operating environment | Ubuntu on WSL2 |
| Python | 3.12.3 |
| Git | 2.43.0 |
| CI/CD automation server | Jenkins |
| Container platform | Docker |
| Testing framework | pytest |

## 3. Project Structure

```text
jenkins-cicd-project/
├── app.py
├── requirements.txt
├── tests/
│   └── test_app.py
├── screenshots/
├── .gitignore
├── README.md
└── Jenkinsfile
```

The `Jenkinsfile` will be added when the pipeline is implemented.

## 4. Application Description

The application contains a simple Python function that adds two numbers.

The application entry point displays the result of adding 2 and 3.

Expected application output:

```text
CI/CD demo: 2 + 3 = 5
```

## 5. Python Virtual Environment

A Python virtual environment is used to isolate project dependencies from the system-wide Python installation.

Create the virtual environment:

```bash
python3 -m venv .venv
```

Activate it:

```bash
source .venv/bin/activate
```

When activated, the terminal displays `(.venv)` in the command prompt.

## 6. Dependency Installation

The project uses `pytest` as its automated testing framework. The dependency is specified in `requirements.txt`.

Install the required dependency with:

```bash
python -m pip install -r requirements.txt
```

## 7. Automated Testing

The application includes two unit tests:

- `test_add`: verifies the addition of positive numbers.
- `test_add_negative_numbers`: verifies the addition of negative numbers.

Run the tests using:

```bash
python -m pytest -v
```

**Test results:** Pending execution and verification.

**Expected result:** 2 tests pass successfully.

## 8. Application Execution

Run the application using:

```bash
python app.py
```

Expected output:

```text
CI/CD demo: 2 + 3 = 5
```

**Execution status:** Pending verification.

## 9. Evidence and Screenshots

Screenshots will be collected throughout the project to document the implementation and validate the results.

Planned evidence includes:

- Jenkins container running.
- Jenkins dashboard.
- GitHub repository and source code.
- Jenkinsfile and pipeline stages.
- Successful build and automated test results.
- Successful artifact packaging or test deployment.
- Automatic build trigger configuration.

Screenshots will be stored in the `screenshots/` directory.

## 10. Challenges and Lessons Learned

Challenges encountered and their resolutions will be documented as the project progresses.

Key learning objectives include working with Jenkins, Docker, Git, pipeline-as-code, automated testing, secure credentials management, and GitHub integration.

## 11. Project Status

The development environment has been verified, and the initial Python application and test files have been prepared.

The next steps are to validate the application locally, push the source code to GitHub, implement the Jenkinsfile, and execute the complete CI/CD pipeline.

