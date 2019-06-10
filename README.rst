EpiCom - a comorbidity analysis for Epilepsy
============================================
A gene-centric comorbidity analysis for Epilepsy using results from SCAIView.

This repository contains code and resources used for the two analyses described in [1]_

.. [1] Hoyt, C. T. and Domingo-Fernández, D., *et al.* (2018). `A systematic approach for identifying
       shared mechanisms in epilepsy and its comorbidities <https://doi.org/10.1093/database/bay050>`_. 
       Database, 2018(June), bay050.

Methodology
-----------
First, a comorbidity analysis was performed with a `literature-based approach <https://github.com/neurommsig-epilepsy/EpiCom#quantification-of-gene-overlap>`_ based on overlapping co-occurrence of genes with Epilepsy and other diseases. Second, comorbidity analysis was performed on a mechanistic level with a `comparative mechanistic enrichment <https://github.com/neurommsig-epilepsy/EpiCom#comparative-mechanism-enrichment>`_ approach based on a shared therapy, carbamazepime, between epilepsy and Alzheimer's disease.

Structure of the Project
------------------------
1. The resources and results folders contains all documents retrieved from SCAView queries as well as the tables and supplementary information presented in the paper
2. Notebooks
  - `Epilepsy SCAIView Comorbidity Analysis <https://github.com/neurommsig-epilepsy/EpiCom/blob/master/Epilepsy%20SCAIView%20Comorbidity%20Analysis.ipynb>`_ outlines the calculations of pleiotropy rates using the resources in the repository. See `below <https://github.com/neurommsig-epilepsy/EpiCom#quantification-of-gene-overlap>`_.
  - `Epidemiology vs. Literature-Based Comorbidity <https://github.com/neurommsig-epilepsy/EpiCom/blob/master/Epilepsy%20Corpora%20Overview.ipynb>`_ a comparison between epidemiological and literature/gene-based comorbidity analysis
  - `Epilepsy Corpora Overview <https://github.com/neurommsig-epilepsy/EpiCom/blob/master/Epilepsy%20Corpora%20Overview.ipynb>`_ gives a summary of the originally generate corpora compared to which articles were actually curated
  - `Epilepsy Knowledge Assembly Summary <https://github.com/neurommsig-epilepsy/EpiCom/blob/master/Epilepsy%20Knowledge%20Assembly%20Summary.ipynb>`_ contains the summary of the different subgraphs used to generate **Table 2** of the manuscript.
  - `Mechanism Enrichment Score Percentile Calculation <https://github.com/neurommsig-epilepsy/EpiCom/blob/master/Mechanism%20Enrichment%20Score%20Percentile%20Calculation.ipynb>`_ describes the statistical calculations for chosen a threshold based on enrichment scores
3. `carbamazepine_targets.txt <https://github.com/neurommsig-epilepsy/EpiCom/blob/master/carbamazepine_targets.txt>`_ contains the gene list of targets of carbamazepine corresponding to Supplementary Text S1.

Quantification of Gene Overlap
------------------------------
This section corresponds to the "Quantification of Gene Overlap" in the Methodology section of the paper. It uses screenshots as a guide to reproduce the analysis.

Step 1
~~~~~~
Build a query using `SCAIView Query Interface <http://academia.scaiview.com/academia/>`_ the MeSH entry for Epilepsy and the target disease. In this example, "Migraine Disorders" is used. Select "Human Genes/Proteins" from the dropdown labeled "Show Results in:" in order to get the overlapping genes sorted by relevance (relative entropy).

.. image:: https://raw.githubusercontent.com/neurommsig-epilepsy/EpiCom/master/screenshots/step1.png
        :alt: Step 1: How to Make a Query
        :width: 100%
        :align: center

Step 2
~~~~~~
From the list of genes/proteins, the click the export tab to be given options on how to export the gene list and their associated information for programmatic use.

.. image:: https://raw.githubusercontent.com/neurommsig-epilepsy/EpiCom/master/screenshots/step2.png
        :alt: Step 2: Display of Results
        :width: 100%
        :align: center

Step 3
~~~~~~
Click "Export Full Entity Table" in order to retrieve the genes/proteins, their relative entropies, their associated documents, and other useful information.

.. image:: https://raw.githubusercontent.com/neurommsig-epilepsy/EpiCom/master/screenshots/step3.png
        :alt: Step 1: Export Results
        :width: 100%
        :align: center

Step 4
~~~~~~
Repeat Steps 1-3 for several target diseases and stored in the `results <https://github.com/neurommsig-epilepsy/EpiCom/tree/master/resources>`_ folder in this repository.

Step 5
~~~~~~
Clone this repository from GitHub with ``git clone https://github.com/neurommsig-epilepsy/EpiCom.git`` and ``cd`` into the directory. The Jupyter notebook included in this repostory, `Epilepsy SCAIView Comorbidity Analysis <https://github.com/neurommsig-epilepsy/EpiCom/blob/master/Epilepsy%20SCAIView%20Comorbidity%20Analysis.ipynb>`_, can be run from inside ``jupyter notebook`` in order to reproduce the analysis.

Comparative Mechanism Enrichment
--------------------------------
This section corresponds to the "Epilepsy Mechanism Enrichment" and "Comparative Mechanism Enrichment" headings in the Results section. It uses screenshots as a guide to reproduce the analysis.

Step 1
~~~~~~
Submitted a query to `NeuroMMSig <http://neurommsig.scai.fraunhofer.de/>`_ with the `protein targets of carbamazepime <https://github.com/neurommsig-epilepsy/EpiCom/blob/master/genes.txt>`_ coming from `PharmKGB <https://www.pharmgkb.org/chemical/PA448785>`_ against epilepsy.

.. image:: https://raw.githubusercontent.com/neurommsig-epilepsy/EpiCom/master/screenshots/comparison-step1.png
        :alt: Step 1: Query Epilepsy
        :width: 100%
        :align: center

Step 2
~~~~~~
Save the NeuroMMSig enrichment scores with the "Download Excel" button.

.. image:: https://raw.githubusercontent.com/neurommsig-epilepsy/EpiCom/master/screenshots/comparison-step2.png
        :alt: Step 2: Download Results
        :width: 100%
        :align: center

Step 3
~~~~~~
Repeat steps 1-2 for the Alzheimer's disease. Run the Jupyter notebook, `Mechanism Enrichment Score Percentile Calculation <https://github.com/neurommsig-epilepsy/EpiCom/blob/master/Mechanism%20Enrichment%20Score%20Percentile%20Calculation.ipynb>`_, to identify an appropriate percentile cutoff for significant networks.

Step 4
~~~~~~
Perform enrichment with the combine context of Alzheimer's disease and epilepsy then choose all networks with enrichment scores above the cutoff.

.. image:: https://raw.githubusercontent.com/neurommsig-epilepsy/EpiCom/master/screenshots/comparison-step4.png
        :alt: Step 4: Query Combine Context
        :width: 100%
        :align: center

Step 5
~~~~~~
Use the visualization to explore and generate hypotheses.

.. image:: https://raw.githubusercontent.com/neurommsig-epilepsy/EpiCom/master/screenshots/comparison-step5.png
        :alt: Step 5: Generate Hypotheses
        :width: 100%
        :align: center
