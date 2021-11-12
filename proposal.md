Proposal
================

## P8105 Final Project: Drug Use Abuse Among Youth

### Group Member

Xueqing Huang (xh2470)  
Kaiyu He (kh3074)  
Yongzi Yu  
Ruiqi Yan (ry2417)  
Hao Xu (hx2328)  

### Motivation

According to WHO, the United States has the highest level of illegal
drug use compared with other countries in 2019. The two most commonly
used illicit drugs are marijuana and opioids. Overall drug use was also
reported to be on the rise. The NSDUH survey in 2019 indicated that
20.8% of people aged 12 and over had illicit drug use, which is a
notable increase from 2015 *(Buddy, T. 2021)* . Illegal drug abuse is
more important to be prevented among the youth, since drugs are more
harmful to them, such as affecting the growth of brains, impairing
memories and concentration. Thus, we would like to study the drug use
abuse among youth to detect some patterns, which would be useful for
policymakers to develop strategies with explicit targets, and thus
achieve the most effective results.  
Our next step was to examine which patterns are important for the
policymakers to make problem-oriented strategies. The most conspicuous
one is the drug use by the state. We also expect finding the patterns of
different drug use to be helpful, such as average age, race, and gender
of illegal drug use by the drug. Moreover, we learned an example of a
case-control study from the Epidemiology course illustrating that drug
use might be associated with other behaviors affecting personal health,
so we would also develop our study to explore patterns in this area.  

### Intended Final Products

Firstly, the project will work on the findings on the state level,
showing the distribution of overall youth drug use in each state, as
well as the trend of youth drug use rate among races, gender, and age in
each state. We would like to find states with a high incidence of youth
drug use and races that have a disproportionally high rate of youth drug
use. Moreover, we are interested in the average age of initial marijuana
use and the rate of initial marijuana use before age 13 of each race and
gender group and see how it differ among states.  
The second endpoint of the project is exploring the association between
youth drug use and other health risk behaviors. We concern about whether
the higher frequency of drug use is correlated with a higher rate of
risky behaviors, such as driving after drinking, cell phone use while
driving, wearing a seat belt when riding, carrying a weapon and physical
fighting, or behaviors with potential health risk, such as early age
sexual experience, suicide attempt, tobacco use, alcohol abuse, physical
inactivity, underweight/overweight, video game addiction and suicide
attempt.  
Finally, we focus on the difference between marijuana use and other drug
use and whether there is a significant risk behaviour difference between
teenagers who use marijuana and those who use other drugs. We plan to
show most of the results using tables and data visualization and a
dashboard that displays some interactive plots about our results.  

### Anticipated data sources

In this project, we use data of Youth Risk Behavior Surveillance System
(YRBSS) collected by Centers for Disease Control and Prevention (CDC).
The YRBSS was developed in 1990 to monitor health behaviors that
contribute markedly to the leading causes of death, disability, and
social problems among youth and adults in the United States. The data
are collected every two years, and the most up-to-date data were
collected in 2019. We will use the data collected in 2019 on the state
level.

The dataset is so large that it exceeds the upload limit of github.
Therefore, in order to download the dataset, you can use the code in
`download_dataset.Rmd`.

### Planned Analyses, Visualizations and Coding Challenges

-   Planned Analyses: As is stated in the *Intended Final Products*, we
    plan to analyze the distribution of overall youth drug use in each
    state, exploring the association between youth drug use and other
    health risk behaviors as well as the difference between marijuana
    use and other drug use.

-   Visualizations: Plots are dependent on our planned analyses. For the
    first question, density plot and histogram including drug use
    proportion, age, state should clearly show the distribution of
    overall youth drug use in each state. For the second question, we
    need a *m* × *n*(m different drugs, n different behaviors) panel
    plot to show the relationship between different drug use and
    behaviors. Finally, we need pairwise plots of different combinations
    of drug types to declare the interaction of drug use.

-   Coding Challenges:

    -   The answers collected each year is different because questions
        have different serial number and content. To handle this we need
        to adjust our data set specifically according to year. Not a
        simple function or iteration can solve this.  
    -   There are tons of missing values in the data set, simply
        dropping them will cause a huge bias. We need to come up with
        different ways to deal with the missing value according to
        specific variables and our outcomes.
    -   The data set is huge (1.48GB). Some of our teammates’ laptops
        will stuck if the code is not efficient. And we don’t have
        enough experience in improving code efficiency.  
    -   There are many variables included in our final product. We need
        to show as much information as we can and make our plot as clear
        as possible to readers at the same time.

### Planned timeline

`November 1-13`:  
Discuss project topic, find data sources, discuss final products and
planned analyses, and write proposal document.  
`November 14-20`:  
Clean up the data based on variables we want to study.  
`November 21-30`:  
Analyze data and make plots based on cleaned dataset.  
`December 1-11`:  
Write reports and create a webpage for the project.

### Reference

1.  Buddy, T. 2021. *U.S. Has High Levels of Illegal Drug Use*.
    Retrieved from
    <https://www.verywellmind.com/us-has-highest-levels-of-illegal-drug-use-67909>

2.  <https://www.cdc.gov/healthyyouth/data/yrbs/data.htm>
