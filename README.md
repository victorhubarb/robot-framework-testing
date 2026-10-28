# Robot Framework Testing

UI test automation with Robot Framework and SeleniumLibrary, written against Organo, a small React app where you register team members and see them as cards grouped by team. The app is included in the repo so the tests run against a local copy.

The keywords are written in Portuguese in a Given/Then style (`Dado que`, `E`, `Então`), so a test case reads like a sentence.

## What's tested

| Suite | Scenarios |
|---|---|
| `preenchimento_correto.robot` | A valid form creates a card in the chosen team; several cards can be created in a row; one card can be created for each of the 7 teams |
| `preenchimento_incorreto.robot` | Submitting the empty form shows the required-field error for name, role and team |

## How it's organized

```
robot-framework-organo-main/    The React app under test
robot-framework-organo-tests/
├── resources/
│   ├── main.robot              Libraries and resource imports
│   ├── pages/cadastro.robot    Locators and keywords for the registration form
│   └── shared/setup_teardown.robot   Open and close Chrome
└── testes/                     The two suites above
```

- **Page-object style.** All locators and form actions live in `pages/cadastro.robot`. The suites only call keywords.
- **Generated data.** FakerLibrary (pt_BR) produces the name, job title and image URL for each run, so no test depends on fixed values.
- **Loops.** A `FOR ... IN ENUMERATE` loop walks the list of team locators to create one card per team.
- **Setup and teardown.** Each test opens a fresh Chrome window and closes it afterwards.

## Run it

You need Python 3.8+, Node.js 18+ and Chrome. Selenium 4 downloads a matching driver by itself.

```bash
git clone https://github.com/victorhubarb/robot-framework-testing.git
cd robot-framework-testing
pip install robotframework robotframework-seleniumlibrary robotframework-faker

# terminal 1: start the app on http://localhost:3000
cd robot-framework-organo-main
npm install && npm start

# terminal 2: run the tests
cd robot-framework-organo-tests
robot -d results testes/
```

Robot writes `report.html`, `log.html` and `output.xml` to `results/`.

## Known gaps

- The suites assert that a card appears, but not that it is under the right team or has the data that was typed.
- Two keywords end with `Sleep 10s`. Explicit waits on the card count would be faster and less flaky.
- The app URL is hardcoded as `http://localhost:3000`, and there is no CI job.
- The incorrect-input suite covers only the all-fields-empty case.

---

Victor Hugo Barbosa · [GitHub](https://github.com/victorhubarb) · [LinkedIn](https://www.linkedin.com/in/victorhbarbosa/)
