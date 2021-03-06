![alt tag](https://raw.github.com/jfortin1/TCGA_AB_Compartments/master/figures/try.png)

# TCGA_AB_Compartments

Analysis of Hi-C data has shown that the genome can be divided into two compartments
called A/B compartments. These compartments are cell-type specific and are
associated with open and closed chromatin. In our recent Genome Biology paper, ([Fortin et al., 2015](http://www.genomebiology.com/2015/16/1/180)), we showed that we can estimate A/B compartments from 450k methylation array data. This GitHub repo contains the genome-wide A/B compartments estimated for 12 different cancer types from The Cancer Genome Atlas [[TCGA](http://cancergenome.nih.gov/)], at resolution 100kb. For the Hi-C A/B compartments, pleas visit the following page: [Hi-C A/B compartments](https://github.com/Jfortin1/HiC_AB_Compartments)

Citation for using these data:

Jean-Philippe Fortin, Kasper D. Hansen. *Reconstructing A/B compartments as revealed by Hi-C using long-range correlations in epigenetic data*. Genome Biology,16:180, 2015, doi:10.1186/s13059-015-0741-y



## Data format
The data are saved as tab-delimited text files. The first three columns represent the genomic coordinates of the bin, the fourth column reports the value of the eigenvector for the bin, and the fifth column categorizes the bin as "open" or "closed" (A and B compartment respectively). 
```{}
chr    start    end    eigen    domain
chr1	500000	599999	-0.448558697994734	open
chr1	600000	699999	-0.317063576958963	open
chr1	700000	799999	-0.0518659472420911	open
chr1	800000	899999	0.0711965336724111	closed
chr1	900000	999999	0.098443079780858	closed
chr1	1000000	1099999	-0.051011778069161	open
chr1	1100000	1199999	-0.318273718360445	open
chr1	1200000	1299999	-0.53951736779136	open
chr1	1300000	1399999	-0.585600098287715	open

```

## Cancers analyzed

| Abbreviation        | Full name           | 
| ------------- |-------------| 
| BLCA     | Bladder Urothelial Carcinoma | 
| BRCA | Breast invasive carcinoma |
| COAD | Colon adenocarcinoma |
| HNSC | Head and Neck squamous cell carcinoma |
| KIRC | Kidney renal clear cell carcinoma |
| KIRP | Kidney renal papillary cell carcinoma |
| LIHC | Liver hepatocellular carcinoma |
| LUAD | Lung adenocarcinoma |
| LUSC | Lung squamous cell carcinoma |
| PRAD | Prostate adenocarcinoma |
| THCA | Thyroid carcinoma |
| UCEC | Uterine Corpus Endometrial Carcinoma |

## Scripts

The code used to generate A/B compartments from 450k methylation array data is implemented in the `compartments()` function of the devel version of [minfi](https://github.com/kasperdanielhansen/minfi/blob/master/R/compartments.R) on GitHub.

## Visualization 

The subdirectory `scripts` contains an R script `visualization.R` to load the data into R and create a barplot of the eigenvector values (see image above), as well as a little function called `convert2GRanges()` that will convert the data to a GRanges object for convenience. Positive and negative values represent closed and open domains respectively. 

## Note about preprocessing

We preprocessed each methylation cancer dataset separately by using the 'noob' background correction method [[Triche et al., 2013](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3627582/)] followed by Functional normalization [[Fortin et al., 2014](http://www.genomebiology.com/2014/15/12/503)], both implemented in the minfi package [[Aryee et al., 2014](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC4016708/)]  

### References

**[Fortin et al., 2015]**: Jean-Philippe Fortin, Kasper D. Hansen. *Reconstructing A/B compartments as revealed by Hi-C using long-range correlations in epigenetic data*. bioRxiv, doi: http://dx.doi.org/10.1101/019000

**[Fortin et al., 2014]**: Jean-Philippe Fortin, Aurélie Labbe, Mathieu Lemire, Brent W Zanke, Thomas J Hudson, Elana J Fertig, Celia MT Greenwood, Kasper D Hansen. *Functional normalization of 450k methylation array data improves replication in large cancer studies.* Genome Biology, 15(11):503, 2014b, doi:10.1186/s13059-014-0503-2.

**[Triche et al., 2013]**: Timothy J Triche, Daniel J Weisenberger, David Van Den Berg, Peter W Laird, and Kimberly
D Siegmund. *Low-level processing of Illumina Infinium DNA Methylation
BeadArrays*. Nucleic Acids Research, 41(7):e90, 2013. doi:10.1093/nar/gkt090.

**[Aryee et al., 2014]**: Martin J. Aryee, Andrew E. Jaffe, Hector Corrada-Bravo, Christine Ladd-Acosta, Andrew
P. Feinberg, Kasper D. Hansen, and Rafael A. Irizarry. *Minfi: A flexible and comprehensive
Bioconductor package for the analysis of Infinium DNA Methylation microarrays.*
Bioinformatics, 30(10):1363–1369, 2014. doi:10.1093/bioinformatics/btu049.






