Phabricator
===========

Phabricator is the software we use for development. It can be found at
https://marisa.cloud (the website is called marisa dot cloud, but it uses the
software called Phabricator). This page explains a couple of common things you
might want to do in Phabricator.

.. _phab-creating-account:

Creating an account
-------------------

You can either create an account directly or log in with your GitHub account.

Creating an account directly
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To create an account via Phabricator itself, visit `this page
<https://marisa.cloud/auth/register/>`_. You should then get an email with which
you can confirm your account.

Creating an account via GitHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can also log in via your GitHub account by clicking the GitHub logo on `this
page <https://marisa.cloud/auth/start/>`_.

Troubleshooting
^^^^^^^^^^^^^^^

- If you're not getting the verification email, please ask on Discord!
- Similarly, if you created an account with the wrong email address, we can't
  correct the address, but we can delete the account so you can try again.

Receiving updates and notifications
-----------------------------------

Phabricator notifies you about relevant activity, including `your own actions
<https://marisa.cloud/settings/panel/emaildelivery/>`_.

Phabricator offers several tools to receive the notifications you wish to receive.

- If you are interested in a single object (a task, a revision...) just click
  ``Subscribe`` in its page. Adding a comment will subscribe you automatically.
- If you are interested in all the activity within a project, you can click
  Watch Project on the project summary page.

Troubleshooting
^^^^^^^^^^^^^^^

If you receive unexpected mail notifications for a task:

- You might be subscribed to the task.
- You might be a member of a project or of a subproject associated to that task.
  A list of all projects that you are a member of is available.
- You might watch a project associated to that task. A list of all projects that
  you watch is available.
- In your `email preferences
  <https://marisa.cloud/settings/panel/emailpreferences/>`_ under "Maniphest
  Tasks", you might have enabled "One of a task's subtasks changes status".
- You might have a personal Herald rule set up. Check the "X-Herald-Rules"
  message header field to see a list of all applied Herald rules.

Creating a Task
---------------

There are several ways to create a task, depending on the information you want to carry:

- A new task: click the Bookmark button toward the right side of the top
  navigation bar. From the dropdown menu, choose Create Tometo Task. You will get a
  blank form.
- A security problem: click the Bookmark button toward the right side of the top
  navigation bar. From the dropdown menu, choose Report Tometo Security Issue. You will
  get a form pre-tagged with Security, and with a link to special instructions
  for filing security bugs.
- A subtask of an existing task: click **Edit Related Tasks… > Create Subtask**
  located in the right column of the current task. The dependency between both
  tasks will be set, and some values of the parent task will be carried by
  default (Assigned To, Subscribers, Priority, Projects). Subtasks will be
  listed in the parent task under "Task Graph", sorted by most recently updated.

Fill the form, leaving the fields you are not sure about unchanged. Use the live
preview at the end of the page to check whether your text looks as you expect.

Commenting and editing a task
-----------------------------

To reply, you need an account as well.

Phabricator allows you to post and edit comments and descriptions using text
formatting and inserting images or other files. To insert a file, just drag and
drop, paste or select it from the File Upload button.
You can use toolbar at the top of the input text area and you can use
Phabricator's own formatting.

To edit the description of a task, select "Edit Task" in the side bar.

To close a task as a duplicate of another task, select "Edit Related Tasks... >
Close As Duplicate" in the side bar.

Project Management in Phabricator
---------------------------------

More detailed information about this can be found in :doc:`Phabricator/Projects
</phabricator/projects>`.

Parent tasks and subtasks
^^^^^^^^^^^^^^^^^^^^^^^^^

Tasks can be a parent task or a subtask of any number of other tasks. If Task A
is not solved until Task B is solved, then Task A is the parent task, and Task B
is the subtask. Such relations can be set via "Edit Related Tasks...". Parent
tasks and subtasks are displayed under "Task Graph" in the task. This feature
can be used to accomplish a few different things:

- Blockers and Subtasks. A (parent) task might simply be blocked by another
  (sub)task, representing a dependency.
- Tracking. A "workless" (parent) task blocked by several (sub)tasks might be
  tracking a collection of (subtasks within a release or other time period.)

More advanced features
----------------------

Restricting access to tasks
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Access to a specific task can be changed via "Edit Task" and then changing the
"Visible To" field to something else than "Public". This option is only
available to some users.

Note that tasks filed as Security issues are not publicly visible.
