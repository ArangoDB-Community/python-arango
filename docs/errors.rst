Error Handling
--------------

All python-arango exceptions inherit :class:`arango.exceptions.ArangoError`,
which lightly wraps around the HTTP error responses returned from ArangoDB.
The majority of the error messages in the exceptions raised by python-arango
come directly from the server.

Here is an example showing how a python-arango exception can be handled:

.. code-block:: python

    from arango import ArangoClient, ArangoError

    client = ArangoClient()
    db = client.db('my_database')
    students = db.collection('students')

    try:
        students.insert({'_key': 'John'})
        students.insert({'_key': 'John'})  # unique constraint violation
    except ArangoError as exc:
        print(repr(exc))
        print(exc.message)
        print(exc.error_code)
        print(exc.url)
        print(exc.http_method)
        print(exc.http_code)
        print(exc.http_headers)

Exceptions
==========

Below are all exceptions available in python-arango.

.. automodule:: arango.exceptions
    :members:
