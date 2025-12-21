# Python Selenium UI Automation Framework

This repository contains a **custom-built UI automation framework** developed using **Python, Selenium, and PyTest**.  
I designed this framework to automate functional and regression testing for web applications while following **industry-standard automation practices** such as cross-browser testing, CI integration, environment management, and secure handling of sensitive data.

The framework is lightweight, scalable, and suitable for real-world QA Automation and SDET roles.

---

## 🛠 Tech Stack

- **Python**: 3.9 – 3.12  
- **Selenium**: 4.24.0  
- **PyTest**: 8.3.0  
- **CI/CD**: GitHub Actions  
- **Browsers**: Chrome, Firefox, Remote WebDriver  

---

## ✨ Key Features

- Clean and user-friendly UI automation framework
- Built using **Selenium WebDriver** and **PyTest**
- Supports **Chrome, Firefox, and Remote browsers**
- Centralized WebDriver management utilities
- Environment-based execution (**dev**, **stage**)
- Automated test execution via **GitHub Actions**
- Generates **PyTest execution reports and custom logs**
- Secure handling of secrets using **encryption**
- YAML-based **test data management**
- Easily extendable for large automation suites

---

## 📁 Project Overview

- Test scripts written using **PyTest**
- Page Object Model used for better maintainability
- WebDriver setup handled through reusable utilities
- Test data stored in **YAML files**
- Secrets encrypted and decrypted during runtime
- CI pipeline configured for Linux and macOS runners

---

## 🚀 Getting Started

### Prerequisites

- Python installed (3.9 or above)
- Compatible browser drivers available  
  (If not using Selenium ≥ 4.24.0, place drivers inside the `resources` directory)

---

## ▶️ Local Execution

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/slietian/Simple-Python-Selenium-UI-Automation-Framework
2️⃣ Setup Virtual Environment (Poetry)
pip install poetry
poetry shell
poetry install

3️⃣ Environment Configuration

Create a .env file in the root directory:

DEV_URL="your-dev-project-url"
STAG_URL="your-staging-project-url"


Alternatively, environment URLs can be configured inside the properties file:

class Properties:
    _ENV_VARIABLES = {
        "dev": ("DEV_URL", ""),
        "stag": ("STAG_URL", ""),
    }

4️⃣ Run Tests
pytest

🔄 CI/CD with GitHub Actions

The framework is integrated with GitHub Actions to support continuous testing.

Runs automatically on push and pull requests

Executes tests on Linux and macOS

Uses environment variables securely

Example CI configuration:

jobs:
  selenium-tests:
    runs-on: macos-latest
    env:
      DEV_URL: ${{ vars.DEV_URL }}
      STAG_URL: ${{ vars.STAG_URL }}

🔐 Secure Secrets Handling

To protect sensitive data such as passwords:

Secrets are stored in encrypted format

Encryption handled using a secure automation utility

Encryption key stored locally in config/key.properties
(This file is ignored using .gitignore)

For remote execution (CI, Jenkins, BrowserStack), the framework supports HashiCorp Vault integration.

Example PyTest fixture:

@pytest.fixture
def get_password():
    secure = Secure()
    read = YAMLReader.read("data.yaml", to_simple_namespace=True)
    password = read.users.john.details.password
    return secure.decrypt_password(password)

📊 Test Data Management

Test data is stored in YAML files

Easy access and readability

Supports multiple user profiles and test scenarios

🧹 Code Quality (Linting)

Ruff is used for linting and code quality checks

Custom rules defined in .ruff.toml

Can be integrated as an external tool in IDEs

🧪 Demo Application Tested

Tests are executed on the following demo application:
🔗 https://demoqa.com/text-box

🎯 Why This Framework

Designed with real-world automation needs

Easy to understand and extend

CI/CD ready

Secure and scalable

Ideal for QA Automation Engineer / SDET roles

---
