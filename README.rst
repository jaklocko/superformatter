The world's simplest Python template engine
===========================================

Implements a very basic template engine based on the `standard Python formatting feature <https://docs.python.org/2/library/string.html#formatstrings>`_.

Disclaimer
----------

The objective is mostly to have fun with Python and demonstrate what the standard `Formatter` class is able to do.

If you have any funny idea to improve the current implementation (remember: we want to keep it short), pull requests are welcome :).

Usage
-----

.. code-block::

    >>> sf = SuperFormatter()

It does everything the regular `format()` method does (and that's already a lot, see `https://pyformat.info/ <https://pyformat.info/>`_)

But it can also:

- call methods:

.. code-block::

    >>> sf.format('My name is {name.upper:call}', name="eric")
    'My name is ERIC'

- make loops:

.. code-block::

    >>> sf = SuperFormatter()
    >>> sf.format('''Table of contents:
    ... {chapters:repeat:Chapter {{item}}
    ... }''', chapters=["I", "II", "III", "IV"])
    '''Table of contents:
    Chapter I
    Chapter II
    Chapter III
    Chapter IV
    '''

- manage conditions:

.. code-block::

    >>> sf = SuperFormatter()
    >>> sf.format('Action: Back / Logout {manager:if:/ Delete {id}}', manager=True, id=34)
    'Action: Back / Logout / Delete 34'

