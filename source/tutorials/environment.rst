.. _environment:

=============
Environment
=============
COBRA is a terminal friendly snake. In order to setup a friendly environment, please be familiar with using terminal. Note that the command below are all based on terminal command.

1.1 Docker
~~~~~~~~~~~~~~~~~

Docker container is a super handly tool which is able to provide a friendly environment for users. Once you have docer installed on you own machine. COBRA provides a ``Dockerfile`` to make life easier. What you need to do is just ``git clone`` and use the ``Dockerfile`` we provided to setup a Docker environment for COBRA.

.. If you follow the docker usage, you could build it up easily.

.. highlight:: sh

::

   git clone cobra
   cd cobra
   docker build -t COBRA:1.0 .

Note that ``docker build`` will help you to setup a vitual linux environment with all the software prepared.

1.2 Build your own environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you don't like docker, and you want to see what kind of software COBRA required. Don't worry, you can setup manually. ``pip install`` would be a savior for python dependencies of COBRA once you have COBRA repo downloaded.

.. highlight:: sh

::

    pip install -r requirements.txt
    python setup.py install

1.3 Other softwares dependencies
---------------------------------
In order to enhance COBRA's abilities, there're few other softwares required to be installed before you take COBRA home.

a) MEME-Suite
>>>>>>>>>>>>>

In order to reduce the noise level, we used FIMO in MEME-Suite to do motif filtering for COBRA.

.. container:: toggle

    .. container:: header
		   
        **Quick Install for meme-suite**
	
    .. code-block:: sh
       :linenos:

       tar zxf meme_4.11.4.tar.gz
       cd meme_4.11.4
       ./configure --prefix=$HOME/meme --with-url=http://meme-suite.org --enable-build-libxml2 --enable-build-libxslt
       make
       make test
       make install
    
       # configureation
       export PATH=$HOME/meme/bin:$PATH  

More details could be found `here <http://web.mit.edu/meme_v4.11.4/share/doc/install.html>`_.

.. .. warning:: Without MEME-SUITE, COBRA's ChIP-seq sense WILL be influenced.

b) **Distribution Optimization**
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
This is a R package embedded into COBRA, which provides COBRA a more powerful sense of RNA-seq touch. If you are interested in the package, please click `here <https://cran.r-project.org/web/packages/DistributionOptimization/index.html>`_.


