# Network analysis of email sender and recipient domains

## Proposed idea

Make a network visualization of email sender and recipient domains in the Shell papers using [VOSViewer](https://www.vosviewer.com/). This could be an alternative way to identify clusters within the email correspondence, complementing a keyword-based clustering approach. 

## Data
The raw data is available on the [FTM repository](https://github.com/ftmnl/asr)

The script used for the basic-pre-processing can be found in the 
[asreview-ftm-hackathon/Example-for-data-pre-processing-track](https://github.com/asreview-ftm-hackathon/Example-for-data-pre-processing-track)
repository, and the pre-processed data is copied from this repository.

The copied pre-processed data can be found in the `data` folder, named `preprocessed_data.xlsx`.


## Processing data for visualization

Data are processed for visualization using the script in the R Markdown notebook `visualization_processing.Rmd` in the folder `scripts`.  
Required R packages are: `readxl`, `tidytext` and `tidyverse`, which can be installed using the function `install.packages("package-name")`.

Preprocessing is done as follows:

*Identifying email domains*

1. Filter all records of type "Mail"
2. Split the record content (column Abstract) into individual lines (using tokenization)
3. Filter on lines likely containing email addresses (i.e. containing @ and/or "to:" / "from:" / "aan:" / "van:")
4. Split lines into words (using tokenization). NB This automatically gets rid of email prefixes by removing "@"
5. Filter on strings containing one period (.) to identify likely email domains
6. Filter on actual email domains by matching to the [IANA list op top-level domains](https://data.iana.org/TLD/tlds-alpha-by-domain.txt)

*Formatting for visualization*

[...]


## Network visualization

## Result 

## Ideas for future improvement

- further clean email domains (harmonize OCR errors) 
- distinguish from/to to create directional network (but: issue with data quality)
- use date informtation to create time lapse visualization

## Applicability to larger dataset 
In principle, the method can be directly applied to a larger dataset (when preprocessing is done similar to the sample dataset). For a clear visualization, the cut-off value for which domains to include will need to be increased.  