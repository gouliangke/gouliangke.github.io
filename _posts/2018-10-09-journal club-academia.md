---
layout: post
title:  "Journal Club -- discussion on antagonistic QTLs"
categories: Genetics
tags: QTL Genetics journal-club
author: Liangke G
academia: true
---
* content
{:toc}

We did a journal club discussing the paper "Tightly-linked antagonistic-effect loci underlie polygenic demographic variation in C. elegans " on bioRxiv.

## Summary of the paper 
In this paper Bernstein et al. used the experimental genetics to show most genomic regions carry variants with detectable effects on complex traits. They measured the fitness effects of Ceanorhabditis elegans under Nickel stress using a high-throughput phenotyping method that characterize demography as a multivariate trait in growing populations. 
We show that demography under these conditions is genetically complex in a panel of recombinant inbred lines. We then focused on a 1.4-Mb region of the X chromosome. When we compared two near isogenic lines (NILs) that differ only at this region, they were phenotypically indistinguishable. When we used additional NILs to subdivide the region into fifteen intervals, each encompassing ~0.001 of the genome, we found that eleven of intervals have significant effects. These effects are often similar in magnitude to those of genome-wide significant QTLs mapped in the recombinant inbred lines but are antagonized by the effects of variants in adjacent intervals. 



>
## What are RILs and NILs

Before we get to the details of their result, it is worthwhile to understand two important concept in the C. elegans mapping field, that is RIL and NIL. In this bioRxiv paper, Bernstain et al. give a great introduction of these two terms. Here I just quote their introduction:

"The ability to identify loci associated with trait variation is dependent on the constitution of the mapping population and the number of measurements. Two of the most commonly used types of mapping populations are recombinant inbred lines (RILs) and near-isogenic lines (NILs). RILs leverage genotypic replication across random backgrounds, whereas NILs control for background by holding it constant (Doroszuk et al., 2009; Eshed and Zamir, 1995; Keurentjes et al., 2007; Koumproglou et al., 2002; Shao et al., 2010). RILs provide an efficient way to survey the whole genome for loci with significant marginal effects across multiple backgrounds, but those multiple backgrounds also contribute phenotypic variation. Thus, when comparing the phenotype distributions for two genotype classes at a given genetic marker, RILs have abundant variation within each class due to segregating genetic effects. With NILs, those background effects are eliminated, providing greater power to detect differences between focal genotypes. Moreover, when alleles have effects only in certain backgrounds, their marginal effects, detected in RILs, may be quite modest and hard to detect; in NILs, where the background is fixed, epistatic effects are converted to all or none, depending on the background. "

<img src="https://github.com/gouliangke/myblog/raw/master/photos/1.png" height="250" />

(figure from "Tightly-linked antagonistic-effect loci underlie polygenic demographic variation in C. elegans ")

## Results in this paper

They used the N2 and CB4856 as the parental strains, and they identified significant difference between the parent strains in their demographies. N2 has more progeny and a greater proportion of the progeny were measured as adults, consistent with a developmental delay in CB4856 relative to N2. Then they performed multivariant QTL mapping in a RILs population, and identified 7 QTLs that influent the demography in the RILs.  Given the discrepancy between the estimated broad-sense heritabilities and the heritability explained by the detected QTLs, they propose one possible genetic model for our traits ascribes the unexplained heritable variation to a large number of variants spread across the genome. 

<img src="https://github.com/gouliangke/myblog/raw/master/photos/2.png" height="250" />
(figure from "Tightly-linked antagonistic-effect loci underlie polygenic demographic variation in C. elegans ")

They focused on a region on X chromosome, a chromosome that does not have detected QTL. They used a panel of 16 Near Isogenic Lines to test 15 consecutive intervals of 53-148 kb (that is, ~0.001 of the 100 Mb genome) spread along a 1.4 Mb region on the X chromosome, and they found that eleven of intervals have significant effects (or they called QTLs here). Their explanantion for this observation is in the RILs, the effects point in both directions for each trait, indicating that the NIL region harbors a mixture of antogonistic QTL. Each of these QTLs cancel out the effect of others.  

## Discussions 
We found this a very interesting paper, the experiments took large amount of effort and many replicates were conducted in the experiment. There are few points that we feel will improve the paper if the authors could address or control them more carefully. 

1.The reason that drive them focus on a non-QTL region is the QTLs they detected explained only a proportion of the estimated broad sense heritability. This could be a power issue that is caused by the small number of samples. The RIL they used had only 282 progenies. Increasing the number of samples, more and more heritability are expected to be explained by detected QTLs. 
2.It would be cool if there is a control group that is without the nickel stress treatment. We are curious about how the demography are different in the RILs and parents when there is no stress.
3.The statement will be more strong if at least some of the NILs were whole genome sequenced. Because any de-novo mutations existing in the background may interfere with the phenotype, and therefore potentially create some false positive QTLs in the NIL panel. 
