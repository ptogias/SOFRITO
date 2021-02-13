<h1 align="center">
  <img src="logo/sofrito_logo.png" alt="SOFRITO Logo" />
</h1>
<h2 align="center">
  <img alt="Biomedical Concept Annotations Retrieval" src="logo/sofrito_sublogo.png">
</h2>

###### Panagiotis Togias, Maria-Theodora Pandi


<div align="center">

<a href="#patched-fonts" title="">
  <img alt="Website" src="https://img.shields.io/badge/website-up-brightgreen">
  </a>
  
  <a href="#patched-fonts" title="">
  <img alt="Website" src="https://img.shields.io/badge/R-4.0.0-informational">
  </a>
  
  <a href="#patched-fonts" title="">
  <img alt="Website" src="https://img.shields.io/badge/licence-GPL-informational">
  </a>

</div>

***Due to shinyapps.io free licence limitations, SOFRITO cannot be available for multiple users at once. A session from one user must first end for another to start. Also, there is a limit of usage time per month. (Sorry...)***

### Project description

SOFRITO is a freely available tool, created to assist text mining efforts of biomedical literature. Some of the most common steps of such a project include corpus creation, entity extraction and normalization, retrieval of sentences (or other parts of a larger text) and finally, text classification with the purpose of discovering associations between specific entities of interest.

<h1 align="center">
  <img src="sofrito.png" alt="SOFRITO chart" />
</h1>


### SOFRITO is designed to offer:

* Extraction of biomedical concept annotations found in articles (titles & abstracts or full text papers) that correspond to a specific PubMed query, as provided by [PubTator Central (PTC)]( https://www.ncbi.nlm.nih.gov/research/pubtator/)**
This query can either be a general one, or more specific, as described in [PubMed’s instructions](https://pubmed.ncbi.nlm.nih.gov/help/).  PTC performs concept annotation of the collected literature for the following biological entities: genes/proteins, genetic variants, diseases, chemicals, species, cell lines, and provides access to those annotations either through its’ webpage, or programmatically. Retrieving annotations from papers according to their PMID (PubMed ID) is an easy task for someone with small or none programming skills (through PTC’s webpage, PTC’s RESTful API or through the [pubmed.mineR library](https://cran.r-project.org/web/packages/pubmed.mineR/index.html)). However, those annotations are limited on entities found on the Title and Abstract only, even if the entire text of the article is available and has been annotated by PTC. In order to extract annotations from the entire text, an article must be accompanied by a PMCID (ID to U.S. National Institutes of Health's National Library of Medicine (NIH/NLM) free full-text archive of biomedical and life sciences journal literature). Sofrito, uses pubmed.mineR library to collect the PMIDs of articles that correspond to a user defined query and converts those PMIDs to their corresponding PMCIDs (if available) by programmatically accessing [NCBI’s ID convertor](https://www.ncbi.nlm.nih.gov/pmc/pmctopmid/). Consequently, PTC’s annotations of the articles of interest are retrieved in BiocJSON format and after thorough processing are converted in a more easily manageable format. Finally, the annotations can be downloaded by Sofrito’s end user as a comma separated file (.csv), ready for further analysis. 

* Star Allele identification**
 PTC’s Mutation extraction tool, despite its’ overall utility, cannot identify Star Alleles, while those entities are misclassified as Genes. Although Star Alleles might not always be present in articles retrieved from a general query, in certain cases, especially when the query is related to Pharmacogenomics or Pharmacogenetics or Precision Medicine, it is important to tackle this issue and identify the Gene entities that, in reality, correspond to Star Alleles.

* Identification of sentences that contain at least two co-occurring entities**
(e.g., someone might be interested in finding all the sentences where at least a Gene and at least a Mutation are mentioned). The end user has the option to choose two from the following biomedical concepts: Genes, Diseases, Chemicals, Mutations (including Star Alleles – if present), Species and Cell Lines and get a second (.csv) file containing the corresponding sentences. In the case when no entities are chosen, only one file with the annotations for each article is provided, while when either one (or both) of the chosen entities are not identified in the corpus or no sentence containing both entities is found Sofrito provides two files, one with the annotations, and one with the error encountered. 

The data extracted from SOFRITO can be further processed, analyzed, and get easily incorporated in a text mining project, just like in this amazing article where potential pharmacogenomic associations (among Variants are Chemicals) are detected.

****Note:* Until now, the best way of illustrating data outside of a compiler is through excel's *Get & Transform Data* option. We are trying to fix this so data downloaded from SOFRITO are ready to be imported into a common excel file through its *Text to Columns* option.***

Import data from a .csv file into an existing worksheet:<br>
 *  On the Data tab, in the Get & Transform Data group, click From Text/CSV.
 *  In the Import Data dialog box, locate and double-click the text file that you want to import, and click Import.

### To-do List

* Fix .csv format so that files can be parsed automatically in an excel file through excel's 'Text to columns' option.
* Add a 'Stop' button for cases that a user wants to end the process prematurely. -No ability for parallel running functions in R.

### Support
For questions, reach out to either one of the maintainers

* *Panagiotis Togias*<br>
ptogias at outlook.com

* *Maria-Theodora Pandi*<br>
pandimaria17 at gmail.com


### References
* Pandi M-T, van der Spek PJ, Koromina M and Patrinos GP. A Novel Text-Mining Approach for Retrieving Pharmacogenomics Associations From the Literature. Frontiers in Pharmacology. 2020;11:602030. doi:10.3389/fphar.2020.602030

* Wei CH, Allot A, Leaman R, Lu Z. PubTator central: automated concept annotation for biomedical full text articles. Nucleic Acids Res. 2019;47(W1):W587-W593. doi:10.1093/nar/gkz389

* Wei CH, Kao HY, Lu Z. PubTator: a web-based text mining tool for assisting biocuration. Nucleic Acids Res. 2013;41(Web Server issue):W518-W522. doi:10.1093/nar/gkt441

* Wei CH, Leaman R, Lu Z. Beyond accuracy: creating interoperable and scalable text-mining web services. Bioinformatics. 2016;32(12):1907-1910. doi:10.1093/bioinformatics/btv760

* Comeau DC, Wei CH, Islamaj Doğan R, Lu Z. PMC text mining subset in BioC: about three million full-text articles and growing. Bioinformatics. 2019;35(18):3533-3535. doi:10.1093/bioinformatics/btz070

* Rani J, Shah AB, Ramachandran S. pubmed.mineR: an R package with text-mining algorithms to analyse PubMed abstracts. J Biosci. 2015;40(4):671-682. doi:10.1007/s12038-015-9552-2
