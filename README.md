# Open Vault Bank: API Security Assessment (OWASP Top 10)

## 📌 Executive Summary

This repository contains the documentation for a comprehensive security assessment conducted on **Open Vault Bank**, a RESTful API-based digital banking application. The assessment was performed using a black-box methodology to simulate real-world attacks targeting financial transaction integrity and user data confidentiality.

While the platform utilizes modern technologies like JWT and RBAC, the assessment revealed critical implementation flaws that could lead to unauthorized financial transfers and mass data exposure.

## 🛠️ Tools & Technologies

  * **Target:** Open Vault Bank (REST API)
  * **Framework:** OWASP API Security Top 10 (2023)
  * **Testing Suite:** Burp Suite, Postman, JWT.io
  * **Key Concepts:** BOLA, Mass Assignment, Broken Authentication, BFLA

## 🔍 Vulnerability Summary & Remediations

The following table outlines the key vulnerabilities identified (API1–API9, excluding 7 & 10) and the recommended technical fixes.

| API ID | Vulnerability | Remediation Strategy |
| :--- | :--- | :--- |
| **API1** | **Broken Object Level Authorization** | Implement resource-level authorization; use UUIDs instead of sequential IDs. |
| **API2** | **Broken Authentication** | Replace 3-digit OTPs with secure tokens; implement strict rate limiting. |
| **API3** | **Mass Assignment** | Use Data Transfer Objects (DTOs) to whitelist properties; set sensitive fields to read-only. |
| **API4** | **Unrestricted Resource Consumption** | Set execution timeouts; implement pagination and global rate limiting. |
| **API5** | **Broken Function Level Auth** | Apply "deny-by-default" policies and verify user roles server-side for all admin tasks. |
| **API6** | **Unrestricted Access to Flows** | Integrate CAPTCHAs for fund transfers; implement strict business logic sequencing. |
| **API8** | **Security Misconfiguration** | Transition to RS256 (Asymmetric) JWT signing; disable verbose error messages. |
| **API9** | **Improper Inventory Management** | Decommission debug/health endpoints in production; restrict internal routes from `robots.txt`. |

## 📝 Conclusion

The Open Vault Bank platform demonstrates a solid technical foundation with modern architectural practices. However, current implementation gaps around authorization and frontend trust create serious risks to patient confidentiality and system control.

These vulnerabilities potentially violate key industry security standards and financial data protection principles, specifically regarding Access Control, Data Integrity, and Identification. Fixing the identified issues will significantly improve the platform's resilience. It is especially critical to enforce all role and identity checks server-side and adopt strict input validation through DTOs.

## 🚀 Recommendations for Future Hardening

  * **DevSecOps Integration:** Incorporate automated API security scanning (e.g., StackHawk, 42Crunch) into the CI/CD pipeline.
  * **Zero Trust Architecture:** Ensure that no request is trusted by default, regardless of its origin within the network.
  * **Red Team Simulations:** Conduct biannual simulations to validate the effectiveness of implemented security controls.

**Disclaimer:** *This assessment was conducted as part of a controlled security exercise. All testing was performed on a simulated environment.*
