<p align="center">
  <img src="./logoQG.png" />
</p>



## Instructors

- Dr. Marcio Resende, (**Course coordinator**)\
2135 Fifield Hall\
mresende@ufl.edu\
Office Hours by appointment

- Dr. Felipe Ferrão\
2135 Fifield Hall\
lferrao@ufl.edu\
Office Hours by appointment

## Course Description

Advanced training in quantitative genetics is critical for the success of the modern breeder. This course addresses this need both from a theoretical and applied perspective. PCB 6555 Introduction to Quantitative Genetics will be based on lectures and hands-on activities that utilize the content learned in class. The course is intended for students of all disciplines who are interested in quantitative genetic principles and biometric evaluation of characters that exhibit continuous variation in natural populations and breeding programs for animals and/or plants.

## Course Objectives
The course goal is to introduce graduate students to concepts, theories, and methods in quantitative genetics with emphasis on application to breeding programs and statistical analysis of genetic experiments/studies.

## Required and Recommended Literature

- Isik, F., Holland, J., Maltecca, C. - Genetic Data Analysis for Plant and Animal Breeding. (2017).
DOI: 10.1007/978-3-319-55177-7
- Introduction to Quantitative Genetics, Falconer and Mackay, Longman Group Ltd, 1996
- Genetics and analysis of quantitative traits, Lynch and Walsh, Sinauer, 1998

## Software

**You will need to bring your laptop.** The main software used will be R with a library for ASReml-R. R
can be downloaded from www.r-project.org, and ASReml (R library and stand-alone version) is available
for registered students from: www.vsni.co.uk/software/asreml/asreml-teching. You will receive
instructions to download, and install and you will require a license for this software that will be provided by
the instructor. There are numerous online resources available for R; however, if you would like a
traditional textbook, The R Book, is widely available and comprehensive.
- Crawley, M. J. (2012). The R book. John Wiley & Sons.

# Class notes and Hands-on

It is an attempt to organize and make available to any student the class notes used during the Quantitative Genetic course. The material is a compilation of texts, examples, and materials from multiple books and papers that we visited to create the classes. We suggest using it as a guide for lessons. *Important: these class notes do not replace the fundamental role of the textbooks !!* At the end of each topic, there are references. We suggest that you visit the references for a complete understanding. Finally, we hope in the future include more authorial examples using data from our personal research.

```
[pdf] = slides used in class
[html] = open it in your browser
[HW] = homework
[paper] = article suggested
[Download] = link for downloading the files. 
```

**1. Introduction to R applied to popgen analyses**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week1_24.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week1_24.html)

- Theory: Introduction to PorGen
- Practice: Introduction to R applied to popgen analyses

**2. Means,Genotypic Values, and Breeding Values**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week2_24.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week2_24.html)

- Theory: Genetic Effect of complex traits
- Practice: Introduction to Experimental Design and ANOVA
 
- Extra: 
  - Short introduction to linear models [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week2a_2022.html)
 
**3. Genetic Variance and Heritability**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week5_GeneticVariance_24.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week5_GeneticVariance_24.html)

- Theory: Total genetic, additive, and dominance variances. Heritability theory
- Practice: app to check the components of the genetic variance and their relationship to the allele frequencies.

- Extra: 
  - Alternative Heritability Measures [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/h2_2022.html)

**4. Biometric Model**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week6_BiometricModel_24.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week6_BiometricModel_24.html)

- Theory: Dominance deviation and the Biometric Model
- Practice: a toy example on simulating a simpre regression model in R and the Biometric Model

**5. Introduction to Mixed Models**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week3_2022.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week3_2022.html)

- Theory: REML and Mixed Model
- Practice: Mixed Models compared to traditional ANOVA

- Extra: 
  - Introduction to asreml-R [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/2Intro_ASREML.html)

**6. Covariance Between Relatives and Genetic Designs**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week7_2022.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week7_2022.html)

- Theory: Resemblance between relatives, pedigree matrix and genetic design
- Practice:  Progenie test experiments using half-sib and full-sibs. `AGHmatrix` package.

**7. Pedigree Analysis**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week8_2022.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week8_2022.html)

- Theory: Theoretical background on BLUPs
- Practice:  Half sib family (tree data set) and animal model with deep pedigree (pig data set)

**8. Response to Selection**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week9_2022.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week9_2022.html)

- Theory: Breeder’s equation
- Practice: Simulation exploring how different parameters impact the response to selection.

- Extra: 
  - AlphaSims simulation [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week9_AlphaSim.html)

**9. Multivariate Models**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week10_2022.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week10_2022.html)

- Theory: multivariate linear mixed models
- Practice: heterogeneous residual variance and multi-trait  analysis

**10. Spatial Models (by Marco Peixoto)**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week10a_2022.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week10a_2022.html)

- Theory: row-col models and unreplicated trials
- Practice: autoregressive models, variograms and model selection

**11. Genotype-by-Environment (GxE) Interaction**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week11_2022.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week11_2022.html)

- Theory: Finlay and Wilkinson Regression and mixed model
- Practice: MET analysis for wheat and pine data sets 

- Extra: 
  - AMMI and Biplot Analyses [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week11_2022a.html)
  - Factor Analytic and Mixed Models [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week11_2022b.html)

**12. Genomic Selection**

- Hands-on [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week12_2022.html)
- Download [[html]](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week12_2022.html)

- Theory: GBLUP and Realized Genomic Relationships
- Practice: G matrix, GBLUP and cross-validation 

- Extra (classes from the last year and from other courses)
  - GS and CVs [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week12.html)
  - GS + dominance [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week13.html)
  - rrBLUP vs GBLUP [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/survey/3.GS.html)


**Extra classes**

- Non-Gaussian Responses [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week14.html)
- Genetic Value and Mating Desings [[html]](https://htmlpreview.github.io/?https://github.com/lfelipe-ferrao/lfelipe-ferrao.github.io/blob/master/class/quantGenetic/week15.html)




