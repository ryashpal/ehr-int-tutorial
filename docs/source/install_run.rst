Install and Run
===============


Install
+++++++

Follow the below steps to install Pathogene-on-FHIR in your computer.


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

In a destination folder, clone current version of the Pathogene-on-FHIR repository from the GitHub.

.. code-block:: console

   user@hostname:~/workspace$ git clone https://github.com/ryashpal/Pathogene-on-FHIR.git


Open Pathogene-on-FHIR
-----------------

Open the Pathogene-on-FHIR directory that is downloaded from GitHub after cloning.

.. code-block:: console

   user@hostname:~/workspace$ cd Pathogene-on-FHIR


Create Python virtual environment
---------------------------------

The Python virtual environment encaptulates all the libraries required for the Pathogene-on-FHIR. All the necessary libraries listed in a requirements.txt file that can be found at the root of the repository. Below are the instructions to create and install dependancies in the Python virtual environment.

.. note::
   Pathogene-on-FHIR requires Python version 3.9 or higher. For installing Python, please refer the below link: https://www.python.org/downloads/


Create virtual environment
~~~~~~~~~~~~~~~~~~~~~~~~~~

Inside the Pathogene-on-FHIR directory, create a new Python virtual enviroment to conveniently manage all the dependencies required for the utility.

.. code-block:: console

   user@hostname:~/workspace/Pathogene-on-FHIR$ python3 -m venv .venv


Activate virtual environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After creating the Python virtual enviroment, activate the virtual enviroment to start using it for subsequent commands. The prompt will change with ``(.venv)`` appearing in front of it as shown below;

.. code-block:: console

   user@hostname:~/workspace/Pathogene-on-FHIR$ source .venv/bin/activate
   (.venv) user@hostname:~/workspace/Pathogene-on-FHIR$


Install dependencies
~~~~~~~~~~~~~~~~~~~~

Install all the required dependencies listed in the requirements.txt file in the newly created Python virtual environment.

.. code-block:: console

   (.venv) user@hostname:~/workspace/Pathogene-on-FHIR$ pip install -r requirements.txt


Verify
------

Verify the installation by running the following command. The expected output should contain ``Pathogene-on-FHIR <version number>``.

.. code-block:: console

   (.venv) user@hostname:~/workspace/Pathogene-on-FHIR$ python -m Pathogene-on-FHIR -v
   Pathogene-on-FHIR 1.0

Run
+++

Use the below command to run the Pathogene-on-FHIR utility. This will run the utility according to the instructions provided in the configuration file.

For instructions on seting up configuration files, please refer to this `link https://ehr-int-tutorial.readthedocs.io/en/latest/configurations.html`_

.. code-block:: console

   (.venv) user@hostname:~/workspace/Pathogene-on-FHIR$ python src/Run.py
