# TrackLane: Project Requirements Document

**Agile Workflow and Issue Tracking for Small Teams**

**Members:** Rana Muhammad Hamza (BCSF25M015), Muhammad Dawood Saleh Khan (BCSF25M038)
**GitHub Repository:** https://github.com/hmza-01/TrackLane

---

## 1. What the Project Aims to Achieve

TrackLane aims to give small teams and student project groups a single, trustworthy place to plan work, assign it, move it through a defined workflow, and record how much effort was spent, so that nobody has to guess who did what or whether a task was handled properly.

**Goals**

1. **Clear ownership.** Every issue has a reporter and (once assigned) an assignee, so it is always possible to see who is responsible for what.
2. **Enforced workflow.** An issue can only move between statuses in ways the team has defined as valid. Invalid moves are refused, not just discouraged.
3. **Complete history.** Every meaningful change to an issue is remembered: what changed, who changed it, when, and the old and new values. This history cannot be altered or erased.
4. **Visible dependencies.** Teams can see which issues are waiting on other issues, and contradictory dependencies (an issue depending on itself, or issues waiting on each other in a loop) are prevented.
5. **Measurable effort.** Members record time spent on issues, and totals can be viewed per person, per issue and per project.
6. **Reliable answers.** The system can answer, for any project: how work is divided, who has done what, whether the workflow was followed validly, and how much work has been performed.
7. **Sprint visibility.** Work can be grouped into time-boxed sprints, and each sprint can be summarized: what was planned, what was finished, what was left over, how much time was spent and by whom.

## 2. Problems the System Will Solve

Student project groups and small development teams depend on shared task lists, chat messages and spreadsheets. When several people contribute, it becomes hard to tell who is responsible for each task, what has changed and who changed it, whether a task was moved through its workflow in a valid order, and how much effort each person has spent.

| Problem today | What TrackLane does about it |
|---|---|
| Tasks live in chats and spreadsheets; nobody is sure who owns them | Each issue has a recorded reporter and assignee, who must belong to the project |
| Tasks are moved to "Done" without passing through the proper steps | Only permitted status changes are accepted; others are rejected with a clear message |
| Changes are made silently and history is lost | Every change to a tracked issue field is logged with who, when, old value and new value; the log cannot be edited or deleted |
| It is unclear which tasks are blocked | Dependencies between issues are recorded and blocked issues can be listed |
| Effort is claimed but not evidenced | Time is logged against issues and summarized per member and project |
| Supervisors cannot verify individual contributions | Supervisors can review activity, workload distribution and recorded effort per member |
| Nobody can tell whether the work planned for a period was actually finished | Work is grouped into sprints; each sprint reports issues planned, completed and unfinished, the completion rate, and time logged per member |

## 3. What the System Will Do and How It Will Behave

### 3.1 Organizations, users and projects
- Organizations can be created, and users belong to an organization.
- Projects are created within an organization and have a short project key that is unique within that organization (two different organizations may use the same key).
- Users are added to a project with exactly one role in that project (for example manager, developer, QA tester, supervisor). A user can belong to several projects, with a different role in each.
- Only members of a project can be reporters or assignees of its issues.

### 3.2 Issues
- Members can create issues with a title, description, type (such as bug, task, story), priority and starting status.
- Issues can be assigned, reassigned, unassigned and edited.
- Issues can be tagged with labels and shown on a board.
- Comments and attachments can be added to issues.

### 3.3 Workflow and status changes
- Statuses (for example To Do, In Progress, Done) and the allowed moves between them are defined by the team.
- When a status change is requested, the system checks that the move is allowed. If it is not, the change is refused and the issue stays exactly as it was.

### 3.4 History of changes
- Changes to tracked fields of an issue (such as status, assignee, priority, title) automatically produce a history entry showing the user, the time, the old value and the new value.
- History entries cannot be edited or deleted by anyone.
- The full history of an issue can be read in time order to see how it arrived at its current state.

### 3.5 Dependencies
- One issue can be marked as depending on (blocked by) another.
- An issue cannot depend on itself.
- Circular chains (A waits on B, B waits on C, C waits on A) are refused.
- The system can list issues that are currently blocked and what they are blocked by.

### 3.6 Effort tracking
- Members record work done on an issue as a number of minutes, with an optional note and date.
- Zero or negative time is refused.
- Totals of recorded time can be viewed per member, per issue and per project.

### 3.7 Boards
- A project can have boards made of ordered columns (for example one per status).
- Column positions within a board are unique, so the order is always unambiguous.
- Issues appear in the board column matching their status.

