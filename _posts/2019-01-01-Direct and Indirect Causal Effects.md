---
layout: post
title:  "Direct and Indirect Causal Effects"
categories: Statistics
tags: causal-inference statistics
author: Liangke Gou_
academia: true
mathjax: true
---

* content
{:toc}


<img src="https://raw.githubusercontent.com/zj-zhang/picture_store/master/2019-01-dosage-causal-inference/f1.png" width="500" height="300" />


>
**Figure 1**. Overview of LRC-CPPT data in a) treatment and b) control groups. Figure from *Jin and Rubin 2008*.
>




**TL;DR**: Causal effects are comparisons of potential outcomes under different treatment on a common set of units. The use of the concept of ‘direct’ versus ‘indirect’ causal effects is common in statistics, social, economics, and biomedical fields. The most straightforward way to clarify the direct and indirect causality is by using potential outcomes to define causal effects. Here we use two example studies to illustrate the widespread acceptance and application of the potential outcomes framework, also known as the Rubin causal model (RCM), in direct and indirect causal inference.

### 1. Introduction of direct and indirect causal inference 

Causal inference is the process of drawing a conclusion about a causal connection based on the conditions of the occurrence of an effect. The main difference between causal inference and inference of association is that causal inference analyzes the response of the effect variable when the cause is changed while the association revealed the correlation of two variables. Correlation does not imply causation, so further methods must be used to infer causation. Common frameworks for causal inference are structural equation modeling and the Rubin causal model. The Rubin causal model, also known as the Neyman–Rubin causal model, is an approach to the statistical analysis of cause and effect based on the framework of potential outcomes, named after Donald Rubin. The name "Rubin causal model" was first coined by Rubin's graduate school colleague, Paul W. Holland, but it has roots in the context of randomized experiments with randomization-based inference in the work of Neyman (1923) and Fisher (1925).

<img src="https://raw.githubusercontent.com/zj-zhang/picture_store/master/2019-01-dosage-causal-inference/f2.png" width="100%" height="100%" />
>
**Figure 2**. Relationships between treatment assignment, compliance and outcome as formulated by Efron and Feldman (1991).
>

Having demonstrated the underlying assumptions, Efron and Feldman formulated their model accordingly. The overall goal of the modelling is to estimate a true drug dose-response function $\delta(X)=E[Y_x-Y_0]$. The expectation was defined as the appropriate averages over a population U, so $E[Y_x-Y_0]=\sum(Y_x(u)-Y_0(u))/N$, where u is an individual from a population U, and N being the number of elements in U. This is also called average causal effect of X on response by Rubin and Holland. Based on the data distribution in **Figure 1**, the compliance was assumed to have a linear relationship with the cholesterol reduction in the Control group, z. For differences between outcomes in the Treatment and Control groups, denoted by D(z)=T(z)-C(z), was modeled quadratically as $D(z)=d_1\cdot z+d_2\cdot z^2$. If there is no interaction between the dose X and the placebo effect $y_0$ and the outcome  is purely additive of X and $y_0$, then the true dose-response function $\delta(z)=D(z)$; otherwise, the true dose-response function  depends on another continuous function H(x) that we need to specify. In the Efron-Feldman paper, the authors specified $H(x(u))=h_1 \cdot z$ and $x=s(u)\cdot z(u)$. This is basically modelling the individual-specific baseline level is likely to affect the outcome after conditioned on the dosage. The authors also commented that the interaction term has one degree of freedom, similar to Tukey’s test for interactions in a two-way ANOVA study without replication; therefore, specifying the interaction term will enable more sensitive statistical tests.

One pitfall of the Efron-Feldman model is in their transformation of the Control group compliance in order to satisfy "Perfectly Blind" assumption. In the LRC-CPPT data, the compliance distribution in Treatment and Control groups were clearly different (**Figure 3**). However, since the Efron-Feldman model assumes no interaction between treatment assignment and the compliance (**Figure 2**), the model asserts the compliance between the two groups should be identical; subsequently, the Control group compliance values were rank-transformed to match their counterparts in the Treatment group. As we will see in the next section, this somewhat overly restrictive assumption was corrected in the Jin-Rubin model of principal stratification.

<img src="https://raw.githubusercontent.com/zj-zhang/picture_store/master/2019-01-dosage-causal-inference/f3.png" width="50%" height="50%" align="middle"/>
>
**Figure 3**. QQ-plot for observed drug compliance and placebo compliance in the LRT-CPPT data.
>

 
### 2.The Rubin causal model

The Rubin causal model (RCM) is a formal mathematical framework for causal inference, first given that name by Holland (1986). The potential outcomes framework was first proposed by Jerzy Neyman in his 1923 Master’s thesis, but he discussed it only in the context of completely randomized experiments. Rubin, together with other contemporary statisticians, extended it into a general framework for thinking about causation in both observational and experimental studies. Paul W. Holland showed the Rubin causal model in experiments and observational studies is enlarged to analyze the problem of “causes causing causes” and is compared to path analysis and recursive structural equations models in 1986. In Holland’s paper, he used a special quasi-experimental design, the encouragement design, to give concreteness to the discussion of causal models by focusing on the simplest problem that involves both direct and indirect causation. Rubin’s model is shown to extend easily in this situation and to specify conditions under which the parameters of path analysis and recursive structural equations models have causal interpretations (Holland 1988).

