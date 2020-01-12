Releasing Tometo
================

Releasing software can be an arduous task, which is why we're trying really
hard to make it as simple as possible for Tometo. Here's a bunch of information
and guides you might appreciate if you're a person who is in charge of releases.

Basics
------

Right now, a Tometo release is basically just:

- A tag in the source repository (something like ``0.4.2``)
- A corresponding post on the `Tometo Release Blog <https://marisa.cloud/phame/blog/view/1/>`_
- For larger releases (such as `0.x` or `x.0`), a post on the main Tometo
  website at https://tometo.org

Preparing a Release
^^^^^^^^^^^^^^^^^^^

If you have commit access, you can make one commit that includes the version
number changes. That's basically all that's required code-wise. Change the
version numbers in these places:

- ``package.json``
- ``aph/mix.exs``

Call the commit the version number, and create a tag that refers to that commit:

.. code-block:: shell

   git tag x.y.z

Then push them:

.. code-block:: shell

   git push origin master
   git push origin master --tags

Writing a release post
^^^^^^^^^^^^^^^^^^^^^^

Every release, even minor ones, should have a post on the
`Release Blog <https://marisa.cloud/phame/blog/view/1/>`_. Assuming you have
correct permissions to create blog posts there, the minimum a blog post should
contain is a changelog that lists all features, bug fixes and enhancements,
ESPECIALLY the ones that were made by people outside of the usual committers.
If there is very menial stuff authored by usual committers, such as changing
some links in documentation or something, feel free to leave those out, but
don't make assumptions.

That being said, it's your blog post! You can put as many fun little things into
it as you'd like. Once you're done, let the team know and we'll push the release
out onto our social media channels and the Discord. Congrats!!
