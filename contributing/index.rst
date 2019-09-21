Contributing to Tometo
======================

Thanks for your interest in contributing to Tometo! There is more than one way
to contribute to the project, and we appreciate all of them.

If you have any questions, feel free to ask them in the `Tometo Discord Server <https://discord.gg/xqTEcaw>`_.
As a reminder, all contributors, in whichever way, are required to follow the `Code of Conduct <https://docs.tometo.org/conduct>`_.

Feature Requests
----------------

If you have ideas or even concrete suggestions for a feature or an enhancement, it's best
to discuss it first on Discord before diving into the specifics. If you feel up to implement it,
open a `pull request <#pull-requests>`_!

Bug Reports
-----------

While we wish everything in here worked perfectly, bugs are natural to occur.
This is why we recommend that, even when you're not sure it's a bug, to report it anyways.

Please search for already existing or similar reports first before you open an issue.


It also makes our lives much easier if the issue title is as descriptive as possible.
This can be the specific error message given, the steps you used to reproduce it, or
something else that's unique to the bug you're experiencing.

Filing a bug report happens on our bug tracker, and you can find a link to create a new issue `here <https://bugs.marisa.cloud/projects/tometo/issues/new>`_.

If you're running Tometo locally, please include as much information as possible about your setup,
what Rust version you use, what Node version, your operating system, stack traces, et cetera.
To get nice backtraces from Rust (e.g. Otemot), there's a special environment variable you can set:

.. code-block:: shell

   RUST_BACKTRACE=1 cargo run

Pull Reqests
------------

Pull Requests are how we usually land code for Tometo. We use a simple model,
where every contributor pushes changes either to their fork or to a branch on the main repository,
and then brings those changes into the master branch.

Always make sure that your code conforms to the style guidelines by running the following:

.. code-block:: shell

   script/lint

Please don't annoy anyone to review your pull request, people have limited time, and sometimes other things have priorities.

Issue Triage
------------

Issues on the bug tracker can be for different *trackers*, and have other configuration options. Here's some notes on them:

- Don't set a priority unless you know what you're doing
- The `Epic` tracker refers to issues that track a multitude of other issues,
  e.g. for a large feature
