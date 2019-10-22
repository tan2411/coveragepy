.. Licensed under the Apache License: http://www.apache.org/licenses/LICENSE-2.0
.. For details: https://bitbucket.org/ned/coveragepy/src/default/NOTICE.txt

===========
Coverage.py
===========

.. :history: 20090524T134300, brand new docs.
.. :history: 20090613T164000, final touches for 3.0
.. :history: 20090618T195900, minor tweaks
.. :history: 20090707T205200, changes for 3.0.1
.. :history: 20090913T084400, new command line syntax
.. :history: 20091004T211900, version 3.1
.. :history: 20091127T155100, version 3.2
.. :history: 20091205T161429, version 3.2 for real.
.. :history: 20100224T204700, version 3.3
.. :history: 20100306T181500, version 3.3.1
.. :history: 20100725T211700, updated for 3.4.
.. :history: 20100820T151500, updated for 3.4b1.
.. :history: 20100906T134700, updated for 3.4b2.
.. :history: 20100919T163500, updated for 3.4 release.
.. :history: 20110213T081200, claim true 3.2 compatibility.
.. :history: 20110604T114800, update for 3.5b1
.. :history: 20110629T082300, update for 3.5
.. :history: 20110827T221800, update for 3.5.1b1
.. :history: 20110923T081800, update for 3.5.1
.. :history: 20120429T162100, updated for 3.5.2b1
.. :history: 20120503T233800, updated for 3.5.2
.. :history: 20120929T093500, updated for 3.5.3
.. :history: 20121117T094900, Change from easy_install to pip.
.. :history: 20121128T203700, Updated for 3.6b1.
.. :history: 20121223T180600, Updated for 3.6b2.
.. :history: 20121229T112300, Updated for 3.6b3.
.. :history: 20130105T174000, Updated for 3.6
.. :history: 20131005T210000, Updated for 3.7
.. :history: 20131212T213300, Updated for 3.7.1
.. :history: 20140924T073000, Updated for 4.0a1
.. :history: 20150124T023900, Updated for 4.0a4
.. :history: 20150216T201000, Updated for 4.0a5
.. :history: 20150802T160200, Updated for 4.0b1
.. :history: 20150822T092900, Updated for 4.0b2
.. :history: 20150918T072700, Updated for 4.0
.. :history: 20151013T103200, Updated for 4.0.1
.. :history: 20151104T050900, updated for 4.0.2
.. :history: 20151124T065900, updated for 4.0.3
.. :history: 20160110T125900, updated for 4.1b1
.. :history: 20160123T171300, updated for 4.1b2
.. :history: 20160510T125300, updated for 4.1b3
.. :history: 20160521T074500, updated for 4.1
.. :history: 20160726T161300, updated for 4.2
.. :history: 20161226T160400, updated for 4.3
.. :history: 20170116T180100, updated for 4.3.2
.. :history: 20180203T130300, updated for 4.5
.. :history: 20180210T125300, updated for 4.5.1


Coverage.py is a tool for measuring code coverage of Python programs. It
monitors your program, nothing which parts of the code have been executed, then
analyzes the source to identify code that could have been executed but was not.

Coverage measurement is typically used to gauge the effectiveness of tests. It
can show which parts of your code are being exercised by tests, and which are
not.

.. ifconfig:: not prerelease

    The latest version is coverage.py 4.5.4, released July 29, 2019.  It
    is supported on:

    * CPython 2.6, 2.7 and 3.3 through beta 3.8.

    * PyPy2 6.0 and PyPy3 6.0.

    * Jython 2.7.1, though only for running code, not reporting.

    * IronPython 2.7.7, though only for running code, not reporting.

.. ifconfig:: prerelease

    The latest version is coverage.py 4.4b1, released April 4th 2017.  It is
    supported on:

    * Python versions 2.6, 2.7, 3.3, 3.4, 3.5, and 3.6.

    * PyPy2 5.6 and PyPy3 5.5.

    * Jython 2.7.1, though only for running code, not reporting.

    * IronPython 2.7.7, though only for running code, not reporting.

    **This is a pre-release build.  The usual warnings about possible bugs
    apply.** The latest stable version is coverage.py 4.3.4, `described here`_.

.. _described here: https://nedbatchelder.com/code/coverage


