# fisher-test-for-genomic-overlaps

# Introduction

This is a combined bash/R script that will generate a Fisher test p-value that shows significance for the overlap of two sets of genomic regions (for example from ChIP-Seq experiments). 

To calculate Fisher p-value you would need three BED files:
1. First bed file to overlap, i.e. file1.bed
2. Second bed file for overlap, i.e. file2.bed
3. Bed file that will serve as genomic background for overlaps, i.e. background.bed

Note that file names do not have to be file1.bed, file2.bed, background.bed, this is just an example.

As genomic background you can use e.g. combined ENCODE set of open chromatin regions or a similar data set. Genomic background is necessary to calculate the constituents of the Fisher test contingency matrix: overlap of A and B in the background BG set, A but not B in BG, B but not A in BG, BG without A and B. 

We provide a combined ENCODE DHS data set in a bed file which you can use as a background set, background.bed.

# Dependancies

You need to run the script in bash shell, and you also need to have R installed, as well as Rscript that needs to be installed in the PATH folder /usr/bin/Rscript

# Example run

Run ./fishertest.sh with the three file names as subsequent multiple arguments

# Example output
./fishertest.sh file1.bed file2.bed background.bed

Number of uniq A overlapping B in genomic background

275

Number of uniq B overlapping A in genomic background

273

Number of uniq A not overlapping B in genomic background

36885

Number of uniq B not overlapping A in genomic background

3757

Number of genomic background not overlapping A or B

2233270

List of 7
 
 $ p.value    : num 9.42e-85
 
 $ conf.int   : atomic [1:2] 3.9 5.01
  ..- attr(*, "conf.level")= num 0.95
 
 $ estimate   : Named num 4.43
  ..- attr(*, "names")= chr "odds ratio"
 
 $ null.value : Named num 1
  ..- attr(*, "names")= chr "odds ratio"
 
 $ alternative: chr "two.sided"
 
 $ method     : chr "Fisher's Exact Test for Count Data"
 
 $ data.name  : chr "A_B" - attr(*, "class")= chr "htest"
