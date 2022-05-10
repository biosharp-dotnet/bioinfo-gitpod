# Trimming pipeline

In this session we will design our first bash pipeline script and understand the results of running `fastp` on the quality of `FASTQ` files.

## 1. Pre-trimming QC analysis


### 1.1 Setup conda in bash


**NOTE**: Before starting this exercise, please close all default terminals on Gitpod and then start a new terminal.


Please run the following commands on the shell 


```bash
conda init bash 

exec $SHELL
```


### 1.2 Download the relevant datasets 


```
wget ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR598/001/ERR5987181/ERR5987181_1.fastq.gz


wget ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR598/001/ERR5987181/ERR5987181_2.fastq.gz

```


### 1.3 Create a `qc-env` using `conda`

For this exercise, please refer to the content covered as part of `LearningCommandLine_2`


### 1.4 Generate the `fastqc` report for these samples


For this exercise, please refer to the content covered as part of `LearningCommandLine_2`


## 2. Post-trimming QC analysis

### 2.1 Create a `fastp-env` using `conda`


```bash
conda create --name fastp-env bioconda::trimmomatic
```


### 2.2 Run fastp on the downloaded samples

```bash

fastp -i ERR5987181_1.fastq.gz  -o ERR5987181_1.trimmed.fastq.gz 

```

### 2.3 Generate the `fastqc` report for these `trimmed` samples


For this exercise, please refer to the content covered as part of `LearningCommandLine_2`



## 3. Compare the QC results of pre/post trimming analysis using `multiqc`


```
multiqc ./
```

### 3.1 Run a web server using Python to visualize HTML files

```bash
python -m http.server 8000
```

You should see a notification on the bottom-left of the screen for this PORT, `A service is available on port 8000`, click on `Open Browser` and then select the `html` files.

**If you do NOT** see that notification, please navigate to another tab in your browser add `8000` to the beginning of your Gitpod URL, for example `8000-biosharpdotn-tdrcgitpod-ehsr91d5nlc.ws-eu43.gitpod.io/`