For Enterprise
--------------

.. image:: media/Tidelift_Logos_RGB_Tidelift_Shorthand_On-White.png
   :width: 75
   :alt: Tidelift
   :align: left
   :class: tideliftlogo
   :target: https://tidelift.com/subscription/pkg/pypi-coverage?utm_source=pypi-coverage&utm_medium=referral&utm_campaign=readme

.. |br| raw:: html

  <br/>

`Available as part of the Tidelift Subscription. <Tidelift Subscription_>`_ |br|
Coverage and thousands of other packages are working with
Tidelift to deliver one enterprise subscription that covers all of the open
source you use.  If you want the flexibility of open source and the confidence
of commercial-grade software, this is for you. `Learn more. <Tidelift
Subscription_>`_

.. _Tidelift Subscription: https://tidelift.com/subscription/pkg/pypi-coverage?utm_source=pypi-coverage&utm_medium=referral&utm_campaign=docs


Quick start
-----------

Getting started is easy:

#.  Install coverage.py from the `coverage.py page on the Python Package Index`_,
    or by using "pip install coverage".  For a few more details, see
    :ref:`install`.

#.  Use ``coverage run`` to run your program and gather data:

    .. code-block:: console

        # if you usually do:
        #
        #   $ python my_program.py arg1 arg2
        #
        # then instead do:

        $ coverage run my_program.py arg1 arg2
        blah blah ..your program's output.. blah blah

#.  Use ``coverage report`` to report on the results:

    .. code-block:: console

        $ coverage report -m
        Name                      Stmts   Miss  Cover   Missing
        -------------------------------------------------------
        my_program.py                20      4    80%   33-35, 39
        my_other_module.py           56      6    89%   17-23
        -------------------------------------------------------
        TOTAL                        76     10    87%

#.  For a nicer presentation, use ``coverage html`` to get annotated HTML
    listings detailing missed lines:

    .. code-block:: console

        $ coverage html

    .. ifconfig:: not prerelease

        Then visit htmlcov/index.html in your browser, to see a
        `report like this`_.

    .. ifconfig:: prerelease

        Then visit htmlcov/index.html in your browser, to see a
        `report like this one`_.

.. _coverage.py page on the Python Package Index: https://pypi.python.org/pypi/coverage
.. _report like this: https://nedbatchelder.com/files/sample_coverage_html/index.html
.. _report like this one: https://nedbatchelder.com/files/sample_coverage_html_beta/index.html


Using coverage.py
-----------------

There are a few different ways to use coverage.py.  The simplest is the
:ref:`command line <cmd>`, which lets you run your program and see the results.
If you need more control over how your project is measured, you can use the
:ref:`API <api>`.

Some test runners provide coverage integration to make it easy to use
coverage.py while running tests.  For example, `pytest`_ has the `pytest-cov`_
plugin.

You can fine-tune coverage.py's view of your code by directing it to ignore
parts that you know aren't interesting.  See :ref:`source` and :ref:`excluding`
for details.

.. _pytest: http://doc.pytest.org
.. _pytest-cov: https://pytest-cov.readthedocs.io/


.. _contact:

Getting help
------------

If the :ref:`FAQ <faq>` doesn't answer your question, you can discuss
coverage.py or get help using it on the `Testing In Python`_ mailing list.

.. _Testing In Python: http://lists.idyll.org/listinfo/testing-in-python

Bug reports are gladly accepted at the `GitHub issue tracker`_.
GitHub also hosts the `code repository`_.

.. _GitHub issue tracker: https://github.com/nedbat/coveragepy/issues
.. _code repository: https://github.com/nedbat/coveragepy

Professional support for coverage.py is available as part of the `Tidelift
Subscription`_.

`I can be reached`_ in a number of ways. I'm happy to answer questions about
using coverage.py.

.. _I can be reached: https://nedbatchelder.com/site/aboutned.html



More information
----------------

.. toctree::
    :maxdepth: 1

    install
    For Enterprise <https://tidelift.com/subscription/pkg/pypi-coverage?utm_source=pypi-coverage&utm_medium=referral&utm_campaign=enterprise>
    cmd
    config
    source
    excluding
    branch
    subprocess
    api
    howitworks
    plugins
    contributing
    trouble
    faq
    changes