There are two essential parts to the RCM, and a third optional one. The first part is the use of ‘potential outcomes’ to define causal effects in all situations. The second part is an explicit probabilistic model for the assignment of ‘treatments’ to ‘units’ as a function of all quantities that could be observed, including all potential outcomes. This model is called the ‘assignment mechanism’, and defines the structure of experiments designed to learn about the science from observed data or the acts of nature that lead to the observed data. The third possible part of the RCM framework is an optional distribution on the quantities being conditioned on in the assignment mechanism, including the potential outcomes, thereby allowing model-based Bayesian ‘posterior predictive’ (causal) inference (Imbens and Rubin 2010).

<img src="https://raw.githubusercontent.com/zj-zhang/picture_store/master/2019-01-dosage-causal-inference/f5.png" width="50%" height="50%" align="middle"/>
>
**Figure 5**. Posterior mode for Principal causal effects. Figure from *Jin and Rubin (2008)*.
>


### 3.The example of randomized trials of anthrax vaccine 

In the rest part of this mini review, two examples will be provided to show the cases where Rubin causal model works flexibly, while the traditional variant component analysis may give the non-interpretable conclusions. The first example is the anthrax vaccine analysis. 

Two sets of randomized placebo-controlled trials on anthrax vaccine are being conducted by the United States Centers for Disease Control and Prevention (CDC). This experiment involves human volunteers with extensive reactogenicity measurements and extensive immunogenicity measurements (e.g. blood antibody levels) after vaccination regimens. A parallel second trial was on macaques with parallel immunogenicity measurements, plus survival when challenged with a dose of anthrax that is 500 times a normally lethal dose to the unvaccinated. The experiment design left us with a crucial question that how do we learn about the relative success of different vaccination regimens in humans from the monkey data? The key thought is to use the immunogenicity measurements in humans as ‘biomarkers’ or ‘surrogate outcomes’ for survival when challenged, relying on the immunogenicity–survival relationship in macaques to calibrate how much survival to expect with a specific level of observed immunogenicity in humans (Rubin 2004). 

This example can be simplified as a math problem with the following annotations. There are only two levels of vaccination, in the human trial, $W^*=1$ for low, $W^*=2$ for high; in the macaque trial, $W=1$ for low, $W=2$ for high; and secondly, the planned ‘surrogate outcome’ or ‘biomarker’ (= immunogenicity score) is scalar, $S^*$ in the human trial, $S$ in the macaque trial. Survival to challenge is Y (alive=1;dead=0), but is only available in the macaque trial.

<img src="https://raw.githubusercontent.com/zj-zhang/picture_store/master/2019-01-dosage-causal-inference/f6.png" width="100%" height="100%" />
>
**Figure 1**. Simplified set-up with two levels of vaccination: low versus high.
>

There is clear reason for a particular dose of vaccine $W^*$ in a human with a particular dose $W$ in a macaque. The hope is if the surrogate/biomarker in human and macaque have the same meaning, and $S^*$ is similar in humans, so there is no “direct” effect of W on Y given S, nor of  $W^*$, $Y^*$ given $S^*$. If we forced to look in the macaques for no “direct” effects of $W$ on $Y$, the causal pathway of $W$ to $Y$ should be through $S$, just like $W \to S \to Y$. With no arrow from $W to Y$. Here for another level of simplification, we binarized the S as L = low immunogenicity or H = high immunogenicity. Then we could stratified our data to three strata, where stratum 1 includes those with $S(1) = S(2) = L$, meaning the collection of macaques whose vaccination, whether at a high or low level, would result in low immunogenicity – the LL group. Stratum 2 includes those with S(1) = L and S(2) = H, representing the collection of macaques who, if exposed to the low level vaccination would have low immunogenicity, but if exposed to the high level of vaccination would have high immunogenicity – the LH group. Stratum 3 includes those with $S(1) = S(2) = H$, representing the collection of macaques whose immunogenicity would be high whether the vaccination was at a high level or a low level – the HH group. Here in **Figure 2**, we illustrate the examples of the presence and absence of the direct effects of the vaccination.

### 4.Conclusions

We reviewed the statistical studies that consider drug compliance as an explanatory variable to estimate the causal effect in a randomized treatment-control experimental design. We introduced the LRC-CPPT dataset, which is main example for studying the dosage-compliance-response study and was used by both Efron Feldman and Jin Rubin papers. We recapitulated the statistical models used by Efron-Feldman and Jin-Rubin that utilized different assumptions and approaches to estimate the average causal effect (EF) and principal causal effect (JR) for the active drug. Finally, we discussed the similarity of the compliance factor in the context of genetic studies and extended the potential applications of the compliance causal inference models to the field of genetic association studies.