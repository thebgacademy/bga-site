---
title: Assembling Mitogenomes from PacBio HiFi reads using MitoHiFi
alias: MitoHiFi
date_created: 18_30-04-2024
data_modified: 18_30-04-2024
---
#BGA23/sessions #MitoHiFi #Assembly #Mitochondrion #PacBio #Pipeline #Workshop

> [!caution] This session may now be out of date so beware!!!
> This session is part of  [[tags/BGA23]]

## Session Leader(s)

Marcela Uliano-Silva  
Senior Bioinformatician, Wellcome Sanger Institute

## Description
[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/BGAcademy23/MitoHiFi)
GitHub:: https://github.com/BGAcademy23/MitoHiFi

By the end of this session you will be able to:

1. Run MitoHiFi using docker
2. Understand the different steps done by MitoHiFi
3. Understand intermediate outputs
4. Cases where the pipeline fails

## Prerequisites

1. Understand the terms genome assembly, reads, contigs, PacBio HiFi
2. Understand linux command line basics

> [!warning] !!! warning "Please make sure you MEET THE PREREQUISITES and READ THE DESCRIPTION above"
> 
> You will get the most out of this session if you meet the prerequisites above.
> 
> Please also read the description carefully to see if this session is relevant to you.
> 
> If you don't meet the prerequisites or change your mind based on the description or are no longer available at the session time, please email tol-training at sanger.ac.uk to cancel your slot so that someone else on the waitlist might attend.
> 
## Connecting to gitpod for the session

**[Click here to launch a Gitpod workspace with MitoHiFi](http://gitpod.io/#https://github.com/BGAcademy23/MitoHiFi)**


## Commands for the session

1. Let's assemble something pink (from reads, -r)
   
```
cd /workspace/lecture_examples/deilephila_porcellus

findMitoReference.py --species "Deilephila porcellus" --outfolder . --min_length 14000

mitohifi.py -r ilDeiPorc1.reads.100.fa -f NC_079697.1.fasta -g NC_079697.1.gb -t 1 -o 5
```

2. Let's do a bird (from contigs, -c)

```
cd /workspace/lecture_examples/cygnus_columbianus

findMitoReference.py --species "Cygnus columbianus" --outfolder . --min_length 14000

mitohifi.py -c bCygCol1.hifiasm.contigs.fa -f NC_007691.1.fasta -g NC_007691.1.gb -o 2 -t 3

```

3. Let's do a plant (from contigs, -c)

```
cd /workspace/lecture_examples/climacium_dendroides

findMitoReference.py --species "Climacium dendroides" --outfolder . --min_length 50000

mitohifi.py -c cbCliDend2.hicanu.contigs.fa -f NC_053886.1.fasta -g NC_053886.1.gb -t 6 -o 1 -a plant

```


