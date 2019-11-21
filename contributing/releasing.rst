Releasing Tometo
================

Releasing software can be an arduous task, which is why we're trying really
hard to make it as simple as possible for Tometo. Here's a bunch of information
and guides you might appreciate if you're a person who is in charge of releases.

Basics
------

Every Tometo release includes a bunch of things:

- An archive with the application files in it, namely:

  - A compiled version of the backend (this is a single binary)
  - A folder with the compiled frontend files in it
  - A configuration file (``config.toml``)

- A file signature generated with `Minisign <https://jedisct1.github.io/minisign/>`_

Signatures
^^^^^^^^^^

It's a classic release practice to sign your release artifacts so that users
can make sure that they have the correct artifact, and not a fake one
provided by evil people. Some people use GPG, we use Minisign, which is much,
much simpler. The signature that you generate *always* leads back to you
by way of your public key. Current public keys are listed here:

- `Marisa <https://github.com/fmoko>`_:
  ``RWSOPopFko/YfOOJLGSLQ8wYjGsirt3cuPyTlMptym6K1e3ulPux1Lvx``

Architectures
^^^^^^^^^^^^^

Every release archive is also built for a certain **architecture**. The frontend
is independent of the user's operating system, but because the backend uses
Rust, we're bound to architectures, like ``linux-gnu``, ``darwin`` (MacOS),
``windows`` or ``freebsd``. You can check which architecture you're running by
executing the following:

.. code-block:: shell

   rustup show active-toolchain

The latter part will be your architecture. We simplify these into some shorter
names:

- ``linux-gnu`` for most Linux distros
- ``darwin`` for MacOS
- ``windows`` for Windows
- ``freebsd`` for FreeBSD
- ``netbsd`` for NetBSD

These are *generally* x86 (64 Bit), but you can prefix them if it's different,
like 32 Bit or ARM.

Creating a Release
------------------

You need to have a local setup to create a release. More info in the
`Installing Document <../installation>`_.

If you know the version number and architecture name you're releasing for, run:

.. code-block:: shell

   script/release VERSION ARCHITECTURE

For example:

.. code-block:: shell

   script/release 0.5.52 linux-gnu

This script builds, archives, signs and creates a folder called
``releases/VERSION``, where the resulting artifacts and signatures are moved to.
You can now create a Git tag and corresponding release on GitHub, write a blog
post, or whatever the post-release process is!
