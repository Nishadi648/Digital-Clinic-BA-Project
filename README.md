# 🏥 Digital Clinic Appointment & Queue Management System (DCQMS)
> **Standard Business Analysis Portfolio Project** | *Agile Scrum & Requirements Engineering Framework*

---

## 📌 Project Overview & Problem Statement
Small to medium outpatient clinics frequently face operational congestion, long patient waiting periods, inefficient manual booking records, and unmanaged cancellations.

The **Digital Clinic Appointment & Queue Management System (DCQMS)** digitizes appointment scheduling, introduces automated queue token tracking, and provides clear operational reporting for clinic staff and administration.

---

## 📑 Software Requirements Specification (SRS) Document
The complete, structured **Software Requirements Specification (SRS v1.0)** is available in this repository:
📄 **[Read Full SRS Document (v1.0)](docs/SRS_Digital_Clinic_v1.0.md)**

### Key Highlights of the SRS:
* **Scope Definition:** Outpatient appointment scheduling, queue token generation, SMS alerts, and admin analytics (Excludes EMR, telemedicine, and payments).
* **User Classes:** Patients, Receptionists, Doctors, and Clinic Administrators (RBAC framework).
* **Functional Requirements:** 10 Traceable Functional Requirements (`FR-01` to `FR-10`).
* **Non-Functional Requirements:** Security (TLS 1.3, AES-256), Usability, Performance (<2.0s load), and Availability (99.5%).
* **Agile Jira Backlog:** 4 Epics & User Stories written in **Gherkin Syntax** (`Given-When-Then`).

---

## 🎯 Agile Epics Summary

| Epic ID | Epic Name | Scope Description |
| :--- | :--- | :--- |
| **EPIC-01** | Patient & Authentication Management | Registration, login, profile maintenance |
| **EPIC-02** | Doctor Schedule & Booking Engine | Doctor schedule display, booking, and cancellation workflows |
| **EPIC-03** | Real-Time Queue & Notification System | Sequential queue token generation and automated SMS alerts |
| **EPIC-04** | Clinic Administration & Analytics | Daily summaries, status filtering, volume reporting |

---

## 🛠️ BA Tools & Methodologies Used
* **Requirements Engineering:** SRS Document Preparation, Requirements Traceability
* **Agile Scrum Framework:** Jira Epics, User Stories, Acceptance Criteria (Gherkin format)
* **Modeling & Process Design:** UML Use Case Diagrams, Activity/BPMN Workflows
* **Tools:** Jira, Draw.io / Lucidchart, MS Word, Markdown
