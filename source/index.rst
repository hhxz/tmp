.. raw:: html

    <style>
        .row {clear: both}
        .row h2  {border-bottom: 1px solid gray;}

        .column img {border: 1px solid gray;}

        @media only screen and (min-width: 1000px),
               only screen and (min-width: 500px) and (max-width: 768px){

            .column {
                padding-left: 5px;
                padding-right: 5px;
                float: left;
            }

            .column3  {
                width: 33.3%;
            }

            .column2  {
                width: 50%;
            }
        }
    </style>

########################
COBRA documentation
########################

.. image:: ./img/cobra-white.png
   :alt: cobra logo

.. caution:: YOU ARE BE IN SS-ZOO. THERE MAY BE COBRA IN THIS AREA.

********
Overview
********

COBRA would be an excellent TF targets hunter based on its highly developed sense of smell for ChIP-seq and excellent sense of touch for RNA-seq. However, this is also a greedy snake. In order to let COBRA become your reliable partener, we highly recommond to feed at least 20 ChIP-seq experiments for it. Once COBRA gets enough feeds from users, it could do some cool stuffs, like dotplot painting. Why not have one yourself? Check this page out to see how it works now! 

.. COBRA apples a probabilistic model, which integrates cistromes obtained from TF binding ChIP-seq data and differential gene expression, to compute the target probability based on the experiments. The whole process could be divided by four main steps: high confidence peak clustering, binding site scoring, differential expression analysis, and integration.

.. rst-class:: clearfix row

.. rst-class:: column column2

:ref:`installation` - start here
=============================

For those new to SS-ZOO, start here to get your own COBRA locally now!

.. For the new cobra users, how to setup a COBRA-friendly environment.

.. rst-class:: column column2

:ref:`how-to`
=============

Introduce the COBRA abilities; practical step-by-step guides for the new COBRA users, covering several important topics.

.. rst-class:: column column2

:ref:`key-points`
=================

Explanation and analysis of some key features.

.. rst-class:: column column2

:ref:`reference`
================

Technical reference material, for classes, methods, APIs, commands.

************************
Why the name COBRA?
************************

Actually, you can find lots of ways to make sense of cobra. Here are the ways we think:

- Literally: Combined Binding and Regulatory Analysis.
- Programming language: This snake was written in python.
- In Chinese: Glasses snake. Hopefully, with the glasses, cobra could find the target gene easier.

*************
About SS-ZOO
*************

We currently have ``SpideR``, ``COBRA``. Our new members - ``Priranha``, ``FROGS`` -  will be coming soon!


.. toctree::
    :maxdepth: 3
    :hidden:
    
    tutorials/environment
    tutorials/installation
    guide/howto
    keypoints/keypoints
