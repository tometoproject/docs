Installation
============

Tometo is functionally split into two parts — the frontend, which is a Vue.js
app that's kept in this repository, and the backend, which is a Rust app that's
kept in the ``./otemot`` folder.

Prerequisites
-------------

In order to get the system running on your computer, you'll need some
prerequisites:

- Git
- A PostgreSQL server, and its development headers (sometimes called ``libpq-dev`` or ``postgresql-devel``)
- Node.js, the latest LTS or Stable version should work
- Rust (the correct nightly version should automatically install)
- Python 3 and ``pip``
  (plus development headers, sometimes separate as ``python3-devel``)
- eSpeak (and its development headers, sometimes separate as ``espeak-devel``)
- FFmpeg
- The Google Cloud SDK

Automatic Installation
----------------------

If you have all of the prerequisites installed, you can try cloning the repository and running our automatic
setup script:

.. code-block:: shell

   git clone ssh://git@marie.marisa.cloud:222/t/tometo.git
   # or with HTTPS
   git clone https://marie.marisa.cloud/t/tometo.git
   cd tometo/
   script/localsetup

This will set up everything for you, the only thing you need to do yourself is fill
in the config file.

Manual Installation
-------------------

After you've installed Rust, you should also install ``diesel-cli``, which is what
powers our database management:

.. code-block:: shell

   cargo install diesel_cli --no-default-features --features postgres

If you want to locally develop, I recommend that you also install ``cargo-watch``, which
makes it possible to automatically rerun Cargo commands when you edit a file. You can install it
with a simple ``cargo install cargo-watch``.

You'll also want to install ``aeneas``, which parses text for us (this needs
ffmpeg and espeak installed and available):

.. code-block:: shell
 
   pip3 install --user numpy
   pip3 install --user aeneas

Then, you can clone the repository.

.. code-block:: shell

   git clone https://marie.marisa.cloud/t/tometo

Once you're in the directoy, you'll want to install the dependencies:

.. code-block:: shell

   npm install

Next, to create the necessary database tables and configuration, do this:

.. code-block:: shell

   cd otemot/
   DATABASE_URL=<your database url> diesel setup

As a final step, you should copy the example config file:

.. code-block:: shell

   cp config.example.toml config.toml

Configuration
-------------

Configuration is done through a central config file called ``config.toml``, which
provides configuration for both components.

Don't worry about your config file getting put into version control, it's ignored
by default.

The config file should have documentation for every option.

If you want to override config variables temporarily, you can set environment variables
to match them. For example, to set the ``otemot.secrets.cookie`` key, you would set the
``OTEMOT_SECRETS_COOKIE`` variable.

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
