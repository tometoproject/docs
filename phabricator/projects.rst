Project Management
==================

This guide focuses on productively managing a Tometo project. A project here is
defined as a unit of what makes up Tometo. There's the base ``tometo`` project,
but a project can also be a milestone, a component, a team, and basically
anything else that can be separated by hierarchy.

Tasks
-----

Tasks are the basic building block of Phabricator. A Phabricator task is
something that can define things like bugs, user stories, feature requests, etc.
While a task can represent different kinds of things, all tasks have certain
properties, like title, author (creator), assignee, description, projects/tags,
etc. Unlike many other project management and issue tracking tools, a task can
have a one-to-many relationship with 'projects' - that is, a single task can be
associated with more than one 'project'.

Scope of Tasks
^^^^^^^^^^^^^^

Tasks need to describe an achievable objective. Ideally, tasks are defined with
a scope that can be resolved by one person with a decent amount of effort. Huge
tasks that take several people and several days will be more manageable when you
identify the subtasks required to complete them. Trivial subtasks that one
person can complete in a moment but should be documented can be just added as a
checklist in a description of the main task. A good principle to follow is that
a task should be completeable in ~3 days maximum. If a task is larger than
this, it should be broken down into smaller tasks. Also consider this piece of
advice: does your task require more than a couple of hours of work? Then you may
want to add it to Phabricator. Would there be nasty consequences if you forgot
executing that task? Avoid this by adding it to Phabricator.

Team-level goals are often called "Epics". Some projects have an "Epic" column
in their workboard, which is used for tracking larger goals that require months
worth of work.

If a task fails defining an actionable objective (e.g. never-ending tasks,
support questions, generic complaints...) they might be resolved as Invalid.
Users resolving a task as Invalid should explain their reasons in a comment
(also see the Bug report life cycle). Tasks are fully editable, and if the
causes for the Invalid resolution have been addressed, they can be reopened.

Assigning Tasks
^^^^^^^^^^^^^^^

Each Task may be assigned to one person. As with Priority, this is inherent to
the Task, and affects every Project that Task is in. So it is impossible to have
a Task assigned to Lucy in one Project, but to Kim in another. The assigned
person is displayed as part of the Task card in each Workboard.

In principle, a task gets assigned to whomever will take ownership of it. Some
teams might choose to assign Tasks to people while the Tasks are in a TODO
column. Others would have people assign Tasks to themselves only at the moment
that they are moving them from TODO to DOING. Try to avoid assigning a task to
yourself before you start working on it.

Setting Task priorities
^^^^^^^^^^^^^^^^^^^^^^^

Each Task has a Priority field, which is reflected in the sidebar color of Tasks
that appear in Workboards. Note that this Priority is inherent to the Task, and
thus will be the same in every Project and Workboard that task appears in.

One task can have only one set priority at a time. Priority should normally be
set by the Triage team, the Core team, or committers who plan
to work on the task, or by the Bugwrangler or experienced community members, not
by the reporter filing the bug report or by outside observers. When in doubt, do
not change the Priority field value, but add a comment suggesting the change and
convincing reasons for it.

Within a Workboard, Tasks can be grouped by priority within a column. Choose
"Natural" to have no grouping. Drag and drop Tasks up or down within a column.
This allows a groomed backlog to be sequenced by priority, or could indicate the
urgency of items in a "Needs Review" column. Note that Workboard columns can be
grouped by several criteria, so while discussing a Workboard with someone not in
the room, it is best to agree on and use the same sort order to avoid confusion.

We offer these priority levels on Phabricator:

- Needs Triage - Default option, this indicates that the Triage team or someone
  else with enough experience has to prioritize this task.
- Unbreak Now! - Something is broken or needs to be fixed immediately, setting
  anything else aside.
- High - Someone is working or planning to work on this task soon.
- Medium - Less priority than High, but someone is still planning on working on
  it.
- Low - Less priority than Medium, but someone is still working on it. This
  doesn't necessarily mean the task is not important, it just means that nobody
  has this on their to-do list right now.
- Lowest - Nobody plans to work on this task, but we would be happy if somebody
  does.

Tasks that cannot be worked on yet
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Certain tasks might not be actionable until an action has been performed outside
of the task itself.

If a task depends on another task in Phabricator, you should set the number of
that other task under "Edit Related Tasks... > Edit Subtasks". Afterwards, the
other (sub)task will be displayed under "Task Graph".

Closing a Task
^^^^^^^^^^^^^^

