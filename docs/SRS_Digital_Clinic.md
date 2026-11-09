# SOFTWARE REQUIREMENTS SPECIFICATION (SRS)
## Digital Clinic Appointment & Queue Management System (DCQMS)

* **Project Code:** DCQMS-01
* **Document Version:** 1.0 Final
* **Prepared By:** Business Analyst
* **Date of Completion:** November 2026
* **Project Domain:** Outpatient Healthcare & Agile Scrum

---

### 1. Introduction

#### 1.1 Document Purpose
This Software Requirements Specification (SRS) document details the complete functional and non-functional requirements for the Digital Clinic Appointment & Queue Management System (DCQMS). It establishes a formal requirement baseline for system architecture, Agile backlog management in Jira, quality assurance, and stakeholder verification.

#### 1.2 Problem Statement & Objectives
Small to medium outpatient clinics frequently face operational congestion, long patient waiting periods, inefficient manual booking records, and unmanaged cancellations. 
The primary objectives of the DCQMS project are:
* Digitizing appointment scheduling to minimize front-desk manual workload.
* Introducing automated real-time queue token tracking for transparency.
* Providing clear operational reporting for clinic management and analytics.

#### 1.3 Project Scope
* **In-Scope:** Patient account registration, multi-role authentication, doctor availability management, real-time appointment slot booking, cancellation workflows, automated queue token generation, SMS notifications, and administrative analytics reporting.
* **Out-of-Scope:** Telemedicine/video consultations, Electronic Medical Records (EMR) diagnosis logging, electronic prescription fulfillment, online pharmacy management, and direct online payment processing gateways.

#### 1.4 Acronyms & Definitions
* **DCQMS:** Digital Clinic Appointment & Queue Management System
* **SRS:** Software Requirements Specification
* **BA:** Business Analyst
* **RBAC:** Role-Based Access Control
* **OTP:** One-Time Password (for SMS validation)

---

### 2. Overall Description

#### 2.1 Product Perspective
The DCQMS is a web application designed around Agile software development standards. It acts as an operational bridge connecting patients, front-desk receptionists, doctors, and clinic administrators.

#### 2.2 User Classes & Stakeholder Profiles
* **Patients:** End-users who register accounts, view doctor availability, book/cancel appointments, and receive real-time queue tokens.
* **Receptionists:** Front-desk staff handling walk-in patient registrations, manual slot overrides, and check-in verifications.
* **Doctors:** Medical staff who access real-time daily session schedules, view patient lists, and monitor active queue sequences.
* **Clinic Administrators:** Management personnel who configure system parameters, doctor schedules, and review operational analytics.

---

### 3. Functional Requirements

| Req ID | Module / Requirement Description | Priority | Traceable Jira Epic |
| :--- | :--- | :--- | :--- |
| **FR-01** | System shall allow new patients to register with Name, Mobile Number, Email, and Password with validation. | High | EPIC-01 |
| **FR-02** | System shall authenticate patients and clinic staff securely using encrypted credentials and Role-Based Access Control (RBAC). | High | EPIC-01 |
| **FR-03** | System shall display active doctor profiles, specializations, and verified weekly availability schedules. | High | EPIC-02 |
| **FR-04** | System shall display available real-time appointment slots for selected dates, preventing duplicate slot allocation. | High | EPIC-02 |
| **FR-05** | System shall allow patients to book available slots and issue a unique Reference ID upon confirmation. | High | EPIC-02 |
| **FR-06** | System shall allow patients to cancel eligible appointments up to 2 hours prior to start time and auto-release the slot. | Medium | EPIC-02 |
| **FR-07** | System shall generate a unique sequential queue token number per doctor session upon booking confirmation. | High | EPIC-03 |
| **FR-08** | System shall provide doctors and receptionists with a dedicated live dashboard showing daily appointment lists and active queue sequences. | High | EPIC-03 |
| **FR-09** | System shall dispatch automated SMS confirmation, token updates, and cancellation alerts to registered mobile numbers. | Medium | EPIC-03 |
| **FR-10** | System shall generate daily and weekly analytical reports (total bookings, cancellations, completed visits) for clinic administrators. | Medium | EPIC-04 |

---

### 4. Non-Functional Requirements

#### 4.1 Usability & Browser Compatibility
* **NFR-01:** The web interface must be responsive across desktop, tablet, and mobile browsers (Chrome, Firefox, Safari, Edge) without horizontal scroll distortion.

