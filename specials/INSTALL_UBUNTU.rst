.. -*- coding: utf-8-with-signature-unix; fill-column: 77 -*-
*************************************
Installing Tahoe-LAFS on Ubuntu 20.04
*************************************

Ubuntu 20.04 comes with python 3 installed, but Tahoe does not currently run on python 3.

Tahoe-lafs users will have to install Python 2, and switch to Python 2 to be able to run Tahoe, you can switch back to Python 3 whenever you need to use python 3.

The following instructions are for installing Tahoe-LAFS on Ubuntu 20.04: 

1. Install Python 2.

``sudo apt install python``

2. Once the installation completes, you can check the Python 2, and python 3 version using the “–version” command.

``python2 --version``

``python3 --version``

3. Check all the available Python versions in your system.

``ls /usr/bin/python``

4. Check whether there are any Python-alternatives configured.

``sudo update-alternatives --list python``


5. Configure two Python alternatives. From the Step above, depending on the version of python in your system, we will set our priority.

``sudo update-alternatives --install /usr/bin/python python /usr/bin/python2 1``

``sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 2``

6. Confirm if the Python alternatives are set, and whether they are in use.

``sudo update-alternatives --config python``

7. Check the Python version currently running on the system.(it should show Python 2).

``python --version``

8. Install everything needed to run Tahoe. On a modern Debian/Ubuntu-derived distribution,
 this command will get you everything you need:

``apt-get install build-essential python-dev libffi-dev libssl-dev libyaml-dev virtualenv``

9. Confirm Pip works. Many Python installations already include pip,
 but in case yours does not; get pip for Python 2 with: 
 
``curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py`` 

and run 

``python get-pip.py``.

``pip --version``

10. Confirm if Virtualenv works. If you do not have an OS-provided copy of virtualenv,
 install it with the instructions from the virtualenv documentation.

``virtualenv --version``

11. Install the Latest Tahoe-LAFS Release
We recommend creating a fresh virtualenv for your Tahoe-LAFS install, to isolate it from any python packages that are already installed (and to isolate the rest of your system from Tahoe’s dependencies).

This example uses a virtualenv named venv, but you can call it anything you like. Many people prefer to keep all their virtualenvs in one place, like ~/.local/venvs/ or ~/venvs/.

It’s usually a good idea to upgrade the virtualenv’s pip and setuptools to their latest versions, with ``venv/bin/pip install -U pip setuptools``. Many operating systems have an older version of virtualenv, which then includes older versions of pip and setuptools. Upgrading is easy, and only affects the virtualenv: not the rest of your computer.

Then use the virtualenv’s pip to install the latest Tahoe-LAFS release from PyPI with ``venv/bin/pip install tahoe-lafs``. After installation, run ``venv/bin/tahoe --version`` to confirm the install was successful:

``virtualenv venv``
New python executable in ~/venv/bin/python2.7
Installing setuptools, pip, wheel...done.

``venv/bin/pip install -U pip setuptools``
Downloading/unpacking pip from https://pypi.python.org/...
...
Successfully installed pip setuptools

``venv/bin/pip install tahoe-lafs``
Collecting tahoe-lafs
...
Installing collected packages: ...
Successfully installed ...

``venv/bin/tahoe --version``
tahoe-lafs: 1.14.0
foolscap: ...
