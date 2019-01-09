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


Causal effects are comparisons of potential outcomes under different treatment on a common set of units. The use of the concept of ‘direct’ versus ‘indirect’ causal effects is common in statistics, social, economics, and biomedical fields. The most straightforward way to clarify the direct and indirect causality is by using potential outcomes to define causal effects. Here we use two example studies to illustrate the widespread acceptance and application of the potential outcomes framework, also known as the Rubin causal model (RCM), in direct and indirect causal inference.

<img src="https://github.com/gouliangke/myblog/raw/master/photos/13.png" width="100%" height="100%" />
>
**Figure 1**. Simplified set-up with two levels of vaccination: low versus high. Figure from *Rubin 2004*
>





### 1. Introduction of direct and indirect causal inference 

Causal inference is the process of drawing a conclusion about a causal connection based on the conditions of the occurrence of an effect. The main difference between causal inference and inference of association is that causal inference analyzes the response of the effect variable when the cause is changed while the association revealed the correlation of two variables. Correlation does not imply causation, so further methods must be used to infer causation. Common frameworks for causal inference are structural equation modeling and the Rubin causal model. The Rubin causal model, also known as the Neyman–Rubin causal model, is an approach to the statistical analysis of cause and effect based on the framework of potential outcomes, named after Donald Rubin. The name "Rubin causal model" was first coined by Rubin's graduate school colleague, Paul W. Holland, but it has roots in the context of randomized experiments with randomization-based inference in the work of Neyman (1923) and Fisher (1925).

Having demonstrated the underlying assumptions, Efron and Feldman formulated their model accordingly. The overall goal of the modelling is to estimate a true drug dose-response function $\delta(X)=E[Y_x-Y_0]$. The expectation was defined as the appropriate averages over a population U, so $E[Y_x-Y_0]=\sum(Y_x(u)-Y_0(u))/N$, where u is an individual from a population U, and N being the number of elements in U. This is also called average causal effect of X on response by Rubin and Holland. Based on the data distribution in **Figure 1**, the compliance was assumed to have a linear relationship with the cholesterol reduction in the Control group, z. For differences between outcomes in the Treatment and Control groups, denoted by D(z)=T(z)-C(z), was modeled quadratically as $D(z)=d_1\cdot z+d_2\cdot z^2$. If there is no interaction between the dose X and the placebo effect $y_0$ and the outcome  is purely additive of X and $y_0$, then the true dose-response function $\delta(z)=D(z)$; otherwise, the true dose-response function  depends on another continuous function H(x) that we need to specify. In the Efron-Feldman paper, the authors specified $H(x(u))=h_1 \cdot z$ and $x=s(u)\cdot z(u)$. This is basically modelling the individual-specific baseline level is likely to affect the outcome after conditioned on the dosage. The authors also commented that the interaction term has one degree of freedom, similar to Tukey’s test for interactions in a two-way ANOVA study without replication; therefore, specifying the interaction term will enable more sensitive statistical tests.


 
### 2.The Rubin causal model

The Rubin causal model (RCM) is a formal mathematical framework for causal inference, first given that name by Holland (1986). The potential outcomes framework was first proposed by Jerzy Neyman in his 1923 Master’s thesis, but he discussed it only in the context of completely randomized experiments. Rubin, together with other contemporary statisticians, extended it into a general framework for thinking about causation in both observational and experimental studies. Paul W. Holland showed the Rubin causal model in experiments and observational studies is enlarged to analyze the problem of “causes causing causes” and is compared to path analysis and recursive structural equations models in 1986. In Holland’s paper, he used a special quasi-experimental design, the encouragement design, to give concreteness to the discussion of causal models by focusing on the simplest problem that involves both direct and indirect causation. Rubin’s model is shown to extend easily in this situation and to specify conditions under which the parameters of path analysis and recursive structural equations models have causal interpretations (Holland 1988).

