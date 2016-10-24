Creating a new project
======================

.. note:: The following section only discuss separate-directory projects.

To start a new project, create a directory separated from the ``src/`` directory of PLANES (your dir may be anywhere on
the file system) and create a ``.m`` file inside ::

    $ mkdir /home/you/MyPLANESProject/
    $ cd /home/you/MyPLANESProject
    $ touch MyProject.m

Some other directories will be useful too (such as output for info-files, graphs, FreeFEM
programs & data files) ::

    $ mkdir -p out Profiles m m/Materials FF

The files are organised as follows:

- The root m-file is used to start the experiment (its contents are details hereafter)
- Each subproject has a m-file in ``m/`` and if needed a EDP (FreeFEM) file in ``FF/``.
  They are named : ``<project name>_<num of subproject>_data.m`` and ``<project name>_<num of subproject>.m``
- The materials related m-files used for the project are stored in ``m/Materials/``
- Output (text) files from runs will be sent to ``out/`` and graphs to ``Profiles/``
- A ``m/<project name>_<num of subproject>_postprocess.m`` can be used to define a
  post-processing routine and it will be trigged after the resolution.

.. tip:: You can consider a project as a global experiment. The next step is therefore to specify the different
    configurations for the experiment. If one wants for example to test reflection on a porous material set behind a
    membrane, it may be interesting to try different parameters for the membrane : all the configurations are about the
    same experiment, thus in the same project dir. Configurations are identified by appending an underscore (``_``) and
    a number at the end of m-file and .edp.

.. info:: The ``m/`` and ``m/Materials`` directories are added to the MATLAB/Octave path by PLANES with a higher precedence
    than its internal dirs. The files in those directories can be use to override parts of PLANES at the project level.

Project file
------------

The main file must define some structures, see the example below for more information :

.. code-block:: matlab

    clear all
    close all
    current_dir=pwd;
    PLANES_dir='../../src/Main/';

    frequency.nb=5; % number of frequencies (negative : log spaced)
    frequency.min=100;
    frequency.max=20000;


    % Information about the output graphs
    data_model.profiles.mesh=1; % plot the mesh
    data_model.profiles.x=0; % profiles along x/y axis
    data_model.profiles.y=0;
    data_model.profiles.map=0; % plot a 2D map of the solution
    data_model.profiles.custom=0; % custom plots activation
    data_model.profiles.custom_plots = {}; % cellarray of strings, scripts stored in m/

    % export data ?
    data_model.export.profiles=0;
    data_model.export.nrj=1;
    data_model.export.reset=0; % delete old files before export

    % log level (0 -> 2)
    data_model.verbosity = 1;

    % DGM related (number of waves of the recontruction basis & initial tilt)
    data_model.theta_DGM.nb=4;
    data_model.tilt=0;

    % Fully separated projects
    name.project_directory=current_dir;

    % Call to PLANES
    cd(PLANES_dir)
    PLANES('Project Name', num_of_subproject, data_model, frequency, name)
    cd(current_dir);

