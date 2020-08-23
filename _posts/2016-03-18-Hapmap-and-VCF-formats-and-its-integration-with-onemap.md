---
layout: post
title: Hapmap and VCF formats and its integration with onemap
description: "How to use and convert this formats and call them on onemap."
modified: 2016-06-04
tags: [hapmap, vcf, onemap, transform]
image:
  feature: LogoFundoAzul.jpg
  creditlink: http://augusto-garcia.github.io/
---

*Written by [Cristiane Hayumi Taniguti, Letícia Aparecida de Castro Lara, and Rodrigo Rampazo Amadeu](http://augusto-garcia.github.io/statgen-esalq/people/)*

-   [Hapmap](#hapmap)
-   [VCF](#vcf)
-   [VCF x HapMap](#vcf-x-hapmap)
-   [OneMap - vcf2raw function](#onemap---vcf2raw-function)

Hapmap ("Haplotype Map") and VCF ("Variant Call Format") formats were
developed by International Consortiums to create an expressive database
for polymorphisms in the human genome. They have unique format data
which are our goal to describe in this article. These established data
format are also used in the study of another species. The object here is
described both formats, how to to convert one into another, and how to
make the call in the mapping softwares.

Hapmap
======

The [Hapmap Project](http://hapmap.ncbi.nlm.nih.gov/) was initiated in
2001 by the International HapMap Consortium. Its database is freely
available to the public through the NCBI database dbSNP. The Project is
also described at [Nature 426 :789-796, 2003 \[PMID:
14685227\]](http://www.nature.com/nature/journal/v426/n6968/abs/nature02168.html).
The file format estabilished through the project is also used in others
projects and species.

The Hapmap file format is a table which consists of 11 columns plus one
column for each sample genotyped. The first row contains the header
labels of your samples, and each additional row contains all the
information associated with a single SNP. You can get a Hapmap file by
chromosome or a general file.

The current release consists of attributes, as follows:

    rs#    alleles    chrom     pos     strand    assembly#    center    protLSID    assayLSID    panelLSID    QCcode    sample1 |

-   `rs#` contains the SNP identifier;
-   `alleles` contains SNP alleles according to NCBI database dbSNP;  
-   `chrom` contains the chromosome that the SNP was mapped;
-   `pos` contains the respective position of this SNP on chromosome;
-   `strand` contains the orientation of the SNP in the DNA strand.
    Thus, SNPs could be in the forward (+) or in the reverse (-)
    orientation relative to the reference genome;
-   `assembly#` contains the version of reference sequence assembly
    (from NCBI);
-   `center` contains the name of genotyping center that produced the
    genotypes;
-   `protLSID` contains the identifier for HapMap protocol;
-   `assayLSID` contain the identifier HapMap assay used for genotyping;
-   `panelLSID` contains the identifier for panel of individuals
    genotyped;
-   `QCcode` contains the quality control for all entries;
-   subsequently, the list of sample names.

Below it is an example of VCF file:

    rs#    alleles    chrom    pos    strand    assembly#    center    protLSID    assayLSID    panelLSID    QCcode    Parental_1    Parental_2    ID_1    ID_2
    44509    A/G    02     5565755     +    NA    NA    NA    NA    NA    NA    AG    AA    AA    AA 
    38019    G/A    02     43878360     +    NA    NA    NA    NA    NA    NA    GG    GA    GG    GG
    89440    T/C    04     25220824     +    NA    NA    NA    NA    NA    NA    TC    TT    NN    TT

The codification of the genotypes follows bellow:

<table>
<thead>
<tr class="header">
<th align="left">Code</th>
<th align="left">Meaning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">A</td>
<td align="left">Adenine</td>
</tr>
<tr class="even">
<td align="left">C</td>
<td align="left">Cytosine</td>
</tr>
<tr class="odd">
<td align="left">G</td>
<td align="left">Guanine</td>
</tr>
<tr class="even">
<td align="left">T</td>
<td align="left">Thymine</td>
</tr>
<tr class="odd">
<td align="left">R</td>
<td align="left">A or G</td>
</tr>
<tr class="even">
<td align="left">Y</td>
<td align="left">C or T</td>
</tr>
<tr class="odd">
<td align="left">S</td>
<td align="left">G or C</td>
</tr>
<tr class="even">
<td align="left">W</td>
<td align="left">A or T</td>
</tr>
<tr class="odd">
<td align="left">K</td>
<td align="left">G or T</td>
</tr>
<tr class="even">
<td align="left">M</td>
<td align="left">A or C</td>
</tr>
<tr class="odd">
<td align="left">B</td>
<td align="left">C or G or T</td>
</tr>
<tr class="even">
<td align="left">D</td>
<td align="left">A or G or T</td>
</tr>
<tr class="odd">
<td align="left">H</td>
<td align="left">A or C or T</td>
</tr>
<tr class="even">
<td align="left">V</td>
<td align="left">A or C or G</td>
</tr>
<tr class="odd">
<td align="left">N</td>
<td align="left">any base</td>
</tr>
<tr class="even">
<td align="left">. or -</td>
<td align="left">gap</td>
</tr>
</tbody>
</table>

VCF
===

The VCF data format was developed for the [1000 Genomes
Project](http://www,1000genomes.org) by the International 1000 Genomes
Consortium. For further informations please access the 1000 Genome
Project [webpage](http://www,1000genomes.org) where not only are
included several new populations, but also included the populations of
the HapMap Project. This guide was based upon the
[wiki](http://www.1000genomes.org/wiki/Analysis/vcf4.0) of 1000 Genomes
Project .

The VCF format is divided in meta-information lines, header lines, and
data lines.

Below it is an example of VCF file:

    ##fileformat=VCFv4.0 
    ##fileDate=20160306 
    ##source="Stacks v1.37"
    ##INFO=<ID=NS,Number=1,Type=Integer,Description="Number of Samples With Data"> 
    ##INFO=<ID=AF,Number=.,Type=Float,Description="Allele Frequency"> 
    ##FORMAT=<ID=GT,Number=1,Type=String,Description="Genotype"> 
    ##FORMAT=<ID=DP,Number=1,Type=Integer,Description="Read Depth"> 
    ##FORMAT=<ID=AD,Number=1,Type=Integer,Description="Allele Depth"> 
    ##FORMAT=<ID=GL,Number=.,Type=Float,Description="Genotype Likelihood"> 
    #CHROM    POS    ID    REF    ALT    QUAL    FILTER    INFO    FORMAT    Parental_1    Parental_2    ID_1    ID_2    ID_3 
    Chr02    5565755    44509    A    G    .    PASS    .    GT:DP:AD:GL    0/1:31:23,8:.,42.98,.    0/0:13:9,0:.,18.02,.    0/0:30:30,0:.,41.59,.    0/0:27:27,0:.,37.43,.    0/0:25:25,0:.,34.66,. 

The Meta-information are rows where the first one is mandatory and has
the VCF format version. Depending upon the VCF format version your data
will use one form or another to fill the parameters options. Pay
attention in what version your data and programs are working with and if
they are compatible. The first row can be followed by more, but not
mandatory, lines about the file origin as date of file creation, source,
reference, phasing, etc. After them, it may contain Information lines
`##INFO`. The `##INFO` contains the following entries:

-   `ID` name of the variable (a string);
-   `Number`: number of values (an integer);
-   `Type`: type of variable (integer, float, character, string, and
    flag);
-   `Description`: a string with the descrition.

And has the following syntax:

    ##INFO=<ID=ID,Number=”number”,Type=”type”,Description=”description”>

In the example, the line

    ##INFO=<ID=NS,Number=1,Type=Integer,Description="Number of Samples With Data">

has the identificator `NS`, `“Number of Samples With Data”`, represented
by `1` `Integer`.

After the `##INFO` lines, it should contain the `##FORMAT` lines which
indicate each type of variable of your data. The `##FORMAT` contains the
following entries:

-   `ID` name of the variable (a string);
-   `Number` number of values (an integer if version=4.0);
-   `Type` type of variable (integer, float, character, string, and
    flag);
-   `Description`: a String with the description.

And has the following syntax:

    ##FORMAT=<ID=ID,Number=number,Type=type,Description=”description”>

In the example, the line

    ##FORMAT=<ID=GT,Number=1,Type=String,Description="Genotype">

has the identificator `GT`, a `“Genotype”`, represented by `1` `String`.

After the Meta-information lines containing all the information and
format data, there is the header line. The header line has mandatorily 8
fixed columns and are tab limited. If it has genotypic data, it also has
the `FORMAT` column followed by the sample IDs. The columns and its
respective data information are:

-   `#CHROM` chromosome (alphanumeric string);
-   `POS` position in chromosome (integer);
-   `ID` identificator of the line (alphanumeric string);
-   `REF` reference base(s) (A,C,G,T,N);
-   `ALT` list of alternate non-reference base(s) (A,C,G,T,N);
-   `QUAL` phred-scaled quality score for the assertion made in ALT;
-   `FILTER` PASS if it has passed in all filters, if not, it should
    contain the reason;
-   `INFO` it is about the all INFO earlier described separated by
    semicolon;
-   `FORMAT` all the format IDs separated by colon;
-   `IDs` a tab separated list with sample identificators.

In the example, the header is:

    #CHROM    POS    ID    REF    ALT    QUAL    FILTER    INFO    FORMAT    Parental_1    Parental_2    ID_1    ID_2    ID_3

Where indicates all the columns and the list of sample identificators
(in the case: `Parental_1`,`Parental_2`,`ID_1`,`ID_2`,`ID_3`).

After the header line, it has the data lines tab limited where ‘.’
represents missing data. In the example:

    #CHROM    POS    ID    REF    ALT    QUAL    FILTER    INFO    FORMAT    Parental_1    Parental_2    ID_1    ID_2    ID_3
    Chr02    5565755    44509    A    G    .    PASS    .    GT:DP:AD:GL    0/1:31:23,8:.,42.98,.    0/0:13:9,0:.,18.02,.    0/0:30:30,0:.,41.59,.    0/0:27:27,0:.,37.43,.    0/0:25:25,0:.,34.66,.

It is a SNP at chromosome 2 in the position 5565755 with identificator
equals to 44506. The reference allele is an A and has one alternative
allele G. There is no information about the quality of this data
collected. It passed through the filter. There is no additional
information about it. The samples are represented in the order
GT:DP:AD:GL (genotype, read depth, allele depth, and genotype
likelihood). The sample Euc\_201 cell is:

    0/1:31:23,8:.,42.98,.

In other words, Euc\_202 sample genotype is 0/1, (i.e. A/G) with a read
depth of 31. It has an allele depth of 23 for the first allele and 8 for
the second allele with a genotype likelihood of 42.98.

The genotype can also be represented in terms of insertion and deletion,
please see the [wiki](http://www.1000genomes.org/wiki/Analysis/vcf4.0).

VCF x HapMap
============

Both formats can be easily interchangeable using the software TASSEL 4.
Using the GUI version, just import the file and export as the type you
want. Using the standalone version, first make sure that your TASSEL
directory are in the PATH:

    export PATH=$PATH:~/Programs/TASSEL_standalone

And then,

-   VCF to Hapmap:

<!-- -->

    ./run_pipeline.pl -Xmx5g -fork1 -vcf example.vcf -export -exportType Hapmap -runfork1C

-   Hapmap to VCF:

<!-- -->

    /run_pipeline.pl -Xmx5g -fork1 -h example.hmp.txt -export -exportType VCF -runfork1

<p>Using the software TASSEL 5:</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>git clone https://bitbucket.org/tasseladmin/tasselk-5-standalone.git
</code></pre></div></div>

<p>And then,</p>

<ul>
  <li>VCF to Hapmap:</li>
</ul>

<!-- -->

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>./run_pipeline.pl  -Xmx5g  -fork1  -vcf  example.vcf  -export  -exportType  Hapmap  -fork1c </code></pre></div></div>

<ul>
  <li>Hapmap to VCF:</li>
</ul>

<!-- -->

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>./run_pipeline.pl  -Xmx5g  -fork1  -h  example.hmp.txt  -export  -exportType  VCF  -fork1c </code></pre></div></div>

Besides that, it can be found several others user made scripts available
at github platform to do the same conversion.

VCF format is more informative than the Hapmap format. VCF can have
unlimited information about the data as INFO, FORMAT, and file
description. Hapmap is simpler and easier to edit and handle. However,
Hapmap can store less data and versatile than VCF. When converting one
in another be careful about the data you are missing in the process -
mainly about the INFO and FORMAT fields if VCF. If converting Hapmap to
VCF you can add information about the data after the converstion.

OneMap - vcf2raw function
=========================

Onemap is a software to do genetic linkage analysis and to build genetic
maps in experimental crosses: *F*<sub>2</sub>, backcrosses, RILs, and
full-sib. Its stable version has been available at
[CRAN](http://cran.r-project.org/web/packages/onemap/index.html). Its
last version was updated on 2013-09-09. However, new functions are being
added for a new version. They are still in development and available at
a [github repository](https://github.com/augusto-garcia/onemap). One of
these new functions called “vcf2raw” allows to convert a vcf file to an
OneMap raw file. At this tutorial we will explore the `vcf2raw`
function.

First, it is important to know about the OneMap raw format. For
*F*<sub>2</sub>, backcrosses, and RILs, OneMap uses exactly the same as
the MAPMAKER/EXP input file format. Here we will describe a brief
overview about the format based upon the [OneMap
tutorial](http://htmlpreview.github.io/?https://github.com/augusto-garcia/onemap/blob/master/inst/doc/Inbred_Based_Populations.html),
but you can find more information at [MAPMAKER/EXP
manual](http://home.cc.umanitoba.ca/~psgendb/birchhomedir/doc/mapmaker/mapmaker.tutorial.pdf).
The file should look like this:

    data type f2 intercross
    10 5 2

    *M1 A B H H A - B A A B
    *M2 C - C C C - - C C A
    *M3 D B D D - - B D D B
    *M4 C C C - A C C A A C
    *M5 C C C C C C C C C C

    *weight 10.2 - 9.4 11.3 11.9 8.9 - 11.2 7.8 8.1 
    *length 1.7 2.1 1.8 2.0 1.0 - 1.7 1.0 - 1.1

The first line in the file should have the information about the
population type, that can be denoted as “f2 backcross” for backcross
populations type, or “f2 intercross” for *F*<sub>2</sub>, “ri self” for
RIL produced by selfing, “ri sib” for RIL produced by sib mating. The
second line contains the number of individuals in the progeny, the
number of markers, and the number of quantitative traits. The phenotypic
information may be present at the file, but it will not be used by
OneMap. After these two lines, the file must have the genotypic
information for each marker. The character \* indicates the beginning of
information of a marker, followed by the marker name.

The codification for genotypes is the following:

<table>
<thead>
<tr class="header">
<th align="left">Code</th>
<th align="left">Meaning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">A</td>
<td align="left">homozygous for allele A (from parental 1 - AA)</td>
</tr>
<tr class="even">
<td align="left">B</td>
<td align="left">homozygous for allele B (from parental 2 - BB)</td>
</tr>
<tr class="odd">
<td align="left">H</td>
<td align="left">heterozygous carrying both alleles (AB)</td>
</tr>
<tr class="even">
<td align="left">C</td>
<td align="left">Not homozygous for allele A (Not AA)</td>
</tr>
<tr class="odd">
<td align="left">D</td>
<td align="left">Not homozygous for allele B (Not BB)</td>
</tr>
<tr class="even">
<td align="left">-</td>
<td align="left">Missing data for the individual at this marker</td>
</tr>
</tbody>
</table>

The quantitative trait data should come after the genotypic data and
have a similar format. The trait values for each individual must be
separate by at least one space, a tab or a line break. A dash (-)
indicates missing data.

With this file format we can use the OneMap function called
`read_mapmaker` to import the data to OneMap.

    ?read_mapmaker       #For more informations about this function
    onemap_file_f2 <- read_mapmaker(dir="C:/workingdirectory",
                                    file="your_data_file.raw")

Constructing maps for outcrossing populations OneMap implements the [Wu
et al (2002a)](http://ccb.bjfu.edu.cn/doc/sg2014/sg-wu-paper1.pdf)
strategy and uses its marker type classification described at the
following table.

<table>
<thead>
<tr class="header">
<th align="center"></th>
<th align="center">Parent</th>
<th align="center"></th>
<th align="center">Offspring</th>
<th align="center"></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="center"></td>
<td align="center">Crosstype</td>
<td align="center">Cross</td>
<td align="center">Observed bands</td>
<td align="center">Segregation</td>
</tr>
<tr class="even">
<td align="center">A</td>
<td align="center">1</td>
<td align="center">ab x cd</td>
<td align="center">ac,ad,bc,bd</td>
<td align="center">1:1:1:1</td>
</tr>
<tr class="odd">
<td align="center"></td>
<td align="center">2</td>
<td align="center">ab x ac</td>
<td align="center">a,ac,ba,bc</td>
<td align="center">1:1:1:1</td>
</tr>
<tr class="even">
<td align="center"></td>
<td align="center">3</td>
<td align="center">ab x co</td>
<td align="center">ac,a,bc,b</td>
<td align="center">1:1:1:1</td>
</tr>
<tr class="odd">
<td align="center"></td>
<td align="center">4</td>
<td align="center">ao x bo</td>
<td align="center">ab,a,b,o</td>
<td align="center">1:1:1:1</td>
</tr>
<tr class="even">
<td align="center">B.1</td>
<td align="center">5</td>
<td align="center">ab x ao</td>
<td align="center">ab,2a,b</td>
<td align="center">1:2:1</td>
</tr>
<tr class="odd">
<td align="center">B.2</td>
<td align="center">6</td>
<td align="center">ao x ab</td>
<td align="center">ab,2a,b</td>
<td align="center">1:2:1</td>
</tr>
<tr class="even">
<td align="center">B.3</td>
<td align="center">7</td>
<td align="center">ab x ab</td>
<td align="center">a,2ab,b</td>
<td align="center">1:2:1</td>
</tr>
<tr class="odd">
<td align="center">C</td>
<td align="center">8</td>
<td align="center">ao x ao</td>
<td align="center">3a,o</td>
<td align="center">3:1</td>
</tr>
<tr class="even">
<td align="center">D.1</td>
<td align="center">9</td>
<td align="center">ab x cc</td>
<td align="center">ac,bc</td>
<td align="center">1:1</td>
</tr>
<tr class="odd">
<td align="center"></td>
<td align="center">10</td>
<td align="center">ab x aa</td>
<td align="center">a,ab</td>
<td align="center">1:1</td>
</tr>
<tr class="even">
<td align="center"></td>
<td align="center">11</td>
<td align="center">ab x oo</td>
<td align="center">a,b</td>
<td align="center">1:1</td>
</tr>
<tr class="odd">
<td align="center"></td>
<td align="center">12</td>
<td align="center">bo x aa</td>
<td align="center">ab.a</td>
<td align="center">1:1</td>
</tr>
<tr class="even">
<td align="center"></td>
<td align="center">13</td>
<td align="center">ao x oo</td>
<td align="center">a,o</td>
<td align="center">1:1</td>
</tr>
<tr class="odd">
<td align="center">D.2</td>
<td align="center">14</td>
<td align="center">cc x ab</td>
<td align="center">ac,bc</td>
<td align="center">1:1</td>
</tr>
<tr class="even">
<td align="center"></td>
<td align="center">15</td>
<td align="center">aa x ab</td>
<td align="center">a,ab</td>
<td align="center">1:1</td>
</tr>
<tr class="odd">
<td align="center"></td>
<td align="center">16</td>
<td align="center">oo x ab</td>
<td align="center">a,ab</td>
<td align="center">1:1</td>
</tr>
<tr class="even">
<td align="center"></td>
<td align="center">17</td>
<td align="center">aa x bo</td>
<td align="center">ab,a</td>
<td align="center">1:1</td>
</tr>
<tr class="odd">
<td align="center"></td>
<td align="center">18</td>
<td align="center">oo x ao</td>
<td align="center">a,o</td>
<td align="center">1:1</td>
</tr>
</tbody>
</table>

Letters A, B, C, and D indicate the segregation type (i.e., 1:1:1:1,
1:2:1, 3:1 or 1:1, respectively), while the number after the dot (e. g.,
A.1) indicates the observed bands in the offspring. Therefore, this
information has to be in the input file at each line after the marker
ID. The coding for marker genotypes used by OneMap is also the same one
proposed by [Wu et al
(2002a)](http://ccb.bjfu.edu.cn/doc/sg2014/sg-wu-paper1.pdf) and the
possible values vary according to the specific marker type.

Below, an example of input file which must be saved as text format:

    cross type outcross
    10 5 0 0 0
    ID1 ID2 ID3 ID5 ID6 ID7 ID8 ID9 ID10
    *M1 B3.7    ab,ab,-,ab,b,ab,ab,-,ab,b 
    *M2 D2.18   o,-,a,a,-,o,a,-,o,o 
    *M3 D1.13   o,a,a,o,o,-,a,o,a,o 
    *M4 A.4     ab,b,-,ab,a,b,ab,b,-,a 
    *M5 D2.18   a,a,o,-,o,o,a,o,o,o 

Which can be imported to OneMap by the function `read_onemap`:

    ?read_onemap  #For more information about this function
    onemap_file_outcross <- read_onemap("C:/workingdirectory","example.out.txt")

The first argument of `read_onemap` function is the path to the file
directory and the second is the file name.

With the new function `vcf2raw` it is possible to convert VCF file
format to OneMap format for any of these experimental populations. Plus,
it will keep the position information of the marker at the genome (if it
is available in the VCF) and consider it when building the map.

For some VCF header formats, the function will require a compressed and
indexed VCF file. It can be done by the package
[tabix](https://sourceforge.net/projects/samtools/files/tabix/) that is
part of the [Samtools
software](https://sourceforge.net/projects/samtools/). It is also
available at the Bioconductor inside the package
[RSamtools](https://bioconductor.org/packages/release/bioc/html/Rsamtools.html).

    #Instaling RSamtolls package
    source("https://bioconductor.org/biocLite.R")
    biocLite("Rsamtools")

    #Usage
    library(Rsamtools)
    zipped_vcf <- bgzip("example.vcf", "example.vcf.gz") #Compressing
    idx <- indexTabix("example.vcf.gz", "vcf") #Indexing

The vcf2raw function have the parameters:

-   `input` path to the input VCF file;
-   `output` type of cross. Must be one of: "outcross" for full-sibs;
    "f2 intercross",for an F2 intercross progeny; "backcross"; "riself"
    for recombinant inbred lines by self-mating; or "risib" for
    recombinant inbred lines by sib-mating;
-   `cross` path to the output OneMap file;
-   `parent1` string or vector of strings specifying sample ID(s) of the
    first parent;
-   `parent2` string or vector of strings specifying sample ID(s) of the
    second parent;
-   `min_class` a real number between 0.0 and 1.0. For each parent and
    each variant site, defines the proportion of parent samples that
    must be of the same genotype for it to be assigned to the
    corresponding parent.

In our example we have a outcrossing population with parents Euc\_201
and Euc\_202. We do not have replicates for the parents, so the
“min\_class” parameter will not be used for us. To call the file in `R`:

    ?vcf2raw  #For more informations about the function
    vcf2raw(input = "example.vcf.gz", output = "example.raw", cross = "outcross", parent1 = "Parental_1", parent2 = "Parental_2")

Then we get the example.raw file:

    data type outcross
    3 15 1 1 0
    ID_1    ID_2    ID_3
    *44509    D1.10    a a a
    *38019    D2.15    a a a
    *89440    D1.10    a a a
    *115628    D2.15    a a a
    *124447    D1.10    ab - a
    *132982    D2.15    - ab -
    *155807    D1.10    ab a ab
    *161174    B3.7    ab ab ab
    *169671    B3.7    ab ab ab
    *196363    B3.7    ab ab ab
    *198491    B3.7    ab ab ab
    *226621    B3.7    ab ab ab
    *226621    B3.7    ab ab ab
    *255557    B3.7    ab a ab
    *296873    D1.10    ab - -
    *CHROM    Chr02 Chr02 Chr04 Chr05 Chr05 Chr06 Chr06 Chr07 Chr07 Chr08 Chr08 Chr09 Chr09 Chr11 scaffold_721
    *POS    5565755 43878360 25220824 44192326 64399699 16254627 56636423 1462089 32868350 37209043 41026941 28459570 28459594 12942418 994

The closing lines (begining with `*CHROM` and `*POS`) keep the reference
sequence ID and position for each variant site. The new version of
OneMap will be able to deal with this information in order to increase
the precision of the genetic map. This file is a input file to
`read_onemap` function.

Now you are good to go build your map on onemap package!

------------------------------------------------------------------------
