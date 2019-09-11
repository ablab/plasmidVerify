# plasmidVerify: plasmid contig verification tool

plasmidVerify classifies contigs (output of metaplasmidSPAdes or other assemblers) as plasmidic or non-plasmidic, based on gene content. 


plasmidVerify predicts genes in the contig using Prodigal in the metagenomic mode, runs hmmsearch on the predicted proteins 
and classifies the contig as plasmidic or chromosomal by applying the Naive Bayes classifier (NBC). 
For the set of predicted HMMs, plasmidVerify uses trained NBC to classify this set to be plasmidic or chromosomal. 


## Installation

### Requirements

plasmidVerify is a Python script, thus, installation is not required. However, it has the following dependencies:

* Python 2.7+,
* Prodigal (https://github.com/hyattpd/Prodigal, available via conda),
* hmmsearch (from the hmmer package, http://hmmer.org/download.html),
* Pfam-A database (you can download recent release here: ftp://ftp.ebi.ac.uk/pub/databases/Pfam/releases/)

To work properly, plasmidVerify require Prodigal and hmmsearch in your PATH environment variable.


### Optional BLAST verification

You can verify your output by BLAST to check if you found novel plasmid. In this case, you need to have blastn in your $PATH, Biopython installed, and provide a path to the local copy of nt database. 

## Usage 

    ./plasmidverify.py 
            -f Input fasta file
            -o output_directory 
            --hmm HMM    Path to Pfam-A HMM database

            Optional arguments:
            -h, --help  Show the help message and exit
            --db DB     Run BLAST on input contigs against provided db


Output file: comma-separated table <input_file>_result_table.csv

Output format: contig name, prediction result, log-likelihood ratio, list of predicted HMMs
  
  
Please cite plasmidVeirfy as follows:  
Antipov, D., Raiko, M., Lapidus, A., & Pevzner, P. A. (2019). Plasmid detection and assembly in genomic and metagenomic data sets. *Genome Research*, 29(6), 961-968.
