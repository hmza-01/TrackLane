# Project Proposal

**TrackLane: A Normalized Database for Agile Workflow and Issue
Tracking**

## 1. Project Information

-   **Project Name:** TrackLane -- A Normalized Database for Agile
    Workflow and Issue Tracking

-   **Members and Roll Numbers:** Rana Muhammad Hamza (BCSF25M015),
    Muhammad Dawood Saleh Khan (BCSF25M038)

-   **Chosen DBMS: **PostgreSQL

-   **GitHub Repository:** https://github.com/hmza-01/TrackLane

-   **Assigned Roles:**

    -   Member 1 : Data modeling, normalization , transaction handling,
        views and indexes, queries, procedures and triggers
    -   Member 2 : schema design, schema implementation, performance
        tuning, requirements document
    -   Shared: Frontend, Test plan, data dictionary, and final report.

## 2. Problem Statement

Student project groups and small development teams depend on shared task
lists, chat messages, and spreadsheets to coordinate work. When several
people contribute, it becomes hard to tell who is responsible for each
task, what has changed and who changed it, whether a task was moved
through its workflow in a valid order, and how much effort each person
has spent. Without a structured system this information is scattered,
inconsistent, and difficult to verify.

## 3. Why This Topic Is Important and Unique

TrackLane matters because accountability and progress tracking decide
whether collaborative work succeeds, and teams often discover problems
only after the history is lost. What makes it different from a basic
ticket list is that the rules live in the database, not in an
application: permitted status transitions are stored and checked, every
change to an issue is recorded with who, when, old value, and new value,
and issue dependencies are validated so blocked work can be identified.
The project focuses on workflow validity, audit history, and effort
tracking rather than on screens.

## 4. Proposed Solution

TrackLane is a database-first project management and issue-tracking
system that organizes work into organizations, projects, team
memberships, and issues. Issues are assigned to members, categorized by
type and priority, and tracked through statuses such as To Do, In
Progress, and Done. A status-transition structure defines which
movements are permitted, and an audit history records how each issue
reached its current state. Boards, comments, attachments, labels,
dependencies, project roles, and work logs complete the model. The
database will use primary keys, foreign keys, integrity constraints, and
transactions to stay consistent.

## 5. Stakeholders

-   **Organization Administrators:** manage organizational information
    and users.
-   **Project Managers and Team Leads:** create projects, distribute
    responsibilities, and monitor progress.
-   **Developers and Contributors:** work on assigned issues, update
    progress, and record effort.
-   **QA Testers:** report bugs and verify completed work.
-   **Project Supervisors:** review activity, workload distribution, and
    recorded contributions.

## 6. Questions the Database Should Answer

1.  How is work divided? Which members are assigned to which issues, and
    how is work distributed across projects?
2.  Who has done what? Which users created or modified issues, changed
    assignments, or updated statuses?
3.  Is the workflow valid? Are status changes permitted, and which
    issues are blocked by dependencies?
4.  How much work has been performed? How much time has each member
    recorded against issues and projects?

## 7. Initial Entity List

-   **Organization and Project Management:** ORGANIZATIONS, USERS,
    PROJECTS, PROJECT_MEMBERS, ROLES.
-   **Issue Management:** ISSUES, ISSUE_TYPE, STATUS, PRIORITY,
    ISSUE_LINKS.
-   **Workflow and Accountability:** STATUS_TRANSITIONS, AUDIT_HISTORY.
-   **Collaboration and Effort:** COMMENTS, ATTACHMENTS, WORK_LOGS.
-   **Visualization and Organization:** BOARDS, BOARD_COLUMNS, LABELS,
    ISSUE_LABELS.

## 8. Business Rules Enforced by the Database

1.  A status change is allowed only if a matching row exists in
    STATUS_TRANSITIONS (trigger).
2.  An issue cannot depend on itself, and dependency cycles are rejected
    (CHECK and trigger).
3.  The reporter and assignee of an issue must be members of its project
    (composite foreign key).
4.  Every change to a tracked issue field writes an AUDIT_HISTORY row,
    and audit rows cannot be edited or deleted (trigger).
5.  A project key is unique within an organization (UNIQUE).
6.  Work-log minutes must be greater than zero (CHECK).
7.  Board column positions are unique within a board (UNIQUE).
8.  A user has exactly one role in a given project (composite primary
    key).

## 9. Implementation Approach and Use of AI

The group will gather requirements, design and normalize the ERD, map it
to a relational schema, and implement it in SQL with constraints, views,
indexes, procedures, triggers, transactions, and sample data. AI tools
will be used only for conceptual clarification and feedback, and every
use will be recorded in an AI usage log. The design and SQL will be
written and tested by the group members. The optional AI-built
application track will not be used; the full workflow will be
demonstrated through the frontend and SQL scripts

