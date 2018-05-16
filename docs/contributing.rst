Contributing
------------

Requirements
============

Before submitting a pull request on GitHub_, please make sure you meet the
following **requirements**:

* The pull request points to dev_ (development) branch.
* All changes are squashed into a single commit (I like to use ``git rebase -i``
  to do this).
* The commit message is in present tense (good: "Add feature", bad:
  "Added feature").
* Correct and consistent style: Sphinx_-compatible docstrings, correct snake
  and camel casing, and PEP8_ compliance (see below).
* No classes/methods/functions with missing docstrings or commented-out lines.
  You can take a look at the existing code in python-arango for examples.
* The test coverage_ remains at %100. Sometimes you may find yourself having to
  write superfluous unit tests to keep this number up. If a piece of code is
  trivial and has no need for unittests, use this_ to exclude it from coverage.
* No build failures on TravisCI_. The builds automatically trigger on PR
  submissions.
* Does not break backward-compatibility (unless there is a really good reason).
* Compatibility with all supported Python versions: 2.7, 3.4, 3.5 and 3.6.

.. note::
    The dev branch is occasionally rebased_, and its commit history may be
    overwritten in the process. So before you begin feature work, git fetch or
    pull to ensure that your local branch has not diverged. If you see git
    conflicts and want to start from scratch, run this command:

    .. code-block:: bash

        ~$ git checkout dev
        ~$ git fetch origin
        ~$ git reset --hard origin/dev  # THIS WILL WIPE ALL LOCAL CHANGES

Style
=====

To ensure PEP8_ compliance, run flake8_:

.. code-block:: bash

    ~$ pip install flake8
    ~$ git clone https://github.com/joowani/python-arango.git
    ~$ cd python-arango
    ~$ flake8

You should try to resolve all issues reported. If there is a good reason to
ignore errors from a specific piece of code, visit here_ to see how to exclude
the lines.

Testing
=======

To test your changes, run the integration test suite that comes with
**python-arango** on your local machine. The test suite uses pytest_, and is
designed to run against an actual database instance. Please use the latest
version of ArangoDB with the following configuration:

* **Host**: "localhost"
* **Port**: 8529
* **Username**: "root"
* **Password**: "passwd"

To run the test suite:

.. code-block:: bash

    ~$ pip install pytest
    ~$ git clone https://github.com/joowani/python-arango.git
    ~$ cd python-arango
    ~$ py.test --complete --verbose

To run the test suite with coverage report:

.. code-block:: bash

    ~$ pip install coverage pytest pytest-cov
    ~$ git clone https://github.com/joowani/python-arango.git
    ~$ cd python-arango
    ~$ py.test --complete --verbose --cov=arango --cov-report=html

    # Open the generated file htmlcov/index.html in a browser

The test suite only operates on temporary databases created during the run,
and is meant to be run in disposable environments (e.g. Travis).

Documentation
=============

The documentation (including the README) is written in reStructuredText_ and
uses Sphinx_. To build the HTML version of the documentation on your local
machine:

.. code-block:: bash

    ~$ pip install sphinx sphinx_rtd_theme
    ~$ git clone https://github.com/joowani/python-arango.git
    ~$ cd python-arango/docs
    ~$ sphinx-build . build
    ~$ # Open the generated file build/index.html in a browser


As always, thanks for your contribution!

.. _rebased: https://git-scm.com/book/en/v2/Git-Branching-Rebasing
.. _dev: https://github.com/joowani/python-arango/tree/dev
.. _GitHub: https://github.com/joowani/python-arango
.. _PEP8: https://www.python.org/dev/peps/pep-0008/
.. _coverage: https://coveralls.io/github/joowani/python-arango
.. _this: http://coverage.readthedocs.io/en/latest/excluding.html
.. _TravisCI: https://travis-ci.org/joowani/python-arango
.. _Sphinx: https://github.com/sphinx-doc/sphinx
.. _flake8: http://flake8.pycqa.org
.. _here: http://flake8.pycqa.org/en/latest/user/violations.html#in-line-ignoring-errors
.. _pytest: https://github.com/pytest-dev/pytest
.. _reStructuredText: https://en.wikipedia.org/wiki/ReStructuredText
