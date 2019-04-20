Installing Pelican
##################

Pelican currently runs best on |min_python|; earlier versions of Python are not supported.

Once Pelican is installed, you can run ``pelican --help`` to see basic usage
options. For more detail, refer to the :doc:`Publish<publish>` section.

You can install Pelican via several different methods. The simplest is via
`pip <http://www.pip-installer.org/>`_::

    python -m pip install pelican

Keep in mind that operating systems will often require you to prefix the above
command with ``sudo`` in order to install Pelican system-wide. **You should
not do this** as it may break your operating system. In this case you
can add the ``--user`` flag or try one of the recommended methods below.

**Recommended method 1:** `pipx <https://github.com/pipxproject/pipx/>`_

pipx lets you execute binaries from Python packages in isolated environments.
You can install pipx according to instructions on its  
`homepage <https://github.com/pipxproject/pipx/>`_. After pipx is installed,
you can install pelican::

    $ pipx install pelican
    installed package pelican 4.0.1, Python 3.6.7
    These binaries are now globally available
     - pelican
     - pelican-import
     - pelican-quickstart
     - pelican-themes
    done! ✨ 🌟 ✨

To upgrade or uninstall::

    pipx upgrade pelican
    pipx uninstall pelican

**Recommended method 2:** Virtual Environment

If you prefer to manually manage a Virtual Environment, you can create 
a virtual environment for Pelican via venv_ (or virtualenv_ if you are 
using Python2) before installing Pelican.::

    python -m venv ~/virtualenvs/pelican
    . ~/virtualenvs/pelican/bin/activate

Once the virtual environment has been created and activated, Pelican can be
installed via ``python -m pip install pelican`` as noted above. Alternatively, if you
have the project source, you can install Pelican using the setuptools method::

    cd path-to-Pelican-source
    python -m pip install .

If you have Git installed and prefer to install the latest bleeding-edge
version of Pelican rather than a stable release, use the following command::

    python -m pip install -e "git+https://github.com/getpelican/pelican.git#egg=pelican"

To exit the virtual environment, type ``deactivate``.

Optional packages
-----------------

If you plan on using `Markdown <https://pypi.org/project/Markdown/>`_ as a
markup format, you can install Pelican with Markdown support::

    python -m pip install "pelican[markdown]"

Typographical enhancements can be enabled in your settings file, but first the
requisite `Typogrify <https://pypi.org/project/typogrify/>`_ library must be
installed::

    python -m pip install typogrify

If you are using pipx, you can inject packages into the pipx-managed virtual
environment::

    pipx inject pelican Markdown

Dependencies
------------

When Pelican is installed, the following dependent Python packages should be
automatically installed without any action on your part:

* `feedgenerator <https://pypi.org/project/feedgenerator/>`_, to generate the
  Atom feeds
* `jinja2 <https://pypi.org/project/Jinja2/>`_, for templating support
* `pygments <https://pypi.org/project/Pygments/>`_, for syntax highlighting
* `docutils <https://pypi.org/project/docutils/>`_, for supporting
  reStructuredText as an input format
* `blinker <https://pypi.org/project/blinker/>`_, an object-to-object and
  broadcast signaling system
* `unidecode <https://pypi.org/project/Unidecode/>`_, for ASCII
  transliterations of Unicode text
  utilities
* `MarkupSafe <https://pypi.org/project/MarkupSafe/>`_, for a markup-safe
  string implementation
* `python-dateutil <https://pypi.org/project/python-dateutil/>`_, to read
  the date metadata

Upgrading
---------

If you installed a stable Pelican release via Pip_ and wish to upgrade to
the latest stable release, you can do so by adding ``--upgrade``::

    python -m pip install --upgrade pelican

If you installed Pelican via distutils or the bleeding-edge method, simply
perform the same step to install the most recent version.

If you installed with pipx::

    pipx upgrade pelican

Kickstart your site
-------------------

Once Pelican has been installed, you can create a skeleton project via the
``pelican-quickstart`` command, which begins by asking some questions about
your site::

    pelican-quickstart

If run inside an activated virtual environment, ``pelican-quickstart`` will
look for an associated project path inside ``$VIRTUAL_ENV/.project``. If that
file exists and contains a valid directory path, the new Pelican project will
be saved at that location. Otherwise, the default is the current working
directory. To set the new project path on initial invocation, use:
``pelican-quickstart --path /your/desired/directory``

Once you finish answering all the questions, your project will consist of the
following hierarchy (except for *pages* — shown in parentheses below — which
you can optionally add yourself if you plan to create non-chronological
content)::

    yourproject/
    ├── content
    │   └── (pages)
    ├── output
    ├── tasks.py
    ├── Makefile
    ├── pelicanconf.py       # Main settings file
    └── publishconf.py       # Settings to use when ready to publish

The next step is to begin to adding content to the *content* folder that has
been created for you.

.. _virtualenv: https://virtualenv.pypa.io/en/latest/
.. _venv: https://docs.python.org/3/library/venv.html
