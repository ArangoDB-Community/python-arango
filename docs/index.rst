.. python-arango documentation master file, created by
   sphinx-quickstart on Sun Jul 24 17:17:48 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. image:: /static/logo.png

|

Welcome to the documentation for **python-arango**, a Python driver for
`ArangoDB <https://www.arangodb.com/>`__.


Features
========

- Clean, Pythonic interface
- Lightweight
- High ArangoDB REST API coverage

Compatibility
=============

- Python versions 2.7.x, 3.4.x, 3.5.x and 3.6.x are supported
- Latest version of python-arango (3.x) supports ArangoDB 3.x only
- Older versions of python-arango support ArangoDB 1.x ~ 2.x only

Installation
============

To install a stable version from PyPi_:

.. code-block:: bash

    ~$ pip install python-arango


To install the latest version directly from GitHub_:

.. code-block:: bash

    ~$ pip install -e git+git@github.com:joowani/python-arango.git@master#egg=python-arango


You may need to use ``sudo`` depending on your environment.

.. _PyPi: https://pypi.python.org/pypi/python-arango
.. _GitHub: https://github.com/joowani/python-arango

A Note on Thread Safety and Eventlet
========

This driver should be compatible with eventlet for the most part. By default, python-arango makes API calls using the requests library, which eventlet seems to be able to monkey patch.

Assuming that, all python-arango APIs except Batch Execution and Asynchronous Execution should be thread-safe.


Contents
========

.. toctree::
    :maxdepth: 1

    client
    database
    collection
    document
    indexes
    graph
    aql
    cursor
    async
    batch
    transaction
    admin
    user
    task
    wal
    errors
    logging
    classes
