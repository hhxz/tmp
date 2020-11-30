.. _environment:

=============
Environment
=============

1.1 Docker
~~~~~~~~~~~~~~~~~

We provide a ``Dockerfile`` to make life easier. 

.. If you follow the docker usage, you could build it up easily.

.. highlight:: sh

::

   # cd to the Dockerfile folder
   docker build -t COBRA:1.0 .
   

1.2 Build your own environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you don't like docker, don't worry, ``pip install`` would be a savior.

.. highlight:: sh

::

    # run it in your terminal
    pip install -r requirements.txt
    python setup.py install

Other softwares
-----------------
In order to enhance COBRA's abilities, there're few other softwares required to be installed before you take COBRA home.

- **Quick Install for meme-suite**

.. highlight:: sh

::

   # meme installation
   tar zxf meme_4.11.4.tar.gz
   cd meme_4.11.4
   ./configure --prefix=$HOME/meme --with-url=http://meme-suite.org --enable-build-libxml2 --enable-build-libxslt
   make
   make test
   make install

   # configureation
   export PATH=$HOME/meme/bin:$PATH  

More details could be found `here <http://web.mit.edu/meme_v4.11.4/share/doc/install.html>`_.

.. warning:: WITHOUT MEME-SUITE, THE ABILITY OF THE SENSE OF SMELL WILL INFLUENCED.

- **Distribution Optimization**

This is a R package embedded into COBRA, which provides COBRA a more powerful sense of RNA-seq touch. If you are interested in the package, please click `here <https://cran.r-project.org/web/packages/DistributionOptimization/index.html>`_.


