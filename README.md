LaMachine
===========

This is a virtual machine based on Ubuntu Linux 14.04 (64-bit only)
with the latest development versions of NLP software developed by the Language
Machines research group,  CLST (Radboud University Nijmegen), as well as TiCC
(Tilburg University). It can also serve as a docker.io application rather than
a VM.

Pre-installed software:
- *Timbl* - Tilburg Memory Based Learner
- *Ucto* - Tokenizer
- *Frog* - Frog is an integration of memory-based natural language processing (NLP) modules developed for Dutch.
- *FoLiA-tools* - Command line tools for working with the FoLiA format
- *PyNLPl* - Python Natural Language Processing Library (Python 2 & 3)
- *Colibri Core* - Colibri core is an NLP tool as well as a C++ and Python library for working
  with basic linguistic constructions such as n-grams and skipgrams (i.e patterns
  with one or more gaps, either of fixed or dynamic size) in a quick and
  memory-efficient way. At the core is the tool colibri-patternmodeller which
  allows you to build, view, manipulate and query pattern models.
- *Python bindings* - python-ucto, python-frog, python-timbl (for Python 3)
- *CLAM* - Quickly build RESTful webservices (Python 2)

Some third-party NLP software is also installed out of the box.

Installation & Usage as Virtual Machine (for Linux, BSD, MacOS X, Windows)
=========================================================================

1. Obtain Vagrant from https://www.vagrantup.com/downloads.html or your package manager.
2. Obtain Virtual Box from https://www.virtualbox.org/ or your package manager.

On most Linux distributions, steps one and two may be combined with a simple command such as
``sudo apt-get install virtualbox vagrant`` on Ubuntu, or ``sudo pacman -Syu virtualbox vagrant`` on Arch Linux.

3. Clone this repository and navigate to the directory in the terminal: ``$ git clone https://github.com/proycon/LaMachine && cd LaMachine`` 
4. Power up the VM: ``vagrant up`` (this will download and install everything
the first time)
5. SSH into your VM: ``vagrant ssh``
6. When done, power down the VM with: ``vagrant halt`` (and you can delete it entirely with ``vagrant destroy``)

You may want to adapt Vagrantfile to change the number of CPUs and Memory
available to the VM (2 CPUs and 3GB RAM by default).


Installation & Usage with Docker (for Linux only)
===============================================

1. Obtain Docker from http://www.docker.com or your package manager (``sudo apt-get install docker`` on Ubuntu).
2. Pull the LaMachine image: ``docker pull proycon/lamachine``
3. Start an interactive prompt to LaMachine: ``docker run  -t -i proycon/lamachine /bin/bash``, or run stuff: ``docker run proycon/lamachine <program>``  (use ``run -i`` if the program has an interactive mode; set up a mounted volume to pass file from host OS to docker, see: https://docs.docker.com/userguide/dockervolumes/)

There is no need to clone this git repository at all for this method.

Installation & Usage locally (for Linux/BSD only)
==============================================

LaMachine can also be used on a Linux system without root access (provided a
set of prerequisites is available on the system). This is done through an
extension for Python VirtualEnv, as we provide a lot of Python bindings anyhow.

1. Ensure prerequisites are available on the system. Ask your system
   administrator to install the following packages (Ubuntu, package names may
   differ on other distributions): git-core make gcc g++ autoconf-archive libtool autotools-dev libicu-dev libxml2-dev libbz2-dev zlib1g-dev libtar-dev libboost-all-dev python-dev python3 python3-pip cython3 python3-lxml python3-pycurl python-virtualenv python3-numpy python3-scipy python3-requests"
2. Clone this repository and navigate to the directory in the terminal: ``$ git clone https://github.com/proycon/LaMachine && cd LaMachine`` 
3. Create a virtualenv for Python 3: ``virtualenv --python=python3 lamachine``
4. Activate the virtualenv: ``. lamachine/bin/activate``  (repeat this step whenever you want to access the environment in the future)
5. Bootstrap the virtual environment: ``../virtualenv-bootstrap.sh``

Alternatively, Anaconda is supported too (but untested as of yet), replace
steps three and four with the proper equivalents using ``conda``, ensure you are in the
target environment's directory prior to executing
``virtualenv-bootstrap.sh``. 

This may even work on Mac OS X with a bit of tweaking (not tested yet).
 
Alternatives
====================

If you have no need for a VM or a self-contained environment, and you have proper
administrative access to the system, then install our software using the proper
package manager, provided we have packages available.

* Arch Linux (up to date) -- https://aur.archlinux.org/packages/?SeB=m&K=proycon
* Debian/Ubuntu Linux (packages are currently out of date) -- https://qa.debian.org/developer.php?login=ko.vandersloot@uvt.nl
* Mac OS X (homebrew), missing some sofware (most notably Frog, Colibri Core, and Python bindings)
* CentOS/Fedora (packages are outdated completely)

The final alternative is obtaining all software manually (from github or
tarballs) and compiling everything yourself.
