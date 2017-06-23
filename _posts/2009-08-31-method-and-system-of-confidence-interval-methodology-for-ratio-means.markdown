---

title: Method and system of confidence interval methodology for ratio means
abstract: A method and system for determining whether the number of samples taken from a population of units where the distribution of X and Y variables are unknown by evaluating ratio mean measurements on a computer to determine a confidence interval. The method comprising: inputting samples from the total population with each unit sample having at least two variables X and Y; redefining the multivariate data that comprises the two variables X and Y; estimating the mean; computing the standard error; using a bootstrapping method, generating boot strap samples, computing a Z distribution based upon the bootstrap samples; and computing the confidence interval. The system comprises a processor for performing the steps of the method.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08335660&OS=08335660&RS=08335660
owner: The United States of America as represented by the Secretary of the Army
number: 08335660
owner_city: Washington
owner_country: US
publication_date: 20090831
---
The invention described herein may be manufactured used and or licensed by or for the United States Government.

A computer program listing appendix has been electronically submitted and is hereby incorporated by reference pursuant to 37 C.F.R. 1.96 c .

This invention relates generally to statistical inference and more particularly to ratio mean measurement.

An approach to statistical inference uses bootstrapping to solve problems where the variance is in closed analytic form. Bootstrapping is implemented by creating a number of resamples of the observed sample data set equal in size obtained by random sampling with replacement from the original dataset.

The military and many other government and private organizations have the need to evaluate ratio mean measurements to help them make informed life cycle management decisions. is an illustration of a sample ratio mean. A ratio mean is the ratio of the means of two random variables X and Y whose corresponding terms are paired. The pairs are assumed to be independent. In the correlation between X Y may be positive negative or zero. The X Y in are considered independent and identically distributed i.i.d. with some unknown distribution.

For example the Army tracks and evaluates the performance of many weapon systems using ratio mean metrics such as the maintenance ratio MR . A MR estimate

Since it is inefficient to track every vehicle in an inventory of vehicles ratio mean performance metrics are tracked for a sample of vehicles over a given time period. The entire population performance is inferred based on a sample of vehicles using approximate confidence intervals CI for ratio means. There is need to develop an efficient methodology that provides for the effective use of confidence intervals. Generally speaking the documented standard error SE estimate for a ratio mean accounts for variation in both variables and correlation is not dependable for samples under 30 or larger samples with increased variation in both variables. Therefore another approach is needed.

A preferred embodiment of the present invention is directed to confidence interval methodology for ratio means in which a pre existing nonparametric bootstrap t framework is combined with innovative inputted data determinations to compute approximate confidence intervals for a ratio mean metric. The inputted data is redefined in the sense that each element of the ratio sample i.e. each paired term is redefined using the equation

The ratio mean of interest is evaluated for a given problem by computing the confidence interval CI of that ratio mean using the methodology of the present invention. The confidence interval methodology for ratio means produced in accordance with the principles of the present invention produces realistic approximate confidence intervals CI s around a ratio mean. The nonparametric bootstrap t approach NBTA utilizes three parameters. The three parameters are mean standard error SE and bootstrap standardized Z distribution. In a preferred embodiment confidence interval methodology for ratio means is used to compute approximate confidence intervals for a ratio mean metric.

A preferred embodiment method determines whether the number of samples taken from a population of units is substantially indicative of the total population by evaluating ratio mean measurements on a computer to determine a confidence interval. The method comprises the steps of estimating the parameters needed to construct a satisfactory confidence interval that adheres to standard confidence interval properties. The first step comprises redefining the sample. Next the mean and standard error estimates are determined and the variance stabilized bootstrap standardized Z distribution is constructed using a large number of bootstrap samples BSS with n vehicles or units of any other subject in each sample. The equation is circumflex over z MR i MR SE i where MR i is an estimate of the mean for the iboot strapped sample where i is greater than 0 and less than B preferably in the range of 1000 to 10000 SE i is the standard error for the iboot strapped sample determined by the equation and wherein standardized distribution and standard error are determined by the equations

A more complete appreciation of the invention will be readily obtained by reference to the following Description of the Preferred Embodiments and the accompanying drawings in which like numerals in different figures represent the same structures or elements. The representations in each of the figures are diagrammatic and no attempt is made to indicate actual scales or precise ratios. Proportional relationships are shown as approximates.

The present invention now will be described more fully hereinafter with reference to the accompanying drawings in which embodiments of the invention are shown. However this invention should not be construed as limited to the embodiments set forth herein. Rather these embodiments are provided so that this disclosure will be thorough and complete and will fully convey the scope of the invention to those skilled in the art. In the drawings the thickness of layers and regions may be exaggerated for clarity. Like numbers refer to like elements throughout. As used herein the term and or includes any and all combinations of one or more of the associated listed items.

The terminology used herein is for the purpose of describing particular embodiments only and is not intended to limit the full scope of the invention. As used herein the singular forms a an and the are intended to include the plural forms as well unless the context clearly indicates otherwise. It will be further understood that the terms comprises and or comprising when used in this specification specify the presence of stated features integers steps operations elements and or components but do not preclude the presence or addition of one or more other features integers steps operations elements components and or groups thereof.

It will be understood that although the terms first second etc. may be used herein to describe various elements components regions layers and or sections these elements components regions layers and or sections should not be limited by these terms. These terms are only used to distinguish one element component region layer or section from another region layer or section. Thus a first element component region layer or section discussed below could be termed a second element component region layer or section without departing from the teachings of the present invention.

Unless otherwise defined all terms including technical and scientific terms used herein have the same meaning as commonly understood by one of ordinary skill in the art to which this invention belongs. It will be further understood that terms such as those defined in commonly used dictionaries should be interpreted as having a meaning that is consistent with their meaning in the context of the relevant art and will not be interpreted in an idealized or overly formal sense unless expressly so defined herein.

A preferred embodiment of the present invention comprises apparatus and methodology directed to confidence interval methodology for ratio means in which a pre existing nonparametric bootstrap t approach is utilized to compute approximate confidence intervals for a ratio mean metric.

For example the standard error SE estimate for a ratio mean as reported by Cochran W. G. Sampling Techniques Third edition John Wiley Sons New York 1977 hereby incorporated by reference is 

This standard error SE estimate in equation 1 is only dependable for samples greater than 30 where the coefficient of variation for both variables are less than 10 as reported by Cochran in the publication referenced above. Therefore another approach is needed to estimate the NBTA parameters for smaller samples and larger samples with high variation. The present invention is intended to overcome the deficiencies of the prior art in this regard.

In accordance with the principles of the present invention with respect to the Mean and SE estimates for ratio mean assuming a random sample without replacement of n vehicles man hours and miles for each vehicle from the population of N vehicles the sample ratio mean may be redefined to be a sample arithmetic mean as depicted in the following Table I.

As shown in Table I the sample ratio mean and the sample arithmetic mean are each defined as the summation of man hours divided by the summation of miles. The redefined variable AdjMR accounts for variation in man hours but does not account for variation in miles. Correlation is also not accounted for because the pairing for man hours and miles for each vehicle has been substantially eliminated.

A preferred embodiment of the present invention utilizes a standardized Z estimate for ratio mean and the confidence interval CI . The redefined data based on a random sample can be used as input for the NBTA nonparametric bootstrap t approach can be used to obtain an estimate for the standardized Z distribution. See Efron B. and Tibshirani R. J. An Introduction to the Bootstrap London U.K. Chapman Hall CRC 1998 hereby incorporated by reference.

Bootstrapping as used herein refers to a modern computer intensive general purpose approach to statistical inference falling within a broader class of re sampling methods. A bootstrap sample BSS of n vehicles is a random sample one vehicle at a time with replacement from the original sample of n vehicles. The probability of selecting a given vehicle for each of the n random selections is 1 n.

