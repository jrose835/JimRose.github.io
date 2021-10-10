---
title: 'Using Rank to Compare Homer Motif Enrichments in Different Sets of ATACseq Data'
date: 2055-10-11
permalink: /posts/2021/10/ranking-homer-post/
tags:
  - Transciption factors
  - HOMER
  - Motif Enrichment
---

[HOMER](http://homer.ucsd.edu/homer/) is a fantastic tool used, primarily, to discover motifs within functionally annotated stretches of genomic data. These could be (most commonly) from ChIPseq or ATACseq datasets, which align important functional information--either the presence of particular proteins (ChIP) or overall accessibility of chromatin (ATAC)--to specific regions of the genome.  

Often we do this sort of analysis to infer potential for binding of particular transcription factors or factor families in a given set of genomic regions based on a statistical enrichment of the known binding motifs (or newly discovered ones). 

Today I'm going to share some of my experiences working with the results of HOMER, particuarly when trying to compare enrichments across sets of regions that vary dramatically in sample size.

### Some more background

HOMER enrichment for KNOWN MOTIFS works by first comparing target region sets to background regions as control. These background regions are selected randomly from the genome after matching for GC content of your target set. It then assigns weights for GC content, and sequence bias (imbalances of 1-mers, 2-mers, and 3-mers) to reduce noise, and ultimately calculates an enrichment p-value using the cumulative hypergeometric distribution. 

And it works great! Since this tool was introduced in 2010 it has been widely used to discover important biologically-relevant motifs in genomic datasets and has been cited over 7000 times as of the time of writing this post... 

### But here's the rub

### Ranking


Aren't headings cool?
------