### 3.8 Reporting and review
- **Work division:** which members are assigned to which issues, and how work is distributed across projects.
- **Who has done what:** which users created or modified issues, changed assignments or updated statuses.
- **Workflow validity:** which status changes were made, and which issues are blocked by dependencies.
- **Work performed:** how much time each member has recorded against issues and projects.
- **Sprint progress:** how much of the work planned for a sprint was completed, and how effort was spent within it (see 3.9).

### 3.9 Sprints and sprint analytics

**Sprints**
- A project can have sprints. Each sprint has a name, a start date and an end date, and belongs to exactly one project.
- Sprint names are unique within a project, the end date cannot be before the start date, and sprints of the same project cannot overlap in time.
- Issues can be added to and removed from a sprint, but only issues of the same project as the sprint.
- An issue that is not finished can be carried over to a later sprint. It stays linked to the earlier sprint, so the earlier sprint's record is preserved.
- A sprint is either open or closed. Once a sprint is closed, issues can no longer be added to or removed from it, so its figures stay stable.
- Adding an issue to a sprint or removing it is recorded in that issue's history, like any other tracked change.

**How sprint reports interpret the data**
- **Final status:** a status the team marks as the end of its workflow (for example Done).
- **Planned:** all issues linked to the sprint.
- **Completed:** an issue that reached a final status and was not reopened by the sprint's end date. For a sprint still open, an issue that is currently in a final status. The moment of completion is taken from the issue's history, not from a separate field that could be edited.
- **Unfinished:** planned issues that are not completed.
- **Minutes logged:** work logs on the sprint's issues dated within the sprint's start and end dates. Time logged outside those dates is not counted for the sprint.

**Sprint reports**
- **Sprint summary** (input: one sprint): issues planned, issues completed, issues unfinished, completion rate (completed divided by planned), and total minutes logged. A per-member breakdown shows, for each member, the issues assigned to them in the sprint, how many are completed and the minutes they logged. Unassigned issues appear as their own line.
- **Unfinished issues** (input: one sprint): which issues were not completed and, where applicable, the later sprint they were carried over to.
- **Sprint comparison** (input: one project): all sprints of the project side by side, showing issues planned, issues completed, completion rate and total minutes logged.

### 3.10 Frontend
- A simple frontend demonstrates the full workflow: creating issues, assigning them, moving them through statuses, logging work, viewing history and viewing reports.
- The frontend also lets a user create a sprint, add issues to it, close it and view the sprint reports.

## 4. Scenarios and Situations the System Will Handle

### 4.1 Normal scenarios

| # | Scenario | Expected result |
|---|---|---|
| S1 | A manager creates a project in an organization and adds three members with different roles | Project exists with its key; each member has exactly one role |
| S2 | A developer reports a bug and assigns it to a teammate in the same project | Issue is created with reporter, assignee, type, priority and starting status; a history entry is recorded |
| S3 | The assignee moves the issue from To Do to In Progress | Accepted, because the move is allowed; history shows old and new status, user and time |
| S4 | The assignee logs 90 minutes of work on the issue | Work log saved; totals for the member, issue and project increase by 90 |
| S5 | A QA tester comments on the issue and attaches a file | Comment and attachment are stored and shown with the issue |
| S6 | A manager reassigns the issue to someone else | Assignee changes; history shows previous and new assignee and who changed it |
| S7 | A manager marks issue B as depending on issue A | Dependency is saved; B appears as blocked while A is not complete |
| S8 | A supervisor reviews workload and effort for a project | Report shows issues per member and logged time per member |
| S9 | A manager creates a board with ordered columns and tags issues with labels | Board shows issues in the correct columns; labels are filterable |
| S10 | The same project key (e.g. "WEB") is used in two different organizations | Both are accepted; they do not conflict |
| S11 | A manager creates "Sprint 1" with a start and end date and adds eight issues from the project | Sprint exists with its dates; the eight issues are linked to it; each addition appears in the issue's history |
| S12 | During the sprint, five of the eight issues reach Done and members log time on them; a supervisor opens the sprint summary | Summary shows 8 planned, 5 completed, 3 unfinished, a 62.5% completion rate, total minutes logged and minutes per member |
| S13 | At the end of the sprint the manager closes it and carries two unfinished issues over to "Sprint 2" | Sprint 1 keeps all eight issues and still reports them as 5 completed and 3 unfinished; Sprint 2 lists the two carried-over issues as planned |
| S14 | A supervisor compares all sprints of a project | Report lists each sprint with planned, completed, completion rate and total minutes, side by side |

### 4.2 Invalid scenarios (the system must refuse)

