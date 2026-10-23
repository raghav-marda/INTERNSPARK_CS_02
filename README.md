# 🛡️ InternSpark Cybersecurity Internship — Task 02
## Web Application Security Testing

<p align="center">
  <img src="https://img.shields.io/badge/InternSpark-Cybersecurity%20Internship-blue?style=for-the-badge" alt="InternSpark Cybersecurity Internship">
  <img src="https://img.shields.io/badge/Task-02-orange?style=for-the-badge" alt="Task 02">
  <img src="https://img.shields.io/badge/Focus-Web%20Application%20Security-red?style=for-the-badge" alt="Web Application Security">
  <img src="https://img.shields.io/badge/Environment-Local%20DVWA-green?style=for-the-badge" alt="Local DVWA Environment">
</p>

## 📌 Project Overview

This repository documents **Task 02: Web Application Security Basics**, completed as part of the **InternSpark Cybersecurity Internship**.

The task focuses on understanding and demonstrating common web application vulnerabilities in a controlled, intentionally vulnerable testing environment. The assessment was performed using **Damn Vulnerable Web Application (DVWA)** hosted locally.

The practical assessment covered SQL Injection, Reflected Cross-Site Scripting (XSS), and HTTP request interception using Burp Suite Community Edition.

## 🎯 Objectives

- Understand common web application security vulnerabilities.
- Demonstrate SQL Injection in a controlled testing environment.
- Identify Reflected Cross-Site Scripting (XSS).
- Intercept and inspect HTTP requests using Burp Suite.
- Capture screenshots as evidence of the testing process.
- Recommend mitigation techniques to improve application security.

## 🧰 Tools & Technologies

| Tool / Technology | Purpose |
|---|---|
| **DVWA** | Intentionally vulnerable web application used for security testing |
| **Burp Suite Community Edition** | Intercepting and inspecting HTTP requests |
| **Web Browser** | Interacting with the local DVWA application |
| **GitHub** | Storing assessment documentation and screenshots |

## 🔍 Scope of Assessment

Testing was performed against the local DVWA instance:

- **Target:** `http://127.0.0.1:4280/`
- **Environment:** Local testing lab
- **Application:** Damn Vulnerable Web Application (DVWA)
- **Security Level:** Low
- **Testing Type:** Manual web application security testing

> **Scope limitation:** The tests documented here apply to the local DVWA training application, not to a public website or production application.

## 🧪 Methodology

### 1. SQL Injection Testing

**Objective:** Determine whether user-supplied input can alter the behavior of a database query.

**Test performed:**
- Opened the SQL Injection module in DVWA.
- Submitted a normal user ID and observed the corresponding record.
- Tested the input `1' OR '1'='1' #` in the local lab.
- Observed multiple database records returned instead of a single record.

**Observation:** The input changed the query's logical condition and caused multiple records to be displayed. This demonstrates SQL Injection in the configured DVWA environment.

**Security impact:** In a vulnerable real-world application, SQL Injection may expose unauthorized database records or allow other database operations, depending on the query, database privileges, and application design.

### 2. Reflected Cross-Site Scripting (XSS)

**Objective:** Check whether user-controlled input is reflected into a web page and executed as JavaScript.

**Test performed:**
- Opened the Reflected XSS module in DVWA.
- Submitted the test payload `<script>alert('XSS')</script>`.
- Observed a JavaScript alert displaying `XSS`.

**Observation:** The browser executed the supplied script, demonstrating Reflected XSS in the local DVWA environment.

**Security impact:** Depending on the application context and browser protections, XSS may allow an attacker to execute scripts in a victim's browser, manipulate page content, or attempt to access information available to that page.

### 3. HTTP Request Interception Using Burp Suite

**Objective:** Understand how HTTP requests can be intercepted and inspected during web application testing.

**Test performed:**
- Opened the local DVWA application through the browser configured for Burp Suite.
- Enabled request interception in Burp Suite Proxy.
- Generated a request to the SQL Injection module.
- Inspected the HTTP request and its query parameters, including `id` and `Submit`.
- Captured screenshots showing the intercepted request and parameter details.

**Observation:** Burp Suite allowed the request to be paused and inspected before it was forwarded to the local application.

**Security relevance:** Intercepting requests helps security testers understand how applications receive user input and identify parameters that may require validation and secure handling.

## 📊 Findings Summary