Bootstrapping based on a sample has been used to obtain an estimate for the standardized Z distribution as reported by Efron B. et al. An Introduction to the Bootstrap London U.K. Chapman Hall CRC 1998 hereby incorporated by reference. It is interesting to note that if the sample came from a normal distribution then the Z distribution approaches a standard t distribution. The power of bootstrapping enables the accounting for non normal data. Bootstrapping in conjunction with a preferred embodiment of the present invention is used to generate an approximate confidence interval CI around a ratio mean. This is done by generating a large number of BSS s through a Monte Carlo simulation procedure as set forth in Ross S. M. Introduction to Probability Models New York Academic Press 2003 hereby incorporated by reference.

A standardized circumflex over Z distribution may be estimated by bootstrapping from the sample of n vehicles. In a preferred embodiment B bootstrap samples BSS s are generated of size n from the sample of n vehicles. Each of the n elements of BSS i i 1 to B will contain all vehicle information i.e. man hours miles . For each BSS the mean and SE estimate are computed the same way that was done for the original raw sample.

The number of BSS s B must be large enough to assure that the bootstrap circumflex over Z distribution has reached its true form and shape and involves the number of simulation runs needed to get a process to a steady state. If the process is static with respect to time then a Monte Carlo type of simulation is utilized. If the process is dynamic with respect to time and evolves over time then a continuous or discrete event simulation is utilized as reported in Law A. M. and Kelton W. D. Simulation Modeling and Analysis Third edition McGraw Hill Boston 2000 hereby incorporated by reference.

A preferred embodiment of the present invention uses a computational algorithm that relies on repeated random sampling to compute the results such as Monte Carlo methods or BSS s at a point in time and our steady state is the circumflex over Z distribution reaching its true shape.

Determination of when the true shape is reached is based on some relative error rule of the distributional parameters. Our rule is to pick the minimum number of runs such that the total relative error TRE 

For example performance parameters for many systems can be tracked and evaluated using ratio mean metrics such as Maintenance Ratio MR . A Maintenance Ratio MR estimate is based on a sample of n vehicles from a finite population where man hours and miles are associated with each vehicle. Weapons systems refers to the type of vehicle e.g. tank recovery vehicle etc. . The methodology is useful in making informed life cycle management decisions regarding combat systems.

A confidence interval CI for MR using the methodology of a preferred embodiment in a specific environment will provide better information when making a decision on maintenance augmentation before a mission. Some other useful applications of ratio means include Mean failures divided by mean miles Mean number of explosive devices detected divided by mean number of total explosive devices etc. Many other sample ratio means exist for other problems related to military civil government and private organizations.

The maintenance ratio MR data from 2055 wheeled vehicles served as the finite population to validate the methodology of the preferred embodiment by evaluating coverage and other properties. A sample of 92 tracked vehicles MR data were used to demonstrate the methodology. Data for both wheeled and tracked systems were collected from vehicles between December 2003 and June 2008.

In accordance with a preferred embodiment of the present invention an existing tool bootstrap t approach proposed by Efron B. and Tibshirani R. J. An Introduction to the Bootstrap London U.K. Chapman Hall CRC 1998 hereby incorporated by reference with no parametric assumptions on the distributions and is utilized in conjunction with other methodology of the present invention to compute approximate confidence intervals for a ratio mean metric. The bootstrap t utilizes the estimation of three parameters based on a sample 1 Mean 2 Standard Error SE and 3 Bootstrap standardized Z distribution.

The following is an estimate of the arithmetic mean of the population based on the sample of n AdjMR s 

In this example a Bootstrap Sample BSS of n vehicles comprises random sampling of one vehicle at a time with replacement from the original set of n vehicles. The probability of selecting a given vehicle for each of the n random selections is 1 n.

For example suppose n 4 vehicles were randomly selected without replacement from a population of N vehicles. As shown in box of bootstrap samples are generated from n original vehicles. Some possible BSS s of MR values are 

