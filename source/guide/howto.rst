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

.. note:: Cool, now let us have a look what kind of abilities does this snake have.

Modules
~~~~~~~~~~~~~~
Before we start, let's just quickly go through its main modules. COBRA contains three main modules:


.. list-table:: COBRA main modules
    :widths: 15 10 30
    :header-rows: 1

    * - Command
      - Inputs
      - Outputs
    * - ``cobra chip-init``
      - narrowPeaks, custom PWM files
      - csv file with binding confidence
    * - ``cobra find``
      - binding confidence, csv file with differential expression
      - target genes with target probability
    * - ``cobra vis``
      - outputs from previous steps, labels
      - dotplots and other plots


.. note:: Acturally, COBRA still have some other side abilities which would be introduced later.

If you run ``cobra --help``, you will get the following:

(TODO) fix the help doccs

.. highlight:: sh

::

  (venv)$ cobra --help
  usage: cobra [-h] [--version] {init,check,run,enh,eval,alter,vis,clear} ...
  
   ██████╗ ██████╗ ██████╗ ██████╗  █████╗
  ██╔════╝██╔═══██╗██╔══██╗██╔══██╗██╔══██╗
  ██║     ██║   ██║██████╔╝██████╔╝███████║
  ██║     ██║   ██║██╔══██╗██╔══██╗██╔══██║
  ╚██████╗╚██████╔╝██████╔╝██║  ██║██║  ██║
   ╚═════╝ ╚═════╝ ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝
  usage: cobra [-h] [--version] {init | check | run | eval | alter} ...
  Cobra has three main options for users to find target gene from ChIP-seq and RNA-seq datasets.
   - cobra init
      "cobra init" is an initialisation process for ChIP-seq datasets (narrowpeak in our case).
      Basically, this option is to help user to score each gene to get a idea of the gene importance from ChIP-seq datasets.
   - cobra run
      "cobra run" is a Gaussian Mixture model based process which requires two inputs: initialised ChIP-seq data and RNA-seq data (differential expression).
   - cobra eval
      "cobra eval" is a evaluation option for users to get a roughly idea of their results. Currently, it supports STAT target gene only.
  
  Cobra init process requires some software dependencies, like bedtools, fimo, etc.
  system requirements:
    - bedtools
    - meme
    - python3
  python requirements are in requirements.txt.
  
  positional arguments:
    {init,check,run,enh,eval,alter,vis,clear}
                          subparsers
      init                extract the chip-seq information for next stop, (every option is turn on by default, default species: mouse)
      run                 run the gaussian mixture model and output the result
      enh                 evaluate the result (print the accuracy)
      eval                evaluate the result (print the accuracy)
      alter               This alternative option is for getting stat target gene list
      clear               clear all the cobra init
  
  optional arguments:
    -h, --help            show this help message and exit
    --version, -v         show program's version number and exit


1.1 cobra chip-init
-----------------------

``chip-init``, literally, it is an ability for ChIP-seq data analysis. A simple example could be:

.. highlight:: sh

::

   cobra init --tf STAT1 -i narrowPeak_dir/ --meme stat1_human.meme --human --core 64

.. note:: This command provides at lease 5 information which embedded into those parameters of ``cobra chip-init``: ``tf`` for transcription factors; ``i`` for input; ``meme`` for PWM; ``--human`` or ``--mouse`` for speicies; ``--core`` for num of cores.

.. list-table:: cobra chip-init
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


The ChIP-seq peakcalling data is essential for COBRA training, without

1.2 cobra find
-----------------------

Users could use ``cobra find`` to find potential TF target genes. Here is an example:

.. highlight:: sh

::

   cobra find --tf STAT1 -c chip-init-outs.csv -r rna_dir/ -o output_dir/

Similarly, COBRA this time is going to find the potential TF targets by providing ouptut_dir.

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


1.3 cobra vis
-----------------------

The coolest ability that COBRA have is using ``cobra vis`` to draw some pretty images showing the TF binding status for every gene given the data. From those plots, bioloists would be able to discover some stories easier. Here is the magic command to activate ``cobra vis``.

.. highlight:: sh

::

   cobra vis --tf STAT1 -s mouse --gene STAT1 STAT3 -i output-cobra-find/ -o img/ -t truth.pl


.. list-table:: cobra vis
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


      


