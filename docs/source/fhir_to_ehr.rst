FHIR-to-EHR
===========


FHIR-to-OMOP
~~~~~~~~~~~~

In this functionality, the data is read from the FHIR server and ingested in to the OMOP-CDM standard schema.

The root tag for this functionality is ``run_config_fhir_to_omop`` in the configuration file.

There can be multiple configuration blocks under the parent tag. An outline of a configuration block for migrating FHIR data to OMOP-CDM standard schema is given below;

.. code-block:: json

    # Migrating ``Patient`` entity
    {
        'entity':'Patient',
        'type': 'migrate',
        'urlQueryStringPath':'<Extraction URL Query String File Path>',
        'sqlFilePath':'<Insert SQL query file Path>',
        'sql_json_mapping': {
            '<FHIR JSON tag name 1>': '<SQL outout column name 1>',
            '<FHIR JSON tag name 2>': '<SQL outout column name 2>',
        }
    },

Please refer the table below for information on the configuration fields.

+----------------------+--------------------------------------------------------------------------------------------------------------+
| Configuration Field  | Field Details                                                                                                |
+======================+==============================================================================================================+
| entity               | Identifier string for the migrating entity                                                                   |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| type                 | Type of operation performed (``migrate`` for migration configuration)                                        |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| urlQueryStringPath   | Path to the file containing FHIR resource extraction Query String URL                                        |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| sqlFilePath          | Path to the file containing entity insertion query                                                           |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| sql_json_mapping     | Mapping FHIR JSON tags to SQL output columns                                                                 |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| readFromFHIR         | A Boolean value indicating if the data needs to be read from FHIR (<``True/False``>)                         |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| loadToDB             | A Boolean value indicating if the data needs to be persisted to DB (<``True/False``>)                        |
+----------------------+--------------------------------------------------------------------------------------------------------------+
| save                 | A Boolean value indicating if the intermediate files data needs to be saved to a directory (<``True/False``>)|
+----------------------+--------------------------------------------------------------------------------------------------------------+
| savePath             | Path to the directory where the intermediate files are saved                                                 |
+----------------------+--------------------------------------------------------------------------------------------------------------+

An example configuration block for ``migrate`` functionality is given below;

.. code-block:: json

    # Migrating "patient" entity
    {
        'type': 'migrate',
        'index_file': os.environ['GENOMIC_DATA_LOCATION'] + '/index.csv',
        'jsonTemplatePath': os.environ['GENOMIC_DATA_LOCATION'] + '/templates/MolecularSequence.json',
        'save': True,
        'savePath': os.environ['INTERMEDIATE_DATA_LOCATION'] + '/data/gtf_to_fhir/molecular_sequence',
    },

.. note::

   To map sub-tags, you need to provide the complete path from the root tag down to the sub-tag you're interested in. This path is created by concatenating all the tags within the hierarchy, separated by a double pipe symbol (``||``).
   
   For example, imagine you have a hierarchy like this:
   
   Root Tag

      Level 1 Tag 1

         Sub-tag A

         Sub-tag B

      Level 1 Tag 2

   To map ``Sub-tag A``, you would provide the path: ``Root Tag||Level 1 Tag 1||Sub-tag A``

An example configuration block for ``migrate`` functionality is given below;

.. code-block:: json

    # Migrating "patient" entity
    {
        'entity':'Observation',
        'type': 'migrate',
        'urlQueryStringPath': os.environ['GENOMIC_DATA_LOCATION'] + '/templates/fhir/Patient.json',
        'sqlFilePath': os.environ['GENOMIC_DATA_LOCATION'] + '/templates/sql/insert/Person.sql',
        'sql_json_mapping': {
            'id': 'id',
            'value_as_number': 'valueQuantity||value',
            'measurement_concept_id': 'code||coding||0||code',
            'unit_concept_id': 'valueQuantity||unit',
            'person_id': 'subject||reference',
            'visit_occurrence_id': 'encounter||reference',
            'measurement_datetime': 'effectiveDateTime',
        }
    },

.. note::

   As part of the codebase, we provided the FHIR resource templates for some commonly used resources including Organization, Patient, Encounter, Observation, and RiskAssessment resources. Additionally, we also provided the insertion logic (SQL query files) to persist these resources in the standard OMOP-CDM schema. Futher, the pipeline provides the flexibility for the user to extract data from FHIR resource and persist to any OMOP-CDM entity as they desire.

