# Phylogenetic analysis and tree annotation
## _IQTREE and iTOL_


## Running IQTREE

Download the `MTB-multi.fasta` to your local computer. This file is located on the Google drive in Day_8 of the training material (in Phylo_practical/task)

Go to the IQTREE webserver: 
http://iqtree.cibiv.univie.ac.at/ 

On the IQTREE webserver, navigate to the 'Tree Inference' tab on the left. 
- upload the `MTB-multi.fasta` file as the Input Data
- Set the substitution model to 'Auto' - this way, IQTREE will analyse the data and determine the best nucleotide substitution model to use in the phylogenetic analysis that will follow
- Do Maximum Likelihood phylogenetic analysis (this is the default)
- Do ultrafast bootstrapping and pereform 1000 bootstrap replicates
- Leave all other parameters on the default values
- You can enter your email address if you would like to receive a notification when your analysis has completed
- Press 'sudmit job' 
- Wait for the analysis to finish and download the results from the IQTREE website
 

## Viewing a phylogenetic tree
##### Go to tree visualisation tool
In your internet browser, go to iTOL (the interactive tree of life):
https://itol.embl.de/
##### Upload the tree file
Navigate to "Upload" at the top of the screen and drag and drop the `.treefile` on this page. You also have the option to browse your computer and select the correct file to feed into iTOL. 

_if the phylogenetic analysis has not completed, you can use the precomputed `.treefile` on the Google Drive, The file is calld `MTB-multi.fasta.treefile`_
#####  Rerooting the tree
Use the interactive interface of iTOL to reroot the phylogenet tree to the most recent common ancestor (MRCA) of the _Mycobacterium tuberculosis_ complext (MTBC). The MRCA is labelled as Mcanettii. _Mycobacterium canettii_ is considered as an outgroup to the MTBC.

##### Inspect the metadata
In the Google Drive, you will find an MS Excel document with metadata on smoking status and first line drug resistance for the _Mycobacterium tuberculosis_ isoaltes analysed in this dataset. The sample IDs in the metadata file mathes the sample IDs used in the `fasta` that was used to generate the phylogenetic tree. 

Use the templates provided in the MS Excel document (iTOL_templates.xlsx) to generate annotation files.
### TIP
- Use the Colour Brewer website to selcet colours and determine the Hex codes for the chosen colours: https://colorbrewer2.org/#type=sequential&scheme=BuGn&n=3
- You can create the file in MS Excel at first - and then export the file in tab delimeted text format


### Take note
- iTOL will only understand the annotation file if the sample IDs in the `treefile` and the annotation file in tab delimited `txt` format match EXACTLY
- The format of the annotation file is extremely important
-- Tab delimitation should be specified in the header of the file and applied to the formatting (when you save the file in MS Excel - choose the tab delimited text format)

Once you have generated the annotation files, drop them (drag and drop) on your visualised phylogenetic tree in iTOL. The web tool will automatically pick up the annotation file, interpret the metadata and add the annotation to the displayed phylogenetic tree.

