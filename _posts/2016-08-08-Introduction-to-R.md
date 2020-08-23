---
layout: post
title: Introduction to R
description: "For beginners with focus on Bioinformatics and Genetics."
modified: 2016-08-16
tags: [tips, introduction, tutorial, R]
image:
  feature: LogoFundoAzul.jpg
  creditlink: http://augusto-garcia.github.io/
---

*Written by [Rodrigo Rampazo Amadeu](http://augusto-garcia.github.io/statgen-esalq/people/)*

Table of Contents:

-   [Purpose](#purpose)
-   [Installing R](#installing-r)
-   [Using R](#using-r)
-   [R as calculator](#r-as-calculator)
-   [Functions](#functions)
-   [R creating objects](#r-creating-objects)
-   [Vectors](#vectors)
-   [Creating vectors from scratch](#creating-vectors-from-scratch)
-   [Logical Operation](#logical-operation)
-   [Data frame](#data-frame)
-   [Matrices](#matrices)
-   [Lists](#lists)
-   [Importing and exporting data](#importing-and-exporting-data)
-   [Libraries](#libraries)
-   [Graphic Plotting](#graphic-plotting)
-   [Scatterplot](#scatterplot)
-   [Histogram](#histogram)
-   [Density](#density)
-   [Boxplot](#boxplot)
-   [Boxplot by cylindrade](#boxplot-by-cylindrade)
-   [Costumizing your graphics](#costumizing-your-graphics)
-   [Exporting a graphic](#exporting-a-graphic)
-   [Exploring your data](#exploring-your-data)
-   [Exploring matrices](#exploring-matrices)
-   [Fitting Linear Models: a genetic simple
    example](#fitting-linear-models-a-genetic-simple-example)
-   [Simulating data](#simulating-data)
-   [Simulating data](#simulating-data-1)
-   [Correlation plot](#correlation-plot)
-   ["for"](#for)
-   ["if"](#if)
-   ["for" with vectors](#for-with-vectors)
-   [One simple way to apply on genetics: Recoding a genotype
    vector](#one-simple-way-to-apply-on-genetics-recoding-a-genotype-vector)
-   [Saving and loading your
    progress](#saving-and-loading-your-progress)
-   [About it](#about-it)

This short-course was made by Rodrigo Rampazo Amadeu from the
[Statistical-Genetics Laboratory](http://statgen.esalq.usp.br),
Department of Genetics, Luiz de Queiroz College of Agriculture,
University of Sao Paulo, Brazil and was first applied on a Introduction to R workshop.

You can found complete courses at:

-   [Coursera](https://www.coursera.org/learn/r-programming)

-   [Datacamp](https://www.datacamp.com/courses/free-introduction-to-r)

-   [TryR](http://tryr.codeschool.com/)

-   Or installing the [swirl](http://swirlstats.com/) package

You can found a great primer presentation about R
[here](https://augusto-garcia.github.io/R-Introduction).

There are a lot of good tutorials files on web.

-   [CRAN's R Introduction](https://cran.r-project.org/doc/manuals/r-release/R-intro.pdf)

-   [Verzani's simpleR](https://cran.r-project.org/doc/contrib/Verzani-SimpleR.pdf)

-   [Torfs & Brauer's Short R Introduction](https://cran.r-project.org/doc/contrib/Torfs+Brauer-Short-R-Intro.pdf)

-   Or just [Google R](https://www.google.com.br/search?q=R)!

Purpose
-------

The idea of this course is to present the basic commands and concepts
about the R language for genetic and bioinformatic students.

    #Everything typable in R is be presented inside boxes.
    #First lesson, if you run on R a line starting with # it will not run. # for comments.

Installing R
------------

Install R, we strongly advise you to use RStudio for your firsts R
contact. To install it go to
[RStudio](https://www.rstudio.com/products/rstudio/download/) and follow
the instructions.

Using R
-------

Open R, if you are using RStudio you need to create a new script
pressing the green plus symbol on the top left corner. Then, you will
see a script window and a console window, all the commands here is to be
used and wroted on the console window. We strongly advise you to write
it down on the script window and press *run* line by line on the top
right corner (shortcut: `Ctrl+Enter`). In this way you can
save and track all of your code. Try to write on the script and to run the following lines.

R as calculator
---------------

Sum

    3+3   #I can comment or annotate my scripts by writing after the # sign

Divide

    (3+3)/3

Square Root

    9^0.5 #or
    sqrt(9)

Exponent

    2^10

Logaritm

    log(10)
    log(10,base = 10)
    log(10,base = 2)

Exponential *e*

    exp(2)

Tip: Keep in mind to save your script as your work progress. To do it, just press `Ctrl+s`.

Functions
---------

There are a lot of functions in R. A function is represented by a name
and can be used calling it names followed by arguments. To visualize
what a function does, you can type `?functionname`, for example:

    ?log

If you are using Rstudio this command you change a window in the right
side of your screen, if not, probably you are going to see a pop-up
window in your screen. This new window says what the function `log`
does. Mainly in the help there is a description, the usage, and the
arguments of it. For example, this function has the arguments x (which
has to be a numeric or complex vector), and base.

Other functions good to know, try to use them!

    ?seq
    seq(from=0, to=100, by=3) #we can write in this way, or
    seq(0,100,3) #make sequence

    ?rep
    rep(x=1,times=3) #or
    rep(1,3)

R creating objects
------------------

To create a object use the following syntax:

    x = 10

Your object name 'x' followed by '=' and then your variable. In some
script you will see this '&lt;-' symbol, '&lt;-' gives you the same
result as '='.

Now, everytime you call (type) 'x' you we receive 10. For example,

    x*2
    x+x
    x^x
    log(x,x)
    x%%3 #module operator

You can also have a character object (which can not be used in math
operations):

    x_name = "name"

You can call it in the same way:

    x_name

To see which type your object is:

    class(x_name)
    class(x)

Pay attention, R is case-sensitive (*i.e.* 'X' is different than 'x').
When in doubt, write everything of your script in lower case.

You can track all your created objects typing 'ls()'.

Another important class is the logical whice can be TRUE or FALSE. For
example:

    1<0 #is 1 greater than 0? FALSE
    1==0 #is 1 equal 0? FALSE
    1>0 #is 1 lower than 0? TRUE

Pay attention here, '==' is different than '='!

This logical operation can be wrote in an R object

    z=1<0

Vectors
-------

A vector can be create using the following syntax:

    x = c(1.5,2.1,2.5,3.4,4.3,6.1) #A vector with numeric value
    y = c("A","A","B","B","C","C") #A vector with character values

The above line will create: the 'x' vector with 6 numeric objects, and
the 'y' vector with 6 character objects. To visualize this information
in a fashion way you can use the function `str`. To visualize a specific
object you can use:

    x[6] #the sixth object of vector x
    y[2] #the second object of vector y 

This function is really powerful when working with big data, keep it in
mind, it gives you all the `str`ucture of the object. Keep in mind, a
vector can has only *one* type of data, for instance character or
numeric.

    str(x) #a vector with 6 numeric objects (1:6)
    str(y) #a vector with 6 character objects (1:6)

Notice that you replace the old x object by this new one. Be careful
when naming your objects. With vector, you can make more complex
calculus.

    sum(x) #the sum of the vector objects
    mean(x) #the mean of the vector objects
    var(x) #the variance between the vector objects
    sum(y) #returns error, because y is not numeric

We can combine 'y' and 'x' in a more complex function structure. For
example with the 'tapply' function. In this function first you choose
your atomic object (vector x), following by your index (vector y), and
then for the function you want to use. Foe example:

    tapply(x,y,sum) #Compute the sums of x by each y categorie
    tapply(x,y,mean) #Compute the means of x by each y categorie
    tapply(x,y,var) #Compute the variance of x by each y categorie

Now, with this tools we can build a dice for example!

    #Create a object called dice and put a vector with number from 1 to 6 by 1.
    dice = seq(1,6,1)
    #Sample 1 number from the object dice
    sample(dice,1)

Creating vectors from scratch
-----------------------------

You can also create vectors with this following functions:

    ?rep
    rep(1,10) #Creates a vector of 1s repeated 10 times
    rep(NA,5) #Creates a vector of NAs repeated 5 times

    ?seq
    seq(1,10,1) #Creates a vector from 1 to 10 by 1 of interval
    seq(1,10,0.1) #Creates a vector from 1 to 10 by 0.1 of interval

    ?sample
    sample(seq(1,10,0.1),4) #Sample from the seq(1,10,0.1) 4 numbers

Obviously, you can save this vector on a object, for example:

    my_vector = seq(1,10,1)

Logical Operation
-----------------

We can build a logical vector, for example:

    z <- x>3 #Which x is grater than 3
    class(z)

If you call the object 'z' (writing `z` on console and pressing `enter`)
you will see which values of x is grater than 3. The logical expressions
is very useful when combining with another functions. For example, with
function 'which'. This function returns the exact position of the vector
it has TRUE values. Combined with brackets '\[\]', it can return which
values in x is greater than 3.

    which(z) #The TRUE is in position 5 and 6.
    x[which(z)]

Now it is your turn, using logical operations, the which function, and
brackets, extract out of vector x the numbers lower than 4.

Data frame
----------

We can combine vectors of same lenght in a data frame, to combine x, y,
and z vectors, now renamed to Yield, Individual Name and Rust Absence:

    df = data.frame(Yield=x,Ind=y,Rust=z)

Data frames is a versatile way to combine vectors of different classes
in a single object. You can access the different vectors using the
operator $. For example:

    df$Yield
    df$Ind
    df$Rust

When combining a character vector in a data frame it will be turned as a
factor. In this data frame notation, you can use the same codes earlier
seen. For example for extract the mean using y as index.

    tapply(df$Yield,df$Ind,mean)
    tapply(df$Yield,df$Rust,mean) #see what is going on here

Matrices
--------

We can combine vectors of same length and same class in a matrix, we
have to define the number of rows, the number of columns and the
direction to read the data. Look all the differencs on the below lines.

    x #visualizing your x vector
    matrix(x,nrow=3,ncol=2,byrow=TRUE)
    matrix(x,nrow=2,ncol=3,byrow=TRUE)
    matrix(x,nrow=3,ncol=2,byrow=FALSE)
    matrix(x,nrow=2,ncol=3,byrow=FALSE)

Of course, we can save this matrix as a object

    X <- matrix(x,nrow=3,ncol=2,byrow=TRUE) #note X is different than x (lower case)
    dim(x) #to check the dimension of X

To select a specific object inside this matrix you can use the following
notation:

    X[3,1] #The element of third row and first column
    X[3,] #All the elements of third row
    X[,1] #All the elements of first row
    X[1:2,] #A matrix with all elements of first and second rows

If it is a matrix of numeric objects you can do matrix algebra. For
example:

    t(X) # transpose of X (X prime)
    t(X) %*% X # transpose of X times X
    X*X # element-wise multiplication
    X + 1 #add 1 to all elements of X
    2*X #multiply all elements of X by 2
    solve(t(X) %*% X) # inverse of transpose of X times X
    solve(t(X) %*% X) + 1 # inverse of transpose of X times X plus 1

Lists
-----

We can combine different objects with variable format and lengths in a
list.

    everything <- list(df=df,
                      X=X)

The object everything is a list with two objects: a data frame and a
matrix, you can double-check it using `str()` function:

    str(everything)

To access the information inside a list you can use $ as in data frames.

    everything$x

Or you can use an indicator of the level your information is. For
example, to access the first object of the first level of your list
(*i.e.* x vector):

    everything[[1]]

If you want to access the second object of the first level object of
your list (*i.e.* the second object of x):

    everything[[1]][[2]]

If you want to access the third object of the second level object of the
first level object of your list (*i.e.* the second object of x):

    everything[[1]][[2]][[3]]

And this classification goes on. Now try to access the fifth value of
vector x using this approach.

To add a new object in a list, be sure in what level you are working
with.

To add a new vector inside the data frame (first object of everything):

    everything[[1]][[4]] = c(1,2,3,4,5,6)

To create a new third object:

    everything[[3]] = c(1,2,3,4,5,6)

To add 1 on this new object:

    everything[[3]] = everything[[3]]+1

An important guide to play with data frames in the function str().

    str(everything)

This function print the structure of your data frame and show all the
categories of it. Be familiar with lists, almost every data is handle in
this format.

Importing and exporting data
----------------------------

First download the data at
[here](https://raw.githubusercontent.com/rramadeu/Tutorials_File/master/Intro_R/data.csv).
To read the data, first you need to set up your working directory of R
as the same of your file is. It is a good procedure to create a folder
to every different R job you are working, after creater this folder and
put your data there, set it as your working directory. If you are using
Rstudio, it is easy go to *Session -&gt; Set Working Directory -&gt; To
Source File Location* and select the folder your file is. Otherwise, you
can use the function of set work directory (`setwd()`), the arguments of
the folder file using this function can be slightly different depending
upon your operational system. To make of the syntax type getwd() and
follow the same syntax it shows. Use a specific folder for a specific
project/course, please do not mess up your R files with different
courses and projects. Additionally let\`s save your script, go to *File
-&gt; Save As* and save at the same folder of your data is. Another
advise is AVOID empty space in your file names, this will save you some
time. Replace them for underline \*\_\* or dash *-*.

Example of 'setwd' function (if you used the easy way of RStudio, skip
this chunk), pay attention here, it depends on your current OS. If you
do not know how to declare it, go to the folder you want to work and
look its properties.

    getwd()
    setwd("Rodrigo/Intro_R/") ##fill with your path to archives

Reading the data, if you can choose, choose csv format files, they are
easy to read and understand. Before you call it in R, pay attention in
what the exactly way your data is. For example in the 'data.csv' file,
the data has 2 vectors with column names ('header') and our missing data
('na.strings') is coded as -9.

    read.table("data.csv")
    read.table("data.csv",header = TRUE, na.strings=NA)

Saving the table in a object:

    data = read.table("data.csv",header = TRUE, na.strings=NA)

If you want to save this object in a csv file:

    write.table(data,file="data_export.csv")

Look at the file you create and notice the differences between it
(`data_export.csv`) and `data.csv`. To let it in the same format we have
to use some additional arguments of the function:

    write.table(data,file="data_export.csv",row.names=FALSE,quote=FALSE,na="NA")

Now we have a copy of the file originated created. The default field
separator is " " (single space), if you want comma as separator, just
add 'sep=","' on the arguments. Pay attention in what you are writing
and reading, this can drag a lot of minor errors in your data analysis.

Libraries
---------

Library is a set of functions and dataset you can add to your base R.
Some libraries were already installed with your base R and someothers
have to be installed. The most famous package repository is the
[CRAN](https://cran.r-project.org/), to install a package from there you
need to type `install.packages("packagename")`. In bioinformatics, the
repository [Bioconductor](https://www.bioconductor.org/) is a very
useful, to install a package of it please go to the webpage of the
repository and follow the instruction. After installed, you have to call
the library to use its functions and datasets. On the next section we
will use data from the *datasets* package, which should be already
available with your R. To use this package type:

    library(datasets)

Graphic Plotting
----------------

There are several types of graphics in R. We will present some of the
most used ones. We will use the data `mtcars` from the library
*datasets*. To look all the data from this package go to
<https://stat.ethz.ch/R-manual/R-devel/library/datasets/html/00Index.html>.

    data(mtcars) #Now mtcars is an object
    ?mtcars #To look the data description
    mtcars #To look the data

Scatterplot
-----------

To plot a scatterplot graphic (x × y graphic) where x will be *mpg*
(Miler/Gallon) and y will be number of *hp* (Gross horsepower)

    plot(x=mtcars$mpg,y=mtcars$hp)
    #Changing title (main) and axis label (xlab and ylab)
    plot(x=mtcars$mpg,y=mtcars$hp, main="Scatterplot mpg x hp", xlab="mpg", ylab="hp")

Histogram
---------

    hist(x=mtcars$mpg, main="Histogram of mpg", xlab="mpg")

Density
-------

    plot(density(mtcars$mpg), main="Density", xlab="mpg")

Boxplot
-------

    boxplot(x=mtcars$mpg, main="Boxplot of mpg", xlab="mpg")

Boxplot by cylindrade
---------------------

In this case we use `x ~ y` which means x as function of y. For example:

    boxplot(mtcars$mpg ~ mtcars$cyl, main="Boxplot of mpg", xlab="mpg")

Costumizing your graphics
-------------------------

You can see some examples on

    demo(graphics)

Exporting a graphic
-------------------

You can save a graphic using the RStudio interface, after plot it just
click on export at the same window of the plot, and follow the
instructions. Another way to do it, it is from the command line, for
example to save a png graphic first you need to create a png file with
the function `png`, then plot your graphic, and at last close your png
file with `dev.off()`. For example:

    png(filename = "Rplot.png",
        width = 480, height = 480)
    boxplot(mtcars$mpg ~ mtcars$cyl, main="Boxplot of mpg", xlab="mpg")
    dev.off()

There are several ways and formats to save a R graphic, all the ways
follow those paths, create a file, plot, close the device. `?png` to
more information about it.

The graphics here presented are the basic ones, you can make better ones
with the package `ggplot2` and interactive ones with package `shiny`.

Exploring your data
-------------------

Beyond the graphical exploration we can do some descriptive analysis in
our data:

'summary' function to get the quartiles and mean values.

    summary(mtcars$mpg)
    summary(mtcars$cyl)
    tapply(mtcars$mpg,mtcars$cyl,summary) #summary of mpg within cyl 

To regress mpg against hp you can use the 'lm' function which fit linear
models. If your objective is fit a posterior analysis of variance for
stratum (factors), you have to use the 'aov' function.

    model = lm(mtcars$mpg ~ mtcars$hp) # '~' means 'is function of'
    summary(model) # ANOVA of the model
    plot(model) # To look the residual graphics

    plot(x=mtcars$hp,y=mtcars$mpg) #plotting the points
    abline(model) #to plot the curve
    cor(mtcars$cyl,mtcars$mpg) #correlation between x and y

With you want compare mpg with cyl (as factor)

    model = aov(mtcars$mpg ~ as.factor(mtcars$cyl)) # '~' means 'is function of'
    summary(model) #ANOVA
    plot(model) # To look the residual graphics

For multiple comparision (*e.g.* Tukey test), you can use the 'TukeyHSD'
function.

    TukeyHSD(model)

If you want a more presentable Tukey test, you can use this same test of
other packages. For example, the 'agricolae' package. To use it, you
need first to install it. After installed, you need to call it with
'library' function. Note that is a quite different to use compared with
'TukeyHSD' function, everytime you will use a new function look at its
help or google about it. In some cases it can be confuse to use new
functions! In the case of Tukey function of 'agricolae' package, we need
to declare de mean square of residuals and its degree of freedom.

    install.packages("agricolae")
    library(agricolae)
    (HSD.test(y=mtcars$mpg,trt="mtcars$cyl",MSerror=10.39,DFerror=29))

Exploring matrices
------------------

To look a covariance matrix within a data frame

    x=cov(mtcars)
    heatmap(x, Rowv = NA, Colv = NA, scale = "row")

Fitting Linear Models: a genetic simple example
-----------------------------------------------

On the next chunk we fit a model using genotypes and phenotypes
information. On the first model we fit a model considering genotype as
factor, on the second model we fit the genotype as numeric, try to
understand what is going on on both examples. On regresion analysis, the
default on R is to consider the first level of the factor as the
intercept. From <http://augusto-garcia.github.io/R-Introduction/>.

    genotypes = c("AA", "aa", "aa", "Aa", "AA", "Aa")
    phenotypes = c(9, 4, 3, 7, 10, 8)

    genotypes = as.factor(genotypes)
    phenotypes = as.numeric(phenotypes)

    str(genotypes)
    str(phenotypes)

    model = lm(phenotypes ~ genotypes)
    model
    summary(model)

    genotypes = as.numeric(genotypes)
    model = lm(phenotypes ~ genotypes)
    summary(model)
    tapply(phenotypes, INDEX = genotypes, FUN = mean)

    plot(y=phenotypes,x=genotypes)
    abline(model)

    plot(y=phenotypes, x=genotypes, xaxt="n")
    abline(model)
    axis(side=1,at=seq(1,3,1))

Simulating data
---------------

[Here](http://www.stat.umn.edu/geyer/old/5101/rlook.html) you can find
several probability density functions that R can handle. The core idea
on simulating data from this distributions is to know what each of this
4 family functions does (`r`,`p`,`q`,and `d`). Knowing this, you can
simulate or extract data from every probability density function. Here
we present the 4 functions of the normal (Gaussian) distribution:

    #Normal Distribution
    ?rnorm #the first argument is from the family and the following 2 are mean and standard deviation

    #Distribution Family functions
    rnorm(10,0,1) #“r”: random, randomly generated numbers
    pnorm(0,0,1) #“p”: probability, cumulative density function
    qnorm(0.5,0,1) #“q”: quantiles, cumulative density function (quantiles)
    dnorm(1,0,1) #"d": density, height of the probability density function

Simulating data
---------------

Plotting it in a histogram.

    hist(rnorm(1000,0,1))

If we use `set.seed` function, before a sample, we fix the next sample,
so every time we run this script it will sample the exact same values if
`set.seed` has the same seed (in this case `100`)

    set.seed(100) #set seed you will fix the next sample
    hist(rnorm(1000,0,1))

Correlation plot
----------------

Here we present how to simulate data, to build and to export a
correlation plot. First we sample from a Normal Distribution 50 values
and saved them on vector A. Then, based on this vector we sum or
substract values with the objective to create some correlated data. The
vector F has no priori correlation with the others vectors. With this
data we computed the correlation and made the plot.

    ## Correlation Plot
    library(corrplot)
    A = rnorm(50,10,6)
    B = -(A-rnorm(50,10,2))
    plot(A,B)

    C = B+rnorm(50,2,3)
    plot(A,C)
    plot(B,C)

    D = -(C+rnorm(50,1,3))
    plot(C,D)

    E = D+rnorm(50,3,5)
    plot(D,E)

    F = rnorm(50,10,10)
    plot(F,D)

    #Getting the correlation between A and B, full formula:
    var(A,B)/sqrt((var(A)*var(B)))

    #Getting the correlation A and B, reduced function
    ?cor
    cor(A,B)

    #Getting the correlation matrix (A,B,C,D, 'n F):
    cor.matrix = cor(data)
    cor.matrix

    #Changing the method
    corrplot(cor.matrix, method="color")

    #Corr value inside the cell (black for the color of the coef.)
    corrplot(cor.matrix, method="color", addCoef.col="black")

We can export a graphic with high quality determining how many dot per
inches we want (dpi). In the following chunk we export a graphic in TIFF
format with 300 dpis:

    ## Exporting a graphic with high quality
    tiff(filename = "Rplot.tiff", width = 5, height = 5, units="in", res=300)
    #Corr value inside the cell (black for the color of the coef.)
    corrplot(cor.matrix, method="color", addCoef.col="black")
    dev.off()

"for"
-----

Using `for` is a great way to do repetitive tasks in R, it shorts your
script and saves your time. We will present some basic loop ideas and
concepts. In the following `for`, you have a counter letter `i` which
starts on 1 and goes to 10, 1 by 1. Each loop will add 1 to your object
`x`. If your `x` is 0 as here stated, after the loop will be
10. In other words, you will add one on x ten times.

    x=0
    for( i in 1:10){
      x = x+1
    }
    x

A big help of the `for` structure is the function `print`, you can use it
to print on console what is going on on your loop and let you track your
loop. For example:

    x=0
    for( i in 1:10){
      x = x+1
      print(i)
    }
    x

In the `for` above, you print the `x` value of after adding 1 inside each loop. You can also print your object within the loop (if your object is not too big). For example:

    x=0
    for( i in 1:10){
      x = x+1
      print(i)
      print(x)
    }
    x

Notice that the print order is first `i` and then `x` (on this case they are equal). You can also use a explicit print way using the function
`paste`:

    x=0
    for( i in 1:10){
      x = x+1
      print(paste("i=",i))
      print(paste("x=",x))
    }
    x

"if"
----

Using `if` is a great way to make alternative routes in your script.
Attention, inside a `if` structure has to have a logical object, if it
has a non-logical object it will be interpreted as TRUE. In the
following example we verify if the `x` number is `0`, if yes, print
`x is equal to 0`.

    ## If 1
    x=0
    if(x==0){
      print("x is equal to 0")
    }

In the following example we verify if the `x` number is `0`, if yes,
print `x is equal to 0`, if not, print `x is different to 0`.

    ## If 2
    x=0
    if(x==0){
      print("x is equal to 0")
    }else{
      print("x is different to 0")
    }

In the following 2 examples we scan a vector from x to x+10 and verify
each one is even and each one is odd, and print the condition. The first
example uses 2 ifs and the second uses if and else.

    # For + If
    x=0
    for(i in 1:10){
      if(x%%2==0){
        print(paste(x,"is even"))
      }
      if(x%%2==1){
        print(paste(x,"is odd"))
      }
      x=x+1
    }

    x=0
    for(i in 1:10){
      if(x%%2==0){
        print(paste(x,"is even"))
      }else{
        print(paste(x,"is odd"))
      }
      x=x+1
    }

"for" with vectors
------------------

In the following `for` we are checking which number of a given vector is
even and which is odd, if it is even multiply by 10, else multiply by
100.

    x = c(1:20) #1:20 means build a vector with numbers from 1 to 20
    j = length(x) #function length return the length of the object, in this case 20
    for( i in 1:j){
      if( x[i]%%2 == 0){
        x[i] = 10*x[i]
      }else{
        x[i] = 100*x[i]
      }
    }
    x #looking the result

When using `for` and `if` structures pay attention on the opening and
closing brackets. On RStudio you can track the opening/closing brackets
letting your text cursor on it. It is a good programming skill to keep
the indentation of the script growing up as it goes deeper on the if/for
structures and, of course, comment your code!

One simple way to apply on genetics: Recoding a genotype vector
---------------------------------------------------------------

Here we have a vector with AA, Aa, aa, and . (missing data) and we want
to recode it to 2, 1, 0, and NA. First we extrach how many objects are
in our genotype vector, then we create a vector of NAs which will
receive the new values, and, finally, we do the for with ifs.

    genotypes = c("AA", "aa", "aa", "Aa", "AA", "Aa",".")
    n = length(genotypes)
    genotypes_recoded = rep(NA,n)

    for(i in 1:n){
      if(genotypes[i]=="aa"){
        genotypes_recoded[i] = 0
      }
      if(genotypes[i]=="Aa"){
        genotypes_recoded[i] = 1
      }
      if(genotypes[i]=="AA"){
        genotypes_recoded[i] = 2
      }
    }

Clearly there are many other ways to do the calculations above
presented, in better and fasters ways, this
[post](https://www.r-bloggers.com/strategies-to-speedup-r-code/) presents
some tips to speedup our loops, however some basic knowledge is
required.

Saving and loading your progress
--------------------------------

If you have to stop your work or are afraid to lose the current
progress, save a image of all your R objects. To do it. If your Rdata
files are not too big, try to not overwrite them as you work on your
script and to named in a sequential way so you can track your progress
and keep backups.

    save.image("today_date.Rdata") 

    load.image("today_date.Rdata")

Keep in mind to save your script as your work progress. To do it, just press `Ctrl+s`.

About it
--------

We are currently writing this course, if you find any mistake (including
misspelling ones) or want to add something else please drop us an email
at *rramadeu at gmail dot com*. This material is written using
*RMarkdown*.

    sessionInfo()

    ## R version 3.2.2 (2015-08-14)
    ## Platform: x86_64-pc-linux-gnu (64-bit)
    ## Running under: Ubuntu 15.10
    ## 
    ## locale:
    ##  [1] LC_CTYPE=pt_BR.UTF-8       LC_NUMERIC=C              
    ##  [3] LC_TIME=pt_BR.UTF-8        LC_COLLATE=en_US.UTF-8    
    ##  [5] LC_MONETARY=pt_BR.UTF-8    LC_MESSAGES=en_US.UTF-8   
    ##  [7] LC_PAPER=pt_BR.UTF-8       LC_NAME=C                 
    ##  [9] LC_ADDRESS=C               LC_TELEPHONE=C            
    ## [11] LC_MEASUREMENT=pt_BR.UTF-8 LC_IDENTIFICATION=C       
    ## 
    ## attached base packages:
    ## [1] stats     graphics  grDevices utils     datasets  methods   base     
    ## 
    ## loaded via a namespace (and not attached):
    ##  [1] magrittr_1.5    formatR_1.4     tools_3.2.2     htmltools_0.3.5
    ##  [5] yaml_2.1.13     Rcpp_0.12.6     stringi_1.1.1   rmarkdown_1.0  
    ##  [9] knitr_1.13      stringr_1.0.0   digest_0.6.9    evaluate_0.9
