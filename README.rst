.. image:: https://travis-ci.com/agronholm/typeguard.svg?branch=master
  :target: https://travis-ci.com/agronholm/typeguard
  :alt: Build Status
.. image:: https://coveralls.io/repos/agronholm/typeguard/badge.svg?branch=master&service=github
  :target: https://coveralls.io/github/agronholm/typeguard?branch=master
  :alt: Code Coverage
.. image:: https://readthedocs.org/projects/typeguard/badge/?version=latest
  :target: https://typeguard.readthedocs.io/en/latest/?badge=latest

This library provides run-time type checking for functions defined with `PEP 484`_ argument
(and return) type annotations.

Three principal ways to do type checking are provided, each with its pros and cons:

#. the ``check_argument_types()`` and ``check_return_type()`` functions:

   * debugger friendly (except when running with the pydev debugger with the C extension installed)
   * does not work reliably with dynamically defined type hints (e.g. in nested functions)
#. the ``@typechecked`` decorator:

   * automatically type checks yields and sends of returned generators (regular and async)
   * adds an extra frame to the call stack for every call to a decorated function
#. the stack profiler hook (``with TypeChecker('packagename'):``):

   * emits warnings instead of raising ``TypeError``
   * requires very few modifications to the code
   * multiple TypeCheckers can be stacked/nested
   * does not work reliably with dynamically defined type hints (e.g. in nested functions)
   * may cause problems with badly behaving debuggers or profilers
   * cannot distinguish between an exception being raised and a ``None`` being returned

See the documentation_ for further instructions.

.. _PEP 484: https://www.python.org/dev/peps/pep-0484/
.. _documentation: https://typeguard.readthedocs.io/en/latest/
