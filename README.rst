Annotator Store
===============

This is a backend store for `Annotator <http://annotatorjs.org>`__.

The functionality can roughly be separated in two parts:

1. An abstraction layer wrapping Elasticsearch, to easily manage annotation
   storage. It features authorization to filter search results according to
   their permission settings.
2. A Flask blueprint for a web server that exposes an HTTP API to the annotation
   storage. To use this functionality, build this package with the ``[flask]``
   option.

Getting going
-------------

For docker the simplest method is  `docker-compose up` which will give you annotator and elasticsearch

There are a number of required env variables as bellow
    - `SECRET_KEY` - The secret key that will be used for authentication
    - `ES_HOST` - The address to access your Elasticsearch server on
    - `AUTH` - Whether to enable authentication, possible values are `True` or `False`


You should see something like::

    * Running on http://127.0.0.1:5000/
    * Restarting with reloader...

If you wish to customize the configuration of the Annotator Store, make
your changes to ``annotator.cfg`` or dive into ``run.py``.

Additionally, the ``HOST`` and ``PORT`` environment variables override
the default socket binding of address ``127.0.0.1`` and port ``5000``.

Store API
---------

The Store API is designed to be compatible with the
`Annotator <http://okfnlabs.org/annotator>`__. The annotation store, a
JSON-speaking REST API, will be mounted at ``/api`` by default. See the
`Annotator
documentation <http://docs.annotatorjs.org/en/v1.2.x/storage.html>`__ for
details.

Running tests
-------------

We use ``nosetests`` to run tests. You can just
``pip install -e .[testing]``, ensure ElasticSearch is running, and
then::

    $ nosetests
    ......................................................................................
    ----------------------------------------------------------------------
    Ran 86 tests in 19.171s

    OK

Alternatively (and preferably), you should install
`Tox <http://tox.testrun.org/>`__, and then run ``tox``. This will run
the tests against multiple versions of Python (if you have them
installed).

Please `open an issue <http://github.com/openannotation/annotator-store/issues>`__
if you find that the tests don't all pass on your machine, making sure to include
the output of ``pip freeze``.
