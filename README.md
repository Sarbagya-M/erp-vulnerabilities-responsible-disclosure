# Multiple Vulnerabilities in College ERP System (Redacted) – Responsible Disclosure

## Author
**Sarbagya Ratna Maharjan**  
Cybersecurity Enthusiast

## Overview

Between May and June 2025, I discovered and responsibly disclosed **five different vulnerabilities** in a college's ERP system, some of which exposed highly sensitive data of students and staff. All issues were reported have since been patched. These include broken access controls, document leaks, privilege escalation.

This write-up summarizes each finding with redacted and anonymized technical details to preserve confidentiality and uphold ethical disclosure standards.


## Disclosure Timeline

| # | Date       | Vulnerability                                 |
|---|------------|-----------------------------------------------|
| 1 | May 11     | Super Admin Access via Broken Access Control  |
| 2 | May 29     |Student Document Leak|
| 3 | May 29     |SMS Messaging Interface Access                       |
| 4 | May 31     | HR Report Access via Broken Access Control    |
| 5 | June 14    | Direct URL Access to Student Docs (No Auth)   |



## Vulnerability Details

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

#### Screenshot (Redacted)
![Super Admin Panel Access](screenshots/1.png)
![Super Admin Panel Access](screenshots/2.png)
![Super Admin Panel Access](screenshots/3.png)

### 2. Student Document Leak
- **Type:** Broken Access Control
  
- **Summary:** Lack of authorization checks allowed access to uploaded student documents (e.g., admission files, certificates, citizenship)  
 
    
- **Impact:**
  
  - Exposure of personal and academic records  
  - Violation of student data privacy and institutional data protection policies
    
- **Fix Recommendation:**
  
  - Implement strict access control checks based on user roles and user IDs
  - Enforce backend validation of user permissions before serving file resources

#### Screenshot (Redacted)
![student documents](screenshots/stddtl.png)


### 3. Unauthorized Access to SMS Messaging Interface

- **Type:** Broken Access Control

- **Summary:** The ERP's SMS messaging module did not enforce role-based access control, allowing unauthorized users to access the bulk messaging interface. This included features for sending announcements, fee reminders, and event alerts to students, along with the full log of previously sent messages.

- **Impact:**

  - Risk of misuse by sending fake or unauthorized messages to students
  - Potential reputational damage and operational disruption
  - Exposure of metadata such as phone numbers and sent message logs

- Fix Recommendation:
  - Restrict access to the messaging interface to authorized administrative roles only
  - Implement server-side access control checks before sending or viewing messages
 
 #### Screenshot (Redacted)
 ![SMS portal](screenshots/4.png)
![SMS log](screenshots/5.png)




### 4. HR Report Access via Broken Access Control
- **Type:** Broken Access Control

- **Summary:** An internal report viewing interface allowed access to sensitive HR reports without verifying the user's role or privilege level. The backend report-fetching endpoint could be accessed directly and lacked proper access control, allowing any authenticated user to retrieve confidential employee data.

- Data Exposed:

  - Full names and employment info
  - Bank account details, SSF/CIT numbers, PAN numbers

- Fix Recommendation:

  - Implement access validation on all report exports
  - Use session-bound or signed URLs with authorization middleware
#### Screenshot (Redacted)
![sensitive information](screenshots/6.png)

### 5. Direct URL Access to Student Files (Bypass Patch)

- Type: Insecure Direct File Access

- Summary: Even after patching document access, files remained retrievable via predictable URLs. No session or login was required.

- Impact:

  - Anyone with or able to guess the URL could access private files

- Fix Recommendation:

  - Move files out of public directories
  - Use signed, time-bound download tokens for access

#### Screenshot (Redacted)
![student document](screenshots/7.png)

### Ethical Disclosure Statement

This repository serves purely as an educational, redacted, and anonymized technical disclosure. No live URLs, identifiable organization names, or sensitive personal information have been shared. All vulnerabilities were discovered passively through legal means and disclosed responsibly.

### Contact

Got feedback or want to collaborate on projects? Feel free to connect:
- [LinkedIn](https://www.linkedin.com/in/sarbagya-maharjan-68409222b/) 
