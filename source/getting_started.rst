Getting Started
===============

Get the code
------------

As PLANES is in continuous development, the only available version today is on Github_.

You can either download the lastest version as a `zip file here`_ or get it through Git_ to stay on the cutting edge ::

    $ git clone https://github.com/OlivierDAZEL/PLANES

Understanding architecture
--------------------------

In the ``src/`` folder, you'll find all the scripts, the folders inside ``src/`` have self-explanatory names :

``FEM/`` & ``DGM/`` & ``PW/``
    Implementation of Finite Elements & Discontinuous Galerkin Methods, Plane wave based methods (multilayer)

``Material/`` & ``Physics/``
    Material properties & modelling

``Mesh/``
    Mesh management routines (reading, modification, tagging, etc...)

``Plots/``
    Output functions

``Polynomials/``
    Function to combine, derive, integrate, etc.. polynomials

``Problems/`` & ``Solutions/``
    Directory for m-files describing configurations & analytical solutions of problems (legacy)


The most important for you will be ``src/Main``.
This folder contains the main routines, ``PLANES_main.m`` for legacy projects & ``PLANES.m`` [#]_ for newer,
separate-directory projects.

Other files are initialization, logging and postprocessing routines.


.. [#] Which contains the ``PLANES()`` function.

.. _github: https://github.com/OlivierDAZEL/PLANES
.. _git: https://git-scm.com
.. _zip file here: https://github.com/OlivierDAZEL/PLANES/archive/master.zip

