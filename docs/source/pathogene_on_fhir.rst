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

For instructions on seting up configuration files, please refer to this `link https://ehr-int-tutorial.readthedocs.io/en/latest/pathogene_on_fhir.html#run-config`_

.. code-block:: console

   (.venv) user@hostname:~/workspace/Pathogene-On-FHIR$ python src/Run.py


Config
++++++

This utility uses two configuration files

* App Config
* Run Config

App Config
----------

The App Config file contains app level customisations including FHIR server and database server details;

FHIR Server Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~

The following FHIR server connection details needs to be updated in the configuration file to perfrm CRUD operations on the FHIR resources;

.. code-block:: json

    fhir_server_base_url: '<FHIR Server Base URL>'

Database Server Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following database server connection details needs to be updated in the configuration file to perform CRUD operations on the OMOP-CDM standard schema;

.. code-block:: json

    # database connection details
    db_details = {
        "sql_host_name": '<Host Name>',
        "sql_port_number": '<Port Number>',
        "sql_user_name": '<User Name>',
        "sql_password": '<Password>',
        "sql_db_name": '<DB Name>',
    }

Run Config
----------

The Run Config file contains step-by-step instructions on how to run this application.

It can perform 4 different functionalities;

* OMOP-to-FHIR
* GTF-to-FHIR
* REMAP-to-FHIR
* FHIR-to-OMOP

OMOP-to-FHIR
~~~~~~~~~~~~

In this functionality, the data is read from the OMOP-CDM standard schema and ingested in to the FHIR server.

The root tag for this functionality is ``run_config_omop_to_fhir`` in the configuration file.

There can be multiple configuration blocks under the parent tag. An example of a configuration block for migrating patient entity is given below;

.. code-block:: json

    # Migrating ``patient`` entity
    {
        'entity': 'Patient',
        'type': 'migrate',
        'sqlFilePath': '<Extraction SQL File Path>',
        'jsonTemplatePath': '<FHIR Reource JSON Template File Path>',
        'json_sql_mapping': {
            '<SQL outout column name 1>': '<FHIR JSON tag name 1>',
            '<SQL outout column name 2>': '<FHIR JSON tag name 2>',
        },
        'readFromDb': <True/False>,
        'loadToFHIR': <True/False>,
        'save': <True/False>,
        'savePath': '<Save Path>',
    },

Please refer the table below for information on the configuration fields.

+----------------------+--------------------------------------------------------------------------------------------------------------+
| Configuration Field  | Field Details                                                                                                |
+======================+==============================================================================================================+
| entity               | Identifier string for the migrating entity                                                                   |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| type                 | Type of operation performed (``migrate`` for migration configuration)                                        |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| sqlFilePath          | Path to the file containing entity extraction SQL query                                                      |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| jsonTemplatePath     | Path to the file containing FHIR resource JSON template                                                      |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| json_sql_mapping     | Mapping SQL output columns to FHIR JSON tags                                                                 |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| readFromDb           | A Boolean value indicating if the data needs to be read from DB (<``True/False``>)                           |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| loadToFHIR           | A Boolean value indicating if the data needs to be persisted to FHIR (<``True/False``>)                      |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| save                 | A Boolean value indicating if the intermediate files data needs to be saved to a directory (<``True/False``>)|
+----------------------+--------------------------------------------------------------------------------------------------------------+
| savePath             | Path to the directory where the intermediate files are saved                                                 |
+----------------------+--------------------------------------------------------------------------------------------------------------+

.. note::
   To map sub-tags, you need to provide the complete path from the root tag down to the sub-tag you're interested in. This path is created by concatenating all the tags within the hierarchy, separated by a double pipe symbol (``||``).
   
   For example, imagine you have a hierarchy like this:
   
   ->Root Tag
   ->->Level 1 Tag 1
   ->->->Sub-tag A
   ->->->Sub-tag B
   ->->Level 1 Tag 2

   To map ``Sub-tag A`, you would provide the path: ``Root Tag||Level 1 Tag 1||Sub-tag A``

An example configuration block is given below;

.. code-block:: json

    # Migrating "patient" entity
    {
        'entity': 'Patient',
        'type': 'migrate',
        'sqlFilePath': os.environ['GENOMIC_DATA_LOCATION'] + '/templates/sql/Person.sql',
        'jsonTemplatePath': os.environ['GENOMIC_DATA_LOCATION'] + '/templates/fhir/Patient.json',
        'json_sql_mapping': {
            'id': 'id',
            'sex': 'gender',
            'patient_name': 'name||text',
        },
        'readFromDb': True,
        'loadToFHIR': True,
        'save': True,
        'savePath': os.environ['INTERMEDIATE_DATA_LOCATION'] + '/data/omop_to_fhir/patient',
    },

.. note::

   As part of the codebase, we provided the FHIR resource templates for some commonly used resources including Organization, Patient, Encounter, Observation, and RiskAssessment resources. Additionally, we also provided the extraction logic (SQL query files) for these resources from the standard OMOP-CDM schema. Futher, the pipeline provides the flexibility for the user to extract data from any schema and persist to any FHIR resource as they desire.


GTF-to-FHIR
~~~~~~~~~~~

In this functionality, the data is read from the GTF files and ingested in to the FHIR server.

The root tag for this functionality is ``run_config_gtf_to_fhir`` in the configuration file.

REMAP-to-FHIR
~~~~~~~~~~~~~

In this functionality, the data is read from the REMAP files and ingested in to the FHIR server.

The root tag for this functionality is ``run_config_remap_to_fhir`` in the configuration file.

FHIR-to-OMOP
~~~~~~~~~~~~

In this functionality, the data is read from the FHIR server and ingested in to the OMOP-CDM standard schema.

The root tag for this functionality is ``run_config_fhir_to_omop`` in the configuration file.

