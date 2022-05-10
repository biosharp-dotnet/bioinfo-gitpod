# TB-profiler
## Command line interface

[![N|Solid](https://raw.githubusercontent.com/jodyphelan/jodyphelan_github_io_old/master/img/tb-profiler-logo-rectangle.png)](https://github.com/jodyphelan/TBProfiler)



This tutorial will guide you to install TB-profiler in your GitPod environment and to determine *Mycobacterium tubrculosis* strain types and drug resistance profiles from WGS data using TB-profiler. 



## Installing TB-profiler in your GitPod environment
First we need to configure Conda with the required channels. Run the following commands in your terminal:

```bash
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
```
Next, we will create the Conda environment for TB-profiler
```bash
conda create --name tb-profiler tb-profiler
```
Follow the on screen prompts (Press "y" when asked whether you would like to proceed)

- Note that this process may take some time as all the TB-profiler dependencies (other programs and tools) will be downloaded

Once this process has finished, install TB-profiler using conda: 

```bash
conda install -c bioconda tb-profiler
```

The latest version of TB-profiler is now installed in your GitPod environment. However, you need to activate the Conda environment: 

```bash
conda activate tb-profiler
```

## Preparing to run TB-profiler
To get an overview of the usage information for tb-profiler, run: 

```bash
tb-profiler
```

To get information on how to run a specific tool within the TB-profiler pipeline, call TB-profiler, specify the tool, and use the `-h` argument to access the help page; 
(Of course you can also read the online documentation provided on the TB-profiler Github page)

For example, to see how the 'profile' tool of TB-profiler works, run: 

```bash
tb-profiler profile -h
```

Next, create a directory where you would like the TB-profiler output (results) to be stored: 
(you can give the directory/folder a different name)

```bash
mkdir my_TBP_output_directory
```

Change directories (move into) the directory that you have just created: 

```bash
cd my_TBP_output_directory
```
##### *Mycobacterium tuberculosis* WGS data to analyse


The rest of this tutorial assumes that you have downloaded 3 *Mycobacterium tuberculosis* genomes (raw WGS datasets) analysed in this publication (https://journals.asm.org/doi/full/10.1128/jcm.02362-21?rfr_dat=cr_pub++0pubmed&url_ver=Z39.88-2003&rfr_id=ori%3Arid%3Acrossref.org), the ENA study accession is: PRJEB45389 

You can run nf-core/fetchngs pipeline to download the FASTQ files of 3 samples with the following sample accession numbers: 

- ERX5627944	
- ERX5627009	
- ERX5627671	


**TIP**: 
1) Make a directory inside the 'datasets' directory where you will download the downloaded WGS data. 
2) Create a text file with a list of the sample accessions before running FetchNGS. You can use `nano`  or another CLI text editor to create a text file, or even use a combination of the `echo` and `cat` commands to create a text file using the `>` to save the output of your constructed code to a text file. 

### nf-core FetchNGS

Refer to the documentation of NextFlow FetchNGS: https://nf-co.re/fetchngs/1.5.
```sh
nextflow run nf-core/fetchngs --input accession_numbers.txt -profile docker
```




## Running TB-profiler on a single isolate

This command assumes that you have saved the downloaded *Mycobacterium tuberculosis* FASTQ files in a directory called mtb_fastqs within the datasets directory. FecthNGS will create additional directories where the results of the pipeline (and thus FASTQ files) are stored. 

```bash
tb-profiler profile -1 ./workspace/tdrc-gitpod/datasets/mtb_fastqs/results/fastq/ERX5627009_ERR5987184_1.fastq.gz -2 /workspace/tdrc-gitpod/datasets/mtb_fastqs/results/fastq/ERX5627009_ERR5987184_2.fastq.gz -p ERX5627009 -t 12 --txt
```

Refer to the TB-profiler manual for additional arguments. The arguments provided in this example include: 

- `-1` : Note that this uses the number 'one', not the letter "L", give the relative or absolute path to the forward reads (R1) of the isolate that you want to analyse
- `-2` : the relative or absolute path to the reverse reads of the isolate that you want to analyse with TB-profiler. If the isolate is sequenced single endedly and only one FASTQ file is available, leave out the -2 argument
- `-p` : prefix, this is the name of the output file and should correspond to the isolate ID
- `-t` : the number of threads to use on the server and translates to the computational resources that will be assigned to perform the task
- `--txt` : Note that this argument has two dashes. It specifies to include the results in a plain text format, as opposed to the default output in Jason format

Wait for the analysis to finish. Once it has completed, you can view the results files that were created by navigating to the appropriate output directories, using `ls` to view the contents of directories and using `less`, `cat`, `more`, `head`, or `tail`, to view the created output files. 

## Running TB-profiler on multiple isolates 

To run TB-profiler on multiple isolates, you can 1) create a bash script that lists the same command above for each sample that you wish to analyse, 2) use a more sophisticated method to run several analyses in parallel, or 3) use a for-loop to run TB-profiler on all FASTQ files in a specified directory. 

First, change directories to where you have downloaded the *mycobacterium tuberculosis* FASTQ files:
```bash
cd ./workspace/tdrc-gitpod/datasets/mtb_fastqs/results/fastq/
```
Remember to update the command above if the files that you have downloaded are in a different dirrectory.  

- For this to work correctly, the file names have to follow the naming scheme used in this dataset
--The sample ID must be followed by an underscore
--The forward and reverse reads must be indicated as "_1" and "_2", respectively




```bash

#!/usr/bin/env bash

set -uex

LOCATION=$PWD

for sample_1 in `ls $LOCATION/*_1*fastq.gz` ; do

#    echo "Processing $sample_1"

    read2=`echo $sample_1 | sed 's/_1/_2/g'` ; 
    
#    echo "Read_2: $read2"
    
    sample_basename=`basename $sample_1 _1.fastq.gz` ;

 #   echo "Sample_ID: $sample_basename"
    
     tb-profiler profile -1 $sample_1 -2 $read2 -t 14 -p $sample_basename --txt; 

done
```
Note that this command requires a semi-advanced understanding of the bash programming language. 
##### Brief explanation of this command: 

- sample_1 : the variable assigned to the forward (R1) reads of each isolate
- sed is used to manipulate the file name of the forward reads to specify the file name for the reverse (R2) reads (in a similar way to 'find and replace' in MS Word, and also to assign the sample ID which should be the base name (everything before the first underscore) of either of the FASTQ read files
- basename is used to assign the prefix (sampleID) to each set of FASTQ files


## Summarising the TB-profiler results of multiple samples 

Collate the results from multiple isolates to get a summary file and additional annotation files that can be used to annotate phylogenetic trees when using iTOL to view phylogenies:

```bash
tb-profiler collate --full
```
Note: to create the summary by running the ‘collate’ tool without arguments, you need to be in the directory from where TB-profiler was executed. It is also possible to specify the TB-profiler results directory and to only summarise the results for a selection of isolates with TB-profiler outputs. Please refer to the TB-profiler Github page or run the ‘collate’ tool within TB-profiler using the -h argument to access the help page with usage information:

```bash
tb-profiler collate -help
```

The TB-profiler documentation also has a guide to write your own custom collate script. 


  

