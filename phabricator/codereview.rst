Code Review
===========

*Differential* is the code review tool in Phabricator. It's used to land most
significant code-changes into Tometo codebases. Along with Differential,
*Arcanist* is used to push your local changes to Differential, opening a new
*revision* (basically a pull request) as a result.

Who can create revisions?
-------------------------

Anyone can create revisions. You may not have push access to the project you're
contributing a revision to, but Arcanist can also operate off of local commits
(and in fact, this is what you should do if you're a first-time contributor!).
Tometo Committers can push their work to a feature branch, creating revisions
off them works the same way.

Install Arcanist
----------------

While you don't *need* to install Arcanist, the fact is that it makes repeat
contributions much easier once you wrap your head around it. Arcanist has a
great `quick-start guide
<https://secure.phabricator.com/book/phabricator/article/arcanist_quick_start/>`_
that should help you get it set up on your PC. You can also check your
distribution's package manager and install it from there (saves you the trouble
of installing PHP by yourself).

Don't forget to run ``arc install-certificate``!

The Code Review Workflow
------------------------

Usually, our workflow is somewhat like this:

For new contributors
^^^^^^^^^^^^^^^^^^^^

- You locally set up Tometo
- You make your changes, and commit the result (either on ``master`` or on your
  own branch, it doesn't matter)
- You run ``arc diff``, which creates a revision with your local changes
- Someone reviews your revision, if you need to make changes you run ``arc
  diff`` again after making them to update the revision
- Once it's accepted, the reviewer commandeers (takes control of) the revision
  and lands it into the source repository
- You're done!

For committers
^^^^^^^^^^^^^^

- You make changes and push them to a feature branch
- You run ``arc diff`` to create a revision
- After the revision has been reviewed and accepted, you run ``arc land`` locally
- You're done!

For reviewers
^^^^^^^^^^^^^

- Someone creates a revision
- To locally test it, run ``arc patch <revision number>`` to make Arcanist
  locally download the revision diff
- You review accordingly
- After accepting the revision, optionally land it if the author doesn't have
  push access

Troubleshooting
---------------

Arcanist can be a delicate beast, and you should feel free to ask in the
#development channel on Discord if you're unsure about something or if something
doesn't work. In the worst case, just recreate your revision.
