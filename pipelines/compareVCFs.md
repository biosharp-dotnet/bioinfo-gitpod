# Compare two VCF
## determine the variant difference between two VCF files



This tutorial will guide you to install vcftools and tabix in your GitPod environment and to determine the number of overlapping and unique variants between two VCF files. 



## Installing `vcftools` in your GitPod environment


```sh
git clone https://github.com/vcftools/vcftools.git
cd vcftools
./autogen.sh
./configure
make
sudo make install
```

We also need to install a program called `tabix` in order to process the VCF index files. 

```sh
sudo apt install tabix
```

The latest version of `vcftools` and `tabix` is now installed in your GitPod environment. 

Next, download the annotated  `VCF` files of sample47 and sample48 of the text dataset of Viralrecon, as well as the VCF index files. These are located at nf-core-awsmegatests/viralrecon/results-42e38bba3da80484bc480f53d2130642a349e8c6/platform_illumina/variants/ivar/snpeff. The links to the files are already copied below. 

```sh
wget https://nf-core-awsmegatests.s3-eu-west-1.amazonaws.com/viralrecon/results-42e38bba3da80484bc480f53d2130642a349e8c6/platform_illumina/variants/ivar/snpeff/SAMPLE_47.snpeff.vcf.gz

wget https://nf-core-awsmegatests.s3-eu-west-1.amazonaws.com/viralrecon/results-42e38bba3da80484bc480f53d2130642a349e8c6/platform_illumina/variants/ivar/snpeff/SAMPLE_47.snpeff.vcf.gz.tbi

wget https://nf-core-awsmegatests.s3-eu-west-1.amazonaws.com/viralrecon/results-42e38bba3da80484bc480f53d2130642a349e8c6/platform_illumina/variants/ivar/snpeff/SAMPLE_48.snpeff.vcf.gz

wget  https://nf-core-awsmegatests.s3-eu-west-1.amazonaws.com/viralrecon/results-42e38bba3da80484bc480f53d2130642a349e8c6/platform_illumina/variants/ivar/snpeff/SAMPLE_48.snpeff.vcf.gz.tbi

```

## Preparing to run TB-profiler
To get an overview of the usage information for `vcf-compare`, run: 

```sh
vcf-compare -h
```

Next, use `vcf-compare` to determine the number of variants that overlap the number of variant differences between sample47 and sample48: 
```sh
vcf-compare SAMPLE_47.snpeff.vcf.gz SAMPLE_48.snpeff.vcf.gz > compare_47-48.txt
```
