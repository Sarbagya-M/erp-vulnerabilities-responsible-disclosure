# Multiple Vulnerabilities in College ERP System (Redacted) – Responsible Disclosure

## 👨‍💻 Author
**Sarbagya Ratna Maharjan**  
Cybersecurity Enthusiast

## 🗃️ Overview

Between May and June 2025, I discovered and responsibly disclosed **four different vulnerabilities** in a college's ERP system, some of which exposed highly sensitive data of students and staff. All issues were reported and patched. These include broken access controls, document leaks, privilege escalation.

This write-up summarizes each finding with redacted and anonymized technical details to preserve confidentiality and uphold ethical disclosure standards.

---
## 📅 Disclosure Timeline

| # | Date       | Vulnerability                                 | Status         |
|---|------------|-----------------------------------------------|----------------|
| 1 | May 11     | Super Admin Access via Broken Access Control  | ✅ Fixed       |
| 2 | May 29     | Student document access                       | ✅ Fixed       |
| 3 | May 31     | HR Report Access via Broken Access Control    | ✅ Fixed       |
| 4 | June 14    | Direct URL Access to Student Docs (No Auth)   | ✅ Fixed       |

---

## 📂 Vulnerability Details

### 1. Super Admin Access via Broken Access Control

- **Type:** Broken Access Control / Privilege Escalation

- **Summary:** An administrative interface was left exposed without proper authentication or role checks. This allowed direct access to high-privilege functionalities.

- **Impact:**

  - Full access to user account management
  - Ability to manipulate user roles
  - Unrestricted access to administrative control panels

- Fix Recommendation:

  - Restrict access to admin panels with strong role validation
  - Enforce authentication for all sensitive endpoints

#### 🔎 Screenshot (Redacted)
![Super Admin Panel Access](screenshots/1.png)
![Super Admin Panel Access](screenshots/2.png)
![Super Admin Panel Access](screenshots/3.png)

### 2. Student Document Leak + SMS Messaging Interface Access

- **Type:** Broken Access Control
  
- **Summary:** Lack of authorization checks allowed access to:  
  - Uploaded student documents (e.g., admission files, certificates, citizenship)  
  - The ERP’s SMS messaging interface used for sending bulk messages, notices, and fee payment alerts to students
    
- **Impact:**
  
  - Exposure of personal and academic records  
  - Potential misuse of the SMS system to send unauthorized messages
    
- **Fix Recommendation:**
  
  - Apply access control checks based on user roles and IDs  
  - Isolate document access by user/session context  
  - Restrict SMS interface access to authorized personnel only  

### 3. HR Report Access via Broken Access Control
- **Type:** Broken Access Control

- **Summary:** An internal report viewing menu allowed access to sensitive HR reports without verifying the user's role or authentication level. The underlying API endpoint fetching the report data had no access control, making the data retrievable by any logged-in user.

- Data Exposed:

  - Full names and employment info

  - Bank account details, SSF/CIT numbers, PAN numbers

- Fix Recommendation:

  - Implement access validation on all report exports

  - Use session-bound or signed URLs with authorization middleware








