## Covid test data


```
wget "https://github.com/nf-core/test-datasets/blob/modules/data/genomics/sarscov2/illumina/fastq/test_1.fastq.gz?raw=true" -O covid_1.fastq.gz

wget "https://github.com/nf-core/test-datasets/blob/modules/data/genomics/sarscov2/illumina/fastq/test_2.fastq.gz?raw=true" -O covid_2.fastq.gz

wget "https://github.com/nf-core/test-datasets/blob/modules/data/genomics/sarscov2/illumina/fasta/contigs.fasta?raw=true"  -O covid.contigs.fasta

wget "https://github.com/nf-core/test-datasets/blob/modules/data/genomics/sarscov2/illumina/bam/test.paired_end.bam?raw=true" -O covid.paired_end.bam

wget "https://github.com/nf-core/test-datasets/blob/modules/data/genomics/sarscov2/illumina/vcf/test.vcf.gz?raw=true" -O covid.vcf.gz

wget "https://github.com/nf-core/test-datasets/blob/modules/data/genomics/sarscov2/illumina/vcf/test.vcf.gz.tbi?raw=true" -O covid.vcf.gz.tbi

wget "https://github.com/nf-core/test-datasets/blob/modules/data/genomics/sarscov2/illumina/vcf/test.bcf?raw=true" -O covid.bcf

```


# Hands-on creation of `SAM` file, 

### 1. Create a `conda` environment called `samtools-env`

```

conda create --name samtools-env --channel bioconda --channel conda-forge samtools=1.11 tabix

```

### 2. Activate the conda environment 

**NOTE:** After activation, your Gitpod terminal sould display `(samtools-env)` 

```
$ conda activate samtools-env
```

### 3. Confirm if `samtools` have been installed, it should print some info about the version

```
$ samtools --version

samtools 1.11
Using htslib 1.11
Copyright (C) 2020 Genome Research Ltd.
```

### 4. Create the `sam` file 

```
samtools view -h covid.paired_end.bam -o covid.paired_end.sam
```

### 5. Confirm the contents of the file 

```
head covid.paired_end.sam

```
