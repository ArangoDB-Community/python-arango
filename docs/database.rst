.. _database-page:

Databases
---------

A single ArangoDB instance can house multiple databases, which in turn contain
their own set of worker processes,  :ref:`collections <collection-page>`, and
:ref:`graphs <graph-page>`. There is always a default database named ``_system``.
This default database cannot be dropped, can only be accessed with root
privileges, and provides operations for managing other user-defined databases.

Here is an example showing how databases can be managed with multiple users:

.. code-block:: python

    from arango import ArangoClient

    # Initialize the ArangoDB client as root
    client = ArangoClient(username='root', password='')

    # Create a database, again as root (the user is inherited from client
    # initialization if the username and password are not specified)
    db = client.create_database('my_database', username=None, password=None)

    # Retrieve the properties of the new database
    db.properties()

    # Create another database, this time with a predefined set of users
    db = client.create_database(
        name='another_database',
        # Users jane, john and jake will have access to the new database
        users=[
            {'username': 'jane', 'password': 'foo', 'active': True},
            {'username': 'john', 'password': 'bar', 'active': True},
            {'username': 'jake', 'password': 'baz', 'active': True},
        ],
        # API calls through this database object uses jake's credentials
        username='jake',
        password='baz'
    )

    # To switch to a different user, simply create a new database object with
    # the credentials of the desired user (which in this case would be jane's)
    db = client.database('another_database', username='jane', password='foo')

    # Delete an existing database as root
    client.delete_database('another_database')

Refer to :ref:`ArangoClient` and :ref:`Database` classes for more details
on database management, and the :ref:`user-page` page for more details on user
management and database access control.
