EHR-Int
=======

EHR-Int aims to provide a more comprehensive understanding of disease progression by integrating Electronic Health Record (EHR) data with bacterial genomic sequencing data. This approach considers both the host's response (reflected in EHR data) and the characteristics of the pathogen itself (obtained through genomic sequencing). This integrated analysis has the potential to lead to more accurate and informative models for disease progression.

**High-Level Architecture**

The high-level architecture of EHR-Int is depicted below:

.. image:: images/ehr_int_architecture.png

EHR-Int is a modular system, consisting of four independent codebases:

1. **Pathogene on FHIR**: This module focuses on representing pathogen data using the FHIR (Fast Healthcare Interoperability Resources) standard.
2. **FHIR Genomics IG**: This module defines the specific implementation guide for representing genomic data within the FHIR framework.
3. **FHIR Genomics Test**: This module deals with the representation of genomic tests using FHIR resources.
4. **FHIR Genomics JS**: This module provides JavaScript libraries for working with FHIR-formatted genomic data.

.. note::

   The table with module details has been removed as it seems to contain placeholder content.

**Workflow**

The workflow diagram illustrating the interaction between these modules is depicted in the following image:

.. image:: images/ehr_int_workflow.png

.. note::

   This project is under active development.

.. topic:: Acknowledgements

   .. image:: images/monash.png
      :width: 20 %

   .. image:: images/alfred.png
      :width: 20 %

   .. image:: images/superbugai.png
      :width: 20 %

   .. image:: images/RMIT_University_Logo.png
      :width: 20 %

Contents
--------

.. toctree::
   :maxdepth: 1

   pathogene_on_fhir
   fhir_genomics_ig
   fhir_genomics_test
   fhir_genomics_js
