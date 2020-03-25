Installation
############

Installation can be done either in a `Vagrant <https://vagrantup.com>`_ virtual
machine or locally, directly on your machine. The upside to Vagrant is that it
uses an automated provisioning script, which means no having to install
dependencies or even setting up the project. You run two commands, and then you
have a fully functioning setup of Tometo.

The downside is that it *is* a virtual machine -- it's not truly on your
computer, but running inside an emulated Ubuntu VM. Doing that can stress your
RAM and CPU, so if you don't have a computer with modern-day decent specs, you
might be better off directly installing Tometo. I would still recommend you to
give Vagrant a try though, and if it runs super sluggish, you can still switch
to locally running.

Via Vagrant
===========

First, you want to `download Vagrant
<https://www.vagrantup.com/downloads.html>`_. On most systems, Vagrant uses
`VirtualBox <https://www.virtualbox.org/>`_ in the background, so you'll want to
install that too, unless you already have another hypervisor installed (don't
worry if you don't know what that is - neither do I).

Next, download the source code. If you have `Git <https://git-scm.org>`_
installed, you can clone the repository like this:

.. code-block:: shell

   git clone https://git.tometo.org/source/tometo.git

If you don't want to install Git or have no idea what that is, our GitHub mirror
provides a ZIP download `here <https://github.com/tometoproject/tometo/archive/master.zip>`_.

Once you have it downloaded and extracted to somewhere you like, open a Terminal
(cmd.exe or PowerShell on Windows) in the folder you extracted the code to and
run this:

.. code-block:: shell

   vagrant up

This **will** take a while, so maybe make some tea in the meantime. Once it's
done, you can run this:

.. code-block:: shell

   vagrant ssh

You're now in a full Ubuntu Linux virtual machine that just so happens to have
Tometo installed into it! The cool thing about this is that all of the changes
you make in the directory you downloaded Tometo into will automatically appear
on that virtual machine. You can now use the Tometo command-line scripts to
start the server, like this:

.. code-block:: shell

   script/watch

See also the "Running" section at the bottom of this page.

Locally
=======

Prerequisites
-------------

In order to get the system running on your computer, you'll need some
prerequisites:

- Git
- A PostgreSQL server, and its development headers (sometimes called ``libpq-dev`` or ``postgresql-devel``)
- Elixir (and Erlang, but usually those two are installed side-by-side)
- Node.js, the latest LTS or Stable version should work
- Python 3 and ``pip``
  (plus development headers, sometimes separate as ``python3-devel``)
- eSpeak (and its development headers, sometimes separate as ``espeak-devel``)
- FFmpeg

Optionally, there's some more advanced features you can enable, which need some of these dependencies:

- A Google Cloud service account API key that has access to the Text-To-Speech API

.. note::
   These still need to be documented properly.

Automatic Installation
----------------------

Before doing any installation, make sure you have Elixir's package manager
scripts downloaded locally! Run this command to do so:

.. code-block:: shell

   mix local.hex

If you have all of the prerequisites installed, you can try cloning the repository and running our automatic
setup script:

.. code-block:: shell

   git clone ssh://vcs@git.tometo.org:2222/source/tometo.git
   # or with HTTPS
   git clone https://git.tometo.org/source/tometo.git
   cd tometo/
   script/localsetup

This will set up everything for you, the only thing you need to do yourself is fill
in the config file for Aph and run the database setup. The config file can be
found in ``aph/config/config.exs``. This is where you fill in your database
credentials. After you're done doing that, you can then run the database setup:

.. code-block:: shell

   cd aph
   mix ecto.create

Manual Installation
-------------------

You'll want to install ``aeneas``, which parses text for us (this needs
ffmpeg and espeak installed and available):

.. code-block:: shell
 
   pip3 install --user numpy
   pip3 install --user aeneas

Check that it's installed correctly:

.. code-block:: shell

   python3 -m aeneas.diagnostics

Then, you can clone the repository.

.. code-block:: shell

   git clone https://git.tometo.org/source/tometo.git

Once you're in the directoy, you'll want to install the dependencies for the frontend:

.. code-block:: shell

   npm install

And the backend:

.. code-block:: shell

   cd aph
   mix deps.get

Now you can go ahead and copy the backend configuration file:

.. code-block:: shell

   cp aph/config/config.example.exs aph/config/config.exs

Next, to create the necessary database tables and configuration, fill in your
database configuration in ``aph/config/config.exs`` and run this:

.. code-block:: shell

   cd aph
   mix ecto.create

Configuration
-------------

Configuration is (unfortunately) different for frontend and backend. The
frontend loads environment variables either through you directly setting them or
through ``.env``, while Aph loads its own config contained in ``aph/config/``.

.. note::
   TODO: Add production configuration info here

Running
-------

We have multiple scripts to provide some common uses if you're planning on working on Tometo.
These include:

- ``script/build``: Runs a production build
- ``script/lint``: Makes sure your code looks nice and is ready to commit
- ``script/fix``: Automatically corrects your code based on our linting rules
  (this modifies your actual code files)
- ``script/run``: Runs both the frontend and the backend
- ``script/run_b``: Runs only the backend
- ``script/run_f``: Runs only the frontend
- ``script/watch``: Runs and watches for changes for the frontend and backend. This is what you want most of the time.
