====
utmp
====

Pure-Python library to decode/read utmp and wtmp files.
Please note that there is an alternative library which uses the underlying C API: pyutmp_

This package requires Python 2.7.

Python 3.x users: use utmp_. This is a fork of utmp_ which adds nothing but a dependency on enum_, since it's not part of the Python 2.x stdlib.

What is utmp/wtmp?
==================
**utmp**, **wtmp**, **btmp** and variants such as **utmpx**, **wtmpx** and **btmpx** are files on Unix-like systems that keep track of all logins and logouts to the system.

The utmp file keeps track of the current login state of each user. The wtmp file records all logins and logouts history. The btmp file records failed login attempts.

On Linux the ``wtmp`` and ``btmp`` files are usually located in the ``/var/log/`` directory.

Usage
=====

The ``utmp.read`` function decodes a binary utmp/wtmp stream and yields record objects:

.. code-block:: python

    with open('/var/log/wtmp', 'rb') as fd:
        buf = fd.read()
        for entry in utmp.read(buf):
            print(entry.time, entry.type, entry)

.. _pyutmp: https://pypi.python.org/pypi/pyutmp
