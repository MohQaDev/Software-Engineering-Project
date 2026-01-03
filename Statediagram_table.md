# Assignment Lifecycle Documentation




## State-Stimulus Table

| Current State | Stimulus (Event) | Action | Next State |
| :--- | :--- | :--- | :--- |
| **[Initial]** | Instructor creates assignment | Initialize assignment data (title, details, deadline) | **Draft** |
| **Draft** | Instructor edits details | Update assignment fields (title, details, deadline) | **Draft** |
| **Draft** | Instructor publishes assignment | Validate required fields, make visible to students | **Published** |
| **Published** | Students view assignment | Display assignment details to student | **Published** |
| **Published** | Student submits work | Record submission timestamp, store file, notify instructor | **Submitted** |
| **Submitted** | Student views submission status | Display submission confirmation and timestamp | **Submitted** |
| **Submitted** | Instructor begins grading | Lock submission for grading process | **Under Review** |
| **Under Review** | Instructor assigns grade and feedback | Finalize grade, store in database | **Graded** |
| **Graded** | System publishes grade | Store grade in database, trigger notification to student | **[Final State]** |

---

## State Descriptions

| State | Description |
| :--- | :--- |
| **Draft** | Assignment is being created by the instructor but not yet visible to students. Instructor can still edit all fields. |
| **Published** | Assignment is visible to students and accepting submissions. Assignment details are locked. |
| **Submitted** | At least one student has submitted work for the assignment. Multiple submissions possible. |
| **Under Review** | Instructor is actively grading submissions. Submissions are locked from further changes. |
| **Graded** | All submissions have been graded and feedback has been provided. Students can view their results. |

