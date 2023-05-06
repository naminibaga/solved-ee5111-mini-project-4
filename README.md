Download Link: https://assignmentchef.com/product/solved-ee5111-mini-project-4
<br>
The aim of this exercise is to study the importance of conjugate priors while performing Bayesian estimation.

Consider the estimation of the covariance of a bivariate Gaussian distribution. We have access to <em>n </em>observations <em>y<sub>i </sub></em>∼ N(<strong>0</strong><em>,</em><strong>Σ</strong>) for <em>i </em>= 1<em>,…n</em>. Here <em>y<sub>i </sub></em>is a 2×1 vector; <strong>Σ </strong>is a 2×2 matrix. We denote by <em>~y </em>the set of all observations, <em>y<sub>i</sub></em>. Perform the following experiments using as the underlying covariance for <em>n </em>= 10<em>,</em>100<em>,</em>1000.

<ol>

 <li>Estimate the covariance using Maximum Likelihood</li>

 <li>Perform Bayesian estimation and provide a point estimate for the covariance. The conjugate prior distribution is the inverse Wishart distribution. The <em>d</em>-dimensional distribution is given by</li>

</ol>

(1)

Consider the following hyperparameters for the prior:  and <em>ν</em><sub>0 </sub>= 5; here

<em>d </em>= 2. (Refer to Section 3.6 in Gelman)

The posterior density is of the same density with parameters

(2)

<strong>∆</strong><em>n </em>= <strong>∆</strong><strong>0 </strong>+ X<em>y</em><em>i</em><em>y</em><em>i</em><em>T                                                                                                           </em>(3)

<em>i</em>=1

<ol start="3">

 <li>Use of Non-informative prior:</li>

</ol>

As an alternative to the conjugate prior, use the non-informative Jeffrey’s prior given by

<em>p</em>(<strong>Σ</strong>) ∝ |<strong>Σ</strong>|<sup>−2</sup><em>,                                                                          </em>(4)

and the independence-Jeffreys prior given by

<em>p</em>(<strong>Σ</strong>) ∝ |<strong>Σ</strong>|<sup>−3<em>/</em>2</sup><em>.                                                                        </em>(5)

What are the differences in the inferences using non-informative priors as compared to the conjugate prior?

<ol start="4">

 <li>Monte Carlo Bayesian estimation:</li>

</ol>

This method is useful when the posterior is not available in closed form. Note that we require the mean of the posterior distribution.

(6)

(7)

Note that the likelihood is

<em> .                                     </em>(8)

Instead of using the closed form expression for the posterior update, find the posterior using Monte Carlo integration using the following equation

(9)

where each <strong>Σ</strong><em><sub>j </sub></em>∼ <em>p</em>(<strong>Σ</strong>) ( a sample drawn from the prior distribution). Report the values of <em>A </em>for <em>n </em>= 10<em>,</em>100<em>,</em>1000 and for <em>m </em>= 10<sup>3</sup><em>,</em>10<sup>4</sup><em>,</em>10<sup>5 </sup>for <em>p</em>(<strong>Σ</strong>) ∼ <em>InvWishart<sub>ν</sub></em><sub>0</sub>(∆<sub>0</sub>) for the following parameters:

.

Which prior performs better? Why do you think it happens? Can you justify why modeling the prior is important? Note that you can now model your prior distribution as any non-conjugate distribution as well.

<ol start="5">

 <li>Hierarchical Bayes estimation and Gibbs sampling:</li>

</ol>

Consider the following formulation of the prior for covariance.

<em>Diag</em>(10)

<strong>1 </strong><em>a</em><strong>2</strong>

)                                                                                    (11)

For performing Gibbs sampling, use the following equations to draw samples iteratively from one distribution and use the drawn samples in the next equation:

!

<em>y<sub>i</sub>y<sub>i</sub></em><em><sup>T                           </sup></em>(12)

(13)

Use <em>A</em><sub>1 </sub>= 0<em>.</em>05 and <em>A</em><sub>2 </sub>= 0<em>.</em>05. Report the covariance estimate after 10<sup>3 </sup>iterations of Gibbs sampling.

<ol start="6">

 <li>Empirical Bayes:</li>

</ol>

For empirical Bayes, we consider an inverse Wishart prior

<em>.                                          </em>(14)

However, instead of using a distribution over the parameters of the Wishart distribution, the marginal likelihood is computed as follows:

Z

<em>p</em>(¯<em>y</em>|<em>ν,</em><strong>∆</strong>) =           <em>p</em>(¯<em>y</em>|<strong>Σ</strong>)<em>p</em>(<strong>Σ</strong>|<em>ν,</em><strong>∆</strong>)<em>d</em><strong>∆                                                 </strong>(15)

The obtained <em>p</em>(¯<em>y</em>|<em>ν,</em><strong>∆</strong>) is then used to maximizing the log likelihood with respect to <em>ν </em>and <strong>∆ </strong>to obtain <em>ν<sub>opt </sub></em>and <strong>∆</strong><em><sub>opt</sub></em>,

<em>y<sub>i</sub>y<sub>i</sub><sup>T                                                                                                                                                                                     </sup></em>(16)

<em>ν<sub>opt </sub></em>= argmax          (17)

where Γ<em><sub>d</sub></em>(<em>a</em>) is the multivariate gamma function,

<em> .                                              </em>(18)

You may employ an iterative optimization algorithm to solve (17). The posterior is given by,

<em>n</em>

<em>p</em>(<strong>Σ</strong>|<em>y,ν</em>¯              <em><sub>opt</sub>,</em><strong>∆</strong><em><sub>opt</sub></em>) = <em>InvWishart</em>(<em>ν<sub>opt </sub></em>+ <em>n,</em><strong>∆</strong><em><sub>opt </sub></em>+ <sup>X</sup><em>y<sub>i</sub>y<sub>i</sub><sup>T</sup></em>)                                  (19)

<em>i</em>=1

Consider the following hyperparameters for the prior:  and <em>ν</em><sub>0 </sub>= 5. You can refer to https://emtiyaz.github.io/Writings/wishart.pdf for more details. Compare the estimate with the one obtained using the conjugate prior, non-informative prior and the hierarchical Bayes method.

<strong>Questions:</strong>

<ul>

 <li>Which of the six methods listed above would you advocate for this problem and why?</li>

 <li>Here, we deal with a dimension of <em>d </em>= 2. For a problem of a higher dimension, which method would you recommend? Justify.</li>

</ul>