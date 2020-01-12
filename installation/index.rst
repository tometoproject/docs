Installation
============

Tometo is functionally split into two parts — the frontend, which is a Vue.js
app that's kept in the ``./ui``, and the backend called Aph, which is an Elixir app that's
kept in the ``./aph`` folder.

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

   git clone ssh://vcs@marisa.cloud:2222/source/tometo.git
   # or with HTTPS
   git clone https://marisa.cloud/source/tometo.git
   cd tometo/
   script/localsetup

This will set up everything for you, the only thing you need to do yourself is fill
in the config file for Aph and run the database setup. The config file can be
found in `aph/config/config.exs`. This is where you fill in your database
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

   git clone https://marisa.cloud/source/tometo.git

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

As a final step, you should copy the example config files:

.. code-block:: shell

   cp .env.example .env

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
- ``script/run``: Runs both the frontend and the backend
- ``script/run_b``: Runs only the backend
- ``script/run_f``: Runs only the frontend
- ``script/watch``: Runs and watches for changes for the frontend and backend. This is what you want most of the time.