There are two essential parts to the RCM, and a third optional one. The first part is the use of ‘potential outcomes’ to define causal effects in all situations. The second part is an explicit probabilistic model for the assignment of ‘treatments’ to ‘units’ as a function of all quantities that could be observed, including all potential outcomes. This model is called the ‘assignment mechanism’, and defines the structure of experiments designed to learn about the science from observed data or the acts of nature that lead to the observed data. The third possible part of the RCM framework is an optional distribution on the quantities being conditioned on in the assignment mechanism, including the potential outcomes, thereby allowing model-based Bayesian ‘posterior predictive’ (causal) inference (Imbens and Rubin 2010).



### 3.The example of randomized trials of anthrax vaccine 

In the rest part of this mini review, two examples will be provided to show the cases where Rubin causal model works flexibly, while the traditional variant component analysis may give the non-interpretable conclusions. The first example is the anthrax vaccine analysis. 

Two sets of randomized placebo-controlled trials on anthrax vaccine are being conducted by the United States Centers for Disease Control and Prevention (CDC). This experiment involves human volunteers with extensive reactogenicity measurements and extensive immunogenicity measurements (e.g. blood antibody levels) after vaccination regimens. A parallel second trial was on macaques with parallel immunogenicity measurements, plus survival when challenged with a dose of anthrax that is 500 times a normally lethal dose to the unvaccinated. The experiment design left us with a crucial question that how do we learn about the relative success of different vaccination regimens in humans from the monkey data? The key thought is to use the immunogenicity measurements in humans as ‘biomarkers’ or ‘surrogate outcomes’ for survival when challenged, relying on the immunogenicity–survival relationship in macaques to calibrate how much survival to expect with a specific level of observed immunogenicity in humans (Rubin 2004). 

This example can be simplified as a math problem with the following annotations. There are only two levels of vaccination, in the human trial, $W^\*=1$ for low, $W^\*=2$ for high; in the macaque trial, $W=1$ for low, $W=2$ for high; and secondly, the planned ‘surrogate outcome’ or ‘biomarker’ (= immunogenicity score) is scalar, $S^\*$ in the human trial, $S$ in the macaque trial. Survival to challenge is Y (alive=1;dead=0), but is only available in the macaque trial.


There is clear reason for a particular dose of vaccine $W^\*$ in a human with a particular dose $W$ in a macaque. The hope is if the surrogate/biomarker in human and macaque have the same meaning, and $S^\*$ is similar in humans, so there is no “direct” effect of W on Y given S, nor of  $W^\*$, $Y^\*$ given $S^\*$. If we forced to look in the macaques for no “direct” effects of $W$ on $Y$, the causal pathway of $W$ to $Y$ should be through $S$, just like $W \to S \to Y$. With no arrow from $W to Y$. Here for another level of simplification, we binarized the S as L = low immunogenicity or H = high immunogenicity. Then we could stratified our data to three strata, where stratum 1 includes those with $S(1) = S(2) = L$, meaning the collection of macaques whose vaccination, whether at a high or low level, would result in low immunogenicity – the LL group. Stratum 2 includes those with S(1) = L and S(2) = H, representing the collection of macaques who, if exposed to the low level vaccination would have low immunogenicity, but if exposed to the high level of vaccination would have high immunogenicity – the LH group. Stratum 3 includes those with $S(1) = S(2) = H$, representing the collection of macaques whose immunogenicity would be high whether the vaccination was at a high level or a low level – the HH group. Here in **Figure 2**, we illustrate the examples of the presence and absence of the direct effects of the vaccination.

<img src="https://github.com/gouliangke/myblog/raw/master/photos/15.png" width="100%" height="100%" />
>
**Figure 2**. Two examples of the presence and absence of direct effects. Figure from *Rubin 2004*


In the top situation, there appears to be a “direct” causal effect of vaccine on survival. We appear to have strong evidence that all the effect of the vaccine is via immunogenicity because conditionally given $S_{obs}$, $Y_{obs}$ and $W_{obs}$ are independent. The last two columns of the Figure 2 reveal that for a given level of observed immunogenicity ($S_obs$), the protection ($Y_obs$) is the same whether high- or low-level vaccination ($W_obs$) took place. When $S_obs=L$, $Y_obs=20$ percent no matter $W_obs=1$ or 2. When $S_obs$=H, $Y_obs$=80 percent no matter $W_obs$=1 or 2. The explanation in this experiments could be all macaques benefit equally from a high- versus low-level vaccination, no matter what their attained immunogenicity. 

