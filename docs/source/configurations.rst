Configurations
++++++++++++++


This utility uses two configuration files

* App Config
* Run Config

App Config
----------

The App Config file contains app level customisations including FHIR server and database server details;

FHIR Server Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~

The following FHIR server connection details needs to be updated in the configuration file to perfrm CRUD operations on the FHIR resources. An outline of the configuration for specifying the FHIR server is given below;

.. code-block:: json

    fhir_server_base_url: '<FHIR Server Base URL>'

.. note::

   There are multiple test servers avaialble freely online to get started with. These servers are listed in this link: https://confluence.hl7.org/display/FHIR/Public+Test+Servers. You can use one of these servers if you do not have access for your own FHIR server.

An example configuration using one of the public FHIR server is given below;

.. code-block:: json

    fhir_server_base_url: 'https://hapi.fhir.org/baseR5/'

Here in this case, I have selected a public HAPI-FHIR R5 server.

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
* FHIR-to-OMOP
* GTF-to-FHIR
* FASTA-to-FHIR
