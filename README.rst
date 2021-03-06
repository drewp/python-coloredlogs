coloredlogs: Colored stream handler for Python's logging module
===============================================================

The ``coloredlogs.ColoredStreamHandler`` class is a simple logging handler that
inherits from `logging.StreamHandler`_ and uses `ANSI escape sequences`_ to
render your logging messages in color. It uses only standard colors so it
should work on any UNIX terminal. Currently this module does not support
non-UNIX terminals (e.g. the Windows console). Here is a screenshot of the demo
that is printed when ``coloredlogs.py`` is executed directly:

.. image:: https://peterodding.com/code/python/coloredlogs/screenshots/terminal.png

Note that the screenshot above includes the custom logging level ``VERBOSE``
defined by my verboselogs_ module: if you install both ``coloredlogs`` and
``verboselogs`` it will Just Work (``verboselogs`` is of course not
required to use ``coloredlogs``).

The logging handler does not use ANSI escape sequences when output redirection
applies (for example when the standard error stream is being redirected to a
file or another program) so if you like the format (see below), you can use it
for your log files as well.

Format of log messages
----------------------

As can be seen in the screenshot above, the logging handler includes four
fields in every logged message by default:

1. A timestamp indicating when the event was logged. This field is visible by
   default. To hide it you can pass the keyword argument
   ``show_timestamps=False`` when you create the handler.
2. The hostname of the system on which the event was logged. This field is
   visible by default. To hide it you can pass the keyword argument
   ``show_hostname=False`` when you create the handler.
3. The name of the logger that logged the event. This field is hidden by
   default. To show it you can pass the keyword argument ``show_name=True``
   when you create the handler.
4. The human friendly name of the log level / severity.
5. The message that was logged.

Usage
-----

Here's an example of how you would use the logging handler::

   # Configure your logger.
   import logging, coloredlogs
   logger = logging.getLogger('your-module')
   logger.addHandler(coloredlogs.ColoredStreamHandler())

   # Some examples.
   logger.setLevel(logging.DEBUG)
   logger.debug("this is a debugging message")
   logger.info("this is an informational message")
   logger.warn("this is a warning message")
   logger.error("this is an error message")
   logger.fatal("this is a fatal message")
   logger.critical("this is a critical message")

For people who like Vim
-----------------------

Although the logging handler was originally meant for interactive use, it can
also be used to generate log files. In this case the ANSI escape sequences are
not used so the log file will contain plain text and no colors. If you use Vim_
and ``coloredlogs`` and would like to view your log files in color, you can try
the two Vim scripts included in the ``coloredlogs`` source distributions and
git repository:

.. image:: https://peterodding.com/code/python/coloredlogs/screenshots/vim.png

Contact
-------

The latest version of ``coloredlogs`` is available on PyPi_ and GitHub_. For
bug reports please create an issue on GitHub_. If you have questions,
suggestions, etc. feel free to send me an e-mail at `peter@peterodding.com`_.

License
-------

This software is licensed under the `MIT license`_.

© 2013 Peter Odding.

.. External references:
.. _ANSI escape sequences: http://en.wikipedia.org/wiki/ANSI_escape_code#Colors
.. _GitHub: https://github.com/xolox/python-coloredlogs
.. _logging.StreamHandler: http://docs.python.org/2/library/logging.handlers.html#streamhandler
.. _MIT license: http://en.wikipedia.org/wiki/MIT_License
.. _peter@peterodding.com: peter@peterodding.com
.. _PyPi: https://pypi.python.org/pypi/coloredlogs
.. _verboselogs: https://pypi.python.org/pypi/verboselogs
.. _Vim: http://www.vim.org/
