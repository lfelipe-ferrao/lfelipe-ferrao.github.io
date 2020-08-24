# HOMEWORK 1

## POPULATION GENETICS

### Install packages
```
source("https://bioconductor.org/biocLite.R")
biocLite("impute")
install.packages("snpReady")
```

### Question 1:

Read the [paper](https://bmcgenomics.biomedcentral.com/articles/10.1186/s12864-017-3805-4) and import the dataset

``` 
a = read.csv("/home/lferrao/Downloads/12864_2017_3805_MOESM2_ESM.csv",
         header = T,na.strings = "-")
``` 

### Question 2:
Produce a table similar to the Table 1. You can try to use the function ``table()`` to count the number of SNPs in each chromosome, for example. 


```
# ---- Marker by chr
chr.total = a$Chromossome
table(chr.total)

# Density of markers - Chr01
 
#Same command to run other chrs ("Chr02", "Chr03" ...)
idx = chr.total %in% "Chr01"
chr1.subset = a[idx,] #Selecting Chr01
max(chr1.subset$Chromossome.Position) # Chr size
mean_of_snp = 533/max(chr1$Chromossome.Position) # snp density
```

### Question 3: 

Using the `snpReady` package  (or another function) transform the SNP data into a 012 format. Just remember that `NN` nucleotides are missing data, so we can replace them for `NA`. 

```
# Transforming the data 
snp = a[,-c(1:15)] # Eliminate cols from 1:15
snp[snp == "NN"]<-NA # Missing data
rownames(snp) = a$SNP.name
snp012 = raw.data(t(as.matrix(snp)), frame = "wide", 
               base=TRUE,  imput = FALSE, 
               call.rate = 0.1, maf=0.0001) # 012 format
dim(snp012$M.clean) #181 ind  vs. 6286 SNPs
```
### Question 4:

Use the `popgen` function from the `snpReady` package to compute population genetic parameters. Compare to the values presented in the original paper and discuss -- in one paragraph -- how the results presented in the original paper could be useful for breeding programs.

```
# Metrics implemented in the snpReady
metric = popgen(M=snp012$M.clean)
head(metric$whole$Markers)
metric$whole$Population
metric$whole$Variability
```
Some results:

- H0 = 0.04
- F = 0.91
- Ne = 99.30

### Question 5:
Based on this data set, try to compute another population metric that might be important to describe the population. It may be one of the metrics already described in the paper (e.g., Fst, dendrogram, linkage disequilibrium) or any other that you judge important. Show the codes used to compute it and discuss an eventual importance of the proposed analysis in the context of the paper. Below, I am running a PCA analysis.

```
# Optional: Running a PCA 
snp012.imputed = raw.data(t(as.matrix(snp)), frame = "wide", 
                  base=TRUE,  imput = TRUE,imput.type = "mean", 
                  call.rate = 0.1, maf=0.0001)
G <- G.matrix(M = snp012.imputed$M.clean, method = "VanRaden", format = "wide") 
EVD<-prcomp(G$Ga) # PCA
summary(EVD)
group.evd = kmeans(EVD$rotation[,1:2],4)$cluster

library(ggrepel)
library(ggplot2)
data = data.frame (EVD$rotatio[,1:2],group = group.evd)

ggplot(data,aes(x= data$PC1, y=data$PC2, color=as.factor(data$group), label=rownames(data))) +
  geom_point(size=2.5, pch=21,color = "black",aes(fill=as.factor(data$group))) +
  #geom_smooth(method=lm, aes(fill=type), alpha=0.15)+
  scale_fill_manual(values=c("#386cb0","#7fc97f",'indianred1',"#fdb462"))+
  scale_color_manual(values=c("#386cb0","#7fc97f",'indianred1',"#fdb462"))+
  geom_label_repel(box.padding = 0.2, size=2.8) +
  theme_bw() +
  theme(legend.position="none",
        legend.title = element_blank())+
  xlab("PC1(8%)")+
  ylab("PC2(1%)")
```