| Finding | Result | Evidence |
|---|---|---|
| SQL Injection | Demonstrated in DVWA at Low security | `01_sql_injection_proof.png` |
| Reflected XSS | JavaScript alert triggered in DVWA | `02_reflected_xss_alert.png` |
| XSS Response | Reflected XSS test page captured | `03_reflected_xss_response.png` |
| HTTP Request Interception | Request captured in Burp Suite | `04_burp_request_interception.png` |
| SQL Injection Parameters | Query parameters inspected in Burp Suite | `05_burp_sqli_parameters.png` |

**Overall assessment:** The testing successfully demonstrated SQL Injection and Reflected XSS in the deliberately vulnerable DVWA lab. Burp Suite was used to inspect HTTP requests and query parameters. These results confirm the behavior of the test environment and should not be interpreted as findings against a separate production application.

## 🛠️ Mitigation Recommendations

### Prevent SQL Injection
- Use parameterized queries or prepared statements.
- Avoid constructing SQL queries through string concatenation with user input.
- Validate input according to the expected data type and format.
- Apply least-privilege permissions to database accounts.
- Avoid displaying detailed database errors to end users.

### Prevent Reflected XSS
- Apply context-appropriate output encoding before displaying user-controlled data.
- Use safe templating practices and avoid inserting untrusted input into executable HTML or JavaScript.
- Validate input where appropriate, without relying on validation as the only XSS defense.
- Consider a properly configured Content Security Policy (CSP) as an additional defensive layer.
- Use secure framework features for escaping untrusted content.

### Improve Overall Web Application Security
- Test applications at multiple security levels and across relevant input points.
- Review authentication, authorization, session handling, and error management.
- Keep frameworks, dependencies, and server components updated.
- Include security testing in the software development lifecycle.
- Retest after applying fixes to verify that vulnerabilities have been addressed.

## 📸 Screenshots & Evidence

All screenshots captured during the practical assessment are available in the [`screenshots/`](screenshots/) directory.

| No. | Screenshot | Description |
|---:|---|---|
| 01 | [SQL Injection Proof](screenshots/01_sql_injection_proof.png) | Multiple records returned after the SQL Injection test |
| 02 | [Reflected XSS Alert](screenshots/02_reflected_xss_alert.png) | JavaScript alert triggered by the test payload |
| 03 | [Reflected XSS Response](screenshots/03_reflected_xss_response.png) | DVWA Reflected XSS page after the test |
| 04 | [Burp Request Interception](screenshots/04_burp_request_interception.png) | Intercepted HTTP request in Burp Suite |
| 05 | [Burp SQLi Parameters](screenshots/05_burp_sqli_parameters.png) | Query parameters displayed in Burp Suite |

## 📁 Repository Structure

```text
INTERNSPARK_CS_02/
├── README.md
├── screenshots/
│   ├── README.md
│   ├── 01_sql_injection_proof.png
│   ├── 02_reflected_xss_alert.png
│   ├── 03_reflected_xss_response.png
│   ├── 04_burp_request_interception.png
│   └── 05_burp_sqli_parameters.png
└── report/
    └── Web_Application_Security_Assessment_Report.pdf
```

*The PDF report should be added to the `report/` directory after it has been prepared.*

## 📄 Assessment Report

The detailed assessment report will document the testing process, observations, screenshot evidence, security implications, and mitigation recommendations.

Once uploaded, access it here:

**[📥 View Web Application Security Assessment Report (PDF)](report/Web_Application_Security_Assessment_Report.pdf)**

## 📚 Learning Outcomes

Through this task, I gained practical experience in:

- Understanding SQL Injection and Reflected XSS.
- Testing an intentionally vulnerable web application in a local lab.
- Inspecting HTTP requests and query parameters with Burp Suite.
- Capturing and organizing security testing evidence.
- Understanding secure coding practices and vulnerability mitigation.
- Documenting technical observations in a structured security assessment.

## ⚠️ Disclaimer

This assessment was conducted for educational purposes using a local DVWA instance intentionally designed to demonstrate web application vulnerabilities.

All testing was limited to the controlled lab environment. The payloads and techniques documented here should only be used on systems that you own or have explicit authorization to test.

This repository is intended to demonstrate cybersecurity learning, practical testing methodology, and responsible vulnerability documentation.

## 👨‍💻 Author

**Raghav Marda**

B.Tech Computer Science & Engineering Student | Cybersecurity Enthusiast

- **GitHub:** [raghav-marda](https://github.com/raghav-marda)
- **Internship:** InternSpark Cybersecurity Internship
- **Task:** 02 — Web Application Security Basics

---

<p align="center">
  <i>Learn responsibly. Test ethically. Build securely.</i>
</p>
