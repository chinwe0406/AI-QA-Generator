# 🧪 AI QA Test Case Generator

> An AI-powered tool that automatically generates structured manual test cases from plain-English feature descriptions — built with the Claude API.

![Demo](https://img.shields.io/badge/Status-Live-brightgreen) ![Built With](https://img.shields.io/badge/Built%20With-Claude%20API-blue) ![Language](https://img.shields.io/badge/Language-HTML%20%2F%20JavaScript-yellow) ![License](https://img.shields.io/badge/License-MIT-lightgrey)

🔗 **[Live Demo](https://chinwe0406.github.io/AI-QA-Generator/)**
---

## 📌 Overview

Writing manual test cases is one of the most time-consuming parts of QA. This tool eliminates that bottleneck.

Paste a feature description or user story — the app sends it to Claude (Anthropic's AI) via the API and returns a full set of professional, structured test cases within seconds. Each test case includes a Test ID, name, preconditions, step-by-step instructions, expected result, priority level, and type classification.

Built as a single HTML file — no frameworks, no installation, no server required. Opens directly in any browser.

---

## ✨ Features

- **AI-generated test cases** from plain-English feature descriptions
- **4 test type categories** — Functional, Security, Edge Cases, Negative Tests
- **3 output formats** — Standard steps, Gherkin (Given/When/Then), Exploratory charters
- **Priority classification** — High / Medium / Low, assigned by the AI based on risk
- **Filter by test type** — view all results or drill into a specific category
- **Export to CSV** — download all test cases ready for Jira, TestRail, or Google Sheets
- **No installation needed** — single HTML file, runs in any modern browser
- **5 built-in example prompts** to get started immediately

---

## 🎬 Demo

**Input:**
```
Users should be able to log in with their email and password.
After 3 failed login attempts, the account should be locked
for 15 minutes and the user notified by email.
```

**Output (sample):**

| ID | Name | Type | Priority |
|----|------|------|----------|
| TC-001 | Valid login with correct credentials | Functional | High |
| TC-002 | Account lockout after 3 failed attempts | Functional | High |
| TC-003 | Lockout email notification is sent | Functional | Medium |
| TC-004 | SQL injection attempt on login form | Security | High |
| TC-005 | Login with empty email field | Negative | Medium |
| TC-006 | Login with maximum-length password | Edge | Low |

---

## 🚀 Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Edge, Safari)
- A free Anthropic API key — get one at [console.anthropic.com](https://console.anthropic.com)

### Run the app

1. Download `qa-generator.html` from this repository
2. Open the file in your browser (double-click, or drag into a browser window)
3. Enter your Anthropic API key in the field provided
4. Type or paste a feature description
5. Select your test types and preferred format
6. Click **Generate Test Cases** (or press `Ctrl/Cmd + Enter`)

No npm install. No server. No build step. Just open and use.

---

## 🛠️ How It Works

```
User inputs feature description
        ↓
App builds a structured QA prompt
(instructs Claude to act as a senior QA engineer)
        ↓
Prompt is sent to Anthropic API (claude-sonnet-4-6)
        ↓
Claude returns structured JSON array of test cases
        ↓
App parses JSON and renders interactive cards
        ↓
User filters by type and exports to CSV
```

### Key technical decisions

**Why a single HTML file?**
Keeping everything in one file makes the tool portable and accessible — no dependencies to install, no environment to configure. Anyone can download and use it immediately.

**Why JSON output from the AI?**
Rather than asking Claude to return free-form text (which would be hard to parse and display), the prompt instructs Claude to return a strict JSON array. This makes the output fully structured and predictable — each field (id, name, steps, expectedResult, priority) maps directly to a UI element.

**Why the Anthropic API directly from the browser?**
This is a portfolio/demonstration tool. For a production application, API calls would be proxied through a backend server to keep the API key secure. The app makes this clear to users and never stores the key.

---

## 📁 Project Structure

```
ai-qa-generator/
│
├── qa-generator.html    # The entire application — HTML, CSS, and JavaScript
└── README.md            # This file
```

---

## 💡 Example Feature Descriptions to Try

Copy and paste any of these into the app:

**Login & authentication**
```
Users can log in with email and password. After 3 failed attempts,
the account locks for 15 minutes and an email notification is sent.
```

**Password reset**
```
Users can request a password reset by entering their email.
They receive a reset link valid for 60 minutes that expires after one use.
```

**File upload**
```
Users can upload profile images up to 5MB in JPEG or PNG format.
Files are scanned for malware before storage. Invalid files are rejected
with a descriptive error message.
```

**Search and filter**
```
Users can search a product catalogue by keyword and filter by category,
price range, and availability. Results are paginated at 20 items per page.
```

---

## 🔐 API Key & Security

- Your API key is entered manually each session and is **never stored** in the browser or in any database
- The key is sent directly to Anthropic's servers over HTTPS — it does not pass through any intermediate server
- For production use, API calls should be routed through a backend to avoid exposing the key client-side
- Get your free API key at [console.anthropic.com](https://console.anthropic.com)

---

## 🧠 Built With

| Technology | Purpose |
|-----------|---------|
| HTML5 / CSS3 | UI structure and styling |
| Vanilla JavaScript | App logic, API calls, CSV export |
| [Anthropic Claude API](https://docs.anthropic.com) | AI test case generation |
| claude-sonnet-4-6 | Language model used for generation |

---

## 📄 Output Format

Each generated test case contains:

| Field | Description |
|-------|-------------|
| **ID** | Sequential identifier (TC-001, TC-002…) |
| **Name** | Descriptive title of what is being tested |
| **Type** | functional / security / edge / negative |
| **Priority** | High / Medium / Low |
| **Preconditions** | What must be true before the test runs |
| **Steps** | Step-by-step instructions for the tester |
| **Expected Result** | What correct behaviour looks like |
| **Notes** | Test data suggestions or known risks |

---

## 🔮 Future Improvements

- [ ] Backend proxy server to secure API key handling
- [ ] Save and load test case sessions
- [ ] Direct Jira / TestRail integration via API
- [ ] Support for uploading existing test plans for gap analysis
- [ ] Team collaboration mode with shared test suites

---

## 👩‍💻 About the Developer

Built by **Chinwendu Sylvia Ekweanya** — a Master of Information Technology student at the University of Waikato, New Zealand, with a background in QA engineering, cloud-native application testing, and financial services.

This project was built to demonstrate practical AI integration skills, combining hands-on QA experience (manual testing, bug reporting, AWS CloudWatch monitoring) with Claude API development.

- 🔗 [LinkedIn](http://www.linkedin.com/in/chinwendu-ekweanya)
- 🐙 [GitHub](https://github.com/chinwe0406)

---

## 📝 License

This project is open source and available under the [MIT License](LICENSE).
