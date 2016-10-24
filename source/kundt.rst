Example and Benchmark : Kundt tube
==================================

PLANES is bundled with an example project (also used as a benchmark) : a simple Kundt
tube of unit length.

The different subprojects implement different methods and couplings :

========== ===========
Subproject Method(s)
========== ===========
0          **FEM on TR6**
1          **FEM on H12**
2          **FEM on TR6** coupled to **FEM on H12**
3          **DGM on TR**
4          **DGM on H**
5          **DGM on TR** coupled to **DGM on H**
6          **FEM on H12** coupled to **DGM on H**
7          **FEM on TR6** coupled to **DGM on H**
========== ===========

These examples can show you how to organized a multi-subprojects project directory as well
as how to use `FreeFEM++`_ and PLANES together.

.. _FreeFEM++: http://www.freefem.org/
