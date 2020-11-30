.. _installation:

=============
Installation
=============

Let's get started by setting up our environment to have your own COBRA.

1.1 Requirements
~~~~~~~~~~~~

Currently, COBRA will only be happy when living with python 3.7 or newer. So please provide a nice environment to make sure it is happy to be with you.

1.2 Working environment
~~~~~~~~~~~~~~~~~~~

COBRA is tested and supported on the following 64-bit systems:

- Fedora 29
- MacOS Catalina 10.15.7

In order to take COBRA home, you can either keep it into a docker container or build up a cosy working environment for it.

See more details from :ref:`environment`.

.. note:: Once you have the environmnet sorted, you can simply install COBRA by following the next step.

1.3 Install COBRA
~~~~~~~~~~~~~~~~~~
Users are welcome to install COBRA either use ``pip package`` or ``build from source``.

1.3.1 pip package manager (TODO)
---------------------------------

Install COBRA with Python's ``pip`` package manager.

.. highlight:: sh

::

   # Requires the latest pip
   pip install --upgrade pip
   # Current stable release
   pip install sslab-cobra
   
1.3.2 Build from source
--------------------------

Download the COBRA source code from github

.. highlight:: sh

::

   # git clone
   git clone https://github.com/ss-lab/cobra.git
   cd cobra

We recommand users to create a virual environment (optional)

.. highlight:: sh

::

   python -m venv venv
   source venv/bin/activate

Install those CORBA required packages

.. highlight:: sh

::

   # build environment
   pip install -r requirements.txt
   python setup.py install


Now, hopefully, COBRA is ready to work!

.. note:: Welcome on board! You have your own COBRA now. The next section will tell you the abilities of COBRA and guide you train this snake step-by-step.
