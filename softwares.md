---
layout: page
permalink: /softwares/
title: Softwares
description: "Softwares released and/or under development."
modified: 2017-09-22
tags: [bioinformatics, statistics, genetics]
image:
  feature: LogoFundoLaranja.jpg
  thumb: LogoIconBlack.jpg
---

Here we list the softwares developed and under development by the Statiscal-Genetics Laboratory and partners.

#### MAPpoly 
Software for constructing genetic maps in autopolyploids with even ploidy levels. It implements the methods and procedures proposed by Mollinari and Garcia (2019) in an R package developed in collaboration. MAPpoly can handle ploidy levels up to 8 when using hidden Markov models (HMM), and up to 12 when using the two-point simplification. To install it, please follow the instructions on Github:
- [www.github.com/mmollina/MAPpoly](https://www.github.com/mmollina/MAPpoly)

The original article can be found at:

- [Mollinari, M., & Garcia, A. A. F. (2019). Linkage analysis and haplotype phasing in experimental autopolyploid populations with high ploidy level using hidden Markov models. G3: Genes, Genomes, Genetics, 9(10), 3297-3314.](https://www.g3journal.org/content/ggg/9/10/3297.full.pdf)

#### OneMap 
Software for constructing genetic maps in experimental crosses: full-sib, RILs, F2 and backcrosses.
To install, we recommend the under development (and constantly upgraded) version from github:
- [www.github.com/augusto-garcia/onemap](https://www.github.com/augusto-garcia/onemap)

Otherwise, you can install the stable version:

- [https://cran.r-project.org/web/packages/onemap/index.html](https://cran.r-project.org/web/packages/onemap/index.html)

The original article can be found at:

- [Margarido, G. R. A., A. P. Souza, and A. A. F. Garcia. "OneMap: software for genetic mapping in outcrossing species." Hereditas 144.3 (2007): 78-79.](https://doi.org/10.1111/j.2007.0018-0661.02000.x)

#### SuperMASSA
It is a graphical Bayesian inference tool for genotyping polyploid compatible with any quantitative genotyping methods. It was mainly developed by Oliver Serang as visiting scientist in the Lab. A suitable pipeline adapted for many markers will be released soon. It can be found at:

- [http://statgen.esalq.usp.br/SuperMASSA/](http://statgen.esalq.usp.br/SuperMASSA/)

The original article can be found at:

- [Serang, Oliver, Marcelo Mollinari, and Antonio Augusto Franco Garcia. "Efficient exact maximum a posteriori computation for bayesian SNP genotyping in polyploids." PLoS One 7.2 (2012): e30906.](https://doi.org/10.1371/journal.pone.0030906)

#### updog
It is an R package that provides a suite of methods for genotyping polyploids from next-generation sequencing (NGS) data. It does this while accounting for many common features of NGS data, such as allele bias, overdispersion, sequencing error, and outlying observations. The package was developed in collaboration with by Dr. David Gerard and partners.

To install it, we recommend the under development (and constantly updated) version from github:

- [https://github.com/dcgerard/updog](https://github.com/dcgerard/updog)

Otherwise, you can install the stable version:

- [https://cran.r-project.org/web/packages/updog/](https://cran.r-project.org/web/packages/updog/)

The original article can be found at:

- [Gerard, D., Ferrão, L. F. V., Garcia, A. A. F., & Stephens, M. (2018). Genotyping Polyploids from Messy Sequencing Data. Genetics, 210(3), 789-807.](https://doi.org/10.1534/genetics.118.301468)

#### AGHMatrix
It is an R package to compute relationship matrices for diploid and autopolyploid species. It handles pedigree and molecular data with dosage. It has been developed in collaboration with [Bluberry Breeding & Genomic Lab](http://www.blueberrybreeding.com/) at University of Florida. It can be found at:

- [https://github.com/prmunoz/AGHmatrix](https://github.com/prmunoz/AGHmatrix)

The original article can be found at:

- [Amadeu, Rodrigo R., et al. "AGHmatrix: R Package to Construct Relationship Matrices for Autotetraploid and Diploid Species: A Blueberry Example." The plant genome (2016).](https://doi.org/10.3835/plantgenome2016.01.0009)

#### fullsibQTL
Software for QTL mapping in outcrossing species using composite interval mapping. It is under development and will be released soon. Based on [Gazaffi et. al 2014](https://doi.org/10.1007/s11295-013-0664-2).
