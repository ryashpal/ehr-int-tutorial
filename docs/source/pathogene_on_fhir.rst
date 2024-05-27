Pathogene On FHIR
=================

Installation
++++++++++++

Follow the below steps to install Pathogene-On-FHIR in your computer.


Login
------

Upon login to a system and opening a terminal, the following prompt should appear, where the ``user`` is the user name and the ``hostname`` is the hostname of the system.

.. code-block:: console

   user@hostname:~$


Change directory
----------------

From the home directory which will be open by default, change to a suitable directory on your computer where the utility needs to be installed. For example, in this tutorial we have changed to ``workspace`` directory.

.. code-block:: console

   user@hostname:~$ cd workspace


Clone
-----

In a destination folder, clone current version of the Pathogene-On-FHIR repository from the GitHub.

.. code-block:: console

   user@hostname:~/workspace$ git clone https://github.com/ryashpal/EHR-Genomics.git


Open Pathogene-On-FHIR
----------------------

Open the Pathogene-On-FHIR directory that is downloaded from GitHub after cloning.

.. code-block:: console

   user@hostname:~/workspace$ cd Pathogene-On-FHIR


Create Python virtual environment
---------------------------------

The Python virtual environment encaptulates all the libraries required for the Pathogene-On-FHIR. All the necessary libraries listed in a requirements.txt file that can be found at the root of the repository. Below are the instructions to create and install dependancies in the Python virtual environment.

.. note::
   Pathogene-On-FHIR requires Python version 3.9 or higher. For installing Python, please refer the below link: https://www.python.org/downloads/


Create virtual environment
~~~~~~~~~~~~~~~~~~~~~~~~~~

Inside the Pathogene-On-FHIR directory, create a new Python virtual enviroment to conveniently manage all the dependencies required for the utility.

.. code-block:: console

   user@hostname:~/workspace/Pathogene-On-FHIR$ python3 -m venv .venv


Activate virtual environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After creating the Python virtual enviroment, activate the virtual enviroment to start using it for subsequent commands. The prompt will change with ``(.venv)`` appearing in front of it as shown below;

.. code-block:: console

   user@hostname:~/workspace/Pathogene-On-FHIR$ source .venv/bin/activate
   (.venv) user@hostname:~/workspace/Pathogene-On-FHIR$


Install dependencies
~~~~~~~~~~~~~~~~~~~~

Install all the required dependencies listed in the requirements.txt file in the newly created Python virtual environment.

.. code-block:: console

   (.venv) user@hostname:~/workspace/Pathogene-On-FHIR$ pip install -r requirements.txt


Verify
------

Verify the installation by running the following command. The expected output should contain ``Pathogene-On-FHIR <version number>``.

.. code-block:: console

   (.venv) user@hostname:~/workspace/Pathogene-On-FHIR$ python -m Pathogene-On-FHIR -v
   Pathogene-On-FHIR 1.0

Run
+++

Use the below command to run the Pathogene-On-FHIR utility. This will run the utility according to the instructions provided in the configuration file.

.. code-block:: console

   (.venv) user@hostname:~/workspace/Pathogene-On-FHIR$ python src/Run.py

