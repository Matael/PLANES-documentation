Identification of Method, Material & Boundary
=============================================

The different elements of the model are specified using labels. Differents structures
keep track of those labels:

- ``elem.model(n)`` type of modelling for the n-th element
- ``edge_msh(n,3)`` type of boundary for the n-th edge
- ``elem.label(n)`` identifier for the material (can be set in the FreeFEM++ mesher)

Types of numerical models
-------------------------

===== ================
Label Solving Method
===== ================
1     FEM on TR6 (6 nodes triangles)
2     FEM on H12 (3 nodes triangles with Hermite splines interpolation)
3     FEM on TR3 (3 nodes triangles)
10    DGM on Triangles
11    DGM on Rectangles
===== ================

.. tip:: The meshes between FEM and DGM can be incompatible.

Types of media
--------------

===== =======
Label Media
===== =======
0     Air
1XXX  Elastic medium
2XXX  Equivalent fluid (rigid frame) material
3XXX  Limp model
4XXX  Poroelastic Material (or FEM with 1998 formulation)
5XXX  Biot (or FEM with 2001 formulation)
80xy  PML (with x and y boolean direction)
===== =======

Types of boundaries
-------------------

===== ==================
Label Type of Boundary
===== ==================
1     Rigid wall
2     Unit pressure (fluid)
3     Unit normal velocity
4     Unit tangential velocity
5     Sliding (PEM)
6     Bonded (PEM) or clamped (elastic)
7     Unit pressure (PEM)
8     Unit normal velocity (PEM)
9     Unit tangential velocity (PEM)
10    Incident air plane wave on acoustic/Biot98 element
11    Incident air plane wave on elastic element
12    Incident air plane wave on Biot 2001 element
13    DtN plate (Dirichlet to Neumann)
20    Transmitted air plane wave on acoustic/Biot 98 element
21    Transmitted air plane wave on elastic element
21    Transmitted air plane wave on Biot 2001 element
60    Unit normal velocity on H12 with flux application
61    DGM radiative boundary
98    Periodicity left
99    Periodicity right
4xx   ZOD even/odd
400   FSI (Fluid-Structure interaction)
1xyz  Excitation wave 1 angle xyz in degree (PEM)
2xyz  Excitation wave 2 angle xyz in degree (PEM)
3xyz  Excitation wave 3 angle xyz in degree (PEM)
500   Velocity diffracion cylindre FEM
===== ==================
