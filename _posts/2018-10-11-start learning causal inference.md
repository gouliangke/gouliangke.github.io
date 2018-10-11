---
layout: post
title:  "Start learning causal inference from an easy classical question"
categories: Statistics
tags: Statistics Causal-inference
author: Liangke G
academia: true
mathjax: true
---

Recently I am taking a class of causal inference, and we did an easy exercise during the class. Despite the fact that this is a basic regression question, it helps us understand how to interpret the coefficients gained in different models, and how the observed coefficients indicate the causal relationship.

##question background and models
So let's first take an look of the background of the question and the models:

<img src="https://github.com/gouliangke/myblog/raw/master/photos/4.png" height="200" />




>
<img src="https://github.com/gouliangke/myblog/raw/master/photos/3.png" height="600" />

##Go through of each question

Here let's take of a look at each of the questions and I will share the understanding of them with you. 

<img src="https://github.com/gouliangke/myblog/raw/master/photos/9.png" height="100" />

Model1: 
$$
\hat{y_b} =171.81+63.76 * 3.45 = 222 
$$ 

Residual of model 1 
$$
y_b-\hat{y_b}=294-222=72
$$

The method of calculating the other two cases will be exactly the same.

<img src="https://github.com/gouliangke/myblog/raw/master/photos/5.png" height="100" />

Slope in model 1 is positive. In model 1 the correlation is directly related to slope. In model 3 the negative correlation observed for smoke is the partial correlation of smoke controlling for sulfur.

<img src="https://github.com/gouliangke/myblog/raw/master/photos/6.png" height="100" />

P value is greater than 0.001, because p value is 0.0011. 
This is a trick question, the things tested here is since F-test and t-test both test $H_0$ in simple regression. Therefore the p value of them is the same. 

P-value for coefficient of smoke:
$$H_0: \beta_i=0$$
$$H_alt: \beta_i \neq 0$$

<img src="https://github.com/gouliangke/myblog/raw/master/photos/7.png" height="50" />

This could be calculated from the variance inflation factor
$$VIF=\frac{1}{1-R_{x1,x2}^2}$$
$$40.45776=\frac{1}{1-R_{x1,x2}^2}$$
$$R_{x1,x2}^2 = 0.99$$

<img src="https://github.com/gouliangke/myblog/raw/master/photos/8.png" height="150" />

Would recommend type C coal. 
A prior perspective is that more pollution is bad for health. Model 3 has the reversal of coefficient of smoke, but high collinearity with sulfur and general concerns about correlation vs. causation lead to descanting interpretation of coefficient in model3 of causal effects. Furthermore, pattern in model1 supports more smoke worse.  

From question 4 we can see smoke and sulfur are highly correlated. When two factors that are stongly correlated, they can show antagonistic coefficients. This is similar in genomic analysis, when two genetic variants are highly linked, it is hard to dicect their effects without genetic engineering. 