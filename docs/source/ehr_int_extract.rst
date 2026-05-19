EHR-Int-Extract
===============


The export functionality enables users to extract linked data from the FHIR server, providing a seamless interface for downstream applications. With this feature, Demographics, Measurements, Genomics, or all three of these entities can be exported as a data matrix. The exported data is formatted to ensure direct compatibility with other utilities, facilitating automated clinical outcome modelling.

1. **Export Demographics**
~~~~~~~~~~~~~~~~~~~~~~~~~~

Help menu
---------

To display the help menu of the EHR-Int-Extract demographic data extract utility.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m src.ehrgen.extract.ExtractDemographics -h

or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m src.ehrgen.extract.ExtractDemographics --help

Output

.. code-block:: console

    usage: ExtractDemographics.py [-h] [-n] [-lrs] [-hrs] [-fd] [-td] [-sp]

    src.ehrgen.extract.ExtractDemographics

    optional arguments:
    -h, --help                  Show this help message and exit
    -n, --name                  Patient name
    -lrs, --lower_risk_score    Specify the lower risk score cutoff value. By default: [-lrs=0]
    -hrs, --higher_risk_score   Specify the higher risk score cutoff value. By default: [-hrs=1]
    -fd, --from_date            From Date in the format [YYYY-MM-DD]
    -td, --to_date              To Date in the format [YYYY-MM-DD]
    -sp, --save_path            Path of the file to store the outputs


2. **Export Measurements**
~~~~~~~~~~~~~~~~~~~~~~~~~~


Help menu
---------

To display the help menu of the EHR-Int-Extract measurements data extract utility.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m src.ehrgen.extract.ExtractMeasurements -h

or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m src.ehrgen.extract.ExtractMeasurements --help

Output

.. code-block:: console

    usage: ExtractMeasurements.py [-h] [-n] [-lrs] [-hrs] [-fd] [-td] [-sp]

    src.ehrgen.extract.ExtractMeasurements

    optional arguments:
    -h, --help                  Show this help message and exit
    -n, --name                  Patient name
    -lrs, --lower_risk_score    Specify the lower risk score cutoff value. By default: [-lrs=0]
    -hrs, --higher_risk_score   Specify the higher risk score cutoff value. By default: [-hrs=1]
    -fd, --from_date            From Date in the format [YYYY-MM-DD]
    -td, --to_date              To Date in the format [YYYY-MM-DD]
    -sp, --save_path            Path of the file to store the outputs


3. **Export Genomics**
~~~~~~~~~~~~~~~~~~~~~~


Help menu
---------

To display the help menu of the EHR-Int-Extract genomics data extract utility.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m src.ehrgen.extract.ExtractGenomics -h

or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m src.ehrgen.extract.ExtractGenomics --help

Output

.. code-block:: console

    usage: ExtractGenomics.py [-h] [-n] [-lrs] [-hrs] [-fd] [-td] [-sp]

    src.ehrgen.extract.ExtracGenomics

    optional arguments:
    -h, --help                  Show this help message and exit
    -n, --name                  Patient name
    -lrs, --lower_risk_score    Specify the lower risk score cutoff value. By default: [-lrs=0]
    -hrs, --higher_risk_score   Specify the higher risk score cutoff value. By default: [-hrs=1]
    -fd, --from_date            From Date in the format [YYYY-MM-DD]
    -td, --to_date              To Date in the format [YYYY-MM-DD]
    -sp, --save_path            Path of the file to store the outputs

4. **Export Integrated Data**
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Help menu
---------

To display the help menu of the EHR-Int-Extract integrated data extract utility.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m src.ehrgen.extract.Extract -h

or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m src.ehrgen.extract.Extract --help

Output

.. code-block:: console

    usage: Extract.py [-h] [-n] [-lrs] [-hrs] [-fd] [-td] [-sp]

    src.ehrgen.extract.Extrac

    optional arguments:
    -h, --help                  Show this help message and exit
    -n, --name                  Patient name
    -lrs, --lower_risk_score    Specify the lower risk score cutoff value. By default: [-lrs=0]
    -hrs, --higher_risk_score   Specify the higher risk score cutoff value. By default: [-hrs=1]
    -fd, --from_date            From Date in the format [YYYY-MM-DD]
    -td, --to_date              To Date in the format [YYYY-MM-DD]
    -sp, --save_path            Path of the file to store the outputs

