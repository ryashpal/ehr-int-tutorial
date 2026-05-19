===========
EHR-Int-Viz
===========

To facilitate the utilisation of integrated data representation, we developed several functionalities as part of the EHR-Int-Viz module.

1. **Search Function**
~~~~~~~~~~~~~~~~~~~~~~

   Developed to facilitate the retrieval of records from a FHIR server based on specified criteria.

   .. image:: images/ehr_int_viz_search.png
      :alt: EHR-Int-Viz Search Interface
      :align: center

2. **Visualisation**
~~~~~~~~~~~~~~~~~~~~

   The resulting records are visualised at both the individual and group level.

   * **Individual Visualisations:**

     * *Summary Plot:* Offering a high-level overview.

        .. image:: images/ehr_int_viz_summary.png
            :alt: EHR-Int-Viz Summary Plot
            :align: center

     * *Detailed Plots:* For much finer granularity.

        .. image:: images/ehr_int_viz_details.png
            :alt: EHR-Int-Viz Details Plot
            :align: center


   * **Group-Level Plots:**

     Provide visualisations of the integrated data for all records matching the search criteria. These plots are categorised into:

     * *AMR Summary*

        .. image:: images/ehr_int_viz_amr_summary.png
            :alt: EHR-Int-Viz AMR Summary Plot
            :align: center

     * *FASTA Summary*

        .. image:: images/ehr_int_viz_fasta_summary.png
            :alt: EHR-Int-Viz FASTA Summary Plot
            :align: center

     * *Token Summary*

        .. image:: images/ehr_int_viz_token_summary.png
            :alt: EHR-Int-Viz Token Summary Plot
            :align: center


3. **Export Function**
~~~~~~~~~~~~~~~~~~~~~~
   
   The search results can be exported into flat files for downstream processing.


4. **Dashboard**
~~~~~~~~~~~~~~~~

    The utility offers interactive dashboards where users can control variables like risk score and admission date in real time to dynamically specify the data used for plotting.

    .. image:: images/ehr_int_viz_dashboard.png
        :alt: EHR-Int-Viz Dashboard
        :align: center