A preferred embodiment comprises bootstrapping among other formulations to generate an approximate confidence interval CI around a ratio mean. This is done by generating a large number of BSS s through a Monte Carlo simulation procedure.

B Bootstrap Samples BSS are generated from the n original vehicles in box of . Next as represented in boxes and C of a standardized bootstrap Z distribution is developed from the sample of n vehicles. The B must be large enough to assure the Z distribution reaches its true form. As referenced in box A each of the n elements of the boot strap sample i i 1 to B contain all vehicle information i.e. man hours and miles for that vehicle.

For each BSS the mean and standard error estimate is computed as represented in box of . The computation of the standardized Z value for each iof the BSS is given by 

Next as represented in estimates are used to compute an approximate 2 sided 100 1 2 confidence interval CI where is the desired area in each tail.

Next the standardized values are ordered and compute the th and 1 th percentiles are computed using the following circumflex over t percentile from the circumflex over Z distribution 1 percentile from the circumflex over Z distribution

For example during the time period of April 1998 through August 2006 in conjunction with the tracking of 92 vehicles recording a total mileage of 81 941 miles and a total of 7 738.9 man hours the MR was 0.094.

The computation of a 90 confidence interval CI 2 sided using a preferred embodiment of the present invention 0.05 implies a 90 confidence interval CI where 100 1 2 equals 90 .

Using the values from box A of 0.0944 circumflex over t E 0.0944 circumflex over t E Where 0.0944 is an estimate of the population MR and where SE 0.008581 is standard error of sampling distribution. t 1.356 t 1.53 are the nonparametric t values used to explain non symmetrical patterns based on bootstrapping .

Factors which effect the foregoing evaluations include sample size location correlation distribution characteristics variation shape and skewness of the two paired variables and outliers. For example assuming all factors are constant except sample size as the sample size increases the confidence interval CI width will decrease or become more efficient . The variability of the sampling distribution for MR increases as more data variability increases. Therefore all other factors constant it can be shown that more variability implies an increase in CI. As correlation increases and all other factors are constant it can be shown that the CI becomes smaller

The circumflex over Z distribution accounts for the correlation of man hours and miles and the variation in man hours and miles. The following mathematical argument creates the framework to the next level of validation 

Using E to serve as the estimate for SE for circumflex over M R knowing that this an imprecise method because circumflex over M R does not fully account for variation in miles. The argument and hypothesis are that the product E circumflex over t is not compromised because the lack of variation of miles in E is accounted for in the circumflex over Z distribution and ultimately circumflex over t . This hypothesis is tested and validated by simulating the confidence interval properties coverage non coverage and efficiency for many ratio mean problems for which validation results were found.

The validity of the present invention methodology was measured by coverage and other confidence interval properties. In order to gauge performance repeated samples from a population were taken and coverage noncoverage efficiency and other properties were evaluated. Coverage was defined to be the percentage of the confidence intervals CIs that contains the true population mean where each CI was constructed with some method or process at a given confidence level for a given paired random sample from a finite population size N or infinite population. For 2 sided CI s non coverage probabilities are the percentage of times the CI misses the true mean to the left or right. Ideally each side has a probability equal to half of the significance level. Efficiency is the average length of all the CI s that were used to create coverage.

Using N 2055 Wheeled vehicles to define our finite population the Finite Population MR 0.0031 the total man hours 29 380 the total miles 9 405 678 Spearman s Rho Correlation 0.25 a determination of the optimal number of S s S is the optimal number of samples without replacement from the finite population becomes a sample size problem where the measurement variable is a desired coverage i.e. lets say 90 and each trial is a binomial outcome.

Using a defined B number of bootstrapped samples BSS to create one confidence interval CI and S number of samples of size n to determine coverage the results of this coverage model 2 sided 90 confidence interval CI with finite population is shown in the following table.

These same results were computed for populations with different MR s distribution shapes and correlation of paired data. The results were generally good except for correlated data near 1 and outliers.

