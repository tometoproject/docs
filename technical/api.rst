API Details
===========

Tometo's API, called Aph, takes care of everything in the backend, such as
interfacing with the database, generating statuses, and so forth. We have a
couple of rules when working with Aph that we try to follow in order to make a
consistent effort at keeping the codebase clean and understandable.

API Interface
-------------

We follow the RESTful API standards. This means a couple of things:

- Use proper HTTP statuses (i.e. ``201`` on a successful ``POST``)
- Routes should be:
  - Plural unless referring to a singleton object (``/api/statuses``,
    ``/api/users``)
  - Usable by multiple methods (``GET /api/users``, ``POST /api/users``)
  - Used for specific cases only when it's unavoidable (``/api/users/:id/invitations``)
- When returning an error, put it in this format:

.. code-block:: json

   {
     "error": true,
     "id": "unique-error-id",
     "message": "Helpful error message"
   }

- Always return full resource objects, not only subsections of them. For
  example, when creating a user, don't only return the username, return the
  entire thing, even if it might seem superfluous.

General Elixir/Phoenix recommendations
--------------------------------------

Phoenix Views
^^^^^^^^^^^^^
Views can either use preloaded data, render different views, render many items, or not render
much at all. This can get confusing quickly, which is why we have some standard naming practices for
the ``render`` function in our views:

Say we've got an example entity called ``Book`` that has a 1-to-many relation with both ``Page`` and ``Word``. The ``book_view.ex`` could include the following:

- ``book.json`` for a MINIMAL version of the entity with no preloads, but all keys (including timestamps).
- ``book_with_page.json`` for ``book.json`` but with a ``Page`` preloaded.
- ``book_full.json`` for ``book.json`` with every foreign resource preloaded.

We don't use a ``data`` key in views, like the Phoenix generators would like you
to believe. Most things in our JSON returns are top-level.

Other Things
^^^^^^^^^^^^

``AphWeb.ErrorView`` contains the most common error codes. Some of them accept
custom messages, some don't — feel free to modify one to include a message, just
be sure to check where else the error is being used from first!

When you want to make sure that only logged in users can access a route, do
this:

.. code-block:: elixir

   use AphWeb.Authorize

   plug :user_check when action in [:your_action_name]

Always use brackets around method calls, it's cleaner and easier to understand.
Piping is usually not worth it when it's only a single pipe (unless you're
working with a ``conn`` struct).

Linting can be done via ``script/lint``, or, if you want to directly fix
potential formatting mishaps, ``script/fix``.