In the bottom situation, there seems to be no “direct” causal effects of vaccination, all effect being “indirect”, “mediated” by immunogenicity, because vaccination affects survival probability through changing immunogenicity. When the immunogenicity is low, the survival rate is 0 at high-level treatment, while the survival is 20 percent when the vaccination treatment is low. Similarly, when observed immunogenicity is high, high-level vaccination appears to reduce survival from 80 to 70 percent. From groups c and d, we know the high-level vaccination does not reduce survival for all. From the potential outcomes, we have the conclusion that unless immunogenicity is altered, high versus low vaccination has no effect on survival, and it is beneficial for one-third of the group and has no effect on the other two-thirds.



### 4.Complex experiments: “direct” and “indirect” causal effects

Here we further discuss the “direct” and “indirect” causal effects using an example where Fisher made a mistake. Fisher discussed about the problems about the “concomitant” variable several times. He wrote about this problem in *Design of Experiments* (DOE) from the first edition in 1935 to the last edition in 1966. The example of the concomitant variable case Fisher mentioned in DOE was about the yield of plants following different kinds of treatments in agriculture experiments, and the variation in plant number itself. Fisher came up with two ideas to answer the effect of the number of plants on the yields. The first one is kind of ignore the problems, meaning if we are satisfied that the variation in plant number is not itself an effect of the treatments being investigate, then the plant number is a true covariate. The other idea is to confine ther investigation to the effects on yield, excluding such as flow directly or indirectly from effects brought about by variations in plant number.  Fisher thought, in this way, it will appear desirable to introduce into the comparisons a correction for the variations in yield directly due to variation in plant number itself (Rubin 2005).

Fisher also wrote about another example in *Statistical Methods for Research Workers*, that is consistent with the previous case. This is example is about is that when we concerned to study the effects of agricultural treatments upon the purity index of the sugar extracted from sugar-beets, then the concomitant variations in sugar-percentage and root weight will affect the analysis. Fisher proposed to solve this problem by using an analysis of covariance applied to the three variates: purity, sugar percentage and root weight. He thought this would enable us to make a study of the effects of experimental treatments on purity alone, after allowance for any effect they may have on root weight or concentration, without us needing to have observed in fact any two plots agreeing exactly in both root weight and sugar percentage. 

His views, which remained unchanged across all the DOE editions, was to conduct an analysis of covariance (ANCOVA) of $Y_{obs,i}$ on $W_i$ and $C_{obs,i}$, where $C_{obs,i} = W_i C_i (1) + (1-W_i) C_i (0)$. This analysis is equivalent to a regression analysis of observed outcome on treatment indicator and observed prediction. Using only the $Y_(obs,i)$ and the treatment indicator $W_i$ in place of the potential outcomes, one cannot directly state the critical benefit of randomization in achieving ignitability. Essentially, an ANCOVA compares the average observed $Y_i$ (1) with the average observed $Y_i$ (0) for units with a common value of $C_(obs,i)$, which generally does not estimate a causal effect of any kind.

Here we used the examples in **Figure 3 and 4** to illustrate the problem. Suppose that Figures 3 and 4 represent very large randomized experiments of N units, say N plots; the concomitant C is the number of plants established in each plot, the primary outcome Y is the yield in each plot, the treatment is a new fertilizer, and the control is the standard fertilizer. In each experiment, half of the units are randomly assigned to the treatment and the other half of the units are assigned to the control. 


<img src="https://github.com/gouliangke/myblog/raw/master/photos/16.png" width="100%" height="100%" />
>
**Figure 3**. An example with a treatment effect on the concomitant C, but no treatment effect on the primary outcome Y. Figure modified from *Rubin 2005*


