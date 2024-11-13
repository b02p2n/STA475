java c
STA475 Assignment #2 (Fall 2024)
Instructions
Due date: Friday October 11th at 11:59pm
•  No-questions-asked grace period until Monday October 14th at 5pm
•  No late submissions will be accepted after this time
Where to submit:
•  Crowdmark:  Submit your answers to each question in correct space on Crowdmark
•  You can submit as many times as you like before the deadline
•  Email submissions will NOT be accepted
Other notes:
•  For some questions, you will need to use R; please include all code and relevant output in the pdf submission (make sure the code is visible in the pdf and doesn’t run out of the margins).  If the question asks you to answer a question based on R output, make sure your answer is easy for your TA to find (i.e. start with your answer, then have the code and output afterwards for reference).  Your TA should be able to understand your answer without looking at your and output (as appropriate), but may refer to these to better understand what you did.
•  While you may discuss questions with your classmates, you MUST submit independent work that you did yourself.  Students submitting identical solutions  (e.g. identical sen- tences, derivations steps, or chunks of code) will be investigated for violations of academic integrity.
•  If   you   believe   you’ve   found   a   typo   or   error   in   the   assignment,   please   email sta475@utoronto.ca  so  I  can  look  into  it  and  get  back  to  the  class  as  quickly  as possible.
Question 1 [8 points]
In this question, you will simulate time-to-event data with one binary predictor, where the log-rank test and Wilcoxon test yield different results at the 5% significance level.
(a) Simulate survival data for two groups (e.g. treatment and control), with at
least n = 100 in each group, where the log-rank test and Wilcoxon test yield
different results at the 5% significance level.  Provide the  R code you used to
simulate the data (make sure to include set.seed() at the beginning to ensure reproducibility)
# Set random seed for reproducibility
set.seed(475) # You can change the integer, but leave this line here
# Simulate survival data
(b) Use R to conduct a logrank test and report the p-value for the difference in
survival distributions between groups for the data you simulated in (a)?  Write 1-2 sentences summarizing your findings.
# Perform. logrank test
(c) Use R to conduct a Wilcoxon test and report the p-value for the difference in
survival distributions between groups for the data you simulated in (a)?  Write 1-2 sentences summarizing your findings.
# Perform. Wilcoxon (Breslow) test
(d) Plot the K-M estimates for the two groups in the data you simulated in (a).
(e) Write 2-3 sentences commenting on why the log-rank and Wilcoxon tests
yield different results for the data you simulated in (a), by making specific reference to the plot you produced in (d).
Question 2 [6 points]
The time to recurrence, in months, for patients on an existing and novel treatment for lung cancer is compared using the following model:
Y = log(T) = 1 + 2Z + 0.3W ,
where W has a standard logistic distribution and Z = I(novel treatment is administered).
(a) Derive an expression for P (T > t) in terms of t and z, based on the expression above and the distribution of W.
(b) Use your answer from part (a) to estimate the probability of remaining in remission for more than 1 year, both under the new and standard treatments.
(c) Use your answer from (a) to estimate the probability of remaining in remission for more than 2 years, both under the new and standard treatments.
(d) Write 1-3 sentences carefully interpreting the effect of the new treatment on the median time to remission.
Question 3 [12 points]A software company is analyzing the time-to-failure of their operating system under different conditions. They fit an AFT model to study the effects of two predictors on the time until the first critical error occurs:  (1) system load (high/normal) and (2) a new optimization algorithm (present/absent). They obtain the following results:
1.  The acceleration factor for high system load compared to normal system load is 1/2.25, controlling for presence or absence of the optimization algorithm.
2.  The acceleration factor for systems using the new optimization algorithm compared to those without it is 1/0.8, controlling for the system load (high or normal)
3.  The  median  time-to-failure  for  systems  under  normal  load  without  the  optimization algorithm is 1000 hours.Note:  The corrections in red relate to the clarification notes covered on Tues Oct 8th.  These values should lead to answers that make more intuitive sense, in terms of the impact of heavy load vs  normal  load,  and  using  an optimizing  algorithm vs  no optimizing  algorithm.   The original values essentially had the wrong ”baseline” group.  It’s possible that if you leaned on your intuition, your answers may have been correct even with the original values.
(a) What is the response of interest in this problem?
(b) In this context, are longer values of the response variable desirable (e.g. good) or undesirable (e.g. bad)?  Explain your reasoning.(c) Carefully interpret the effect of high system load on the time to first critical error in 2-3 sentences.  Make sure your answer includes a comment about whether or not high system load accelerates or delays the occurrence of critical errors.
(d) Carefully interpret the effect of the new optimization algorithm on the time to first
critical error in 2-3 sentences.  Make sure your answer includes a comment about
whether or not the new optimization algorithm accelerates or delays the occurrence of critical errors.
(e) Calculate the median time-to-failure for systems under high load without the optimization algorithm.
(f ) If 90% of sys代 写STA475 Assignment #2 (Fall 2024)C/C++
代做程序编程语言tems under normal load without optimization survive for 500 hours without a critical error, how long do 90% of systems under normal load with optimization survive?
(g) What is the median time-to-failure for a system under high load with the new optimization algorithm?  Justify your answer by showing your calculations.
(h) The company wants to achieve a median time-to-failure of at least 800 hours for systems under high load.  Can this be achieved with the new optimization algorithm? Explain your reasoning.
Question 4 [9 points]In this question, you’ll consider the diabetic retinopathy data we looked at in class.  In class, we fit several parametric models to these data, to model the time to blindness in the right eyes of diabetes patients, and here you will use several approaches to determine which model is most appropriate.
eyes <- diabetic |> filter(eye == "right")
(a) Fit weibull, exponential, lognormal, and log-logistic models to these data, with no predictors.
(b) Create one plot with the Kaplan-Meier estimate of the time to blindness in right eyes for these patients, as well as the parametric estimates for the models you fit in part (a).  Write 2-3 sentences summarizing what you learn from this plot.
Hint: You can modify the code from class to create this plot, and you can use the helper functions from class as well (you’ll find them on Quercus).
(c) Create a probability-probability (P-P) plot for each parametric model you fit
in (a). Write 2-3 sentences summarizing what you learn from this plot. Hint: You can modify the code from class to create this plot.
(d) What is one advantage of using the visualization approach from part (b) to choose a parametric model?
(e) What is one advantage of using the visualization approach from part (c) to choose a parametric model?
Question 5 [7 points]
library(tidyverse)
library(survival)
library(asaur)
hepatoCellular %>%
select(Number, Age, Gender, OS, Death, RFS, Recurrence) %>%
glimpse()
Rows: 227
Columns: 7
$ Number      1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, ~
$ Age         57, 58, 65, 54, 71, 32, 79, 27, 55, 35, 34, 60, 38, 72, 41,~
$ Gender     0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 0, 1, 1, 1, 1, 0, 1, 1,~
$ OS          83, 81, 79, 76, 7, 13, 38, 19, 4, 76, 3, 78, 8, 72, 63, 33,~
$ Death       0, 0, 0, 0, 1, 1, 1, 0, 1, 0, 1, 0, 0, 0, 0, 1, 0, 0, 1, 1,~
$ RFS         13, 81, 79, 76, 3, 3, 30, 19, 4, 76, 1, 78, 1, 72, 35, 33, ~
$ Recurrence  1, 0, 0, 0, 1, 1, 1, 0, 1, 0, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1,~
(a) Fit a Weibull model to estimate the survival curve for overall survival of
patients with hepatocellular carcinoma based on the hepatoCellular data.  Print a summary of your fitted model.
(b) Fit an exponential model to estimate the survival curve for overall survival of patients with hepatocellular carcinoma based on the hepatoCellular data. Print a summary of your fitted model.
(c) Conduct a likelihood ratio test to determine whether the exponential model is suitable to represent these data, compared to the Weibull model.  State your null and alternative hypotheses (be sure to define any parameters you refer to), write the form of the test statistic, calculate the test statistic and p-value using R, and write 1-2 sentences summarising your findings.
(d) In the likelihood ratio test you conducted above, how many degrees of freedom did you use for the chi-squared distribution?  Explain why in  1-2 sentences.
Question 6 [10 points]Using the pharmacoSmoking data from the asaur package you will investigate the effect of triple therapy (grp == combination) vs patch (grp == patchOnly) treatments for smoking cessation. The response of interest is time (in days) until relapse of smoking.  We will exclude individuals from this analysis who did not quit smoking for at least one day
library(asaur)
glimpse(pharmacoSmoking)
Rows: 125
Columns: 14
$ id            21, 113, 39, 80, 87, 29, 16, 35, 54, 70, 84, 85, 25, 47~
$ ttr            182, 14, 5, 16, 0, 182, 14, 77, 2, 0, 12, 182, 21, 3, 1~
$ relapse        0, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1~
$ grp             patchOnly, patchOnly, combination, combination, combina~
$ age             36, 41, 25, 54, 45, 43, 66, 78, 40, 38, 64, 51, 37, 65,~
$ gender          Male, Male, Female, Male, Male, Male, Male, Female, Fem~
$ race            white, white, white, white, white, hispanic, black, bla~
$ employment      ft, other, other, ft, other, ft, pt, other, ft, ft, oth~
$ yearsSmoking    26, 27, 12, 39, 30, 30, 54, 56, 25, 23, 30, 35, 23, 50,~
$ levelSmoking    heavy, heavy, heavy, heavy, heavy, heavy, heavy, light,~
$ ageGroup2       21-49, 21-49, 21-49, 50+, 21-49, 21-49, 50+, 50+, 21-49~
$ ageGroup4       35-49, 35-49, 21-34, 50-64, 35-49, 35-49, 65+, 65+, 35-~
$ priorAttempts   0, 3, 3, 0, 0, 2, 0, 10, 4, 10, 12, 1, 5, 6, 5, 2, 1, 1~
$ longestNoSmoke  0, 90, 21, 0, 0, 1825, 0, 15, 7, 90, 365, 7, 1095, 180,~
pharmacoSmoking <- pharmacoSmoking %>%
filter(ttr >= 1)
(a) You will first fit Weibull and lognormal models to these data (overall, not separated by treatment) and produce one or more plots of your choice to identify which of the parametric models is most suitable for these data (among these two choices).  Explain your answer in 1-2 sentences, making specific references to the plot(s) you produced.
(b) Using the parametric model you chose in part (a), fit two separate models, one for
each treatment group. What are the estimated values of a and τ for each group?
(c) Conduct hypothesis test(s) to determine whether the two groups have different survival distributions.  Be sure to formally state your null and alternative hypotheses, report relevant test statistics and p-values, and interpret your conclusions.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
