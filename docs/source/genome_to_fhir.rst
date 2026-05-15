Genome-to-FHIR
==============


GTF-to-FHIR
~~~~~~~~~~~

In this functionality, the gene marker data is read from the GTF files and ingested in to the FHIR server.

The root tag for this functionality is ``run_config_gtf_to_fhir`` in the configuration file.

There can be multiple configuration blocks under the parent tag. An outline of a configuration block for migrating GTF file is given below;

.. code-block:: json

    ## Migrating ``GTF`` files
    {
        'type': 'migrate',
        'index_file': '<Index File Path>',
        'jsonTemplatePath': '<FHIR Reource JSON Template File Path>',
        'save': <True/False>,
        'savePath': '<Save Path>',
    },

Please refer the table below for information on the configuration fields.

+----------------------+------------------------------------------------------------------------------------------------------------------------------+
| Configuration Field  | Field Details                                                                                                                |
+======================+==============================================================================================================================+
| type                 | Type of operation performed (``migrate`` for migration configuration)                                                        |
+----------------------+------------------------------------------------------------------------------------------------------------------------------+
| index_file           | Path to the index file (csv) containing ``specimen_id``, ``person_id``, ``episode_id``, ``annotation_file (GTF File)``       |
+----------------------+------------------------------------------------------------------------------------------------------------------------------+
| jsonTemplatePath     | Path to the file containing FHIR resource JSON template                                                                      |
+----------------------+------------------------------------------------------------------------------------------------------------------------------+
| save                 | A Boolean value indicating if the intermediate files data needs to be saved to a directory (<``True/False``>)                |
+----------------------+------------------------------------------------------------------------------------------------------------------------------+
| savePath             | Path to the directory where the intermediate files are saved                                                                 |
+----------------------+------------------------------------------------------------------------------------------------------------------------------+


An example configuration block for ``migrate`` functionality is given below;

.. code-block:: json

    # Migrating "patient" entity
    {
        'type': 'migrate',
        'index_file': os.environ['GENOMIC_DATA_LOCATION'] + '/index.csv',
        'jsonTemplatePath': os.environ['GENOMIC_DATA_LOCATION'] + '/templates/Measurement.json',
        'save': True,
        'savePath': os.environ['INTERMEDIATE_DATA_LOCATION'] + '/data/gtf_to_fhir/measurement',
    },

.. note::

   In this functionality, the gene markers present in the GTF file are read and perisisted in the FHIR resource as provided in the ``jsonTemplatePath``. In this example. we are using ``Measurement`` FHIR resource for representing the gene markers, but the utility offers flexibility to persist this information in any desired FHIR resource.

FASTA-to-FHIR
~~~~~~~~~~~~~

In this functionality, the data is read from the FASTA files and ingested in to the FHIR server.

.. note::

   FASTA file is a custom format designed to represent the tokensised genomic sequences that are obtained using LLM models.

The root tag for this functionality is ``run_config_fasta_to_fhir`` in the configuration file.

There can be multiple configuration blocks under the parent tag. An outline of a configuration block for migrating FASTA file is given below;

.. code-block:: json

    ## Migrating ``FASTA`` files
    {
        'type': 'migrate',
        'index_file': '<Index File Path>',
        'jsonTemplatePath': '<FHIR Reource JSON Template File Path>',
        'save': <True/False>,
        'savePath': '<Save Path>',
    },

Please refer the table below for information on the configuration fields.

+----------------------+------------------------------------------------------------------------------------------------------------------------------+
| Configuration Field  | Field Details                                                                                                                |
+======================+==============================================================================================================================+
| type                 | Type of operation performed (``migrate`` for migration configuration)                                                        |
+----------------------+------------------------------------------------------------------------------------------------------------------------------+
| index_file           | Path to the index file (csv) containing ``specimen_id``, ``person_id``, ``episode_id``, ``annotation_file (GTF File)``       |
+----------------------+------------------------------------------------------------------------------------------------------------------------------+
| jsonTemplatePath     | Path to the file containing FHIR resource JSON template                                                                      |
+----------------------+------------------------------------------------------------------------------------------------------------------------------+
| save                 | A Boolean value indicating if the intermediate files data needs to be saved to a directory (<``True/False``>)                |
+----------------------+------------------------------------------------------------------------------------------------------------------------------+
| savePath             | Path to the directory where the intermediate files are saved                                                                 |
+----------------------+------------------------------------------------------------------------------------------------------------------------------+


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

   In this functionality, the FASTA file is read and perisisted in the FHIR resource as provided in the ``jsonTemplatePath``. In this example. we are using ``MolecularSequence`` FHIR resource for representing the FASTA file, but the utility offers flexibility to persist this information in any desired FHIR resource.

