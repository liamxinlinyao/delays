# The history of publishing delays

Here, we explore the history of scientific publishing delays. The findings from the analysis are discussed in a blog post by Daniel Himmelstein and feature in *Nature News*.

Delays are calculated from publisher-deposited PubMed history dates. Only journal articles published between 1960 and 2015 are included. Specifically, two delay types are calculated:

+ **acceptance delay** — the number of days from receival to acceptance
+ **publication delay** — the number of days from acceptance to online publication

## Execution and notebooks

To re-execute the analysis, run the following notebooks in the following order:

1. [`eutilities.ipynb`](eutilities.ipynb) (python): Use PubMed's EUtility API to retrieve the list of relevant IDs using [ESearch](http://www.ncbi.nlm.nih.gov/books/NBK25499/#_chapter4_ESearch_) and article summaries using [ESummary](http://www.ncbi.nlm.nih.gov/books/NBK25499/#_chapter4_ESummary_). 
2. [`process-esummary.ipynb`](process-esummary.ipynb) (python): Extract history dates from the ESummary XML output.
3. [`extract-delays.ipynb`](extract-delays.ipynb) (R): Calculate acceptance and publications delays from the PubMed history dates.
4. [`process-nlm-catalog.ipynb`](process-nlm-catalog.ipynb) (python): Download and process the NLM Catalog which contains the journals indexed by PubMed.
5.  [`visualize-history.ipynb`](visualize-history.ipynb) (R): Plot historical delays and export several TSV summaries of the dataset.

## Datasets

The following data files are generated during execution:

1. [`pubmed-journals.tsv`](data/pubmed-journals.tsv): a dataframe of the NLM Catalog (journals in PubMed)
2. [`history-dates.tsv.bz2`](data/history-dates.tsv.bz2): a dataframe with all history dates extracted from the PubMed XML
3. [`delays.tsv.gz`](data/delays.tsv.gz): a dataframe of all acceptance and publication delays
4. [`journal-summaries.tsv`](data/journal-summaries.tsv): a dataframe of summarizing delays for each journal
5. [`yearly-summaries.tsv`](data/yearly-summaries.tsv): a dataframe of summarizing delays for each year
6. [`yearly-percentiles.tsv`](data/yearly-percentiles.tsv): a dataframe of delay percentiles for each year
7. [`slopes.tsv`](data/slopes.tsv): a dataframe journal-specific delay slopes (Δ days of delay per year)

The following data files are generated but ignored due to large file size from the repository:

1. `esearch_journal-articles_1960-2015.tsv.gz` with the list of relevant PubMed IDs
2. `download/esummary_journal-articles_1960-2015.xml.bz2` with the XML formatted output from the ESummary API queries
