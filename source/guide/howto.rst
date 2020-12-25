.. _how-to:

================
How-to guides
================

After building up the environment for COBRA from the :ref:`installation`, this page will help you explore the abilities of COBRA, and guide you how to train this snake to do its jobs.

Setup
~~~~~~~~~~~~~~
.. TODO setup document

Before you start, please make sure you have all the required environment prepared. If you haven't done so yet, please check those out!

- :ref:`environment`
- :ref:`installation`

.. admonition:: when you are ready

		Cool, now let us have a look what kind of abilities does this snake have.	

Main Modules
~~~~~~~~~~~~~~
Before we start, let's just quickly go through its main modules. Currently, COBRA contains three main modules:


.. list-table:: COBRA main modules
    :widths: 15 10 30
    :header-rows: 1

    * - Command
      - Inputs
      - Outputs
    * - ``cobra scorepeak``
      - narrowPeaks, custom PWM files
      - csv file with binding confidence
    * - ``cobra find``
      - binding confidence, csv file with differential expression
      - target genes with target probability
    * - ``cobra plot``
      - outputs from previous steps, labels
      - dotplots and other plots


*Note that: COBRA still have some other side abilities which would be introduced later. If you run* ``cobra --help`` *, you will get all the information you need.*

----------

.. .. raw:: html
.. 
..   <embed>
..   <div class="admonition-todo admonition" id="index-0">
..   <p class="first admonition-title">TODO</p>
..   <p class="last">Fix orders</p>
..   </div>
..   </embed>   


:cobra scorepeaks:

   :ref:`scorepeaks` **is to calculate binding confidence for each gene given the ChIP-seq peakcalling.** For example, let's say you are interested in human STAT1 direct targets. You'll need two inputs to run ``cobra scorepeak``.

   - ``narrowPeak_dir/``: a directory contains all the narrowPeak files `(>20 files)`
   - ``stat1_human.meme```: custom PWM file.

   Our current working folder structure shows below

   .. code-block:: sh
      :emphasize-lines: 2

      [users]$ ls
      narrowPeak_dir   stat1_human.meme   

   If you have those two files prepared, you will be able to run ``cobra scorepeak`` now!
   

.. container:: toggle

    .. container:: header
		   
        **show an example of** ``cobra scorepeaks``
	
    .. code-block:: sh
       :linenos:

       cobra scorepeak --tf STAT1 -i narrowPeak_dir/ --meme stat1_human.meme --human --core 8


.. raw:: html

   <details>
   <summary><a>Parameters of cobra scorepeaks</a></summary>

.. list-table:: cobra scorepeaks cheating sheet
    :widths: 10 20
    :header-rows: 1

    * - Parameters
      - Functions
    * - ``--tf``
      - TF of interest *(default: STAT1)*
    * - ``-i``
      - input of narrowPeaks *(default: ./)*
    * - ``--meme``
      - input of custom PWM files *(default: tf_speicies.meme)*
    * - ``--human`` or ``--mouse``
      - given one to select speicies *(default: mouse)*
    * - ``--core``
      - num of cores to use *(default:1)*

.. raw:: html

   </details>
   
-----------
   
:cobra find:

   This module is to find the TF direct target genes by given the binding scores for each gene plus differential expression analysis results. COBRA will require two inputs as well:

   - csv file with binding confidence (``human_stat1.csv``)
   - Differential expression analysis data (``rna_dir/``)

.. container:: toggle

    .. container:: header
		   
        **show an example of** ``cobra find``
	
    .. code-block:: sh
       :linenos:

       cobra find --tf STAT1 -c chip-init-outs.csv -r rna_dir/ -o output_dir/
   

       
.. raw:: html

   <details>
   <summary><a>Parameters of cobra find</a></summary>

.. list-table:: cobra find
    :widths: 10 20
    :header-rows: 1

    * - Parameters
      - Functions
    * - ``--tf``
      - TF of interest *(default: STAT1)*
    * - ``-c``
      - csv files of chip confidence binging outputs *(default: ./)*
    * - ``-r``
      - input of differential expression data or directory.
    * - ``-o``
      - output dir. If it is not exist, create one.

.. raw:: html

   </details>
   
-----------

:cobra plot:

   The coolest ability that COBRA has is using ``cobra plot`` to draw some pretty images showing the TF binding status for every gene given the data. From those plots, bioloists would be able to discover some stories easier. You could set

   Here is the magic command to activate ``cobra plot``.

.. container:: toggle

    .. container:: header
		   
        **show an example of** ``cobra plot``
	
    .. code-block:: sh
       :linenos:

       cobra plot --tf STAT1 -s mouse --gene STAT1 STAT3 -i output-cobra-find/ -o img/ -t truth.pl

.. raw:: html

   <details>
   <summary><a>Parameters of cobra plot</a></summary>


.. list-table:: cobra plot
    :widths: 10 20
    :header-rows: 1

    * - Parameters
      - Functions
    * - ``--tf``
      - TF of interest *(default: STAT1)*
    * - ``-s``
      - species
    * - ``--gene``
      - list of genes of interest
    * - ``-i``
      - outputs of cobra find (target genes with probs)
    * - ``-o``
      - image outputs dir
    * - ``-t``
      - labels or targets (provided by users)

.. raw:: html

   </details>


-----------

   
Test COBRA
~~~~~~~~~~~~~~

a) Load test data
>>>>>>>>>>>>>>>>>>

For those new friends, you may not have your data prepared yet to train this snake.
Don't worry, in order to get familiar with users, COBRA itself have a test dataset in its pocket.
All you need to do is to do ammunition loading using ``cobra load`` which will automatically load the ChIP-seq data into ``./narrow/``, RNA-seq data into ``./rna/``.
Why not give it a trail now?

.. highlight:: sh

::

   # ammunition loading
   cobra load

If you check your folder with ``ls``, you will find two folders -  ``narrow`` and ``rna`` from  your current working directory (please make sure that COBRA have the permission to ``mkdir`` in the current working directory). Also, if you want to load in other folders, you can simply use the parameter ``--dir`` or ``-d`` following by the folder you want. (COBRA documentation writor assume that you are lazy and will load test data in the current working directory.)

b) Run cobra normally
>>>>>>>>>>>>>>>>>>>>>>
Once you have your test data prepared, you could simply run ``cobra scorepeaks`` and ``cobra find`` step by step to get the results.

.. highlight:: sh

::

   # this step would generate multiple files for future usage (by default --tf: STAT1)
   cobra scorepeaks -i narrow/ --meme stat1_human.meme --human --core 8

   ######### Done: after a few seconds #########

   # gives input files or folders and output folders (GMM model will be trained)
   cobra find -c human_stat1.csv -r rna/ -o output/

   ######### A few seconds later: you will find your results in output/ #########

c) Generate figures
>>>>>>>>>>>>>>>>>>>>>

Let's do some visualisation now. If you do ``ls``, you will find there are a few files available now. You have ``fimo.csv`` which is a intermediate step of motif filtering.

   
