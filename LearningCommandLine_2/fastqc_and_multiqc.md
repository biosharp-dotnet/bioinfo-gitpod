# In terminal-1

```
conda init bash 

exec $SHELL

conda create --name qc-env --channel bioconda --channel conda-forge fastqc multiqc

conda activate qc-env

fastqc covid_1.fastq.gz

fastqc covid_2.fastq.gz

multiqc .

```

# In terminal-2

In a separate terminal 

`python -m http.server 8000`

You should see a notification on the bottom-left of the screen for this PORT, `A service is available on port 8000`, click on `Open Browser` and then select the `html` files.

Navigate to another tab in your browser add `8000` to the beginning of your Gitpod URL, for example `8000-biosharpdotn-tdrcgitpod-ehsr91d5nlc.ws-eu43.gitpod.io/`
