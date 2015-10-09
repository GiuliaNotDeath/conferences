## Session Title
------------------------

Using AmgX to accelerate PETSc-based CFD codes

## Contact
------------------------

Pi-Yueh Chuang
PhD Student, George Washington University

## Format
------------------------

25-minute Talk

## Audience Level
------------------------

All

## Topics
------------------------

* Computational Fluid Dynamics
* Supercomputing and HPC

## Other Topic
------------------------

## Session Description
------------------------

We show how to apply AmgX–NVIDIA's experimental library of multi-GPU linear solvers and multigrid preconditioners–to accelerate existing PETSc applications using a wrapper we have developed. With AmgX and this wrapper, programmers can accelerate their existing PETSc applications by adding fewer than 10 lines to their codes. An example using PetIBM–our PETSc-based scalable immersed boundary CFD solver–demonstrates how AmgX can immediately speed up an application and shows how multi-GPU capability can be used for large-scale 3D CFD simulations. This speed-up reduces execution time, lowering computational expense. We demonstrate potential savings using Amazon AWS clusters as an example. We also present performance benchmarks of AmgX and tips for optimizing multigrid preconditioners on GPUs. This presentation is co-authored with Professor Lorena Barba.

## Extended Abstract & Results
------------------------

This work aims to easily accelerate our immersed boundary method CFD codes -- PetIBM, a scalable codes parallelized using PETSc -- without much pain or many modifications to source codes. We choose AmgX for our GPU solvers because its multi-GPU capacity can break the memory limit of a single GPU. We develop a wrapper of AmgX for PETSc to ease the collaboration between them. Before using AmgX in PetIBM, we first explore the performance of AmgX by using 2D and 3D Poisson problems and compare results to the PETSc KSP solvers. The benchmarks show AmgX achieved good speed up. For example, using AmgX and 1~16 K20m to solve a 3D Poisson problem with 4M unknowns against using PETSc KSP solver and a 32-CPU cluster shows a speed up of 5x~15x; for larger problems, using AmgX and 32 K20m GPUs on a 100M-unknown problem has 62x, 26x, 9x speed up comparing to PETSc and 128, 256, 512 CPUs; even using only 1 C2050, an old-generation GPU, shows a 2X speed up comparing to PETSc and 32 CPUs. Solving larger problems on GPUs is limited by the memory on each GPU card. Therefore, we believe with newr GPUs, such as K40, we can observe the same speed up using but less GPUs. By the benchmarks, we also found that optimized parameters for multigrid preconditioners not only depend on the problems to solve but also number of GPUs and model of GPUs. Strategies to set GPU-based multigrid preconditioners also differ from those on CPUs. For instance, F and W cycle may be useful on CPU-based solvers, while the simplest V cycle is more suitable for GPU solvers because solving coarsest-grid system is relatively expansive on GPUs. We are looking forward to more systematic benchmarks in order to give users more sense about how to efficiently use AmgX. Next, we speed up PetIBM using AmgX. In PetIBM, solving Poisson system costs 90% of executing time when using PETSc KSP solvers. We expect a significant speed up of using AmgX. Besides, with the multi-GPU capacity, we can solve larger scale problems or have finer grid resolutions to carry out turbulent flow simulations on multiple GPUs. In additions, with AmgX, users can lower down their money cost on hardware. Take Amazon AWS clusters as an example, if we want to solve the abovementioned 100M-unknown problem on a AWS 512-CPU cluster, it costs about $28 per hour, while solving it on a 32-GPU cluster using AmgX costs about $20 per hour. The more important, the executing time required on the 32-GPU cluster is 9x less than that on the 512-CPU cluster. We expect to present a significant saving on money using PetIBM plus AmgX as an example.

## Presenter Public Speaking History
------------------------
The author is one of the members in Professor Lorena Barba's group. Previous experience of author's speaking history is:

Presentation for paper competition, 19th National Computational Fluid Dynamic Conference, Penghu, Taiwan, 2012

