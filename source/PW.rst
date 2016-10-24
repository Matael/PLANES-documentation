Using the PLANES Plane Wave Solver
==================================

The Plane Wave solver relies on a method close to the Transfer Matrix Method. It can be
used to model a wide range of layered systems, even including 3D fully anisotropic PEMs.

.. todo:: add the paper (2013)

The solver relies on project similar to those for the FEM/DGM solver. The function to call
is the following ::

  PLANES_Multilayer(name, number, data_model, multilayer, frequency)

With:

- ``name`` is a string associated to the name of the project. This string is the same than the folder in the project area.
- ``number`` is an integer. This is the number of the subproject.
- ``data_model`` is a structure that contains the data of the model. In the present case, it only contains the angle of incidence.
- ``multilayer`` is a structure array which contains one or several multilayer structures (see below).
- ``data_model`` is a structure that contains the data of the model. In the present case, it only contains the angle of incidence. It can be either a real number or an array of two real numbers.
- ``frequency`` is the structure associated to frequency (see below).


At the end of the resolution, the solver outputs a PW file named ``out/<project name>_<num
of subproject>.PW``.

It's a plain text file with 6n+1 columns. The first column corresponds to the frequency
axis, the others are the following (for each multilayer structure):

- Absorption coefficient
- Real part of the reflexion coefficient
- Imaginary part of the reflexion coefficient
- Transmission loss
- Real part of the transmission coefficient
- Imaginary part of the transmission coefficient

.. info:: If the structures have a rigid backing, the transmission-related colums are omitted.

The multilayer structure
------------------------

The different multilayer structures are gathered in a single object containing several
arrays:

- ``multilayer.nb(1,m)`` correspond to the number of layer of multilayer structure ``m``.
- ``multilayer.termination(1,m)`` correspond to the termination condition of multilayer structure ``m``. The value is 0 for rigid backing and 1 for a radiation condition
- ``multilayer.d(l,m)`` correspond to the thickness of the layer ``l`` of multilayer structure ``m``. It is a real number.
- ``multilayer.mat(l,m)`` correspond to the material of the layer ``l`` of multilayer structure ``m``. The label is an integer associated to the convention `presented here`_.

.. _presented here: control_codes.html

