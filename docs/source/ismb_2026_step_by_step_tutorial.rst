Step-by-step Guide
==================


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


Generate Synthetic EHR Data
+++++++++++++++++++++++++++

For this tutorial, we use synthetic data generated specifically to demonstrate the utility of the pipeline. Please execute the following notebook to generate the required synthetic dataset:

`Data Generation Notebook <https://gitlab.com/superbugai/pathogene-on-fhir/-/blob/main/src/init/generate_random_data.ipynb?ref_type=heads>`_


Import Synthetic Data to the Database
+++++++++++++++++++++++++++++++++++++

To import the generated synthetic EHR data into your PostgreSQL database, follow the step-by-step instructions provided in the guide below:

`Database Import Guide <https://gitlab.com/superbugai/pathogene-on-fhir/-/blob/main/src/init/import_generated_data.md?ref_type=heads>`_


Configuration
+++++++++++++

Finally, use the configuration file provided below to set up the workflow before running the utility:

`Workflow Configuration File <https://gitlab.com/superbugai/pathogene-on-fhir/-/blob/main/src/patfhir/config/RunConfig.py?ref_type=heads>`_

Harmonise
+++++++++

Use the below command to run the Pathogene-on-FHIR utility. This will create an harmonised EHR and genomic data representation by running the utility according to the instructions provided in the configuration file.

.. code-block:: console

   (.venv) user@hostname:~/workspace/Pathogene-on-FHIR$ python src/Run.py


Export
++++++

The export functionality enables users to extract harmonised data from the FHIR server, providing a seamless interface for downstream applications. With this feature a combined representation consisting of Demographics, Measurements, and Genomics can be obtained. The exported data is formatted to ensure direct compatibility with other utilities such as EHR-QC and EHR-ML, facilitating automated clinical outcome modelling.

.. code-block:: console

    (.venv) user@hostname:~/workspace/Pathogene-on-FHIR$python -m src.ehrgen.extract.Extract --sp <path_to_save>
