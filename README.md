# Multiple Vulnerabilities in College ERP System (Redacted) – Responsible Disclosure

## 👨‍💻 Author
**Sarbagya Ratna Maharjan**  
Cybersecurity Enthusiast

## 🗃️ Overview

Between May and June 2025, I discovered and responsibly disclosed **four different vulnerabilities** in a college's ERP system, some of which exposed highly sensitive data of students and staff. All issues were reported and patched. These include broken access controls, document leaks, privilege escalation.

This write-up summarizes each finding with redacted and anonymized technical details to preserve confidentiality and uphold ethical disclosure standards.


## 📅 Disclosure Timeline

| # | Date       | Vulnerability                                 | Status         |
|---|------------|-----------------------------------------------|----------------|
| 1 | May 11     | Super Admin Access                            | ✅ Fixed       |
| 2 | May 29     | Student document access                       | ✅ Fixed       |
| 3 | May 31     | HR Report Access via IDOR                     | ✅ Fixed       |
| 4 | June 14    | Direct URL Access to Student Docs (No Auth)   | ✅ Fixed       |


## 📂 Vulnerability Details




