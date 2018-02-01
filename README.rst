EpiCom - an Epilepsy comorbidity analysis using the overlapping genes in the literature
=======================================================================================

This repository contains code and resources used for the analysis described in Hoyt et al., 2018.

Structure of the project
------------------------

1. The resources and results folders contains all documents retrieved from SCAView queries as well as the tables and supplementary information presented in the paper

2. Notebooks: 

  - 'Epilepsy SCAIView comordbity analysis' outlines the calculations of pleitropy rates using the resources in the repository.
  - 'Epilepsy Knowledge Assembly Summary' contains the summary of the different subgraphs used to generate Table 2 of the manuscript.
  - 'Mechanism Enrichment Score Percentile Calculation' describes the statistical calculations for chosen a threshold based on  enrichment scores 

Quantification of Gene Overlap
------------------------------
This header corresponds to the first header in the methodology section of the paper. It uses screenshots as a guide to reproduce the analysis.

Step 1
~~~~~~
Build a query using `SCAIView Query Interface <http://academia.scaiview.com/academia/>`_ the MeSH entry for Epilepsy and the target disease. In this example, "Migrane Disorders" is used. Select "Human Genes/Proteins" from the dropdown labeled "Show Results in:" in order to get the overlapping genes sorted by relevance (relative entropy).

.. image:: https://raw.githubusercontent.com/cthoyt/EpiCom/master/screenshots/step1.png
        :alt: Step 1: How to Make a Query
        :width: 100%
        :align: center
			
Step 2
~~~~~~
From the list of genes/proteins, the click the export tab to be given options on how to export the gene list and their associated information for programmatic use.
		
.. image:: https://raw.githubusercontent.com/cthoyt/EpiCom/master/screenshots/step2.png
        :alt: Step 2: Display of Results
        :width: 100%
        :align: center
		
Step 3
~~~~~~
Click "Export Full Entity Table" in order to retrieve the genes/proteins, their relative entropies, their associated documents, and other useful information.
	
.. image:: https://raw.githubusercontent.com/cthoyt/EpiCom/master/screenshots/step3.png
        :alt: Step 1: Export Results
        :width: 100%
        :align: center

Step 4
~~~~~~
Steps 1-3 are repeated for several target diseases and stored in the `results <https://github.com/cthoyt/EpiCom/tree/master/resources>`_ folder in this repository

Step 5
~~~~~~
Clone this repository from GitHub with ``git clone https://github.com/cthoyt/EpiCom.git`` and ``cd`` into the directory. The Jupyter notebook included in this repostory, `Epilepsy SCAIView Comorbidity Analysis <https://github.com/cthoyt/EpiCom/blob/master/Epilepsy%20SCAIView%20Comorbidity%20Analysis.ipynb>`_, can be run from inside ``jupyter notebook`` in order to reproduce the analysis.