Lognormal distributions with very small CV s less than 0.2 were the best fitting distributions based on MLE using the 1221 CI lengths for each sample size case.

The coverage for preferred embodiment was very close to the required 90 at the low medium and high samples sizes. Also note the non coverage left and right probabilities are close to required 5 for the preferred embodiment except not as balanced when sample size is very small n 15 . Notice how this balance improves as sample size increases. Also different confidence levels were tested with good results.

It is noted that the Coefficient of Variation for Efficiency CVE efficiency MR MR 0.0031 is used for comparison purposes if the population MR are different. This measure of variation based on the efficiency to MR ratio is very similar to CV which measures the variation based on the standard deviation to the mean.

Coverage and its related properties for the preferred embodiment were tested with many ratio mean problems and were shown to perform very well for various measures of sample size correlation location and distribution mix demonstrating the methodology as a reliable and stable tool for building CI s around ratio means.

The only scenarios where coverage starts to deviate away from the required level is for extremely high correlation with highly skewed data existence of outliers in the data that cause the location parameter to shift or cases where the sample sizes are extremely small. When the two variables for the ratio mean are highly correlated the confidence interval tends to be extremely short.

It has been demonstrated that the preferred embodiment methodology is a reliable and stable tool for building confidence intervals CIs around ratio means. Currently the methodology is being used to quantitatively analyze maintenance ratios and other ratio mean performance metrics for fielded systems. The Office of Inspector General for the Department of Health and Human Services has used this methodology for reporting ratio mean confidence intervals to the U.S. Congress. Some other existing applications include performance evaluations for military test systems evaluations of a detection demonstration hypothesis testing development for comparing two ratio means aging effects hypothesis testing and paired reliability hypothesis testing.

The present invention may be utilized in conjunction with observations of failures cost overruns and schedule overruns are routinely better predicted by the simulations than by human intuition or alternative soft methods.

The terminology confidence interval as used herein is an interval estimate of a population parameter which instead of relying on a single value uses an interval likely to include the parameter which may be used to indicate the reliability of an estimate. The likelihood that the interval will contain the parameter is determined by the confidence level or confidence coefficient. Increases in desired confidence level widens the confidence interval. The confidence interval may be qualified by a particular confidence level that is expressed as a percentage such as 90 confidence interval with the end points generally referred to as the limits the higher the confidence level the wider the confidence interval will be.

As used herein the terminology standardized circumflex over Z distribution or circumflex over Z distribution terminology is used herein as defined on page 160 in Efron B. and Tibshirani R. J. An Introduction to the Bootstrap London U.K. Chapman Hall CRC 1998 hereby incorporated by reference and implies the variance transformation distribution using multivariate or ratio data.

As used herein the terminology population means the total number of units under surveillance study inspection or control wherein the units can be vehicles people animals or any subject.

As used herein the terminology sample or samples means a representative unit from the total group which may be selected randomly or by using a selection process.

As used herein the terminology confidence interval means an estimate of a population parameter where instead of estimating the parameter by a single value an interval likely to include the parameter is determined. The likelihood the interval contains the parameter is determined by the confidence level or confidence coefficient.

As used in the following claims the terminology computer means processor microprocessor controller microcontroller multiprocessor CPU or computer network.

As used in the following claims the terminology sample means a number of unts which is a random sample of the population. For ratio mean problems the sample is paired values X i and Y i where i is the iunit.

As used in the following claims the terminology processor means computer microprocessor controller microcontroller multiprocessor CPU or computer network.

As used in the following claims the terminology redefined means each element of the ratio sample i.e. each paired term is redefined using the equation

Although various preferred embodiments of the present invention have been described herein in detail to provide for complete and clear disclosure it will be appreciated by those skilled in the art that variations may be made thereto without departing from the spirit of the invention.

It should be emphasized that the above described embodiments are merely possible examples of implementations. Many variations and modifications may be made to the above described embodiments. All such modifications and variations are intended to be included herein within the scope of the disclosure and protected by the following claims.

