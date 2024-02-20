1. Extracted the variants those are having the DP greater tha or equal to 15 from the 1232 in-house samples.

2. using rsID_Genomic_pos_extraction python script extracted the all star allele rsID's and the genomic positions from the allele defination tables for level 1A, 1B 13 genes. (CYP3A4, CYP2C19, CYP2B6, NAT2, CYP3A5, SLCO1B1, CYP2C9, G6PD, NUDT15, UGT1A1, CYP2D6, TPMT, CYP2A6).

3. we have retrieved the positional information for those 13 selective genes rsID's.

4. We have filtered the variants those are covering these 13 gene coordinates from 1232 sample vcf files, Using BCF tools view -R function
     bcftools view -R coordinates.bed Input.vcf.gz > 13_genes_covered.vcf
    
5. After the filteration criteria we have applied Depth filter >= 15. Then we have developed In-House python scripts for the condition1,2,3 with the input of all the vcf files.
The scripts include diplotypes, and counts of the resulted star alleles based on zygosity, avg read depth from the vcf files. 
