**Analysis of Pharmacogenes with 1232 In-House patient VCF samples** 

1. We have extracted the all star allele rsID's and the genomic positions from the allele defination tables for level 1A, 1B 13 genes (**CYP3A4, CYP2C19, CYP2B6, NAT2, CYP3A5, SLCO1B1, CYP2C9, G6PD, NUDT15, UGT1A1, CYP2D6, TPMT, CYP2A6**) using rsID_Genomic_pos_extraction python script.

2. The complete positional information for those 13 selective genes were retrieved using UCSC and prepared the input files for further analysis. 

3. We have filtered the variants those are covering these 13 gene coordinates from 1232 sample vcf files, Using BCF tools view -R function
     _bcftools view -R coordinates.bed Input.vcf.gz > 13_genes_covered.vcf_
    
4. After the filteration criteria we have applied Depth filter >= 15. Then we have developed In-House python scripts for the
   
    **Condition1**: The 13 genes coordinates file consider as the Support file for consition2. Each gene coordinates contains the chromosome, start, and end positions columns. Mapped the each vcf file with the coordinates file and retrieved the variants those are lies in between the genes region also extracted the covered variants from KAPA bed file. once extracted the excel files for each sample pooled the respective counts for the each position using (CHROM, POS, REF, ALT, Zygosity) columns.
   
   **Condition2**: From the 13 genes single shared exact variant positional information extracted the variants those are from the vcf files on the basis of CHROM, POS, REF, ALT columns and verified these variants with the KAPA bed file to know the variants coverage status. Final output contains the 13 gene variants along with the covered status of all the 1232 samples. 

   **Condition3**: the 13 genes single shared variants mapped with the vcf files and extracted the exact upstream and downstream positions those are near with Bed file and retrieved the minimal distance positions to identify the nearest snp for vcf files.
These scripts include

   **Diplotypes**: The output files of the condition2 are the input files for this diplotypes. On the factorial method extracted the number diplotypes for each gene of all samples using their haplotype. 

and counts of the resulted star alleles based on zygosity, avg read depth from the vcf files. 

