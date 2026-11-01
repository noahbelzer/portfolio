# Academic Portfolio

## University of Edinburgh — School of Informatics
The following are papers I completed for the postgraduate course "Practical Introduction to High Performance Computing" offered through the EPCC (formerly the Edinburgh Parallel Computing Centre). I utilized Message Passing Interface (MPI) for parallel computing in C on [ARCHER2](https://www.epcc.ed.ac.uk/hpc-services/archer2), the UK's national supercomputer.

### I. ***Parallel Performance and Scalability of a 2D CFD Solver on ARCHER2*** (2026)
#### OVERVIEW:
<ul>
A performance study of an MPI-parallel computational fluid dynamics code, carried out on ARCHER2. The solver computes steady-state flow in a square cavity with an inlet and an outlet, solving Laplace's equation for the stream function by Jacobi iteration on a regular grid. The MPI version uses a 1D domain decomposition in *x*, with halo exchanges between neighboring ranks at each step. An optional viscous mode additionally solves for vorticity at a given Reynolds number.<br><br>

Rather than optimizing the solver, the goal here was to characterize it by measuring how runtime, speedup and parallel efficiency respond to problem size, numerical workload, toolchain, and implementation language, and to design the measurements so that each variable could be isolated cleanly under a fixed compute budget.
</ul>

#### EXPERIMENTS:
<ul>
  
**1. Strong scaling.** Four grid sizes from 2048² to 16384², run on 1–32 fully populated nodes (128–4096 MPI ranks) at a fixed 5000 iterations. Speedup and efficiency are normalized to a 128-rank baseline rather than a single core, since serial runs at the larger grid sizes exceed the queue time limit.<br>

**2. Effect of the vorticity solve.** The same grid sizes and rank counts re-run with Re = 2.5, isolating the cost of the additional per-cell computation and its effect on the compute-to-communication ratio.<br>

**3. Compiler and optimization flags.** Cray CCE, GCC and AOCC compared across default, `-O0`, `-O1`, `-O2`, `-O3` and `-g` at two problem sizes, reported as both wall-clock time and cell update rate (cells/s) so results are comparable across grid sizes.<br>

**4. C vs. Fortran.** The two implementations compared at matched iteration counts, compiler and flags, with per-iteration timings used to separate steady-state cost from startup overhead.<br>

Serial baselines were measured for each experiment where the runtime permitted it.
</ul>

#### TOOLS:
<ul>
C, Fortran, MPI · ARCHER2 (HPE Cray EX) · Cray CCE, GCC, AOCC · Slurm batch submission · MATLAB for analysis and plotting · LaTeX
</ul>

#### RESULTS:
<ul>
Optimization flags account for a larger share of single-node performance than compiler choice: `-O1` through `-O3` cut runtime by roughly a factor of 4–7 over `-O0`, while the three compilers land within a few percent of each other at equivalent flags. The C and Fortran implementations perform comparably, with C holding a small edge in per-iteration time at higher rank counts. The scaling runs show clear benefit from parallelism at the larger grid sizes and diminishing returns at the smallest, where per-rank subdomains become too thin to amortise halo exchange.
</ul>

* [View pages 1 to 3](university-of-edinburgh/Preview_Parallel_Performance_and_Scalability.pdf)
* [Request to view more](https://docs.google.com/forms/d/e/1FAIpQLSdbuGH-L-Yr3PkZWuVhhFcg-feyPhWO-C0NZBhjf1yoO0CK9g/viewform?usp=publish-editor)
> 🔒 **Note:** University guidelines prevent this document from being publicly posted. Recruiters and researchers may click **"Request to view more"** and I will reply ASAP.

### II. ***Fugaku vs. Leonardo: Architecture Comparison for Sparse CFD Workloads*** (2026)
#### OVERVIEW:
<ul>
A comparative analysis of two Top500 supercomputers and their suitability for iterative sparse linear solvers in computational fluid dynamics. This is an analysis and technical writing project rather than a benchmarking study. The method is to characterize both architectures in detail, then infer how a specific CFD application would behave on each by drawing on published sparse-solver results measured on that hardware.
</ul>

#### SCOPE:
<ul>
  
**Architectural profiles.** Fugaku (Fujitsu A64FX, Armv8.2-A with 512-bit SVE, 48 cores and 32 GiB of HBM2 at ~1 TB/s per node, Tofu Interconnect D, three-tier LLIO/FEFS/archival storage) set against Leonardo (Booster partition: Intel Xeon Platinum 8358 with four NVIDIA A100s per node, 512 GiB DDR4, HDR InfiniBand in a Dragonfly+ topology, plus a CPU-only DCGP partition). The comparison covers the homogeneous CPU design against the heterogeneous accelerated one, including Leonardo's switch/cell topology and the distance matrix used for locality-aware job placement.<br>

**Programming environments.** Compiler and library support on each system: Fujitsu MPI and RIKEN-MPICH, OpenMP, XcalableMP, FDPS and SSL II/EigenExa on Fugaku; Intel oneAPI, the NVIDIA HPC SDK, CUDA, OpenACC and cuBLAS/MKL on Leonardo, with attention to where source portability holds and where performance portability breaks down.<br>

**Workload suitability.** Each system assessed against compute-bound, memory-bound, communication-bound and I/O-bound application classes, with the architectural reason for each verdict.<br>

**Case study: FUN3D.** NASA Langley's CFD solver, where sparse linear solves can dominate wall-clock time. Since NASA's SLAT toolkit is not publicly released, performance is inferred from two published studies that did run on the target hardware: SpMV and iterative-kernel measurements on A64FX (Gurhem et al.), and PSCToolkit scaling to 8192 GPUs on Leonardo (D'Ambra et al.).<br>

**Kernel-level analysis.** A CSR SpMV implementation from the TBSLA framework is examined line by line to ground the architectural argument; the indirect access `v[colidx[j]]` that makes the kernel memory-bound, the load imbalance that irregular row lengths create under OpenMP row-wise parallelism, and the limits of SVE gather intrinsics on non-contiguous data.
</ul>

#### ARGUMENT:
<ul>
Sparse solver performance in CFD is governed by data movement rather than floating-point throughput, which reframes the comparison between the two machines. Fugaku's HBM2 bandwidth suits bandwidth-bound kernels directly and at very large node counts, but scaling of full iterative sequences is constrained by global vector assembly and communication. Leonardo offers a higher ceiling through GPU bandwidth and parallelism, and demonstrably strong weak scaling, but realizing it requires GPU-targeted code, storage formats other than CSR to avoid non-coalesced access, and careful management of halo exchanges and reductions, with published strong-scaling efficiency falling to around 44% from 1 to 16 GPUs.
</ul>

#### TOOLS:
<ul>
LaTeX · literature review across vendor documentation, Top500, and peer-reviewed and preprint sources
</ul>

* [View pages 1 to 3](university-of-edinburgh/Preview_Parallel_Applications_on_HPC_Architectures.pdf)
* [Request to view more](https://docs.google.com/forms/d/e/1FAIpQLSdbuGH-L-Yr3PkZWuVhhFcg-feyPhWO-C0NZBhjf1yoO0CK9g/viewform?usp=publish-editor)
> 🔒 **Note:** University guidelines prevent this document from being publicly posted. Recruiters and researchers may click **"Request to view more"** and I will reply ASAP.

---

## University of Maryland, Baltimore County — Department of Mathematics & Statistics
### Senior Thesis: ***Numerical Simulations in Financial Mathematics Applications*** (2025)
* Faculty Mentor: [Dr. Bedřich Sousedík](https://userpages.umbc.edu/~sousedik/)
* Supported by a **$1,000 Undergraduate Research Award (URA)**. The accompanying poster was presented at UMBC's Undergraduate Research and Creative Achievement Day (URCAD) on April 16, 2025.

#### DESCRIPTION:
<ul>
Our research explored concepts in mathematics, economics, and machine learning, including the Stochastic Discount Factor (SDF) and No-Arbitrage Pricing Theory, as well as the foundations of deep learning. As part of the research, we implemented a general nonlinear asset pricing model developed by Chen, Pelger, and Zhu in their paper "Deep Learning in Asset Pricing" (2024).<br><br>

We reproduced their results by modifying their Python code, which allowed us to implement a Generative Adversarial Network (GAN) using Feedforward Neural Networks (FFNs), Recurrent Neural Networks (RNNs), and Long Short-Term Memory (LSTM) units. The adversarial structure involved two competing networks that optimized in opposing directions: the Conditional Network, which identified mispriced assets by maximizing pricing errors, and the SDF Network, which learned to minimize the worst-case pricing errors. Then, we evaluated model performance using metrics such as the Sharpe ratio, explained variation, and weighted cross-sectional mean. Our main output was a decile portfolio plot, showing the cumulative excess returns of ten portfolios relative to the risk-free rate.<br>

In addition to reproducing these results, we created our own simplified programs using Python and MATLAB, and we supplemented our research with readings including "Machine Learning for Asset Management and Pricing" (2024) by Schellhorn and Kong, and "Essentials of Investments, 9th Edition" (2012) by Bodie, Kane, and Marcus. We also received $1,000 in funding to create a poster and present our work at Undergraduate Research and Creative Achievement Day (URCAD) on April 16, 2025.
</ul>

* [View the poster](university-of-maryland-baltimore-county/Numerical_Simulations_in_Financial_Mathematics_Applications_URCAD_Poster.pdf)
* [View the supplementary report](university-of-maryland-baltimore-county/Numerical_Simulations_in_Financial_Mathematics_Applications_URCAD_Report.pdf)
* [View the poster on the professor's site](https://userpages.umbc.edu/~sousedik/classes/slides/undergraduate/URCAD_Poster_Belzer_and_Sousedik_corrected.pdf)

---
### Parallel Computing Reports
The following are reports I completed for the combined undergraduate/graduate course "Introduction to Parallel Computing" offered through the Department of Mathematics & Statistics. I utilized Message Passing Interface (MPI) for parallel computing in C on the [UMBC High Performance Computing Facility](https://hpcf.umbc.edu/).

### I. ***Parallel Finite Difference Method for the Poisson Problem*** (2024)
#### DESCRIPTION:
<ul>
This report explores the numerical solution of the Poisson problem on a unit square domain using the Finite Difference Method (FDM) and parallel computing. By implementing the solution in C, both serial and parallel computations can be run to approximate the answer and measure performance against varying data sizes.<br><br>

The implementation uses Message-Passing Interface (MPI) to distribute the computation, specifically through blocking and non-blocking communication, which leads to improved efficiency. Performance comparisons reveal significant speedups for the parallel C code.<br>

The non-blocking case and blocking case gave very similar results, however, the non-blocking implementation showed improvement, particularly at larger grid sizes, making it the most scalable and efficient approach.
</ul>

* [View pages 1 and 2](university-of-maryland-baltimore-county/Preview_Parallel_Finite_Difference_Method_for_the_Poisson_Problem.pdf)
* [Request to view more](https://docs.google.com/forms/d/e/1FAIpQLSdbuGH-L-Yr3PkZWuVhhFcg-feyPhWO-C0NZBhjf1yoO0CK9g/viewform?usp=publish-editor)
> 🔒 **Note:** University guidelines prevent this document from being publicly posted. Recruiters and researchers may click **"Request to view more"** and I will reply ASAP.
  
### II. ***Optimized Power Method*** (2024)
#### DESCRIPTION:
<ul>
The purpose of this report is to compare the results obtained using Basic Linear Algebra Subprograms (BLAS) in the utility functions with those from a previous assignment, where we implemented a parallel version of the power method in C. For context, the power method is used to compute approximations to the largest eigenvalue in magnitude and associated eigenvector of a matrix. For this assignment, we are using the utility functions from the previous report that included a parallel version of the power method.<br><br>

We used the standard initial guess for the eigenvector x ∈ R^n with components x_j = 1/√n for all 0 ≤ j < n. Our power method function returns the eigenvalue approximation λ, the eigenvector approximation x, and the number of iterations taken. We used the same n-values that we used in HW 3b (1024, 2048, 4096, 8192, 16384, 32768, 65536, and 131072). After conducting a test for each n-value, we compared the new λ values to the values we obtained in the previous assignment and verified that they matched.
</ul>

* [View page 1](university-of-maryland-baltimore-county/Preview_Optimized_Power_Method.pdf)
* [Request to view more](https://docs.google.com/forms/d/e/1FAIpQLSdbuGH-L-Yr3PkZWuVhhFcg-feyPhWO-C0NZBhjf1yoO0CK9g/viewform?usp=publish-editor)
> 🔒 **Note:** University guidelines prevent this document from being publicly posted. Recruiters and researchers may click **"Request to view more"** and I will reply ASAP.

---

## Copyright

© 2026 Noah Belzer. All rights reserved.

Every document in this repository was written by me, except where a work is explicitly co-authored and credited within the document itself. University assignments are labeled.

**No license is granted.** Currently, these documents are made available for reading and evaluation only. No part of them may be reproduced, redistributed, republished, adapted, translated, or used as training data for machine learning systems without my prior written permission. Free-to-use files will be clearly labeled and separated from my academic work.

If you are a student at either the University of Edinburgh or UMBC, and are enrolled in the same course, I cannot share the course papers or reports with you. Reproducing any part of them as your own work can constitute plagiarism under the academic misconduct policies of the University of Edinburgh and/or University of Maryland, Baltimore County (UMBC).
