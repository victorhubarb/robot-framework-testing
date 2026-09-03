# Robot Framework Testing 🤖

![Status](https://img.shields.io/badge/status-completed-green?style=for-the-badge)
![QA](https://img.shields.io/badge/Robot%20Framework-Automated%20Testing-red?style=for-the-badge)

Automated UI tests written with Robot Framework using BDD-style keywords in Portuguese — testing the Organo React app with SeleniumLibrary, FakerLibrary for dynamic data, and FOR loops for multi-card scenarios.

---

## Overview

This project applies Robot Framework to automate UI tests for the Organo web application. Tests follow a BDD (Behavior-Driven Development) structure with keywords written in Portuguese (`Dado que`, `Então`, `E`) — making test cases readable as plain language. FakerLibrary generates random names, job titles, and image URLs so tests never rely on hardcoded data. The suite covers happy paths (correct form submission, multiple cards, one card per team) and error paths (required field validation).

---

## Architecture

```
robot-framework-testing/
├── robot-framework-organo-main/        # The React app under test (Organo v1)
│   └── src/                            # React source — run locally before executing tests
└── robot-framework-organo-tests/       # Test suite
    ├── resources/
    │   ├── main.robot                  # Imports — SeleniumLibrary + FakerLibrary
    │   ├── pages/
    │   │   └── cadastro.robot          # Page keywords — field locators + user actions
    │   └── shared/
    │       └── setup_teardown.robot    # Suite setup/teardown — open/close Chrome
    └── testes/
        ├── preenchimento_correto.robot     # Happy path test cases
        └── preenchimento_incorreto.robot   # Error path — required field validation
```

### Test Cases

**preenchimento_correto.robot:**
- Verify that correctly filled form fields create a card in the expected team
- Verify that more than one card can be created when fields are filled correctly
- Verify that one card can be created for each available team

**preenchimento_incorreto.robot:**
- Verify that submitting without required fields shows validation error messages

### Key Concepts Applied

| Concept | How it shows up |
|---|---|
| **BDD keywords** | Test steps written as `Dado que`, `Então`, `E` — readable as plain language |
| **Page Object pattern** | `cadastro.robot` centralizes all locators and actions for the form page |
| **FakerLibrary** | `FakerLibrary.First Name`, `FakerLibrary.Job`, `FakerLibrary.Image Url` — no hardcoded test data |
| **FOR loop** | Creates multiple cards and iterates through all 7 teams dynamically |
| **SeleniumLibrary** | `Open Browser`, `Input Text`, `Click Element`, `Element Should Be Visible` |
| **XPath locators** | Teams selected via `//option[contains(.,'Programação')]` — robust to text changes |
| **Setup/Teardown** | Every test opens Chrome before and closes it after via `Test Setup`/`Test Teardown` |

---

## How to Run

**Prerequisites:** Python · Robot Framework · SeleniumLibrary · FakerLibrary · ChromeDriver

```bash
git clone https://github.com/victorhubarb/robot-framework-testing.git
cd robot-framework-testing

# Install dependencies
pip install robotframework
pip install robotframework-seleniumlibrary
pip install robotframework-faker

# Start the React app locally (separate terminal)
cd robot-framework-organo-main
npm install && npm start

# Run the tests (in a separate terminal)
cd robot-framework-organo-tests
robot -d results testes/
```

Results are saved as HTML and XML reports in the `results/` folder.

---

## Technologies

- **Robot Framework** — keyword-driven test automation
- **SeleniumLibrary** — browser automation
- **FakerLibrary** — dynamic test data generation
- **Python** — required runtime
- **React** (Organo v1) — the application under test

---

## Author

**Victor Hugo Barbosa**
[GitHub](https://github.com/victorhubarb) · [LinkedIn](https://www.linkedin.com/in/victorhbarbosa/)
