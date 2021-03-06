.. _setup:

==================
Installation Guide
==================

Yann is built on top of `Theano`_. `Theano`_ and all its pre-requisites are mandatory.
Once theano and its pre-requisites are setup you may choose to setup and run this toolbox.
Theano setup is documented in the `theano toolbox documentation`_. Yann is built with theanoo 0.8 
but should be forward compatible unless theano makes a drastic release. 

.. _Theano: http://deeplearning.net/software/theano/ 
.. _theano toolbox documentation: http://deeplearning.net/software/theano/install.html


Prerequisites
=============

Python + pip / conda
--------------------

  Yann needs Python 2.7. 
  Please install it for your OS.. Some modules that are required
  don't come with default python. But don't worry python comes with a package installer
  called pip. You can use pip to install additional packages.  
  
  For a headache free installation, the 
  `anaconda <https://www.continuum.io/downloads>`_ distribution of python is 
  very strongly recommended because it comes with a lot of goodies pre-packaged.  

C compiler
----------

  You need a C compiler, not because yann needs C, but theano and probably numpy
  requires C compilers. Make sure that your OS has one. Apple osX or macOS users, if you are using 
  Cuda and cuDNN, prefer using command line tools 7.x+. 8 doesn't work with cuDNN at the moment of 
  writing this documentation. You can download older versions of xcode and command line tools 
  `here <https://developer.apple.com/download/more/>`_.

Cuda 
----

  If you need the capability of a Nvidia GPU, you will need a suitable `CUDA toolkit and drivers
  <https://developer.nvidia.com/cuda-toolkit>`_. Some compoenents of the code depend
  on `cuDNN <https://developer.nvidia.com/cudnn>`_, so `cuDNN <https://developer.nvidia.com/cudnn>`_
  is highly recommended.
  
  Nvidia has the awesome cuDNN library that is free as long as you
  register as a `developer <https://developer.nvidia.com/cudnn>`_. I highly recommend using this.
  If you didn't install CUDA, you can still run the toolbox, but it will be much slower running on a
  CPU.

  .. Note ::

    Although `libgpuarray <http://deeplearning.net/software/libgpuarray/installation.html>`_  
    is also supported, it is not tested fully and might not work as well. Cuda Backend is strongly 
    recommended.

numpy/scipy 
-----------

  Numpy 1.6 and Scipy 0.11 are needed for yann. Make sure these work well with a blas system. Prefer 
  `Intel MKL <https://software.intel.com/en-us/intel-mkl>`_ for blas, which is also availabe from 
  anaconda. MKL is free for students and researchers and is available for a small price for others.

  If you use pip use 

  .. code-block:: bash

     pip install numpy
     pip install scipy
  
  to install these. If you use anaconda, use

  .. code-block:: bash
 
    conda install numpy
    conda install scipy
  

  to set these up

Theano 
------

Once all the pre-requisites are setup, install `theano`_ version 0.8 or higher.

.. _theano: http://deeplearning.net/software/theano/ 

The following ``.theanorc`` configuration can be used as a sample normally, 
but you may choose other options.


.. code-block:: bash

  [global]
  floatX=float32
  device=gpu0
  optimizer_including=cudnn
  mode = FAST_RUN

  [nvcc]
  nvcc.fastmath=True
  allow_gc=False

  [cuda]
  root=/usr/local/cuda/

  [lib]
  cnmem = 0.5

If you use the `libgpuarray <http://deeplearning.net/software/libgpuarray/installation.html>`_ 
backend instead of the CUDA backend, use ``device=cuda0`` or whichever device you want to run on.


Addtional Dependencies
======================

Yann also needs the following as additional dependencies that opens up additional features. 

skdata
------

Used as a port for datasets. This is Needed if you are using some common benchmark datasets. 
Install by using the following command:

.. code-block:: bash

  pip install skdata

progressbar
-----------
  
  Yann uses `progressbar <https://pypi.python.org/pypi/progressbar>`_ for aesthetic printing. You 
  can install it easily by using 

  .. code-block:: bash

    pip install progressbar
    
  If you don't have progressbar, yann will simply ignore it. 

matplotlib 
----------

  Not needed now, but might need in future. 
  Yann will switch from openCV to matplotlib. Install it by 

  .. code-block:: bash

    pip insall matplotlib
  
cPickle and gzip
----------------

  Most often the case is that these come with the python installation, 
  if not please install them. 


Yann Toolbox Setup
====================
 
Simply download the toolbox into a directory somewhere by 

.. code-block:: bash

    git clone https://github.com/ragavvenkatesan/yann
    
And add that path to your code by using:

.. code-block:: bash

    import sys
    sys.path.insert(0,"<path-to-yann-toolbox">

If not, quite simply have the toolbox in the directory where you are running the code so this is 
included in your codes.

.. Warning ::

    A ``Pypy`` installer will soon be setup. Once the distribution release is made, we can have 
    a pip install for yann.

