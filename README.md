# Robot Framework Testing <a name="readme-top"></a>
![Static Badge](https://img.shields.io/badge/status-completed-green?style=for-the-badge)

## Introduction
**Robot Framework Testing** is a project configured to perform automated tests using the **Robot Framework**. The repository is composed of two main folders:
1. **robot-framework-organo-main**: Contains the website files that will be tested.
2. **robot-framework-organo-tests**: Contains the tests that will be executed using the Robot Framework.

Before executing the tests, it is necessary to run the website locally and configure the correct address in the test configuration file.

## Table of Contents
- [Installation](#installation)
- [Website Setup](#website-setup)
- [Usage](#usage)
- [Test Structure](#test-structure)
- [Technologies](#technologies)
- [Contributors](#contributors)

## Installation

### Prerequisites
- Python installed
- Robot Framework installed

### Steps to run
1. Clone the repository:
   ```bash
   git clone https://github.com/victorhubarb/robot-framework-testing.git
   cd robot-framework-testing
   ```
2. Install the dependencies:
   ```bash
   pip install robotframework
   ```

## Website Setup
1. Navigate to the **robot-framework-organo-main** folder:
   ```bash
   cd robot-framework-organo-main
   ```
2. Run the website locally. Make sure it is accessible from a local address (e.g. `localhost:3000`).
3. In the **robot-framework-organo-tests** directory, configure the localhost address being used in the test configuration file so that the Robot Framework knows where to test the website.

## Usage

To run the tests:
```bash
robot -d results tests/
```
This will execute the defined tests and store the results in the `results` folder.

## Test Structure
- **UI Testing**: Verifies the user interface in different scenarios.
- **API Testing**: Ensures that the APIs used by the application are working.

## Technologies
- **Robot Framework**
- **Python**

## Contributors
- [Victor Barbosa](https://github.com/victorhubarb)
<p align="right">(<a href="#readme-top">back to top</a>)</p>
