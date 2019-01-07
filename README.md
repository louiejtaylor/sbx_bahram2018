# sbx_bahram2018
Sunbeam extension to reproduce key results from Bahram et al 2018 (PMID: 30069051)

## Background

This report uses the [Sunbeam pipeline](https://github.com/sunbeam-labs/sunbeam) to reproduce findings from "Structure and function of the global topsoil microbiome" [(PMID: 30069051)](https://www.ncbi.nlm.nih.gov/pubmed/30069051) by Bahram *et al*. A key finding of this paper is that bacterial diversity is highest in temperate habitats, but lower in extreme latitudes and near the equator. This extension tests whether we can reproduce this finding using Sunbeam and Kraken.

## Installing

Make sure you have Sunbeam installed--if not, [see the instructions here](https://sunbeam.readthedocs.io/en/latest/quickstart.html)

Clone the repo into your Sunbeam extensions directory, and install dependencies through Conda:

    source activate sunbeam
    cd $SUNBEAM_DIR/extensions
    git clone https://github.com/louiejtaylor/sbx_bahram2018
    conda install -c bioconda -c conda-forge --file sbx_bahram2018/requirements.txt

You'll want a Kraken database to query--see the [Kraken documentation](http://ccb.jhu.edu/software/kraken/MANUAL.html#kraken-databases) for database-building instructions if you don't already have one.

## Running

Since the Bahram 2018 data is available through NCBI SRA, all you need to do is pass the SRA project identifier to `sunbeam init`:

    sunbeam init Bahram2018 --data_acc ERP020652
    
And then run Sunbeam, specifying `bahram_report` as the target rule:

    sunbeam run --configfile Bahram2018 --cores 20 bahram_report
    
