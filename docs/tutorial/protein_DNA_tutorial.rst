=========================
Protein-DNA with MELD
=========================

Intro
===========================

In this tutorial we are going to prepare a setup script and other necessary files required for a Protein-DNA simulation. It is recommended that you review "getting started" before this one. The ideal goal of this part is to sample many binding/unbinfding events so that the protein has enough chances of exploring and finding the right binding pose. For sake of simplicity, I'm using 1azp, a small protein-DNA complex from PDB. Here's a list of files needed for this tutorial:

DNA-sequence.dat
DNA-hbonds.dat
secondary-structure.ss
protein-DNA-contacts.dat
protein-contacts.dat
starting-structure.pdb
restraints.py
setupMELD.py

DNA-sequence.dat
----------------------------
This is a simple dat file with the sequence of the first DNA strand in FASTA format without the header.

setupMELD.py
----------------------------

This is the main file that will prepare the simulation setup for OpenMM. All other files mentioned abolve will be used in setupMELD.py

First things first, import the necessary modules:
.. code-block:: python

    import numpy as np
    from meld.remd import ladder, adaptor, master_runner
    from meld import comm, vault
    from meld import system
    from meld import parse
    from meld.system.restraints import LinearRamp,ConstantRamp
    import glob
    from restraints import *
