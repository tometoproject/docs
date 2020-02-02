How to report a bug
===================

These guidelines explain how to write a good bug report or feature request (a
task) in Tometo's task tracker (see :doc:`Phabricator </phabricator/index>` for
more information). Well-written tasks are more likely to be worked on quickly.

Quick recommendations
---------------------

- Be clear
- Be clear: explain how to reproduce the problem, step by step, so others can
  reproduce the bug, or understand the request.
- Include only one problem per task
- Include any relevant links and examples

Before you do anything
----------------------

Can you reproduce the issue?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Try to reproduce your bug using a recent version of the software, to see whether
it has already been fixed.

Has someone else already reported the issue?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Use the search box of `Tometo's bugtracker <https://marisa.cloud>`_ to see if
your bug has already been reported, or the feature requested. You can also
perform more advanced searches on the advanced search page.

If you are unsure whether a bug has already been reported, you should report the
bug. It is better to have duplicate bugs than it is to have unreported bugs.

Reporting a new bug or feature request
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you have faced a bug in a recent version and no one else appears to have
reported it, then:

1. Go to https://marisa.cloud
2. You will have to log in (or register) if you haven't already done so (see
   :ref:`phab-creating-account`)
3. Click the bookmark button in the upper right corner and choose "Create Tometo
   task"
4. Fill out at least the following fields:

  - **Title**: A short one-sentence summary that explains the problem (not your
    suggested solution).

    - Good: ``Selecting avatar is not functional``
    - Bad: ``Software crashes``

  - **Description**: Full details of the issue, giving as much detail as
    possible. This should include:

    - For bugs:

      - Steps to reproduce: Minimized, easy-to-follow steps that will trigger
        the described problem. Include any special setup steps.
      - Actual Results: What the application did after performing the above
        steps.
      - Expected Results: What the application should have done, if there was no
        bug.

    - For feature requests:

      - A description of what you would like to achieve, and why. Explain what
        you hope the feature will solve (the actual underlying problem) along
        with specific examples; but do not demand a specific solution, as there
        might be other/better solutions. A user story might be an effective way
        of conveying this.

    - Please also provide any other information that may be useful, such as:

      - The web browser, computer systems or hardware you've seen the bug on
      - Links or diffs to one or more pages where you encountered the bug
      - Whether the problem appears every time, only occasionally, only on
        certain pages, or only under specific circumstances

    - To attack a log file or a screenshot, click the **Upload File** button (a
      cloud with an arrow) in the toolbar of the Description field.
    - Select the **projects** that are relevant for this bug:

      - The default projects are *tometo-triage* (this is important to leave)
        and *tometo* (you should leave this unless the bug has nothing to do
        with the core Tometo software).
      - If any other teams might be interested in this, or if the bug appeared
        in a different component, please attach them to the task. Otherwise, a
        team member will do it for you once you've created the task.

    - **Subscribers**: If you know any people who will be interested in getting
      notified of this task, you can add them here. Otherwise, ignore this
      field.

Check if your report is complete, then press the Create Task button.

The priority for the task will be set by the Triage team, and the people who
will be planning to work on this task.

That's all! Thank you so much for helping to improve Tometo!
