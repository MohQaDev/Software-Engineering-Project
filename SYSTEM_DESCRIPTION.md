# Learning Management System (LMS) - System Documentation

## 1. Project Definition and Purpose
The **Learning Management System (LMS)** is a centralized, web-based platform designed to facilitate digital teaching, structured learning, and academic management. The system provides a secure environment where instructors can deliver course content and assessments, while students can interact with resources and track their academic progress. By replacing manual paperwork with automated digital workflows, the LMS ensures data accuracy, real-time feedback, and high accessibility for all academic stakeholders.

---

## 2. Context and Business Environment
The LMS sits at the center of the educational business environment, serving as the primary engine for academic operations. As illustrated in the **Context Model**, the system interacts with several external and internal entities:

* **Instructors:** The primary content providers who manage curriculum and evaluate students.
* **Students:** The primary consumers of learning materials and recipients of feedback.
* **Administrators:** Oversee system configuration, user roles, and security.
* **Email/Notification Services:** An external integration used to trigger real-time alerts regarding deadlines, new assignments, and published grades.



---

## 3. Key Business Processes (Activity Flow)
The system’s utility is defined through two primary business processes that govern the flow of data:

* **Assignment Lifecycle Management:** This process manages the creation and publication of assessments. The system enforces a validation workflow ensuring an assignment is "Published" before becoming visible to students.
* **Evaluation and Feedback Loop:** This process captures student submissions, facilitates instructor grading, and automates the generation of performance analytics.



---

## 4. User Interactions (Use Cases)
Functionality is partitioned by user roles to ensure a streamlined experience. For the **Student** (the primary actor), the system provides several composite use cases:

* **Academic Tasks:** Viewing and submitting assignments.
* **Performance Monitoring:** Accessing detailed performance reports and GPA metrics.
* **Resource Management:** Viewing courses and system notifications.

Detailed interactions, such as "View Performance Report," involve **Instructors** as secondary actors who must finalize grading data before the system can successfully respond to the student’s stimulus.



---

## 5. System Structure and Data Architecture
The static architecture of the platform is defined by five core entities maintained in a centralized relational database:

* **User Hierarchy:** Utilizes **Generalization (Inheritance)** to define a base `User` class that extends into `Student`, `Instructor`, and `Administrator`.
* **Course & Assignment Relationship:** A **Composition** relationship exists between Courses and Assignments; assignments cannot exist without an associated course.
* **Submissions and Grades:** These entities capture the critical intersection between student work and instructor evaluation.



---

## 6. Primary Behavior (Data and Event Logic)
The LMS utilizes a hybrid of data-driven and event-driven logic to manage complexity:

### Event-Driven Behavior (State Logic)
The system tracks the status of assignments and submissions using a **State Diagram**. Objects transition between states (e.g., `Draft` → `Published` → `Submitted` → `Graded`) based on specific stimuli.
* *Example:* The stimulus "Instructor begins grading" transitions a submission to the `Under Review` state, which locks the file from further student changes.



### Data Flow and Sequencing
The **Sequence Diagrams** define the chronological flow of messages between the UI, Controllers, and the Database. This ensures that:
1.  **Stakeholders** understand the business logic flow.
2.  **Developers** have a blueprint for implementing specific API endpoints, database queries, and error-handling routines (e.g., handling "No Assignments Found" scenarios).
