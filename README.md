# Bioorthogonal non-canonical amino acid tagging reveals translationally active subpopulations of the cystic fibrosis lung microbiota
Talia D. Valentini, Sarah K. Lucas, Kelsey A. Binder, Lydia C. Cameron, Jason A. Motl, Jordan M. Dunitz, Ryan C. Hunter

**Abstract**
Culture-independent studies of cystic fibrosis lung microbiota have provided few mechanistic insights into the polymicrobial basis of disease. Deciphering the specific contributions of individual taxa to CF pathogenesis requires comprehensive understanding of their in situ ecophysiology. To test our hypothesis that only a subset of CF microbiota are actively growing in vivo, we applied bioorthogonal non-canonical amino acid tagging (BONCAT) to visualize and quantify translational activity. We report that the percentage of BONCAT-labeled (i.e. active) bacterial cells varies substantially between patients (6-56%). We also used flow cytometry and genomic sequencing to assign taxonomy to BONCAT-labeled cells. While many abundant taxa are indeed “active”, most bacteria detected by conventional molecular profiling also comprise a dormant subpopulation suggesting a heterogeneous growth rates in situ. Differentiating translationally active subpopulations adds to our evolving understanding of CF lung disease and may help guide therapies targeting bacteria most likely to be susceptible to antibiotics.

## Sequence File Availibility
Please download sequence files associated with BioProject: PRJNA604587
https://www.ncbi.nlm.nih.gov/bioproject/PRJNA604587/

## System Requirements
At the time of submission, this code was written with tools and dependencies that were operational on macOS Catalina 10.15.3. Session info including package versions is reported at the end of each R notebook. The development of this code was done using R (v. 3.6.2). The R Notebooks are written in Rmarkdown, which includes R code chunks and is best run in RStudio. The code was developed using RStudio (v. 1.2.1335).

## Prerequisites
**For sequence trimming and filtering**  
Running the BONCAT_Cutadapt script requires the cutadapt command. Here cutadapt was installed as a conda package in miiconda3. Installation instructions can be found here: https://cutadapt.readthedocs.io/en/stable/installation.html  

**DADA2 formatted SILVA-132 taxonomy reference files**  
The DADA2 formatted Taxonomy training sets used in this publication are provided in "../data/DADA2/taxonomyTrainingSets".  
  
DADA2 formatted Taxonomy training sets are available to download through this link:https://benjjneb.github.io/dada2/training.html  
  
The original source of the downloads is here:https://zenodo.org/record/1172783

## Order of implementation (apprx. 2 hours)
1. Clone this repository to your local computer.
2. Download sequences from the SRA database to a folder in this location "../data/fastq/fastq_JAN2020"
3. Run through the BONCAT_Cutadapt.Rmd notebook
    * This will require making the "cutadapt" directory in figures for the final quality plots.
4. Run through the BONCAT_DADA2.Rmd notebook
    * This will produce the count table, taxonomy table, and phylogenetic tree. Depending on computing resources, this is the notebook that will take the longest to run.
4. Run through the BONCAT_Decontam_2020.Rmd notebook
    * This will produce a create a phyloseq object, use the Decontam package to identify contaminating reads in the DNA extraction control, and filter them from the dataset. It will result in the "../data/decontam/ps-decontam_prev5.RData" file.
5. Run through the BONCAT_Phyloseq_JAN2020.Rmd notebook
    * This notebook contains all the analysis for the production of figures displaying microbiome data in the manuscript.