#### 4.2 Security & Access Control
* **NFR-02:** All sensitive patient data and passwords must be encrypted in transit using TLS 1.3 and at rest using AES-256 encryption standards.
* **NFR-03:** Role-Based Access Control (RBAC) must restrict administrative configuration and analytical data access strictly to verified staff accounts.

#### 4.3 Performance & Reliability
* **NFR-04:** System page load times and booking transactions must complete within 2.0 seconds under standard concurrent operational loads.
* **NFR-05:** The system must maintain 99.5% operational availability during standard clinic operating hours (7:00 AM – 9:00 PM).

---

### 5. Agile Backlog & Jira Requirements Mapping

#### 5.1 Epics Overview

| Epic ID | Epic Name | Scope Description |
| :--- | :--- | :--- |
| **EPIC-01** | Patient & Authentication Management | User registration, multi-role secure login, profile maintenance. |
| **EPIC-02** | Doctor Schedule & Booking Engine | Schedule display, real-time availability, booking, and cancellation workflows. |
| **EPIC-03** | Real-Time Queue & Notification System | Sequential queue token generation and automated SMS alerts. |
| **EPIC-04** | Clinic Administration & Analytics | Daily summaries, status filtering, capacity tracking, and volume reporting. |

#### 5.2 User Stories & Acceptance Criteria (Gherkin Syntax)

##### 🔹 Story ID: US-01 (EPIC-01) - Patient Account Registration
* **User Story:** As a new patient, I want to create an account using my personal and contact details so that I can book appointments online.
* **Acceptance Criteria:**
  * **Given** valid user details (Name, Valid Mobile, Email, Strong Password), **when** submitted, **then** the system must create an account and send a welcome verification SMS.
  * **Given** an existing email address or mobile number, **when** entered during registration, **then** the system must reject duplicate registration and show an appropriate error message.

##### 🔹 Story ID: US-02 (EPIC-02) - Book Doctor Appointment
* **User Story:** As a registered patient, I want to select an available doctor and open time slot so that I can secure an OPD appointment.
* **Acceptance Criteria:**
  * **Given** an authenticated session, **when** an available slot is selected and confirmed, **then** the system must lock the slot and issue a unique Reference ID.
  * **Given** a slot currently being processed by another user, **when** attempted to book, **then** the system must prevent double-booking and prompt to select another slot.

##### 🔹 Story ID: US-03 (EPIC-02) - Cancel Appointment Workflow
* **User Story:** As a patient, I want to cancel my active appointment so that the slot becomes available for other patients in need.
* **Acceptance Criteria:**
  * **Given** an active booking, **when** cancelled at least 2 hours prior to the session start time, **then** the system must update status to "Cancelled" and auto-release the slot.
  * **Given** a cancellation request within less than 2 hours of the session, **then** the system must notify the patient that late cancellation is restricted and direct them to contact front-desk support.

##### 🔹 Story ID: US-04 (EPIC-03) - Generate Sequential Queue Token
* **User Story:** As a patient with a confirmed booking, I want to receive a sequential queue token number so that I know my position in the clinic queue.
* **Acceptance Criteria:**
  * **Given** a confirmed booking, **then** the system must assign a unique daily sequential queue number per doctor (e.g., DOC-A-001).
  * **Given** a cancelled booking, **then** the system must flag the token invalid without breaking or corrupting the remaining queue sequence.

##### 🔹 Story ID: US-05 (EPIC-03) - Automated SMS Alerts
* **User Story:** As a patient, I want to receive an immediate SMS notification so that I have offline access to my booking details and queue token.
* **Acceptance Criteria:**
  * **Given** a confirmed or cancelled booking, **then** the system must trigger an SMS containing Doctor Name, Time, Reference ID, and Queue Token within 60 seconds.

##### 🔹 Story ID: US-06 (EPIC-04) - Admin Analytical Volume Report
* **User Story:** As a clinic administrator, I want to generate daily and weekly appointment reports so that I can analyze patient traffic and cancellation trends.
* **Acceptance Criteria:**
  * **Given** admin role authorization, **when** filtering by Date Range, Doctor, or Status (Completed, Cancelled, No-Show), **then** the system must generate a visual and downloadable report summary.

---
> **Note:** *This is an initial release document (v1.0 Draft). Additional requirements and expansions will be continuously updated.*
