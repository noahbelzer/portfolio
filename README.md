# Academic Portfolio

## University of Maryland, Baltimore County — Department of Mathematics & Statistics
### Senior Thesis: ***Numerical Simulations in Financial Mathematics Applications*** (2025)
* Faculty Mentor: Dr. Bedřich Sousedík
* Supported by a **$1,000 Undergraduate Research Award (URA)**. The accompanying poster was presented at UMBC's Undergraduate Research and Creative Achievement Day (URCAD) on April 16, 2025.

#### Description:
Our research explored concepts in mathematics, economics, and machine learning, including the Stochastic Discount Factor (SDF) and No-Arbitrage Pricing Theory, as well as the foundations of deep learning. As part of the research, we implemented a general nonlinear asset pricing model developed by Chen, Pelger, and Zhu in their paper "Deep Learning in Asset Pricing" (2024).

We reproduced their results by modifying their Python code, which allowed us to implement a Generative Adversarial Network (GAN) using Feedforward Neural Networks (FFNs), Recurrent Neural Networks (RNNs), and Long Short-Term Memory (LSTM) units. The adversarial structure involved two competing networks that optimized in opposing directions: the Conditional Network, which identified mispriced assets by maximizing pricing errors, and the SDF Network, which learned to minimize the worst-case pricing errors. Then, we evaluated model performance using metrics such as the Sharpe ratio, explained variation, and weighted cross-sectional mean. Our main output was a decile portfolio plot, showing the cumulative excess returns of ten portfolios relative to the risk-free rate.

In addition to reproducing these results, we created our own simplified programs using Python and MATLAB, and we supplemented our research with readings including "Machine Learning for Asset Management and Pricing" (2024) by Schellhorn and Kong, and "Essentials of Investments, 9th Edition" (2012) by Bodie, Kane, and Marcus. We also received $1,000 in funding to create a poster and present our work at Undergraduate Research and Creative Achievement Day (URCAD) on April 16, 2025.

* [View the poster](university-of-maryland-baltimore-county/Numerical_Simulations_in_Financial_Mathematics_Applications_URCAD_Poster.pdf)
* [View the supplementary report](university-of-maryland-baltimore-county/Numerical_Simulations_in_Financial_Mathematics_Applications_URCAD_Report.pdf)
* [View the poster on the professor's site](https://userpages.umbc.edu/~sousedik/classes/slides/undergraduate/URCAD_Poster_Belzer_and_Sousedik_corrected.pdf)

---
### Parallel Computing Reports
The following are reports I completed for the combined undergraduate/graduate course "Introduction to Parallel Computing" offered through the Department of Mathematics & Statistics. I utilized Message Passing Interface (MPI) for parallel computing in C on the [UMBC High Performance Computing Facility](https://hpcf.umbc.edu/).

### I. ***Parallel Finite Difference Method for the Poisson Problem*** (2024)
#### Description:
This report explores the numerical solution of the Poisson problem on a unit square domain using the Finite
Difference Method (FDM) and parallel computing. By implementing the solution in C, both serial and parallel
computations can be run to approximate the answer and measure performance against varying data sizes.

The implementation uses Message-Passing Interface (MPI) to distribute the computation, specifically through
blocking and non-blocking communication, which leads to improved efficiency. Performance comparisons reveal
significant speedups for the parallel C code.

The non-blocking case and blocking case gave very similar results,
however, the non-blocking implementation showed improvement, particularly at larger grid sizes, making it the
most scalable and efficient approach.

* [View pages 1 and 2](university-of-maryland-baltimore-county/Preview_Parallel_Finite_Difference_Method_for_the_Poisson_Problem.pdf)
  
### II. ***Optimized Power Method*** (2024)
#### Description:
The purpose of this report is to compare the results obtained using Basic Linear Algebra Subprograms (BLAS)
in the utility functions with those from HW 3b, where we implemented a parallel version of the power method
in C. For context, the power method is used to compute approximations to the largest eigenvalue in magnitude
and associated eigenvector of a matrix. For this assignment, we are using the utility functions from the previous
report that included a parallel version of the power method.

We used the standard initial guess for the eigenvector x ∈ R^n with components x_j = 1/√n for all 0 ≤ j < n.
Our power method function returns the eigenvalue approximation λ, the eigenvector approximation x, and the
number of iterations taken. We used the same n-values that we used in HW 3b (1024, 2048, 4096, 8192, 16384,
32768, 65536, and 131072). After conducting a test for each n-value, we compared the new λ values to the
values we obtained in the previous assignment and verified that they matched.

- [View page 1](university-of-maryland-baltimore-county/Preview_Optimized_Power_Method.pdf)

[Request to view more](https://docs.google.com/forms/d/e/1FAIpQLSdbuGH-L-Yr3PkZWuVhhFcg-feyPhWO-C0NZBhjf1yoO0CK9g/viewform?usp=publish-editor)

> 🔒 **Note on Access:** University guidelines prevent these documents from being publicly posted, but I am glad to discuss my original work with recruiters and researchers. Please click **"Request to View"** to submit your email, and I will reply ASAP.

---

## University of Edinburgh — School of Informatics

The following are papers I completed for the postgraduate course "Practical Introduction to High Performance Computing" offered through the EPCC (formerly the Edinburgh Parallel Computing Centre). I utilized Message Passing Interface (MPI) for parallel computing in C on [ARCHER2](https://www.epcc.ed.ac.uk/hpc-services/archer2), the UK's national supercomputer.

* ***Parallel Applications on HPC Architectures*** **(2026)**
* ***Parallel Performance and Scalability*** **(2026)**

[Request to View](https://docs.google.com/forms/d/e/1FAIpQLSdbuGH-L-Yr3PkZWuVhhFcg-feyPhWO-C0NZBhjf1yoO0CK9g/viewform?usp=publish-editor)

> 🔒 **Note on Access:** University guidelines prevent these documents from being publicly posted, but I am glad to discuss my original work with recruiters and researchers. Please click **"Request to View"** to submit your email, and I will reply ASAP.

---

## Copyright

© 2026 Noah Belzer. All rights reserved.

Every document in this repository was written by me, except where a work is explicitly co-authored and credited within the document itself. University assignments are labeled.

**No license is granted.** Currently, these documents are made available for reading and evaluation only. No part of them may be reproduced, redistributed, republished, adapted, translated, or used as training data for machine learning systems without my prior written permission. Free-to-use files will be clearly labeled and separated from my academic work.

If you are a student at either the University of Edinburgh or UMBC, and are enrolled in the same course, I cannot share the course papers or reports with you. Reproducing any part of them as your own work can constitute plagiarism under the academic misconduct policies of the University of Edinburgh and/or University of Maryland, Baltimore County (UMBC).
