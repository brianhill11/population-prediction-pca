# Population Prediction with 1000 Genomes data using PCA and a Random Forest Classifier
This notebook contains code for predicting 1000 Genomes populations using principal component analysis (PCA) and a random forest classifier 

## Getting the data

The VCFs can be downloaded from [here](http://hgdownload.cse.ucsc.edu/gbdb/hg19/1000Genomes/phase3/)

The population information file can be downloaded from here: ftp://ftp.1000genomes.ebi.ac.uk/vol1/ftp/release/20130502/integrated_call_samples_v3.20130502.ALL.panel

## Pre-processing

Before using the 1000 Genomes VCF files, we first do a bit of pre-processing. 
First, we concatenate the VCFs together into one giant VCF file using [bcftools](https://samtools.github.io/bcftools/). The command for doing this is in the script `concat_phase3_vcfs.sh`. 

Then, we filter the variants to use a subset using [vcftools](http://vcftools.sourceforge.net). The command for doing this is: 
```
vcftools --gzvcf all.1kg.phase3_shapeit2_mvncall_integrated_v1b.20130502.vcf.gz --snps pruned_SS2_ids_out.txt --recode
```

Finally, the data should be ready for processing. 
