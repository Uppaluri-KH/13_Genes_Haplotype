**Analysis of Pharmacogenes** 

1. We have extracted the all star allele rsID's and the genomic positions from the allele defination tables for level 1A, 1B 13 genes (CYP3A4, CYP2C19, CYP2B6, NAT2, CYP3A5, SLCO1B1, CYP2C9, G6PD, NUDT15, UGT1A1, CYP2D6, TPMT, CYP2A6) using rsID_Genomic_pos_extraction python script.

2. The complete positional information for those 13 selective genes were retrieved using UCSC and prepared the input files for further analysis. 

3. We have filtered the variants those are covering these 13 gene coordinates from 1232 sample vcf files, Using BCF tools view -R function
     _bcftools view -R coordinates.bed Input.vcf.gz > 13_genes_covered.vcf_
    
4. After the filteration criteria we have applied Depth filter >= 15. Then we have developed In-House python scripts for the condition1,2,3 with the input of all the vcf files.
These scripts include diplotypes, and counts of the resulted star alleles based on zygosity, avg read depth from the vcf files. 