A task can be closed as Resolved, Declined, or Invalid. It can also be merged as
a duplicate of another task (details). When a task is associated with multiple
projects, care should be taken to coordinate the closing of a task with all
involved parties. Anyone marking a task as declined or invalid should
include a comment explaining why.

Projects
--------

Projects are the basic organizational method in Phabricator; they are a way to
organize tasks and manage workflow or to "tag" for queries and general
organization.

Types of Projects
^^^^^^^^^^^^^^^^^

There are several types of top-level projects in our Phabricator. Each type has
to follow the purpose, color and icon defined in these guidelines.

- Types you can request to be created directly:

  - **Component** corresponds to a distinct and recognizable piece of software,
    service, event or any set of periodically occuring tasks of the same type
    (i.e. access or requests). If you're unsure, go for this. *Icon: Briefcase,
    Color: Blue*

    - **Umbrella** could be used for larger Projects that don't have a distinct
      codebase and instead consist of several smaller projects. *Icon:
      Umbrella, Color: Blue*

  - **Group** corresponds to an existing team. *Icon: Group, Color: Violet*
  - **Goal** can be used for goals that will be met at some point in time,
    such as feature implementations. *Icon: Goal, Color: Checkered*
  - **User** allow you to track progress of personal tasks. *Icon: User, Color:
    Orange*

- Types that should be discussed before being created:

  - **Tag** is used as a cross-component keyword (like "translation"), a
    "never-ending" project. *Icon: Tag, Color: Yellow*
  - **ACL** are projects that regulate access. This should be used instead of
    locking down resources to projects like Groups, or locking projects
    themselved. *Icon: Policy, Color: Red*

Archiving a Project
^^^^^^^^^^^^^^^^^^^

If/when your Project is complete, abandoned, or otherwise no longer active, it
should be archived. This prevents clutter and signals to others that the Project
is inactive.

Assuming you have appropriate permissions, to archive a Project:

1. go to your Project page;
2. click the **Manage** item in the navigation bar on the left;
3. click **Archive Project**.

Make sure to handle the open tasks of your archived Project: Either associate
the tasks with at least one other active Project, or close the tasks as declined
in combination with an explanatory comment.

Workboards
----------

The workboard is the primary user interface for viewing and manipulating tasks
that belong to a project. Projects which are used solely as supplemental
"flags", for example i18n, may not use their boards. Boards are useful to follow
the development status of tasks within a 'project'. Keep in mind that boards are
not just a means of managing the flow of work. It's a communication tool both
for your team/project/etc as well as to the public/etc. Boards
should be used and maintained with this in mind; the simpler and clearer the
language used, as well as the clarity of organization of your board, the better
for communicating to a broader audience.

Every 'project' has one single board. You can access it by clicking the
Workboard icon in the left-side menu of the project. If there is no such icon,
the board is disabled. You can enable it via "Manage" in the left-side menu and
then choosing "Edit Menu" on the right.

Columns
^^^^^^^
Project boards may display the tasks in the project in multiple columns. A
project that is itself used as a tag (i18n, Need-volunteer) may not use its
board and thus will not have columns.

When you first set up the board for a project, you can choose "New Empty Board"
which starts with a single "Backlog" column; or you can choose "Import board
columns from another project" to use another board's set of columns as a
starting point. After that you can create arbitrary columns in the board such as
In development, Blocked with questions, Code review, and Done.
Then much like other 'project' management tools you can drag and drop tasks
within and between columns to recategorize them. The order of tasks within each
column is maintained, and you can drag and drop tasks up and down, so it is
common to treat this as another kind of prioritization or stack ranking. A task
can belong to only one column within each board.

Typical uses of workboards
^^^^^^^^^^^^^^^^^^^^^^^^^^

- Workflow
  - Typical columns track the state of tasks, such as Todo, Doing and Done
  - This supports both Scrum-type work and Kanban-style work
  - Tasks are moved from column to column regularly
- Categories
  - Columns might group Tasks by component, functional area or even complexity

Examples
""""""""

- Backlog, Doing, Review, Blocked, (Done)
- To Do, In Progress, In Review, (Done)
- Backlog, Needs Plan, Needs Code, Non-Code, In Development, Needs Review

"Done"
""""""

Each Task has a Status field, which includes the state of Resolved. Resolved
tasks are by default hidden from Workboards. When they are displayed, they
appear grayed out and struck out. Other statuses include Open and Stalled.

It is important not to mark a task Resolved until it is considered done by ALL
of the projects it is in. It's fine to move a Task to your own Workboard's DONE
column, but before you mark a task Resolved, ensure that no other project still
wants to keep tracking its progress.