The first two rows in the represent those units with common values of the potential outcomes, and randomly assigning them would result in half being assigned to control, represented by the first row, and half being assigned to treatment, represented by the second row, and analogously for the second pair of rows. For the sake of easily description, I named the four assignment groups as group a, b, c and d as shown in the figure above. By comparing groups, a and b, we know the outcomes are the same between these groups even they were one control and one treatment, similarly to the group c and d. when we compare groups a and c, we can see that despite the fact these two belong to the same control groups, the outcomes Y were different, because the variation in the concomitant variable C. In general, Figure 3 reveals that all units, there is a causal effect of treatment on the concomitant variable C of size1. But there is no effect on the primary outcome variable Y for any unit. Because all unites have a treatment effect on C and no effect on Y, after adjusting for the concomitant variable C, the “direct” effect of treatment on Y is simply chosen to be 0. This conditioning on the observed value of the concomitant C_obs, which is the approach recommended by Fisher, leads to a contradictory conclusion: when C_obs=3, those plots that received the new treatment do worse with a treatment effect of -2. When we compare groups b and c, we can find the effect of treatment was -2 as these two groups had the same concomitant variable value and just differed by the treatment control assignment. The negative treatment effect is clearly incorrect as it revealed by an examination of the potential outcomes in Figure 3. 

Here we used the example in Figure 3 to illustrate a flaw in Fisher’s proposed solution. 


<img src="https://github.com/gouliangke/myblog/raw/master/photos/17.png" width="100%" height="100%" />
>
**Figure 4**. An example with constant treatment effect on the outcome, Y, and “direct” effect for units with no treatment effect on the concomitant C. Figure modified from *Rubin 2005*


This example is analogous to Figure 3 except there is a constant treatment effect on Y of size 1 for all units and there is no effect on the concomitant C when we focus on group c and d. For groups a, b, e and f, the treatment effect on the concomitant is 1. It is clear that the direct effect of treatment is size 1 in groups that have no treatment effect on the concomitant. In this example, Fisher’s recommended analysis of covariance (ANCOVA) will also provide and incorrect answer. The ANCOVA of $Y_{obs,i}$ on $W_i$ and $C_{obs,i}$ implies that the “direct” causal effect of treatment on primary outcome is of size -1 after accounting for the effect of treatment on concomitant. This negative effect seems is incorrect again. 

There are other valid ways to analyze data like these. One is to combine C and Y into one outcome variable, such as the ratio Y/C, and another way is to consider (C, Y) as a bivariate outcome variable. A third way is to use the principal stratification approach of Frangakis and Rubin (2002). 



### 5.Conclusion

We went through two brief examples that showed the widespread acceptance of the potential outcomes formulation of causal effects in both randomized experiments and in observational studies. Randomized experiments have two special features that make causal inference easy to draw: ignorability and propensities between 0 and 1. When conducting causal inference, maintaining the distinction between observed values (eg. concomitants such as $C_{i,obs}$ and which potential outcomes they reflect is critical for clear thinking. It is all too easy to slip into ignoring the difference and reaching invalid conclusions or non-interpretable results. Data are not only measurements, but also should reflect what they measure and whether this is a treatment group. A statement like “the value of $C_obs$ is 3” is not generally helpful without telling more information out is this observation an outcome of treatment or not. Scientific inferences change, in general, when $C_obs=3$ implies that $C(1)=3$ versus when it implies that $C(0)=3$.


### Reference

Holland P. W., 1988 CAUSAL INFERENCE, PATH ANALYSIS AND RECURSIVE STRUCTURAL EQUATIONS MODELS. ETS Res. Rep. Ser. 1988: i-50. https://doi.org/10.1002/j.2330-8516.1988.tb00270.x
Imbens G. W., and D. B. Rubin, 2010 Rubin Causal Model, pp. 229–241 in Microeconometrics, Palgrave Macmillan UK, London.
Rubin D. B., 2004 Direct and indirect causal effects via potential outcomes. Scand. J. Stat. 31: 161–170.
Rubin D. B., 2005 Causal Inference Using Potential Outcomes. J. Am. Stat. Assoc. 100: 322–331. https://doi.org/10.1198/016214504000001880


