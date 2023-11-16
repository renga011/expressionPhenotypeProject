# Code for analyses done in Renganaath & Albert (2023): Trans-eQTL hotspots shape complex traits by modulating cellular states

We divide our the analyses done in this paper into NUM areas. Each area has a separate code folder containing the scripts for performing those analyses. All analyses were performed in R versions 4.3.1 or 3.5.2. 

All but one script was written by Kaushik Renganaath. The script for comparing the results of the genetic correlations with that of the QTL effect correlations and the hotspot effect correlations (results for which are presented in Table S5 of the paper) was written by Frank. W. Albert with minor modifications by Kaushik Renganaath.

The scripts are all indexed in the order in which they ought to be run. Because the intermediate R objects generated in earlier scripts may sometimes be used again in subsequent scripts, mixing up the order of the scripts may throw errors in later scripts. We don't provide the intermediate R objects that are generated by our code in this repository. We just provide those that are not generated by our code in the directories titled "RObjects_092522" & "otherFiles_101522", so that the user can use them to run our code. Some R objects whose size is very large can be accessed from figshare repository at https://doi.org/10.6084/m9.figshare.24573214. If anyone wants access to R objects or files to run specific scripts, they may request those from Kaushik Rengaaath via email (renga011@umn.edu).

Our code picks up or saves R objects to the directory titled "RObjects_092522", saves the plots to "plots_092522/" and other files like the data tables from Albert et al. (2018) or Bloom et al. (2013) that were used by us, in the directory titled "otherFiles_101522". In our code, these directories are contained in a directory that is denoted by the variable results_dir. You may adjust the value of this variable to the path of your results directory. Kindly ensure that the directories titled "RObjects_092522" and "otherFiles_101522", which are provided by us in this repository are also saved to your results directory so that the code can properly access the required data files. 

For some analyses, the code is so written so as to parallelly process multiple files using the SLURM high performance computing cluster provided by the Minnesota Supercomputing Institute, Univ of Minnesota, Twin Cities. The shell scripts used to run our code on the SLURM HPC cluster are also provided in the directories. These are not indexed like the R scripts in the directory as we provide them as mere templates to run our code on your respective HPC clusters.

# The details of the different areas are as follows -

### 1. Data preparation
This directory contains the code used to prepare the data analyzing the data done in this chapter. The following code operations are performed.

1.1. Initial data preparation

	A. Load the genotype, expression, trait and QTL data published in Albert et al. (2018) and Bloom et al. (2013).

	B. Subset segregants with data in both Albert et al. (2018) and Bloom et al (2013)

	C. Subset the genotype data to include only the 11,530 markers in Albert et al. (2018) with LD < 1.

	D. Correct the expression measurements for batch and OD covariates (covariate data was sourced from Albert et al. (2018); available as a separate file in the directory titled "otherFiles_101522")
	E. Formating the QTL tables of both studies to include specific data that will be useful for further analyses.


1.2. Make custom color palette for the 46 traits and theme for legend and axes of all plots in this paper.

### 2. Genetic correlations
2.1. Compute genetic correlations for all gene/trait combinations.

2.2. Compare genetic correlations before and after correcting for growth in the base medium used for each of the 46 traits.

2.3. Perform principal components analysis across all growth traits.

2.4. Downsampling analyis for computing number of significant genetic correlations at different segregant panel sizes.

2.5. Plotting and analyzing the results of the genetic correlation analyses.

### 3. Colocalization analyses
3.1. Subset the genotype data to include markers with LD < 0.95

3.2. Prepare the genotype, expression and trait data according to the input data format for running the colocalization function in the qtl2pleio package (Boehm et al. 2013)

3.3. Split the QTLs data to individual files for parallelly performing colocalization analyses on the SLURM HPC.

3.4. Code for performing the colocalization analysis.

3.5. Integrate the individual colocalization results into one consolidated table.

3.6. Analyze and plot the colocalization results.

3.7. Plot example of a colocalized locus (diplayed in Figure 2D of the paper)

### 4. QTL effect correlations
Compute the expression and growth effects at all eQTLs of a gene and perform weighted correlation tests between them. Applied to all genes and traits.

### 5. Overlap of trans eQTLs and gQTLs
5.1. Generate 1000 random gQTL sets across the genome.

5.2. Plot Figure 4, compute expected number of overlaps with hotspots using random 1000 gQTL sets (from 5.1)

### 6. Heritability estimates
6.1. Get heritability explained by 102 the trans eQTL hotspots that were mapped by Albert et al. (2018).

6.2. Get the heritability explained by 1000 sets of 102 random genetic markers for computing the expectation of the heritability explained by hotspots. (Note: we directly provide the 1000 random sets we used as an R object. If you want, you can generate your own set of 102 random genetic markers using the table of genotypes)

6.3. Plot heritability explained by the hotspots for the 46 growth traits.

### 7. Hotspot effect correlations
7.1. Compute and analyze the hotspot effect correlations across the 102 trans eQTL hotspots from Albert et al. (2018) and across 1000 sets of 102 random genetic loci (similar to 6.2).

7.2. Consolidate and plot the results of the hotspot effect correlations

### 8. GO term enrichment
8.1. GO term enrichment for genes with significant genetic correlation, QTL effects correlation and hotspot effects correlation.

8.2. Get average genetic correlation coefficient for different groups of genes in Brauer et al. (2008) and Gasch et al. (2000)

8.3. Plot Figure 6

### 9. Comparison of different analyses
9.1. Get and plot the contribution of local eQTLs, trans eQTLs of a gene and the 102 trans eQTL hotspot markers to the genetic correlation.

9.2. Plot the genetic correlation, QTL effects correlation and hotspot effects correlation for specific example gene (HSP12) and across all genes and traits.

9.3. Compare the lists of genes with significant genetic correlation with those having sigificant QTL effects correlation and those with significant hotspot effect correlation.

### 10. Mediation analyses
10.1. Compute the mediation of the IRA2 hotspot's effect on growth in presence of hydrogen peroxide by expression of the genes regulated by the hotspot.

10.2. Analyze and plot mediation results.