| # | Scenario | Expected result |
|---|---|---|
| R1 | A user moves an issue directly from To Do to Done when that move is not permitted | Rejected with an error; status and history unchanged |
| R2 | An issue is assigned to a user who is not a member of its project | Rejected |
| R3 | An issue is created with a reporter who is not a member of its project | Rejected |
| R4 | An issue is made dependent on itself | Rejected |
| R5 | A depends on B, B on C, and someone makes C depend on A | Rejected as a cycle |
| R6 | Someone tries to edit or delete a history entry | Rejected; history remains intact |
| R7 | A work log of zero or negative minutes is submitted | Rejected |
| R8 | A second project with an already used key is created in the same organization | Rejected |
| R9 | Two columns are given the same position on one board | Rejected |
| R10 | A user is given a second, different role in the same project | Rejected |
| R11 | A sprint is created with an end date before its start date | Rejected |
| R12 | A sprint is created whose dates overlap another sprint of the same project | Rejected |
| R13 | A second sprint with an already used name is created in the same project | Rejected |
| R14 | An issue is added to a sprint that belongs to a different project | Rejected |
| R15 | An issue is added to or removed from a closed sprint | Rejected; the sprint's figures remain unchanged |

### 4.3 Edge cases
- Several fields of an issue are changed at once: one history entry is recorded per changed field.
- An update that changes nothing does not produce misleading history entries.
- A change that is rejected part-way leaves no partial changes behind; it succeeds completely or not at all.
- Two users edit the same issue at nearly the same time: both changes are processed safely and both appear in history.
- An unassigned issue is still valid and appears in workload reports as unassigned.
- An issue with no work logs shows zero recorded effort rather than being left out of reports.
- A sprint with no issues shows zeros in its summary, and its completion rate is shown as "not applicable" instead of causing a division error.
- An unassigned issue in a sprint is counted in the sprint totals and shown as "Unassigned" in the per-member breakdown.
- An issue that was completed and later reopened is no longer counted as completed in a sprint that is still open. In a closed sprint, completion is judged as of the sprint's end date, so reopening the issue later does not change that sprint's figures.
- An issue carried over to the next sprint counts as unfinished in the earlier sprint and as planned in the later one, and its time is counted only in the sprint whose dates the work log falls within.
- Adding the same issue to the same sprint twice does not create a duplicate link or a duplicate history entry.
- Time logged on a sprint's issue on a date outside the sprint's dates is not counted in that sprint's minutes.

## 5. Scope

### 5.1 Included
- Organizations, users, projects, project membership and per-project roles.
- Issues with types, priorities, statuses, assignees and reporters.
- Enforced workflow of permitted status changes.
- Tamper-proof history of issue changes.
- Issue dependencies with self-dependency and loop prevention.
- Comments, attachments, labels and boards with ordered columns.
- Work logging and effort summaries.
- Reports covering work division, contributions, workflow validity and effort.
- Sprints with dates, open/closed state and carry-over of unfinished issues.
- Sprint analytics: sprint summary (planned, completed, unfinished, completion rate, time logged per member), unfinished-issue list and sprint comparison per project.
- A simple frontend demonstrating the full workflow, including sprints.

### 5.2 Excluded
- Real-time collaboration (live updates, live cursors).
- Email, SMS or chat notifications and reminders.
- Integration with outside tools (GitHub, Slack, calendars, etc.).
- Advanced sprint analytics: velocity, burndown and burnup charts, story points, and automated estimation.
- Mobile applications.
- Advanced account security such as single sign-on, two-factor authentication and password recovery.
- Full-text search across all content.
- Import and export from other issue trackers.
- Billing, invoicing or payroll based on logged time.
- A polished, production-grade user interface.

## 6. What the System Will NOT Do or Support

- It will **not** let the history of an issue be edited or deleted, for any user.
- It will **not** accept a status change that is not in the permitted list, whoever requests it.
- It will **not** decide which workflow is right; it enforces whatever moves the team has defined.
- It will **not** automatically assign issues, estimate effort, predict deadlines or prioritize work.
- It will **not** produce velocity figures, burndown charts or forecasts of how a sprint will end; sprint reports describe what has happened, not what will happen.
- It will **not** change the figures of a closed sprint afterwards, and it will **not** allow sprints of one project to overlap or issues to be placed in a sprint of another project.
- It will **not** verify that logged time is truthful; it records what members report and makes it reviewable.
- It will **not** track changes to every possible field; only the designated tracked fields of an issue are recorded.
- It will **not** allow a user to hold several roles within the same project at once.
- It will **not** allow one project to be shared between multiple organizations.
- It will **not** act as a file storage or document management system beyond attaching files to issues.
- It will **not** replace full tools such as Jira; it is a focused system for workflow validity, accountability and effort tracking.
