# A Comprehensive Knowledge Map of Computer Graphics

**Author: Xx1899**

> 🇨🇳 [中文版本 (Chinese Version)](./计算机图形学知识体系目录.md)

---

## Chapter 1 · Mathematical Foundations

> 💡 **Top Picks:**
> - [ericjang/awesome-graphics](https://github.com/ericjang/awesome-graphics) ![Stars](https://img.shields.io/github/stars/ericjang/awesome-graphics?style=flat) — Curated list of CG tutorials, books, math & programming resources
> - [zheng95z/fun-with-computer-graphics](https://github.com/zheng95z/fun-with-computer-graphics) ![Stars](https://img.shields.io/github/stars/zheng95z/fun-with-computer-graphics?style=flat) — Massive collection of CG courses, books, & tutorials (Chinese-friendly)
> - [ssloy/tinyrenderer](https://github.com/ssloy/tinyrenderer) ![Stars](https://img.shields.io/github/stars/ssloy/tinyrenderer?style=flat) — Learn CG math by building a software rasterizer from scratch (~500 lines C++)
> - [Apress/mathematics-for-computer-graphics](https://github.com/Apress/mathematics-for-computer-graphics) — Code companion for *Mathematics for Computer Graphics* (Vince)

### 1.1 Linear Algebra
- 1.1.1 Scalars, Vectors & Vector Spaces
- 1.1.2 Vector Operations (Dot Product, Cross Product, Tensor Product, Mixed Product)
- 1.1.3 Matrices & Matrix Operations (Addition, Multiplication, Transpose, Inverse, Pseudoinverse)
- 1.1.4 Determinant & Rank
- 1.1.5 Linear Transformations (Scaling, Rotation, Shear, Reflection, Projection)
- 1.1.6 Homogeneous Coordinates & Affine Spaces
- 1.1.7 Eigenvalues & Eigenvectors
- 1.1.8 Singular Value Decomposition (SVD)
- 1.1.9 Principal Component Analysis (PCA)
- 1.1.10 Quaternions (Definition, Operations, Interpolation, Conversion to Rotation Matrices)
- 1.1.11 Dual Quaternions
- 1.1.12 Rotation Groups SO(3), SE(3) & Lie Algebras
- 1.1.13 Fundamentals of Tensor Algebra
- 1.1.14 Sparse Matrices & Iterative Solvers

> 📚 **Resources:**
> - [MIT 18.06 Linear Algebra (Gilbert Strang)](https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/) — Classic linear algebra course
> - [fastai/numerical-linear-algebra](https://github.com/fastai/numerical-linear-algebra) ![Stars](https://img.shields.io/github/stars/fastai/numerical-linear-algebra?style=flat) — Jupyter book + high-performance numerical LA
> - [kenjihiranabe/The-Art-of-Linear-Algebra](https://github.com/kenjihiranabe/The-Art-of-Linear-Algebra) ![Stars](https://img.shields.io/github/stars/kenjihiranabe/The-Art-of-Linear-Algebra?style=flat) — Visual graphic notes on key LA concepts
> - [3b1b/manim](https://github.com/3b1b/manim) ![Stars](https://img.shields.io/github/stars/3b1b/manim?style=flat) — Mathematical animation engine for visualizing linear algebra
> - [mml-book/mml-book.github.io](https://github.com/mml-book/mml-book.github.io) ![Stars](https://img.shields.io/github/stars/mml-book/mml-book.github.io?style=flat) — *Mathematics for Machine Learning* companion (Ch.2-5 cover LA)

### 1.2 Calculus
- 1.2.1 Limits, Continuity & Differentiability
- 1.2.2 Derivatives & Partial Derivatives (Single-variable & Multivariable)
- 1.2.3 Gradient, Divergence, Curl
- 1.2.4 Jacobian Matrix & Hessian Matrix
- 1.2.5 Chain Rule & Automatic Differentiation (Forward / Reverse Mode)
- 1.2.6 Taylor Expansion & Function Approximation
- 1.2.7 Definite & Indefinite Integrals
- 1.2.8 Multiple Integrals (Double, Triple)
- 1.2.9 Line Integrals & Surface Integrals
- 1.2.10 Integral Transforms (Fourier Series, Fourier Transform, Laplace Transform)
- 1.2.11 Spherical Harmonics
- 1.2.12 Wavelet Transform Fundamentals
- 1.2.13 Calculus of Variations & Function Spaces
- 1.2.14 Differential Forms & Exterior Algebra Fundamentals

> 📚 **Resources:**
> - [3Blue1Brown Essence of Calculus (YouTube)](https://www.youtube.com/playlist?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr) — Visual, intuitive calculus explanations
> - [ageron/handson-ml3](https://github.com/ageron/handson-ml3) ![Stars](https://img.shields.io/github/stars/ageron/handson-ml3?style=flat) — Hands-On ML book covering calculus, gradient descent, autodiff
> - [dair-ai/ML-Course-Notes](https://github.com/dair-ai/ML-Course-Notes) ![Stars](https://img.shields.io/github/stars/dair-ai/ML-Course-Notes?style=flat) — Curated calculus & ML math notes from top courses
> - [sympy/sympy](https://github.com/sympy/sympy) ![Stars](https://img.shields.io/github/stars/sympy/sympy?style=flat) — Python symbolic math for derivatives, integrals, transforms

### 1.3 Differential Geometry
- 1.3.1 Curve Theory: Arc-length Parameterization, Frenet Frame (Tangent, Normal, Binormal)
- 1.3.2 Curve Theory: Curvature & Torsion
- 1.3.3 Surface Theory: First Fundamental Form (Metric Tensor)
- 1.3.4 Surface Theory: Second Fundamental Form (Shape Operator)
- 1.3.5 Surface Theory: Normal Curvature, Principal Curvature, Gaussian Curvature, Mean Curvature
- 1.3.6 Geodesics & Geodesic Distance
- 1.3.7 Isometric Transformations, Conformal Mapping
- 1.3.8 Laplace-Beltrami Operator on Surfaces
- 1.3.9 Manifold Fundamentals
- 1.3.10 Riemannian Metrics & Riemannian Geometry Fundamentals
- 1.3.11 Exterior Differentiation & Stokes' Theorem
- 1.3.12 Discrete Differential Geometry (DDG)

> 📚 **Resources:**
> - [geometry-central/geometry-central](https://github.com/nmwsharp/geometry-central) ![Stars](https://img.shields.io/github/stars/nmwsharp/geometry-central?style=flat) — Modern C++ library for surface mesh geometry & DDG
> - [libigl/libigl](https://github.com/libigl/libigl) ![Stars](https://img.shields.io/github/stars/libigl/libigl?style=flat) — Swiss-army-knife geometry processing library
> - [Discrete Differential Geometry (Keenan Crane, CMU)](https://www.cs.cmu.edu/~kmcrane/Projects/DDG/) — Freely available notes, slides & videos
> - [alecjacobson/geometry-processing](https://github.com/alecjacobson/geometry-processing) — Course assignments & code (Gaussian curvature, geodesics, Laplace-Beltrami)

### 1.4 Computational Geometry
- 1.4.1 Convex Hull: Graham Scan, QuickHull
- 1.4.2 Delaunay Triangulation
- 1.4.3 Constrained Delaunay Triangulation (CDT)
- 1.4.4 Voronoi Diagram
- 1.4.5 Polygon Triangulation (Ear Clipping, Trapezoidal Decomposition)
- 1.4.6 Boolean Operations (Polygon Clipping, Polyhedron Boolean)
- 1.4.7 Bounding Volume Hierarchies (AABB, OBB, Bounding Sphere, k-DOP)
- 1.4.8 Spatial Partitioning: BVH, k-d Tree, Octree, BSP Tree
- 1.4.9 Nearest Neighbor Search & Range Queries
- 1.4.10 Point-to-Geometry Distance Computation
- 1.4.11 Geometric Intersection: Line Segments, Planes, Triangles, Polyhedra
- 1.4.12 Scanline Algorithms & Plane Sweep
- 1.4.13 Robust Geometric Computation (Floating-Point Error Handling, Exact Arithmetic)

> 📚 **Resources:**
> - [CGAL/cgal](https://github.com/CGAL/cgal) ![Stars](https://img.shields.io/github/stars/CGAL/cgal?style=flat) — C++ Computational Geometry Algorithms Library (the gold standard)
> - [Habrador/Computational-geometry](https://github.com/Habrador/Computational-geometry) ![Stars](https://img.shields.io/github/stars/Habrador/Computational-geometry?style=flat) — Unity/C# implementations of 2D/3D CG algorithms
> - [Turfjs/turf](https://github.com/Turfjs/turf) ![Stars](https://img.shields.io/github/stars/Turfjs/turf?style=flat) — JavaScript spatial analysis & computational geometry
> - [locationtech/jts](https://github.com/locationtech/jts) ![Stars](https://img.shields.io/github/stars/locationtech/jts?style=flat) — Java Topology Suite, core algorithms in Java

### 1.5 Probability & Statistics
- 1.5.1 Probability Spaces & Random Variables
- 1.5.2 Common Distributions (Uniform, Normal, Poisson, Exponential, Beta, Gamma)
- 1.5.3 Conditional Probability & Bayes' Theorem
- 1.5.4 Expectation, Variance, Covariance
- 1.5.5 Markov Chains & Markov Random Fields (MRF)
- 1.5.6 Gaussian Processes
- 1.5.7 Monte Carlo Methods (Importance Sampling, Stratified Sampling, Latin Hypercube)
- 1.5.8 Markov Chain Monte Carlo (MCMC) & Metropolis-Hastings
- 1.5.9 Quasi-Monte Carlo Methods (QMC)
- 1.5.10 Multiple Importance Sampling (MIS)
- 1.5.11 Resampled Importance Sampling (RIS / ReSTIR)
- 1.5.12 Information Theory Fundamentals: Entropy, KL Divergence, Mutual Information

> 📚 **Resources:**
> - [CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers](https://github.com/CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers) ![Stars](https://img.shields.io/github/stars/CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers?style=flat) — Full book + code: Bayesian stats, MCMC from scratch
> - [chi-feng/mcmc-demo](https://github.com/chi-feng/mcmc-demo) ![Stars](https://img.shields.io/github/stars/chi-feng/mcmc-demo?style=flat) — Interactive browser-based MCMC visualization (MH, HMC, NUTS)
> - [probml/pml-book](https://github.com/probml/pml-book) ![Stars](https://img.shields.io/github/stars/probml/pml-book?style=flat) — *Probabilistic Machine Learning* by Kevin Murphy (full book + code)
> - [graykode/distribution-is-all-you-need](https://github.com/graykode/distribution-is-all-you-need) ![Stars](https://img.shields.io/github/stars/graykode/distribution-is-all-you-need?style=flat) — Visual cheatsheet of common probability distributions

### 1.6 Numerical Analysis
- 1.6.1 Floating-Point Representation & IEEE 754 Standard
- 1.6.2 Numerical Error Analysis (Rounding, Truncation, Ill-conditioning)
- 1.6.3 Solving Linear Systems (Gaussian Elimination, LU/Cholesky Decomposition)
- 1.6.4 Iterative Methods (Jacobi, Gauss-Seidel, Conjugate Gradient, Multigrid)
- 1.6.5 Interpolation (Linear, Polynomial, Spline, Radial Basis Functions RBF)
- 1.6.6 Function Approximation (Least Squares, Moving Least Squares MLS)
- 1.6.7 Numerical Integration (Newton-Cotes, Gauss Quadrature, Adaptive Integration)
- 1.6.8 Numerical Solution of ODEs (Euler, Runge-Kutta, Verlet, Implicit Integration)
- 1.6.9 Numerical Solution of PDEs (Finite Difference FDM, Finite Element FEM, Finite Volume FVM)
- 1.6.10 Boundary Element Method (BEM) & Meshless Methods
- 1.6.11 Numerical Solution of Eigenvalue Problems
- 1.6.12 Preconditioners for Sparse Linear Systems
- 1.6.13 Optimization Fundamentals (Gradient Descent, Newton's Method, Quasi-Newton, Conjugate Gradient)

> 📚 **Resources:**
> - [fastai/numerical-linear-algebra](https://github.com/fastai/numerical-linear-algebra) ![Stars](https://img.shields.io/github/stars/fastai/numerical-linear-algebra?style=flat) — Iterative solvers, SVD, QR, LU decomposition in Python
> - [SciML/DifferentialEquations.jl](https://github.com/SciML/DifferentialEquations.jl) ![Stars](https://img.shields.io/github/stars/SciML/DifferentialEquations.jl?style=flat) — Julia suite for numerical ODE/PDE solvers
> - [scientific-python/scipy](https://github.com/scipy/scipy) ![Stars](https://img.shields.io/github/stars/scipy/scipy?style=flat) — Python's standard library for numerical integration, optimization, interpolation
> - [JuliaMath](https://github.com/JuliaMath) — Julia packages for numerical analysis (FFT, linear solve, special functions)

### 1.7 Signal & Image Processing
- 1.7.1 Continuous / Discrete Signals & Systems
- 1.7.2 Sampling Theorem (Nyquist-Shannon)
- 1.7.3 Aliasing & Anti-aliasing
- 1.7.4 Discrete Fourier Transform (DFT) & Fast Fourier Transform (FFT)
- 1.7.5 Filtering (Low-pass, High-pass, Band-pass, Band-stop)
- 1.7.6 Convolution & Correlation
- 1.7.7 Reconstruction Kernels (Box, Tent, Lanczos, Mitchell-Netravali, Gaussian)
- 1.7.8 Multi-resolution Analysis (Image Pyramids, Wavelet Decomposition, Mipmap)
- 1.7.9 Image Gradients (Sobel, Prewitt, Scharr)
- 1.7.10 Edge Detection (Canny, Marr-Hildreth)
- 1.7.11 Histogram Processing & Equalization
- 1.7.12 Morphological Operations (Dilation, Erosion, Opening/Closing)

> 📚 **Resources:**
> - [scikit-image/scikit-image](https://github.com/scikit-image/scikit-image) ![Stars](https://img.shields.io/github/stars/scikit-image/scikit-image?style=flat) — Python image processing algorithms & tutorials
> - [opencv/opencv](https://github.com/opencv/opencv) ![Stars](https://img.shields.io/github/stars/opencv/opencv?style=flat) — Industry-standard computer vision library (filtering, FFT, edge detection)
> - [mikound/awesome-signal-processing](https://github.com/mikound/awesome-signal-processing) — Curated list of signal processing resources
> - [AllenDowney/ThinkDSP](https://github.com/AllenDowney/ThinkDSP) ![Stars](https://img.shields.io/github/stars/AllenDowney/ThinkDSP?style=flat) — *Think DSP* book + code: signals, FFT, convolution, filters

### 1.8 Optimization Theory
- 1.8.1 Unconstrained Optimization (Gradient Descent, Newton's Method, L-BFGS)
- 1.8.2 Constrained Optimization (Lagrange Multipliers, KKT Conditions)
- 1.8.3 Linear Programming & Quadratic Programming (QP)
- 1.8.4 Convex Optimization Fundamentals
- 1.8.5 Global Optimization (Simulated Annealing, Genetic Algorithms, Particle Swarm)
- 1.8.6 Alternating Direction Method of Multipliers (ADMM)
- 1.8.7 Sparse Optimization & Compressed Sensing
- 1.8.8 Gradient Descent Variants (SGD, Adam, RMSprop)

> 📚 **Resources:**
> - [epfml/OptML_course](https://github.com/epfml/OptML_course) ![Stars](https://img.shields.io/github/stars/epfml/OptML_course?style=flat) — EPFL Optimization for ML (convex, SGD, ADMM, Quasi-Newton)
> - [cvxpy/cvxpy](https://github.com/cvxpy/cvxpy) ![Stars](https://img.shields.io/github/stars/cvxpy/cvxpy?style=flat) — Python-embedded convex optimization modeling language
> - [scipy/scipy](https://github.com/scipy/scipy) ![Stars](https://img.shields.io/github/stars/scipy/scipy?style=flat) — `scipy.optimize`: gradient descent, Newton, L-BFGS, global optimization
> - [jakevdp/PythonDataScienceHandbook](https://github.com/jakevdp/PythonDataScienceHandbook) ![Stars](https://img.shields.io/github/stars/jakevdp/PythonDataScienceHandbook?style=flat) — Clear gradient descent & optimization tutorials
> - [cvxgrp/cvx_short_course](https://github.com/cvxgrp/cvx_short_course) — Stanford convex optimization short course (Boyd & Vandenberghe)

## Chapter 2 · Modeling

### 2.1 Explicit Representations

#### 2.1.1 Polygon Meshes
- 2.1.1.1 Mesh Data Structures (Face List, Winged-Edge, Half-Edge, Directed-Edge)
- 2.1.1.2 Manifold vs. Non-manifold Meshes
- 2.1.1.3 Mesh Topology (Euler Characteristic, Genus, Boundaries, Holes)
- 2.1.1.4 Vertex Normal & Face Normal Computation
- 2.1.1.5 Mesh Formats (OBJ, PLY, STL, FBX, glTF, USD, Alembic)
- 2.1.1.6 Adaptive Mesh Refinement (AMR)

#### 2.1.2 Parametric Curves
- 2.1.2.1 Polynomial Interpolation Curves (Lagrange, Hermite)
- 2.1.2.2 Bézier Curves (Bernstein Basis, de Casteljau Algorithm, Degree Elevation/Reduction)
- 2.1.2.3 B-Spline Curves (Knot Vector, Basis Function Recurrence, Local Support)
- 2.1.2.4 NURBS: Weights, Rational Form, Conic Section Representation
- 2.1.2.5 T-Splines
- 2.1.2.6 Subdivision Curves (Chaikin Algorithm, Four-Point Method)

#### 2.1.3 Parametric Surfaces
- 2.1.3.1 Tensor Product Surfaces
- 2.1.3.2 Bézier Surfaces
- 2.1.3.3 B-Spline Surfaces (Uniform, Non-uniform)
- 2.1.3.4 NURBS Surfaces (Trimmed NURBS)
- 2.1.3.5 Surfaces of Revolution & Swept Surfaces
- 2.1.3.6 Coons Surfaces & Gordon Surfaces
- 2.1.3.7 N-Sided Patch Filling

#### 2.1.4 Subdivision Surfaces
- 2.1.4.1 Catmull-Clark Subdivision (Quad Meshes)
- 2.1.4.2 Loop Subdivision (Triangle Meshes)
- 2.1.4.3 Doo-Sabin Subdivision
- 2.1.4.4 √3 Subdivision
- 2.1.4.5 Butterfly Subdivision (Interpolatory)
- 2.1.4.6 Semi-sharp Crease & Boundary Feature Handling
- 2.1.4.7 Adaptive Subdivision

### 2.2 Implicit Representations

#### 2.2.1 Traditional Implicit Methods
- 2.2.1.1 Algebraic Surfaces (Zero-sets of Polynomials)
- 2.2.1.2 Isosurfaces
- 2.2.1.3 Blobby Models / Metaballs
- 2.2.1.4 Function Representation (F-Rep / FRep)
- 2.2.1.5 Signed Distance Fields (SDF) & Operations (Union, Intersection, Difference, Smooth Blend, Offset)
- 2.2.1.6 R-Functions (Rvachev Functions)
- 2.2.1.7 Fractals (Mandelbrot Set, Julia Set, IFS Iterated Function Systems)

#### 2.2.2 Neural Implicit Representations
- 2.2.2.1 SIREN (Sinusoidal Activation Networks)
- 2.2.2.2 Positional Encoding & Fourier Features
- 2.2.2.3 Occupancy Networks
- 2.2.2.4 DeepSDF
- 2.2.2.5 Neural Radiance Field (NeRF) & Variants
- 2.2.2.6 Instant Neural Graphics Primitives (Instant NGP, Multi-resolution Hash Encoding)
- 2.2.2.7 3D Gaussian Splatting (Explicit-Implicit Hybrid)

### 2.3 Voxels & Discrete Representations
- 2.3.1 Uniform Grids
- 2.3.2 Sparse Voxel Octree (SVO)
- 2.3.3 Adaptively Sampled Distance Fields (ADFs)
- 2.3.4 Adaptive Mesh Refinement (AMR)
- 2.3.5 Clipmaps & Virtual Textures
- 2.3.6 Signed Distance Field Voxelization
- 2.3.7 OpenVDB (Sparse Hierarchical Voxel Data Structure)

### 2.4 Point Clouds & Point-Based Representations
- 2.4.1 Point Cloud Acquisition (LiDAR, Structured Light, Photogrammetry, Depth Cameras)
- 2.4.2 Point Cloud Registration (ICP: Point-to-Point, Point-to-Plane, Generalized ICP, Go-ICP Global Registration)
- 2.4.3 Point Cloud Features (PFH, FPFH, SHOT, ISS Keypoints, Normal Estimation)
- 2.4.4 Point Cloud Filtering (Voxel Downsampling, Statistical Outlier Removal, Bilateral Filtering)
- 2.4.5 Point Cloud Segmentation & Clustering (RANSAC, Region Growing, Euclidean Clustering, Supervoxels)
- 2.4.6 Point-Based Rendering (Point Splatting, QSplat, Surfels)
- 2.4.7 Point Cloud Completion & Upsampling

### 2.5 Constructive Solid Geometry (CSG)
- 2.5.1 Primitives: Cube, Sphere, Cylinder, Cone, Torus
- 2.5.2 Boolean Operations (Union ∪, Intersection ∩, Difference \, Symmetric Difference)
- 2.5.3 CSG Trees & Evaluation
- 2.5.4 Boundary Evaluation Algorithms
- 2.5.5 Point Classification for CSG Models (Point Classification & Ray Casting)

### 2.6 Procedural Modeling
- 2.6.1 Noise Functions (Perlin, Simplex, Worley/Voronoi, Curl Noise)
- 2.6.2 Fractional Brownian Motion (fBm) & Turbulence
- 2.6.3 L-Systems: Plant & Tree Modeling, Stochastic & Parametric L-Systems
- 2.6.4 Shape Grammars: Architecture & City Modeling
- 2.6.5 Fractal Terrain (Diamond-Square / Midpoint Displacement, Erosion Simulation)
- 2.6.6 Tile-Based / Wave Function Collapse (WFC)
- 2.6.7 Self-Similar Structure Generation
- 2.6.8 Physically-Based Growth Simulation (Diffusion-Limited Aggregation DLA)
- 2.6.9 Data-Driven Procedural Modeling (Learning Rules from Examples)

### 2.7 Data-Driven Modeling
- 2.7.1 Photogrammetry & Structure from Motion (SfM)
- 2.7.2 Multi-View Stereo (MVS): PMVS, PatchMatch
- 2.7.3 Depth Map Fusion (TSDF / KinectFusion, Voxel Hashing)
- 2.7.4 Semantic Modeling (from Images / Point Clouds to Semantic CAD)
- 2.7.5 Reverse Engineering & CAD Reconstruction
- 2.7.6 3D Generative Models (3D GANs, Diffusion Models, Autoregressive Models)
- 2.7.7 Text-to-3D (DreamFusion, SJC, Magic3D, ProlificDreamer)
- 2.7.8 Image-to-3D (Single-view / Multi-view Reconstruction Networks)

### 2.8 Scene Graphs & Hierarchical Representations
- 2.8.1 Scene Graph Data Structure (Hierarchical Tree Transforms)
- 2.8.2 Entity-Component-System (ECS) Architecture
- 2.8.3 Bounding Volume Hierarchy (BVH) Construction & Update
- 2.8.4 Level of Detail (LOD) — Discrete LOD, Continuous LOD, View-Dependent LOD
- 2.8.5 Instancing & Indirect Drawing
- 2.8.6 GPU-Driven Rendering Batching & Batch Strategies
- 2.8.7 Large-World Coordinate Handling (Floating-Point Precision, Camera-Relative Rendering, Multi-Origin)

---

## Chapter 3 · Rendering

### 3.1 Rendering Equation & Theoretical Foundations

#### 3.1.1 Radiometry
- 3.1.1.1 Radiant Flux (Power) Φ
- 3.1.1.2 Irradiance E — Incident Area Density
- 3.1.1.3 Radiant Exitance (Radiosity) B / M
- 3.1.1.4 Radiant Intensity I — Per Unit Solid Angle
- 3.1.1.5 Radiance L — Per Unit Projected Area, Per Unit Solid Angle
- 3.1.1.6 Spectral Radiometry
- 3.1.1.7 Solid Angles & Projected Solid Angles

#### 3.1.2 BRDF / BTDF / BSDF / BSSRDF
- 3.1.2.1 BRDF Definition & Properties (Non-negativity, Helmholtz Reciprocity, Energy Conservation)
- 3.1.2.2 Isotropic BRDF vs. Anisotropic BRDF
- 3.1.2.3 Diffuse Reflection Models (Lambert, Oren-Nayar, Disney Diffuse)
- 3.1.2.4 Specular Reflection & Smooth-Surface Microfacet Models (Cook-Torrance)
- 3.1.2.5 Microfacet Theory: Normal Distribution Function NDF (Beckmann, GGX/Trowbridge-Reitz, GTR)
- 3.1.2.6 Microfacet Theory: Geometric Shadowing-Masking Function (Smith, Cook-Torrance, Heitz Height-Correlated Masking)
- 3.1.2.7 Microfacet Theory: Fresnel Equations (Schlick Approximation, Full Fresnel)
- 3.1.2.8 Disney Principled BRDF
- 3.1.2.9 BTDF & Refraction
- 3.1.2.10 BSDF = BRDF + BTDF
- 3.1.2.11 Layered Material BRDF (Clear Coat, Thin-Film Interference)
- 3.1.2.12 Wave Optics BRDF (Diffraction, Thin-Film Interference)
- 3.1.2.13 BSSRDF & Subsurface Scattering (Dipole Model, Multipole, Path-Space Formulation)
- 3.1.2.14 Measured BRDF / Data-Driven BRDF (MERL, MIT CSAIL, EPFL Databases)

#### 3.1.3 The Rendering Equation
- 3.1.3.1 Kajiya's Rendering Equation (1986)
- 3.1.3.2 Surface Form: Emission Term + Reflection Term
- 3.1.3.3 Area Form
- 3.1.3.4 Path Form & Path-Space Formulation
- 3.1.3.5 Operator Form & Neumann Series Expansion
- 3.1.3.6 Adjoint Equation & Importance Function

### 3.2 Rasterization Rendering

#### 3.2.1 Graphics Pipeline Overview
- 3.2.1.1 Application Stage (CPU): Scene Management, Visibility Determination, Draw Calls
- 3.2.1.2 Geometry Processing Stage (GPU): Vertex Shader → Tessellation → Geometry Shader
- 3.2.1.3 Rasterization Stage: Primitive Assembly, Triangle Setup, Triangle Traversal
- 3.2.1.4 Pixel Processing Stage: Fragment Shader → Output Merger
- 3.2.1.5 Fixed-Function Pipeline vs. Programmable Pipeline
- 3.2.1.6 Modern GPU Pipeline (Mesh Shader / Task Shader → Simplified Geometry Pipeline)

#### 3.2.2 Geometry Processing
- 3.2.2.1 Model Transform (Model Matrix)
- 3.2.2.2 View Transform (View Matrix / Camera Matrix)
- 3.2.2.3 Projection Transforms: Perspective & Orthographic Projection Matrices
- 3.2.2.4 Perspective Division & Normalized Device Coordinates (NDC)
- 3.2.2.5 Viewport Transform
- 3.2.2.6 Vertex Shader Programming
- 3.2.2.7 Tessellation Shaders (Tessellation Control / Evaluation Shader)
- 3.2.2.8 Geometry Shader
- 3.2.2.9 Primitive Assembly (Points, Lines, Triangles, Triangle Strips/Fans)
- 3.2.2.10 Back-Face Culling
- 3.2.2.11 Clipping (Cohen-Sutherland, Sutherland-Hodgman, Guard Band Clipping)

#### 3.2.3 Rasterization & Fragment Processing
- 3.2.3.1 Line Rasterization (DDA Algorithm, Bresenham's Algorithm)
- 3.2.3.2 Triangle Rasterization (Barycentric Coordinates, Edge Function Method, Scanline Fill)
- 3.2.3.3 Perspective-Correct Interpolation
- 3.2.3.4 Depth Testing & Depth Buffering (Z-Buffer, W-Buffer, Reverse-Z)
- 3.2.3.5 Stencil Testing & Stencil Buffer
- 3.2.3.6 Blending: Alpha Blending, Premultiplied Alpha, Sorting & Blend Modes
- 3.2.3.7 Multi-Sample Anti-Aliasing (MSAA: 2×, 4×, 8×, EQAA/CSAA)
- 3.2.3.8 Super-Sample Anti-Aliasing (SSAA), Coverage Sampling AA (CSAA)
- 3.2.3.9 Temporal Anti-Aliasing (TAA)
- 3.2.3.10 Deep-Learning-Based Anti-Aliasing (DLSS, FSR, XeSS)
- 3.2.3.11 Morphological Anti-Aliasing (MLAA, SMAA, FXAA, CMAA)
- 3.2.3.12 Fragment / Pixel Shader Programming
- 3.2.3.13 Early-Z / Hi-Z Culling
- 3.2.3.14 Variable Rate Shading (VRS)
- 3.2.3.15 Conservative Rasterization
- 3.2.3.16 Tile-Based Rendering Architecture (TBDR)

#### 3.2.4 Texture Mapping
- 3.2.4.1 Texture Coordinates (UV) & Parameterization
- 3.2.4.2 Texture Filtering: Nearest-Neighbor, Bilinear, Trilinear
- 3.2.4.3 Anisotropic Filtering
- 3.2.4.4 Mipmap Generation: Per-Level Downsampling (Box, Kaiser, Lanczos Kernels)
- 3.2.4.5 Texture Sampling & Addressing Modes (Wrap, Mirror, Clamp, Border)
- 3.2.4.6 Compressed Texture Formats (BC1-BC7, ASTC, ETC2, PVRTC)
- 3.2.4.7 Floating-Point Textures & HDR Textures (Half/Float, Shared Exponent Format)
- 3.2.4.8 Cubemaps & Environment Mapping
- 3.2.4.9 Bump Mapping: Normal Perturbation
- 3.2.4.10 Normal Mapping: Tangent Space & Normal Compression
- 3.2.4.11 Displacement Mapping: Vertex Displacement
- 3.2.4.12 Parallax Mapping, Steep Parallax Mapping, Relief Mapping
- 3.2.4.13 Procedural Textures (Checkerboard, Marble, Wood, Cloud Noise)
- 3.2.4.14 Volume Textures (3D Textures) & Noise Volumes
- 3.2.4.15 Texture Atlases & Array Textures
- 3.2.4.16 Virtual Textures (MegaTexture / Tiled Resources / Sparse Textures)
- 3.2.4.17 Bindless Textures
- 3.2.4.18 Ptex (Per-Face Texture Mapping)

#### 3.2.5 Shading Models
- 3.2.5.1 Lighting Fundamentals: Directional, Point, Spot, Area Lights, Ambient Light
- 3.2.5.2 Diffuse Reflection: Lambertian Shading
- 3.2.5.3 Specular Highlights: Phong Reflection Model
- 3.2.5.4 Blinn-Phong Reflection Model (Half-Vector Approximation)
- 3.2.5.5 Physically-Based Rendering (PBR) Concepts: Energy Conservation, Metal/Dielectric Distinction
- 3.2.5.6 Metallic-Roughness Workflow
- 3.2.5.7 Specular-Glossiness Workflow
- 3.2.5.8 Image-Based Lighting (IBL)
- 3.2.5.9 Precomputed Diffuse Irradiance Map
- 3.2.5.10 Prefiltered Environment Map (Specular IBL)
- 3.2.5.11 Split-Sum Approximation
- 3.2.5.12 Environment BRDF Lookup Table (LUT: BRDF Integration Map)
- 3.2.5.13 Deferred Shading: G-Buffer Layout
- 3.2.5.14 Forward+ Rendering / Tiled Forward Shading
- 3.2.5.15 Clustered Shading (Clustered Deferred / Forward)
- 3.2.5.16 Visibility Buffer & Deferred Materials

#### 3.2.6 Shadows
- 3.2.6.1 Planar Projected Shadows (Projective Shadows)
- 3.2.6.2 Shadow Volumes: Stencil Buffer Method (Carmack's Reverse / Depth-Fail)
- 3.2.6.3 Shadow Mapping: Basic Principles
- 3.2.6.4 Perspective Shadow Maps (PSM)
- 3.2.6.5 Cascaded Shadow Maps (CSM)
- 3.2.6.6 Parallel-Split Shadow Maps (PSSM)
- 3.2.6.7 Tight Frustum Culling
- 3.2.6.8 Variance Shadow Maps (VSM)
- 3.2.6.9 Convolution Shadow Maps (CSM)
- 3.2.6.10 Exponential Shadow Maps (ESM)
- 3.2.6.11 Exponential Variance Shadow Maps (EVSM)
- 3.2.6.12 Moment Shadow Maps (MSM)
- 3.2.6.13 Percentage Closer Soft Shadows (PCSS)
- 3.2.6.14 Percentage Closer Filtering (PCF)
- 3.2.6.15 Screen-Space Contact / Short-Range Ambient Occlusion Shadows
- 3.2.6.16 Ray-Traced Shadows (DXR 1.1 / Vulkan RT)
- 3.2.6.17 Virtual Shadow Maps (Unreal Engine 5 Style)
- 3.2.6.18 Translucent / Colored Shadows

#### 3.2.7 Environmental Effects
- 3.2.7.1 Sky Rendering (Skybox, Atmospheric Scattering Models, Precomputed Atmospheric Scattering)
- 3.2.7.2 Volumetric Clouds: Noise-Based, Weather Texture, Ray Marching
- 3.2.7.3 Fog: Linear Fog, Exponential Fog, Height Fog
- 3.2.7.4 Volumetric Light (God Rays / Light Shafts)
- 3.2.7.5 Volumetric Fog & Participating Media
- 3.2.7.6 Rain & Snow Effects (Particle Systems + Screen-Space Effects)
- 3.2.7.7 Water Surface Rendering (Reflection, Refraction, Caustics, Waves, Foam, Crest)
- 3.2.7.8 Underwater Effects (Underwater Fog / Caustics / Color Absorption)

### 3.3 Ray Tracing

#### 3.3.1 Baseline Ray Tracing
- 3.3.1.1 Ray Generation (Perspective Camera, Orthographic Camera, Pinhole Model)
- 3.3.1.2 Ray-Geometry Intersection (Sphere, Plane, Möller-Trumbore Triangle, AABB Slab Method)
- 3.3.1.3 Ray-Parametric Surface Intersection (Newton's Iteration, Bézier Clipping)
- 3.3.1.4 Ray-Implicit Surface Intersection (Ray Marching / Sphere Tracing)
- 3.3.1.5 Whitted-Style Ray Tracing (Recursive Reflection + Refraction + Shadow Rays)
- 3.3.1.6 Snell's Law of Refraction & Total Internal Reflection
- 3.3.1.7 Fresnel Effect Handling (Schlick / Exact Fresnel)
- 3.3.1.8 Distributed Ray Tracing (Cook et al. 1984): Soft Shadows, Motion Blur, Depth of Field, Glossy Reflections

#### 3.3.2 Acceleration Structures
- 3.3.2.1 Bounding Volume Hierarchy (BVH): Construction (SAH Binning/Bucketing, HLBVH, PLOC)
- 3.3.2.2 BVH Traversal (Stack vs. Stackless, Compressed Wide BVH)
- 3.3.2.3 BVH Update & Rebuild (Top-Down / Bottom-Up Rebuild, Refit)
- 3.3.2.4 K-d Tree: Construction (SAH, Midpoint Split), Traversal
- 3.3.2.5 Uniform Grids & Hierarchical Grids
- 3.3.2.6 Octree Acceleration Structures
- 3.3.2.7 Two-Level BVH (TLAS + BLAS, DXR / Vulkan RT Model)
- 3.3.2.8 Shader Execution Reordering (SER)
- 3.3.2.9 Acceleration Structure Quality Evaluation (SAH Cost Model, Traversal Steps, Bounding-Box Tightness)

#### 3.3.3 Path Tracing & Global Illumination
- 3.3.3.1 Path Tracing (Kajiya 1986) Basic Algorithm
- 3.3.3.2 Monte Carlo Integration Recap & Rendering Applications
- 3.3.3.3 Importance Sampling:
  - 3.3.3.3.1 Cosine-Weighted Hemisphere Sampling
  - 3.3.3.3.2 BRDF Importance Sampling (GGX/Beckmann VNDF Sampling)
  - 3.3.3.3.3 Light Source Importance Sampling (Area Sampling, Directional Sampling)
  - 3.3.3.3.4 Environment Map Importance Sampling
- 3.3.3.4 Multiple Importance Sampling (MIS): Balance Heuristic, Power Heuristic
- 3.3.3.5 One-Sample MIS
- 3.3.3.6 Russian Roulette & Path Termination
- 3.3.3.7 Bidirectional Path Tracing (BDPT)
- 3.3.3.8 Vertex Merging & Photon Mapping (Photon Emission, Photon Map, Radiance Estimation)
- 3.3.3.9 Progressive Photon Mapping (PPM)
- 3.3.3.10 Stochastic Progressive Photon Mapping (SPPM)
- 3.3.3.11 Unified Vertex Connection & Merging (VCM / UPS / Unified Path Sampling)
- 3.3.3.12 Photon Beams / Photon Planes
- 3.3.3.13 Metropolis Light Transport (MLT: Primary Sample Space MLT, Path Space MLT)
- 3.3.3.14 Manifold Exploration / Manifold Next Event Estimation (MNEE)
- 3.3.3.15 Path Space Regularization
- 3.3.3.16 Progressive Rendering & Adaptive Sampling
- 3.3.3.17 Path Guiding (Practical Path Guiding, SD-Tree/Quad-Tree Guiding)
- 3.3.3.18 Neural Path Guiding

#### 3.3.4 Real-Time & Interactive Ray Tracing
- 3.3.4.1 Hardware-Accelerated Ray Tracing (NVIDIA RT Core, AMD Ray Accelerator, Intel Arc)
- 3.3.4.2 DXR (DirectX Raytracing) API Fundamentals
- 3.3.4.3 Vulkan Ray Tracing (VK_KHR_ray_tracing_pipeline)
- 3.3.4.4 OptiX Framework
- 3.3.4.5 Metal Ray Tracing
- 3.3.4.6 Denoising:
  - 3.3.4.6.1 Spatial Denoising: Bilateral Filter, Guided Filter, À-Trous Wavelets
  - 3.3.4.6.2 Temporal Denoising: Temporal Accumulation, Motion Vectors, Rejection Sampling
  - 3.3.4.6.3 Regression-Based Denoising (SVGF, BMFR)
  - 3.3.4.6.4 Neural Network Denoising (OptiX Denoiser, OIDN, NRD)
  - 3.3.4.6.5 Super-Resolution Joint Denoising (DLSS Ray Reconstruction)
- 3.3.4.7 Importance Sampling & Path-Space Filtering
- 3.3.4.8 LOD in Ray Tracing (Simplified BVH Geometry, Shader Substitution)
- 3.3.4.9 ReSTIR (Reservoir-based Spatiotemporal Importance Resampling):
  - ReSTIR DI (Direct Illumination)
  - ReSTIR GI (Global Illumination)
  - ReSTIR PT (Path Tracing)
  - Generalized Resampling Theory
- 3.3.4.10 Asynchronous Ray Tracing & Async Compute
- 3.3.4.11 Hybrid Rendering (Raster + Ray Tracing): Hybrid Reflections, Hybrid AO, Hybrid GI

#### 3.3.5 Participating Media Rendering
- 3.3.5.1 Volume Rendering Equation (Radiative Transfer Equation, RTE)
- 3.3.5.2 Absorption Coefficient σₐ, Scattering Coefficient σₛ, Extinction Coefficient σₜ, Phase Function
- 3.3.5.3 Transmittance (Optical Depth)
- 3.3.5.4 Free-Path Sampling (Woodcock Tracking / Delta Tracking)
- 3.3.5.5 Volumetric Path Tracing
- 3.3.5.6 Volumetric Photon Mapping
- 3.3.5.7 Phase Functions: Isotropic, Rayleigh, Mie (Henyey-Greenstein)
- 3.3.5.8 Null-Collision & Heterogeneous Media (Cascaded Shadow Grids, Adaptive Sampling)
- 3.3.5.9 Atmospheric Scattering (Precomputed Atmospheric Scattering, Bruneton Model, Hillaire Real-Time Atmosphere)
- 3.3.5.10 Cloud, Smoke, Fire, Fog Rendering
- 3.3.5.11 Subsurface Scattering (Skin, Marble, Jade & Other Translucent Materials)

### 3.4 Real-Time Global Illumination

#### 3.4.1 Precomputation Methods
- 3.4.1.1 Lightmaps: Offline Baking + Real-Time Texture Mapping
- 3.4.1.2 Light Probes: Spherical Harmonics (SH) / Ambient Occlusion Storage
- 3.4.1.3 Reflection Probes: Box Projection Correction, Blending
- 3.4.1.4 Precomputed Radiance Transfer (PRT)
- 3.4.1.5 Irradiance Volumes

#### 3.4.2 Real-Time Methods
- 3.4.2.1 Screen-Space Ambient Occlusion (SSAO, SSAO+, HBAO, GTAO, CACAO)
- 3.4.2.2 Screen-Space Reflections (SSR): Ray Marching, Hi-Z Acceleration
- 3.4.2.3 Screen-Space Global Illumination (SSGI)
- 3.4.2.4 Reflective Shadow Maps (RSM): Indirect Light Source
- 3.4.2.5 Virtual Point Lights (VPL / Instant Radiosity)
- 3.4.2.6 Light Propagation Volumes (LPV)
- 3.4.2.7 Cascaded Light Propagation Volumes
- 3.4.2.8 Voxel Cone Tracing (VXGI)
- 3.4.2.9 Surfel-Based GI: G-Buffer Surfel Generation, Hierarchical Radiosity
- 3.4.2.10 Ray-Traced GI (RTXGI): Probe Re-lighting + Spatiotemporal Filtering
- 3.4.2.11 Dynamic Diffuse Global Illumination (DDGI)
- 3.4.2.12 Lumen (Unreal Engine 5): Surfel Cards + Screen-Space Tracing + Mesh SDF Tracing + Radiance Cache
- 3.4.2.13 Signed Distance Field-Based GI (SDF Tracing)

### 3.5 Participating Media & Transparent Surfaces
- 3.5.1 Translucency & Transparency Sorting: Order-Independent Transparency (OIT)
  - 3.5.1.1 Depth Peeling
  - 3.5.1.2 Weighted Blended OIT
  - 3.5.1.3 Per-Pixel Linked Lists
  - 3.5.1.4 Moment-Based OIT
  - 3.5.1.5 Stochastic Transparency
- 3.5.2 Volume Rendering (Direct Volume Rendering) — Rasterization Pipeline
- 3.5.3 Volume Ray Marching

### 3.6 Non-Photorealistic Rendering (NPR)

#### 3.6.1 Cartoon / Anime Style
- 3.6.1.1 Edge / Outline Rendering: Inverted-Hull Method, Image-Processing Method, Edge-Detection Based
- 3.6.1.2 Cel Shading / Toon Shading: Quantized Diffuse & Specular
- 3.6.1.3 Contour Types: Contours, Creases, Material Boundaries, Silhouettes
- 3.6.1.4 View-Dependent Line Width Variation

#### 3.6.2 Artistic Styles
- 3.6.2.1 Sketch / Hatching / Cross-Hatching (Tonal Art Maps)
- 3.6.2.2 Watercolor-Style Rendering
- 3.6.2.3 Oil-Painting-Style Rendering
- 3.6.2.4 Pointillism / Mosaic Style
- 3.6.2.5 Halftoning
- 3.6.2.6 Line Art Rendering / Technical Illustration

#### 3.6.3 Abstract & Special Effects
- 3.6.3.1 Noise-Based Stylization (Dithering, Grain)
- 3.6.3.2 Stroke-Based Rendering
- 3.6.3.3 Style Transfer (Deep-Learning-Based Image/Video Stylization)
- 3.6.3.4 Real-Time Style Transfer

### 3.7 Post-Processing & Image-Space Techniques

#### 3.7.1 Tone Mapping & Display
- 3.7.1.1 Tone Mapping Operators: Reinhard, Filmic (Uncharted 2 / ACES), Hable, Gran Turismo
- 3.7.1.2 Exposure Control: Automatic Exposure (Eye Adaptation)
- 3.7.1.3 HDR Display Support (HDR10, Dolby Vision, scRGB)
- 3.7.1.4 Gamut Mapping Between SDR & HDR

#### 3.7.2 Color Processing
- 3.7.2.1 White Balance
- 3.7.2.2 Color Grading: LUTs, CDL, Curves
- 3.7.2.3 Saturation, Contrast, Brightness Adjustments
- 3.7.2.4 Look-Up Table (LUT) Generation & Application
- 3.7.2.5 HDR Display Mapping / Output Transform

#### 3.7.3 Lens Simulation Effects
- 3.7.3.1 Depth of Field (DoF): Bokeh, Bokeh Shape Simulation
- 3.7.3.2 Motion Blur: Per-Pixel Velocity Vectors, Camera/Object Blur
- 3.7.3.3 Bloom: Downsampling Pyramid + Compositing
- 3.7.3.4 Lens Flare: Ghosting, Glow, Diffraction Spikes
- 3.7.3.5 Glare
- 3.7.3.6 Chromatic Aberration
- 3.7.3.7 Vignette
- 3.7.3.8 Film Grain
- 3.7.3.9 Lens Distortion (Radial, Tangential)

#### 3.7.4 Super-Resolution & Image Reconstruction
- 3.7.4.1 Spatial Super-Resolution (FSR 1.0)
- 3.7.4.2 Temporal Super-Resolution (TAAU, DLSS 2/3/4, FSR 2/3/4, XeSS)
- 3.7.4.3 Frame Generation (DLSS Frame Generation, FSR 3 Frame Generation)
- 3.7.4.4 Multi Frame Generation (DLSS 4 / Multi Frame Generation)
- 3.7.4.5 Checkerboard Rendering
- 3.7.4.6 Variable Rate Shading (VRS) + Super-Resolution Synergy

### 3.8 Differentiable Rendering
- 3.8.1 Differentiable Rasterization: Forward & Backward Propagation
- 3.8.2 Differentiable Path Tracing: Edge Sampling, Reparameterization Tricks
- 3.8.3 Differentiable Volume Rendering (Gradients in NeRF Volume Rendering)
- 3.8.4 Differentiable BRDF / Material Optimization
- 3.8.5 Differentiable Geometry Optimization (Mesh Vertex Gradient Propagation)
- 3.8.6 Inverse Rendering:
  - 3.8.6.1 Recovering Geometry from Images (Photometric Stereo, Shape-from-Shading)
  - 3.8.6.2 Recovering Materials & Lighting from Images (Inverse Path Tracing)
  - 3.8.6.3 Joint Inverse Rendering (Simultaneous Estimation of Geometry, Materials & Lighting)
- 3.8.7 Differentiable Rendering Frameworks (Mitsuba 3, Redner, PSDR-CUDA, Nvdiffrast, Slang.D)

### 3.9 Neural Rendering
- 3.9.1 Neural Radiance Field (NeRF): Positional Encoding, Hierarchical Sampling, Coarse-to-Fine
- 3.9.2 NeRF Acceleration (Instant NGP, TensoRF, Plenoxels, DIVeR, MERF, SMERF)
- 3.9.3 Few-View NeRF (PixelNeRF, MVSNeRF, RegNeRF, FreeNeRF)
- 3.9.4 Dynamic NeRF (D-NeRF, HyperNeRF, TiNeuVox, K-Planes)
- 3.9.5 Large-Scale Scene NeRF (Block-NeRF, Mega-NeRF, BungeeNeRF)
- 3.9.6 Editable / Relightable NeRF (NeRF-Editing, NeRF-W / NeRF in the Wild)
- 3.9.7 3D Gaussian Splatting (3DGS):
  - 3.9.7.1 Point Primitives + Covariance Matrices + Spherical Harmonics Colors
  - 3.9.7.2 Adaptive Density Control (Clone / Split)
  - 3.9.7.3 Tile-Based Differentiable Rasterization
  - 3.9.7.4 Variants: 2DGS (Surfel), Dynamic 4DGS, Compressed 3DGS
- 3.9.8 Neural SDF / Occupancy Fields (NeuS, VolSDF, MonoSDF)
- 3.9.9 Neural Materials (Neural BRDF / Neural BTF)
- 3.9.10 Neural Radiance Cache (NRC)
- 3.9.11 Diffusion-Model-Based 3D Generation (DreamFusion / SDS Loss, SJC, ProlificDreamer / VSD)
- 3.9.12 Feed-Forward 3D Reconstruction (LRM, Instant3D, LGM, GRM)

---

## Chapter 4 · Animation

### 4.1 Keyframe Animation
- 4.1.1 Keyframes & Interpolation Curves
- 4.1.2 Linear Interpolation
- 4.1.3 Bézier / Spline Curve Interpolation
- 4.1.4 Easing Functions: Ease-in, Ease-out, Ease-in-out
- 4.1.5 Time Remapping
- 4.1.6 Parameterized Keyframes (Arc-Length Parameterization)

### 4.2 Skeletal Animation

#### 4.2.1 Skeleton Structure
- 4.2.1.1 Joint Hierarchy
- 4.2.1.2 Local vs. Global Transforms
- 4.2.1.3 Bind Pose / Rest Pose
- 4.2.1.4 Joint Limits / Constraints

#### 4.2.2 Forward Kinematics (FK)
- 4.2.2.1 Chain Transform Composition
- 4.2.2.2 Transformation Matrix Stack
- 4.2.2.3 FK in the Animation Pipeline

#### 4.2.3 Inverse Kinematics (IK)
- 4.2.3.1 Analytical IK (Closed-Form for 2-Joint / 3-Joint Chains)
- 4.2.3.2 Cyclic Coordinate Descent (CCD)
- 4.2.3.3 Jacobian Methods (Jacobian Transpose / Damped Least Squares / Pseudo-Inverse)
- 4.2.3.4 FABRIK (Forward And Backward Reaching IK)
- 4.2.3.5 Full-Body IK
- 4.2.3.6 IK Constraints (Look-At, Pole Vector, Goal Matching)

#### 4.2.4 Skinning
- 4.2.4.1 Rigid Skinning / Partition Skinning
- 4.2.4.2 Linear Blend Skinning (LBS / Skeletal Subspace Deformation)
- 4.2.4.3 LBS Artifacts: Candy-Wrapper Effect, Volume Collapse
- 4.2.4.4 Dual Quaternion Skinning (DQS)
- 4.2.4.5 Optimization-Based Skinning
- 4.2.4.6 Rigid / Elasticity-Based Skinning
- 4.2.4.7 Skinning Decomposition (SSDR / Smooth Skinning Decomposition)
- 4.2.4.8 Delta Mush Smoothing
- 4.2.4.9 Pose Space Deformation (PSD)
- 4.2.4.10 Automatic Skinning Weight Computation / Heat Diffusion (Bounded Biharmonic Weights, BBW)

### 4.3 Deformation Techniques

#### 4.3.1 Mesh-Based Deformation
- 4.3.1.1 Free-Form Deformation (FFD): Lattice Deformation
- 4.3.1.2 As-Rigid-As-Possible Deformation (ARAP)
- 4.3.1.3 Laplacian Mesh Editing / Differential Coordinates
- 4.3.1.4 Skeleton-Based Deformation
- 4.3.1.5 Spatial Deformation: Bend, Twist, Taper, Stretch
- 4.3.1.6 Cage-Based Deformation: Mean Value Coordinates, Harmonic Coordinates, Green Coordinates
- 4.3.1.7 Biharmonic Deformation

#### 4.3.2 Blend Shapes
- 4.3.2.1 Blend Shapes / Morph Targets
- 4.3.2.2 Facial Action Coding System (FACS)
- 4.3.2.3 Automatic Blend Shape Generation (Scan-to-Target)
- 4.3.2.4 PCA-Based Expression Compression
- 4.3.2.5 Corrective Blend Shapes

#### 4.3.3 Data-Driven Deformation
- 4.3.3.1 Example-Based Deformation
- 4.3.3.2 Parametric Human Body Models (SMPL, SMPL-X, STAR, GHUM)
- 4.3.3.3 Parametric Face Models (FaceWarehouse, FLAME, 3DMM)
- 4.3.3.4 Parametric Hand Models (MANO)

### 4.4 Rigid Body Simulation

#### 4.4.1 Fundamental Dynamics
- 4.4.1.1 Newton's Laws of Motion & Euler's Equations of Motion
- 4.4.1.2 Rigid Body Kinematics (Position, Orientation, Linear Velocity, Angular Velocity)
- 4.4.1.3 Rigid Body Dynamics (Force, Torque, Inertia Tensor)
- 4.4.1.4 Center of Mass & Equations of Motion in World Coordinates

#### 4.4.2 Time Integration
- 4.4.2.1 Explicit Euler Method
- 4.4.2.2 Semi-Implicit Euler (Symplectic Euler)
- 4.4.2.3 Verlet Integration
- 4.4.2.4 Runge-Kutta Methods (RK4)
- 4.4.2.5 Implicit Integration (Backward Euler)

#### 4.4.3 Collision Detection
- 4.4.3.1 Collision Detection Pipeline: Broad Phase → Narrow Phase → Response
- 4.4.3.2 Broad-Phase Algorithms: Sweep and Prune (SAP), Spatial Hashing, BVH
- 4.4.3.3 Narrow-Phase Algorithms:
  - 4.4.3.3.1 Gilbert-Johnson-Keerthi (GJK) Algorithm
  - 4.4.3.3.2 Expanding Polytope Algorithm (EPA)
  - 4.4.3.3.3 Separating Axis Theorem (SAT)
  - 4.4.3.3.4 Feature-Pair Detection (Lin-Canny, V-Clip)
- 4.4.3.4 Continuous Collision Detection (CCD): Sweep-Based CCD, Speculative CCD
- 4.4.3.5 Collision Response: Impulse-Based, Penalty Force, Constraint Solver
- 4.4.3.6 Friction Models (Coulomb Model, Static & Dynamic Friction)
- 4.4.3.7 Stacking & Resting Contact Handling (Contact Manifold, Contact Graph)

#### 4.4.4 Constrained Dynamics
- 4.4.4.1 Joint Types: Ball-and-Socket, Hinge, Slider, Fixed
- 4.4.4.2 Constraint Equations & Jacobian Matrices
- 4.4.4.3 Force-Based Constraints (Penalty Method)
- 4.4.4.4 Impulse-Based Constraints (Sequential Impulse / PGS Solver)
- 4.4.4.5 Position-Based Dynamics (PBD)
- 4.4.4.6 Extended Position-Based Dynamics (XPBD)
- 4.4.4.7 Reduced Coordinate Methods (Featherstone Algorithm)
- 4.4.4.8 Soft Body Constraints (Strain Constraints: Stretch, Shear, Bend)

### 4.5 Soft Body & Deformable Body Simulation

#### 4.5.1 Mass-Spring Systems
- 4.5.1.1 Mass-Spring Model Fundamentals
- 4.5.1.2 Structural Springs, Shear Springs, Bend Springs
- 4.5.1.3 Damping & Numerical Dissipation
- 4.5.1.4 Cloth Simulation Applications (Provot Cloth Model)

#### 4.5.2 Finite Element Method (FEM)
- 4.5.2.1 Continuum Mechanics Fundamentals: Deformation Gradient, Green Strain, Cauchy Stress
- 4.5.2.2 Constitutive Models: Linear Elastic (Hooke), Hyperelastic (Neo-Hookean, Mooney-Rivlin, StVK)
- 4.5.2.3 Plasticity Models (von Mises, Drucker-Prager)
- 4.5.2.4 FEM Discretization: Tetrahedra, Hexahedra, Shape Functions, Stiffness Matrix Assembly
- 4.5.2.5 Implicit Integration & Newton-Raphson Solver
- 4.5.2.6 Optimization-Based Implicit Integration (Projective Dynamics)
- 4.5.2.7 Fast Corotational FEM

#### 4.5.3 Meshless & Particle Methods
- 4.5.3.1 Smoothed Particle Hydrodynamics (SPH)
- 4.5.3.2 Material Point Method (MPM)
- 4.5.3.3 Moving Least Squares MPM (MLS-MPM)
- 4.5.3.4 Discrete Element Method (DEM)

### 4.6 Fluid Simulation

#### 4.6.1 Grid-Based Methods
- 4.6.1.1 Navier-Stokes Equations
- 4.6.1.2 Incompressibility Condition (div v = 0)
- 4.6.1.3 Staggered Grid (MAC Grid)
- 4.6.1.4 Advection Solvers: Semi-Lagrangian, BFECC, MacCormack
- 4.6.1.5 Pressure Projection & Poisson Equation Solver (Conjugate Gradient, Multigrid)
- 4.6.1.6 Free Surface Handling (VOF Method, Level Set Method, Particle Level Set)
- 4.6.1.7 Vorticity Confinement
- 4.6.1.8 Coupled Boundary Conditions (Solid Wall, Inflow/Outflow, Periodic)

#### 4.6.2 Particle-Based Methods
- 4.6.2.1 SPH Fluid Simulation (WCSPH, IISPH, DFSPH, PCISPH)
- 4.6.2.2 Fluid-Implicit Particle (FLIP / PIC)
- 4.6.2.3 Affine Particle-In-Cell (APIC)
- 4.6.2.4 PolyPIC / High-Order PIC

#### 4.6.3 Hybrid Methods
- 4.6.3.1 FLIP + Grid (Hybrid FLIP)
- 4.6.3.2 Particles + Level Set
- 4.6.3.3 MPM for Fluids (Engineering & Visual Hybrid)

#### 4.6.4 Specialized Fluid Effects
- 4.6.4.1 Free-Surface Flows (Water, Ocean Waves: Gerstner Waves, FFT Ocean)
- 4.6.4.2 Bubbles & Foam
- 4.6.4.3 Viscoelastic Fluids (Giesekus, Oldroyd-B)
- 4.6.4.4 Multiphase Flows (Liquid-Gas, Liquid-Solid Coupling)
- 4.6.4.5 Surface Tension Modeling
- 4.6.4.6 Two-Way Fluid-Rigid Body Coupling
- 4.6.4.7 Real-Time Fluid Simulation (NVIDIA Flex, PhysX Fluids, Unreal Niagara Fluids)

### 4.7 Particle Systems & VFX
- 4.7.1 Particle Fundamentals (Emitters, Velocity, Lifetime, Force Fields)
- 4.7.2 GPU Particles (Compute-Shader-Driven, Transform Feedback)
- 4.7.3 Particle Collisions (with Scene Geometry, Inter-Particle Collisions)
- 4.7.4 Particle Lighting & Rendering (Billboards, Soft Particles, Trails/Ribbons)
- 4.7.5 VFX Applications: Sparks, Explosions, Smoke & Dust, Magic, Debris
- 4.7.6 Niagara (UE) / VFX Graph (Unity) Advanced Particle Systems

### 4.8 Character Animation

#### 4.8.1 Kinematics
- 4.8.1.1 Human Kinematic Model (Joint DOFs, Range of Motion)
- 4.8.1.2 Motion Retargeting
- 4.8.1.3 Motion Warping & Stylization

#### 4.8.2 Motion Synthesis
- 4.8.2.1 Motion Graphs
- 4.8.2.2 Motion Matching: Feature Vector Search
- 4.8.2.3 Learned Motion Matching (Neural Network Acceleration)
- 4.8.2.4 Motion Fields

#### 4.8.3 Procedural Animation
- 4.8.3.1 Procedural Locomotion: Foot IK, Gait Cycle Adaptation
- 4.8.3.2 Procedural Adaptation (Terrain Adaptation, Slope Handling, Obstacle Stepping)
- 4.8.3.3 Physics-Based Character Animation
- 4.8.3.4 Deep Reinforcement Learning for Character Control (DeepMimic, AMP, ASE)

#### 4.8.4 Facial Animation
- 4.8.4.1 Facial Action Coding System (FACS / Action Units)
- 4.8.4.2 Speech-Driven Lip Sync (Viseme Mapping)
- 4.8.4.3 Facial Performance Capture & Retargeting
- 4.8.4.4 Neural-Network-Based Facial Animation (Audio2Face, Video-Driven Facial Animation)

#### 4.8.5 Motion Capture & Processing
- 4.8.5.1 Optical Motion Capture (Vicon, OptiTrack)
- 4.8.5.2 Inertial Motion Capture (Xsens, Rokoko)
- 4.8.5.3 Video-Based Motion Capture (OpenPose, MediaPipe, HybrIK, WHAM)
- 4.8.5.4 Motion Data Formats (BVH, FBX, ASF/AMC, C3D)
- 4.8.5.5 Motion Data Cleaning & Filtering (Denoising, Gap Filling, Smoothing)
- 4.8.5.6 Motion Data Annotation & Segmentation

### 4.9 Crowd Simulation
- 4.9.1 Boids Model (Separation, Alignment, Cohesion)
- 4.9.2 Continuum Crowds Model
- 4.9.3 Social Force Model
- 4.9.4 Velocity-Obstacle-Based Methods (RVO / ORCA)
- 4.9.5 Multi-Agent Reinforcement Learning Navigation
- 4.9.6 Large-Scale Crowd Rendering (Instancing, LOD, Impostors)

### 4.10 Hair & Fiber Simulation
- 4.10.1 Hair Geometry Representation: Guide Hairs + Interpolation
- 4.10.2 Hair Dynamics: FTL (Follow The Leader), Spring Chains
- 4.10.3 Hair Collision Detection & Self-Collision
- 4.10.4 Hair Rendering: Kajiya-Kay Model, Marschner Model, Dual-Cylinder Scattering Model
- 4.10.5 Clump-Based Hair & Level-of-Detail
- 4.10.6 Animal Fur (Fur Shells / Fin Geometry + Transparent Layering)
- 4.10.7 GPU Hair Rendering (TressFX, HairWorks, Compute-Shader-Based)
- 4.10.8 Feather Modeling

---

## Chapter 5 · Geometry Processing

### 5.1 Mesh Data Structures & Basic Operations
- 5.1.1 Mesh Data Structures Overview (Face Sets, Winged-Edge, Half-Edge, Directed-Edge, Corner Table)
- 5.1.2 Adjacency Operations (Vertex→Face, Vertex→Edge, Face→Face, Edge→Face, etc.)
- 5.1.3 Local Topological Operations (Edge Collapse, Edge Split, Edge Flip, Vertex Removal)
- 5.1.4 Euler Operators (Topology-Preserving Editing Primitives)
- 5.1.5 Normal Computation (Uniform / Area / Angle Weighting)
- 5.1.6 Gaussian Curvature & Mean Curvature Estimation (Discrete Differential Geometry Operators)
- 5.1.7 Principal Curvature Direction & Principal Curvature Estimation
- 5.1.8 Shape Diameter Function

### 5.2 Mesh Simplification & Refinement
- 5.2.1 Vertex Clustering
- 5.2.2 Edge Collapse Simplification: QEM Quadric Error Metric (Garland-Heckbert)
- 5.2.3 Appearance-Preserving Simplification (Image-Driven Simplification)
- 5.2.4 Progressive Meshes
- 5.2.5 Adaptive Simplification (View-Dependent LOD / View-Dependent Refinement)
- 5.2.6 Mesh Refinement (Inverse of Subdivision: √3 Refinement, Loop Refinement Application)
- 5.2.7 Remeshing: Isotropic / Anisotropic Remeshing

### 5.3 Mesh Smoothing & Denoising
- 5.3.1 Laplacian Smoothing (Umbrella Operator)
- 5.3.2 Bilateral Mesh Filtering
- 5.3.3 Mean Curvature Flow
- 5.3.4 Optimization-Based Denoising: L₀ Minimization, L₁ Sparse Optimization
- 5.3.5 Non-Local Means Denoising
- 5.3.6 Feature-Preserving Smoothing
- 5.3.7 Guided Normal Filtering
- 5.3.8 Deep-Learning-Based Mesh Denoising

### 5.4 Mesh Parameterization
- 5.4.1 Parameterization Fundamentals (Planar Embedding, Distortion Metrics)
- 5.4.2 Convex Combination Methods (Floater Mean Value Coordinates, Harmonic Maps)
- 5.4.3 Geometry-Energy-Based Methods (Dirichlet Energy, Conformal Energy)
- 5.4.4 Least Squares Conformal Maps (LSCM)
- 5.4.5 As-Rigid-As-Possible Parameterization (ARAP)
- 5.4.6 Fixed-Boundary / Free-Boundary / Angle-Based Flattening (ABF)
- 5.4.7 Globally Seamless Parameterization
- 5.4.8 Cone Singularities & Seam Generation
- 5.4.9 Cross-Parameterization / Consistent Parameterization
- 5.4.10 Volumetric Parameterization (Tetrahedral / Hexahedral Parameterization)
- 5.4.11 UV Atlas Packing (Rectangle Packing)

### 5.5 Surface Reconstruction
- 5.5.1 From Point Clouds to Meshes:
  - 5.5.1.1 Marching Cubes
  - 5.5.1.2 Marching Tetrahedra
  - 5.5.1.3 Poisson Surface Reconstruction
  - 5.5.1.4 Screened Poisson Reconstruction
  - 5.5.1.5 Radial Basis Function Implicit Surface Reconstruction (RBF Reconstruction)
  - 5.5.1.6 Floating-Scale Poisson Reconstruction (FPSR)
- 5.5.2 Multi-View Stereo Reconstruction (MVS Patch-Based, Depth Map Fusion)
- 5.5.3 TSDF-Based Fusion (KinectFusion, Voxel Hashing)
- 5.5.4 Occupancy Field to Mesh Extraction (Multi-resolution Iso-surface Extraction)
- 5.5.5 Deep-Learning-Based Surface Reconstruction (Deep Marching Cubes, Occupancy Networks, Neural Surface)
- 5.5.6 Sketch-Based Modeling (Reconstruction from Line Drawings)
- 5.5.7 Complete & Partial Scan Completion / Registration

### 5.6 Shape Analysis
- 5.6.1 Shape Descriptors:
  - 5.6.1.1 Global: Spherical Harmonic Descriptor, Shape Distributions (D2), Zernike Moments
  - 5.6.1.2 Local: Spin Images, SHOT, FPFH, RoPS
  - 5.6.1.3 Spectral Descriptors (Heat Kernel Signature HKS, Wave Kernel Signature WKS)
- 5.6.2 Shape Correspondence:
  - 5.6.2.1 Functional Maps Framework
  - 5.6.2.2 Spectral Matching / Blended Intrinsic Maps
  - 5.6.2.3 Non-Rigid Registration (Non-rigid ICP, CPD)
- 5.6.3 Symmetry Detection:
  - 5.6.3.1 Reflection Symmetry, Rotational Symmetry, Translational Symmetry
  - 5.6.3.2 Intrinsic Symmetry (Geodesic-Based Symmetry Detection)
- 5.6.4 Mesh Segmentation:
  - 5.6.4.1 Curvature-Based / Watershed-Based
  - 5.6.4.2 Spectral Clustering
  - 5.6.4.3 Randomized Cuts
  - 5.6.4.4 Machine-Learning-Based Segmentation (PointNet Variants for Segmentation)
- 5.6.5 Skeletonization: Medial Axis Transform, Curve Skeleton
- 5.6.6 Mesh Saliency (Visual Attention Regions)

### 5.7 Deformation & Editing
- 5.7.1 Differential-Coordinate-Based Editing (Laplacian Coordinates / δ-Coordinates)
- 5.7.2 ARAP Deformation
- 5.7.3 Spatial Deformation (FFD, Cage Deformation, Green Coordinates)
- 5.7.4 Physics-Based Deformation (Linear Elastic FEM, Neo-Hookean Nonlinear Deformation)
- 5.7.5 Large-Deformation Handling & Rotation Estimation (Polar Decomposition)
- 5.7.6 Shape Interpolation & Deformation Transfer

### 5.8 Mesh Repair & Cleanup
- 5.8.1 Non-Manifold Detection & Repair
- 5.8.2 Consistent Normal Orientation
- 5.8.3 Self-Intersection Detection & Repair
- 5.8.4 Hole Filling (Minimal-Area-Based, Curvature-Continuity-Based)
- 5.8.5 Degenerate & Zero-Area Face Handling
- 5.8.6 Topological Error Repair (Non-Manifold Edges/Vertices, Isolated Vertices, Duplicate Faces)
- 5.8.7 Watertight Conversion
- 5.8.8 Deep-Learning-Based Automatic Repair

### 5.9 Geometry Compression
- 5.9.1 Geometry Compression Fundamentals (Quantization, Prediction, Entropy Coding)
- 5.9.2 Mesh Compression Standards: MPEG-4 3DMC, Draco (Google), Cortocodec
- 5.9.3 Progressive Mesh Compression
- 5.9.4 Neural-Network-Based Geometry Compression
- 5.9.5 Lossy/Lossless Compression of Texture Coordinates & Attributes

---

## Chapter 6 · Color Science & Visual Perception

### 6.1 Photometry & Colorimetry Fundamentals
- 6.1.1 Visible Spectrum & Radiometry Review
- 6.1.2 Photometric Units (Lumen lm, Candela cd, Lux lx, Nit cd/m²)
- 6.1.3 Human Visual System Characteristics (Photoreceptors: Cones/Rods, Spectral Sensitivity)

### 6.2 Color Spaces
- 6.2.1 CIE 1931 XYZ Color Space
- 6.2.2 CIE xy Chromaticity Diagram
- 6.2.3 CIE 1976 L\*a\*b\* (CIELAB) Color Space: Perceptual Uniformity
- 6.2.4 CIE L\*u\*v\* Color Space
- 6.2.5 CIE LCh (Lightness, Chroma, Hue) Color Space
- 6.2.6 sRGB: Primaries, White Point, Gamma Curve, Linear vs. Encoded Values
- 6.2.7 DCI-P3, Display P3
- 6.2.8 Adobe RGB, ProPhoto RGB
- 6.2.9 Rec.709 (HDTV), Rec.2020 (UHD/HDR)
- 6.2.10 ACES (Academy Color Encoding System): ACES2065-1, ACEScg, ACEScct
- 6.2.11 ICtCp (ITU-R BT.2100)
- 6.2.12 Wide Color Gamut (WCG)
- 6.2.13 OKLab / OKLCH (Perceptually Uniform Color Spaces)

### 6.3 Gamma, Transfer Functions & Tone Mapping
- 6.3.1 Gamma Encoding & Correction (Gamma 2.2, sRGB EOTF/OETF)
- 6.3.2 Transfer Functions (OETF / EOTF)
- 6.3.3 PQ (Perceptual Quantizer, ST.2084 / SMPTE 2084)
- 6.3.4 HLG (Hybrid Log-Gamma)
- 6.3.5 Scene-Referred vs. Display-Referred Pipelines
- 6.3.6 Tone Mapping Operators (Review 3.7.1)
- 6.3.7 HDR-to-SDR Dynamic Range Adaptation

### 6.4 Color Appearance Models
- 6.4.1 CIECAM02 / CIECAM16
- 6.4.2 iCAM06 (HDR Image Appearance Model)
- 6.4.3 Chromatic Adaptation Transforms (von Kries, Bradford, CAT02/16)

### 6.5 Visual Perception Models
- 6.5.1 Contrast Sensitivity Function (CSF)
- 6.5.2 Just Noticeable Difference (JND)
- 6.5.3 Visual Masking Effects: Luminance Masking, Texture Masking, Temporal Masking
- 6.5.4 Perceptual Metrics (SSIM, MS-SSIM, FSIM, LPIPS, DISTS, ST-LPIPS)
- 6.5.5 Visual Attention Models (Saliency Maps, Itti-Koch Model, Deep Gaze Prediction)
- 6.5.6 Perception-Driven Rendering Optimization (Foveated Rendering)

### 6.6 High Dynamic Range Imaging
- 6.6.1 HDR Image Formats (OpenEXR, Radiance HDR, PFM, JPEG-XL HDR, AVIF HDR)
- 6.6.2 Multi-Exposure HDR Merging (Debevec & Malik Method, Robertson Method)
- 6.6.3 Ghost Removal
- 6.6.4 HDR Display Technologies (OLED, Mini-LED, Micro-LED Backlight)
- 6.6.5 HDR Environment Map Capture & Processing

---

## Chapter 7 · Hardware Architecture & Systems

### 7.1 GPU Architecture

#### 7.1.1 Rendering Pipeline Hardware View
- 7.1.1.1 Vertex Fetch & Geometry Engines
- 7.1.1.2 Primitive Assembly & Rasterizer (ROPs)
- 7.1.1.3 Texture Mapping Units (TMU) & Cache Hierarchy
- 7.1.1.4 Streaming Multiprocessor (SM / CU / Xe Core) Architecture
- 7.1.1.5 SIMD / SIMT Execution Model: Warp / Wavefront / Subgroup
- 7.1.1.6 Branch Divergence & Occupancy
- 7.1.1.7 Register File & Shared Memory / Local Data Share (LDS)
- 7.1.1.8 Raster Output Units (ROP) & Pixel Blending

#### 7.1.2 Modern GPU Features
- 7.1.2.1 Async Compute & Parallel Queues
- 7.1.2.2 Mesh Shader / Task Shader Pipeline (Replacing Legacy Geometry Pipeline)
- 7.1.2.3 Variable Rate Shading (VRS Tier 1/2)
- 7.1.2.4 Sampler Feedback & Texture-Space Shading
- 7.1.2.5 Ray Tracing Cores (RT Core: BVH Traversal, Triangle Intersection Acceleration)
- 7.1.2.6 Tensor Cores (Matrix Multiply Acceleration, AI Inference/Denoising/DLSS)
- 7.1.2.7 Shader Execution Reordering (SER)
- 7.1.2.8 Opacity & Displacement Micro-Maps (OMM / DMM)
- 7.1.2.9 GPU Work Graphs (GPU-Driven Rendering Pipeline)
- 7.1.2.10 DirectStorage (GPU Direct-to-SSD Access)

#### 7.1.3 Video Memory & Bandwidth
- 7.1.3.1 VRAM Types: GDDR6/6X/7, HBM2/3/3e
- 7.1.3.2 Cache Hierarchy (L1, L2, Infinity Cache / Last-Level Cache)
- 7.1.3.3 Bandwidth Compression (Delta Color Compression, DCC / Lossless Bandwidth Compression)
- 7.1.3.4 Hardware Texture Compression Support (BCn, ASTC, ETC)
- 7.1.3.5 Sparse / Partially Resident Resources (Tiled Resources / Sparse Textures)

### 7.2 Graphics APIs

#### 7.2.1 OpenGL / OpenGL ES / WebGL
- 7.2.1.1 OpenGL Pipeline Model & State Machine
- 7.2.1.2 OpenGL ES 3.x / WebGL 2.0 Capability Sets
- 7.2.1.3 Extension Mechanism (GL_EXT / GL_ARB)
- 7.2.1.4 Bindless Design (Bindless Textures / ARB_bindless_texture)
- 7.2.1.5 AZDO (Approaching Zero Driver Overhead) Techniques

#### 7.2.2 Vulkan
- 7.2.2.1 Instance, Physical Device, Logical Device
- 7.2.2.2 Command Buffers & Command Pools (Multi-Threaded Recording)
- 7.2.2.3 Pipeline State Objects (PSO): Graphics / Compute / Ray Tracing Pipelines
- 7.2.2.4 Descriptor Set Layouts & Descriptor Pools (Descriptor Indexing / Update After Bind)
- 7.2.2.5 Synchronization Primitives: Semaphores, Fences, Pipeline Barriers, Subpass Dependencies
- 7.2.2.6 Render Pass & Dynamic Rendering
- 7.2.2.7 Memory Management: VMA (Vulkan Memory Allocator), Device-Local vs. Host-Visible
- 7.2.2.8 Push Constants & Specialization Constants
- 7.2.2.9 Timeline Semaphores
- 7.2.2.10 Vulkan Ray Tracing (VK_KHR_ray_tracing_pipeline)
- 7.2.2.11 Vulkan Video Encode/Decode (VK_KHR_video_queue)

#### 7.2.3 DirectX 12
- 7.2.3.1 Device Creation & Factory Pattern
- 7.2.3.2 Command Queues, Command Lists, Command Allocators
- 7.2.3.3 Pipeline State Objects (PSO) & Root Signatures
- 7.2.3.4 Resource Descriptor Heaps (CBV/SRV/UAV Descriptor Heaps)
- 7.2.3.5 Resource Barriers & State Transitions
- 7.2.3.6 Fence-Based Synchronization
- 7.2.3.7 DirectX Raytracing (DXR): State Objects (RTPSO), Shader Tables
- 7.2.3.8 DirectML (Machine Learning Inference & Training Acceleration)
- 7.2.3.9 DirectStorage (GPU Direct-to-NVMe SSD)

#### 7.2.4 Metal
- 7.2.4.1 MTLDevice, MTLCommandQueue, MTLCommandBuffer
- 7.2.4.2 Render Pipeline Descriptors (MTLRenderPipelineDescriptor)
- 7.2.4.3 Argument Buffers: GPU-Writable Descriptors
- 7.2.4.4 Heaps & Fence Synchronization
- 7.2.4.5 Metal Ray Tracing (MPSRayIntersector)
- 7.2.4.6 MetalFX (Temporal / Spatial Super-Resolution)

#### 7.2.5 WebGPU
- 7.2.5.1 Adapter & Device Model
- 7.2.5.2 Pipelines (Render Pipeline + Compute Pipeline)
- 7.2.5.3 Bind Group Layouts
- 7.2.5.4 Command Encoders (RenderPass / ComputePass)
- 7.2.5.5 WGSL Shading Language
- 7.2.5.6 Comparison with WebGL & Heterogeneous Fallback

#### 7.2.6 Cross-Platform Abstractions
- 7.2.6.1 bgfx, The-Forge, NVRHI, Diligent Engine
- 7.2.6.2 Google ANGLE (OpenGL ES → Vulkan/Metal/D3D)
- 7.2.6.3 MoltenVK (Vulkan → Metal Translation Layer)
- 7.2.6.4 DXVK / vkd3d-proton (D3D → Vulkan Translation Layer)

### 7.3 Shader Programming Languages

#### 7.3.1 High-Level Shading Languages
- 7.3.1.1 GLSL (OpenGL Shading Language)
- 7.3.1.2 HLSL (High-Level Shading Language): SM 5.0 / SM 6.x Features
- 7.3.1.3 MSL (Metal Shading Language): Based on C++14
- 7.3.1.4 WGSL (WebGPU Shading Language)
- 7.3.1.5 OpenCL Kernel Language (for General-Purpose GPU Computing)

#### 7.3.2 Shader Compilation & Intermediate Representations
- 7.3.2.1 SPIR-V (Standard Portable Intermediate Representation)
- 7.3.2.2 DXIL (DirectX Intermediate Language)
- 7.3.2.3 Metal IR (Based on LLVM Bitcode)
- 7.3.2.4 Shader Compilation Toolchains: glslang, DXC, SPIRV-Cross, Slang, Rust-GPU

#### 7.3.3 Modern Shader Features
- 7.3.3.1 Wave / Subgroup Intrinsics (Ballot, Shuffle, Vote, Reduce)
- 7.3.3.2 16-bit Type Support (min16float, half)
- 7.3.3.3 8-bit Integer Operations (DP4A / Int8 Accelerated Inference)
- 7.3.3.4 Structured Buffers & Byte Address Buffers
- 7.3.3.5 Shader Pointers & Recursion (SPV_KHR_physical_storage_buffer_addresses)
- 7.3.3.6 Bindless Resources (Descriptor Indexing)

### 7.4 GPU Computing & Parallel Programming
- 7.4.1 CUDA (Compute Unified Device Architecture):
  - 7.4.1.1 Thread Hierarchy: Grid → Block → Thread
  - 7.4.1.2 Shared Memory, Constant Memory, Global Memory, Texture Memory
  - 7.4.1.3 Cooperative Groups
  - 7.4.1.4 CUDA Graphs (Reducing Launch Overhead)
  - 7.4.1.5 Multi-Stream Concurrency (Streams / Async Copy / Overlap Compute & Transfer)
- 7.4.2 OpenCL: Platforms, Devices, Contexts, Command Queues, Kernels
- 7.4.3 Vulkan Compute / DirectX Compute Shaders
- 7.4.4 SYCL / DPC++ (Standards-Based C++ Accelerated Programming)
- 7.4.5 HIP (AMD ROCm Heterogeneous Interface)
- 7.4.6 GPU Reduction, Scan, Sort Patterns (Reduction, Prefix Sum, Radix Sort / Bitonic Sort)
- 7.4.7 GPU Parallel Algorithm Design Patterns (Map, Gather, Scatter, Partition)

### 7.5 Rendering Engine Architecture

#### 7.5.1 Common Engine Components
- 7.5.1.1 Resource Manager (Texture, Mesh, Shader, Material Lifecycle Management)
- 7.5.1.2 Scene Management (Scene Graph, Spatial Partitioning, Streaming)
- 7.5.1.3 Render Graph / Frame Graph: Automatic Resource Dependency Resolution & Barrier Generation
- 7.5.1.4 Rendering Pipeline Abstraction (Pass, View, Technique)
- 7.5.1.5 Material System: Shader Variant Management, Parameter Binding
- 7.5.1.6 Draw Call Collection / Sorting / Batching
- 7.5.1.7 Multi-Threaded Rendering Architecture (Game Thread → Render Thread → GPU)
- 7.5.1.8 World Streaming / Level Streaming

#### 7.5.2 Visibility & Culling
- 7.5.2.1 Frustum Culling
- 7.5.2.2 Occlusion Culling:
  - 7.5.2.2.1 Hardware Occlusion Queries
  - 7.5.2.2.2 Software Occlusion Culling (Potentially Visible Set, PVS)
  - 7.5.2.2.3 Hierarchical Z-Buffer (Hi-Z) Occlusion Culling
  - 7.5.2.2.4 Distance-Based Culling
  - 7.5.2.2.5 Portal Culling (Indoor Scenes)
- 7.5.2.3 Visibility Buffer: Two-Stage Visibility + Material
- 7.5.2.4 GPU-Driven Culling (Indirect Draw Count Generation)

#### 7.5.3 Debugging & Performance Analysis
- 7.5.3.1 GPU Debugging Tools: RenderDoc, NVIDIA Nsight, PIX, Xcode GPU Capture
- 7.5.3.2 GPU Performance Counters & Bottleneck Diagnosis (ALU / Bandwidth / Fill-Rate / Latency Bound)
- 7.5.3.3 Shader Performance Analysis (ALUs, Texture Stalls, Occupancy)
- 7.5.3.4 Frame Profiler / Timing Graph
- 7.5.3.5 Graphics Debugging & Pixel History (Pixel History / Mesh Viewer)
- 7.5.3.6 API Validation Layers (Vulkan Validation Layers, D3D12 Debug Layer)

#### 7.5.4 Major Engines
- 7.5.4.1 Unreal Engine 5 Rendering Architecture (Nanite, Lumen, Virtual Shadow Maps)
- 7.5.4.2 Unity Rendering Pipelines (Built-in, URP, HDRP, Custom SRP)
- 7.5.4.3 Godot Rendering Architecture (Vulkan/GLES3 Backends)
- 7.5.4.4 O3DE (Open 3D Engine) Renderer
- 7.5.4.5 Design Considerations for Custom Engines

---

## Chapter 8 · Display & Human-Computer Interaction

### 8.1 Display Technologies
- 8.1.1 LCD, OLED, Mini-LED, Micro-LED, QLED
- 8.1.2 Refresh Rate, Response Time, Input Lag
- 8.1.3 V-Sync, Adaptive Sync (G-Sync / FreeSync), VRR
- 8.1.4 Multi-Monitor Stitching & CAVE Environments
- 8.1.5 Color Calibration & Color Management (ICC Profiles / Display Calibration Workflow)

### 8.2 Virtual Reality (VR)
- 8.2.1 VR Rendering Pipeline (Stereoscopic Rendering: Binocular Disparity, IPD)
- 8.2.2 Lens Distortion Correction (Inverse Barrel Distortion)
- 8.2.3 Chromatic Aberration Correction
- 8.2.4 Asynchronous Time Warp (ATW)
- 8.2.5 Asynchronous Space Warp (ASW)
- 8.2.6 Foveated Rendering (Fixed / Dynamic, Eye Tracking)
- 8.2.7 Latency Sensitivity & Motion-to-Photon Latency Optimization
- 8.2.8 Single-Pass Stereo / Instanced Stereo
- 8.2.9 VR Input & Tracking (6DOF Controllers, Hand Tracking)

### 8.3 Augmented Reality (AR) & Mixed Reality (MR)
- 8.3.1 See-Through AR (Optical / Video See-Through) Rendering
- 8.3.2 Lighting Consistency (Environmental Light Estimation, Environment Probes / IBL)
- 8.3.3 Occlusion Consistency (Real-Time Occlusion Estimation & Segmentation)
- 8.3.4 Plane Detection & Anchoring (ARCore / ARKit / HoloLens Spatial Mapping)
- 8.3.5 Real-Time Semantic Segmentation & Depth Estimation

### 8.4 3D Displays
- 8.4.1 Stereoscopic Displays (Active Shutter / Passive Polarized 3D)
- 8.4.2 Autostereoscopic Displays (Glasses-Free 3D / Lenticular Lens, Parallax Barrier)
- 8.4.3 Light Field Displays
- 8.4.4 Volumetric Displays
- 8.4.5 Holographic Display Concepts

### 8.5 User Interaction & 3D UI
- 8.5.1 3D Picking: Ray Casting, Pixel-ID-Based Color Encoding
- 8.5.2 3D Manipulators (Gizmo / Manipulator): Translation, Rotation, Scaling
- 8.5.3 3D Camera Controls (Orbit, FPS, Trackball, Arcball)
- 8.5.4 Gesture & Motion Interaction (Leap Motion, Kinect, Vision-Based Hand Tracking)
- 8.5.5 Haptic Feedback (Haptic Rendering)
- 8.5.6 Gaze-Based Interaction

---

## Chapter 9 · 3D Vision & Computational Photography

### 9.1 Camera Models & Geometry
- 9.1.1 Pinhole Camera Model
- 9.1.2 Intrinsic Matrix (Focal Length, Principal Point, Distortion Parameters)
- 9.1.3 Extrinsic Matrix (Rotation R + Translation t)
- 9.1.4 Radial & Tangential Distortion Models (Brown-Conrady Model)
- 9.1.5 Fisheye Lens Models (Equidistant Projection, Equisolid Angle Projection, FOV Model)
- 9.1.6 Dual-Camera Models & Panoramic Stitching
- 9.1.7 Light Field / Plenoptic Function

### 9.2 Multi-View Geometry
- 9.2.1 Epipolar Geometry
- 9.2.2 Essential Matrix (E) & Fundamental Matrix (F)
- 9.2.3 Homography (H) & Planar Scenes
- 9.2.4 Triangulation
- 9.2.5 Structure from Motion (SfM):
  - 9.2.5.1 Incremental SfM (COLMAP Style)
  - 9.2.5.2 Global SfM
  - 9.2.5.3 Hierarchical SfM
- 9.2.6 Simultaneous Localization and Mapping (SLAM):
  - 9.2.6.1 Visual SLAM (ORB-SLAM3, DSO, VINS-Mono)
  - 9.2.6.2 Visual-Inertial SLAM (VIO)
  - 9.2.6.3 Dense SLAM (KinectFusion, ElasticFusion, BundleFusion)
  - 9.2.6.4 NeRF / 3DGS-Based SLAM

### 9.3 Depth Estimation
- 9.3.1 Binocular Stereo Matching:
  - 9.3.1.1 Local Matching: SAD, NCC, Census Transform
  - 9.3.1.2 Global Matching: Graph Cuts, Semi-Global Matching (SGM)
  - 9.3.1.3 Deep-Learning-Based Stereo Matching (PSMNet, RAFT-Stereo, CREStereo)
- 9.3.2 Monocular Depth Estimation:
  - 9.3.2.1 Cue-Based (Defocus, Linear Perspective, Relative Size)
  - 9.3.2.2 Deep-Learning-Based (MiDaS, DPT, ZoeDepth, Depth Anything)
- 9.3.3 Time-of-Flight (ToF): Modulated Continuous-Wave, Pulsed
- 9.3.4 Structured Light (Encoded Structured Light, Random Speckle: Kinect v1)

### 9.4 3D Reconstruction
- 9.4.1 Multi-View Stereo (MVS):
  - 9.4.1.1 Voxel Coloring & Space Carving
  - 9.4.1.2 Patch-Based (PatchMatch / PMVS / ACMM)
  - 9.4.1.3 Depth-Map-Fusion-Based (COLMAP MVS, OpenMVS)
- 9.4.2 Photometric Stereo
- 9.4.3 Shape-from-X (Shape from Shading, Defocus, Polarization, Texture)
- 9.4.4 Deep-Learning-Based MVS (MVSNet, CasMVSNet, PatchMatchNet)
- 9.4.5 Neural Implicit Reconstruction (NeuS, VolSDF, Neuralangelo, BakedSDF)

### 9.5 Computational Photography
- 9.5.1 HDR Capture & Fusion
- 9.5.2 Panorama Stitching (Image Registration, Seam Optimization, Gain Compensation)
- 9.5.3 Image / Video Stabilization
- 9.5.4 Portrait Mode (Depth Estimation + Bokeh Rendering)
- 9.5.5 Super-Resolution (Single-Image / Multi-Frame Fusion)
- 9.5.6 Low-Light Enhancement (Multi-Frame Denoising & Fusion)
- 9.5.7 Computational Illumination (Flash/Ambient Decomposition & Re-lighting)
- 9.5.8 Reflection & Obstruction Removal

---

## Chapter 10 · File Formats & Data Exchange

### 10.1 3D File Formats
- 10.1.1 OBJ: Meshes, Normals, Texture Coordinates, Material Libraries (MTL)
- 10.1.2 PLY (Stanford Polygon Format): Supports Vertex Attributes
- 10.1.3 STL: Triangle Mesh Standard (Binary/ASCII), 3D Printing
- 10.1.4 FBX (Autodesk): Scene Hierarchy, Animation, Materials, Embedded Data
- 10.1.5 glTF 2.0 (GL Transmission Format / "3D JPEG"):
  - 10.1.5.1 JSON Scene Description + Binary Buffer (.bin)
  - 10.1.5.2 PBR Material Standard (Metallic-Roughness / Specular-Glossiness Extensions)
  - 10.1.5.3 Animation, Skinning, Morph Target Support
  - 10.1.5.4 Draco Mesh Compression Extension
  - 10.1.5.5 KTX 2.0 Texture Extension (Universal Texture Compression)
  - 10.1.5.6 EXT_meshopt_compression, EXT_texture_webp & Other Extensions
- 10.1.6 USD / Universal Scene Description (Pixar):
  - 10.1.6.1 Hierarchical Scene Composition (Composition Arcs: Sublayer, Reference, Payload, VariantSet)
  - 10.1.6.2 Hydra Rendering Framework
  - 10.1.6.3 USDZ (Apple AR Format)
- 10.1.7 Alembic: Geometry Caching & Animation Exchange
- 10.1.8 Collada (.dae): XML Exchange Format
- 10.1.9 Native Formats: 3DS Max (.3ds), Blender (.blend), Maya (.ma/.mb)
- 10.1.10 CAD Formats: STEP, IGES, JT, BREP

### 10.2 Image & Texture Formats
- 10.2.1 PNG, JPEG, WebP, AVIF, JPEG-XL
- 10.2.2 HDR Formats: OpenEXR, Radiance HDR (.hdr), 32-bit TIFF
- 10.2.3 GPU Texture Formats (BCn, ASTC, ETC2, PVRTC)
- 10.2.4 KTX 2.0 (Khronos Texture Container): Basis Universal Super-Compression
- 10.2.5 DDS (DirectDraw Surface)

### 10.3 Shader & Material Exchange
- 10.3.1 MaterialX (Industry Standard Material Definition & Exchange)
- 10.3.2 MDL (NVIDIA Material Definition Language)
- 10.3.3 OpenPBR (Jointly Advanced by Adobe, Autodesk & Others)
- 10.3.4 UsdShade (USD Material Binding)
- 10.3.5 SPIR-V (Shader Exchange)

### 10.4 Animation & Motion Data Formats
- 10.4.1 BVH (Biovision Hierarchy)
- 10.4.2 FBX Animation Data
- 10.4.3 glTF Animation (Keyframes, Linear Interpolation, Cubic Spline)
- 10.4.4 Alembic Animation Cache
- 10.4.5 C3D (Motion Capture Raw Data)

---

## Chapter 11 · Application Domains

### 11.1 Games & Real-Time Interaction
- 11.1.1 AAA Game Rendering (High-End Graphics Pipeline)
- 11.1.2 Indie Game Rendering Styles (Pixel Art, 2D Lighting, Low-Poly Aesthetic)
- 11.1.3 UI Rendering (Vector Fonts, SDF Text, Resolution-Adaptive Layouts)
- 11.1.4 Mobile Graphics Optimization (Low-Power, Bandwidth-Friendly Strategies)

### 11.2 Film & Animation
- 11.2.1 Offline Renderers (RenderMan, Arnold, V-Ray, Cycles, Redshift, Octane, MoonRay)
- 11.2.2 Visual Effects (VFX) Pipeline: Compositing, Keying, Tracking, Particle Effects
- 11.2.3 Virtual Production: LED Wall + Real-Time Engine Rendering (StageCraft)
- 11.2.4 Performance Capture: Body + Face Synchronized Capture
- 11.2.5 Digital Humans (MetaHuman)

### 11.3 Scientific Visualization
- 11.3.1 Volume Rendering (Direct / Indirect Volume Rendering, Transfer Function Design)
- 11.3.2 Flow Visualization (Streamlines, Streaklines, Line Integral Convolution LIC)
- 11.3.3 Tensor Field Visualization (Hyperstreamlines, Diffusion Tensor Imaging DTI Visualization)
- 11.3.4 Information Visualization (Graphs, Hierarchies, Parallel Coordinates)
- 11.3.5 Geographic Information Visualization (GIS, Terrain Rendering, Large-Scale Point Clouds)
- 11.3.6 Medical Visualization (CT/MRI Reconstruction, Surgical Simulation, Anatomy Education)

### 11.4 Industrial & Engineering Design
- 11.4.1 CAD (Computer-Aided Design): Solid Modeling, Surface Modeling, Parametric Design
- 11.4.2 CAE (Computer-Aided Engineering): FEM Pre-/Post-Processing Visualization
- 11.4.3 CAM (Computer-Aided Manufacturing): Toolpath Visualization
- 11.4.4 BIM (Building Information Modeling)
- 11.4.5 3D Printing Slicing & Support Structure Generation
- 11.4.6 Digital Twin Visualization

### 11.5 Autonomous Driving & Robotics Simulation
- 11.5.1 Sensor Simulation (RGB Cameras, LiDAR, Radar, Depth Cameras)
- 11.5.2 Synthetic Data Generation (Domain Randomization, Autoencoder-Based Realism)
- 11.5.3 Environment Simulation (Weather, Lighting Variation, Dynamic Obstacles)
- 11.5.4 Simulation Platforms (CARLA, AirSim, NVIDIA DRIVE Sim / Omniverse, Isaac Sim)

### 11.6 Virtual Humans / Digital Humans
- 11.6.1 High-Fidelity Facial Reconstruction & Animation (Light Stage, Multi-View 3DMM Fitting)
- 11.6.2 Skin Rendering (Subsurface Scattering, Pore-Level Detail, Micro-Geometry)
- 11.6.3 Eye Rendering (Corneal Reflection, Pupil Refraction, Iris Detail)
- 11.6.4 Hair Rendering (Curve-Based Hair, Marschner Scattering Model)
- 11.6.5 Clothing Simulation & Rendering
- 11.6.6 Real-Time Digital Humans (MetaHuman, NVIDIA ACE / Audio2Face)

---

## Chapter 12 · Frontiers & Interdisciplinary Directions

### 12.1 Neural Rendering & Generation
- 12.1.1 Neural Scene Representations (NeRF, 3DGS, NGP, Triplane)
- 12.1.2 GANs in Computer Graphics
- 12.1.3 Diffusion Models for 3D Generation & Texture Synthesis
- 12.1.4 Autoregressive 3D Generation
- 12.1.5 Multimodal 3D Generation (Text / Image / Video → 3D)

### 12.2 Differentiable Graphics
- 12.2.1 Differentiable Rendering in Inverse Problems
- 12.2.2 Differentiable Physics Simulation
- 12.2.3 End-to-End Differentiable Pipelines
- 12.2.4 Gradient-Driven Content Creation Tools

### 12.3 Cloud Rendering & Streaming
- 12.3.1 Cloud Gaming Architecture (GeForce Now, Xbox Cloud Gaming, Luna)
- 12.3.2 Pixel Streaming: Encoding, Latency Optimization, Bandwidth Adaptation
- 12.3.3 Virtual Workstations (NVIDIA vGPU, AWS Thinkbox Deadline Distributed Rendering)
- 12.3.4 WebRTC & Low-Latency Video Streaming
- 12.3.5 The Role of Edge Computing in Graphics

### 12.4 Quantum Graphics
- 12.4.1 Quantum Computing Potential in Ray Tracing
- 12.4.2 Quantum Monte Carlo Sampling

### 12.5 Bio-Inspired Graphics
- 12.5.1 Bio-Inspired Vision (Rendering Based on Human Eye Models)
- 12.5.2 Neuroscience-Based Graphics Evaluation Metrics
- 12.5.3 Brain-Inspired Computational Photography

### 12.6 Graphics & AI Convergence
- 12.6.1 AI-Assisted Content Creation (AI-Assisted Art / Copilot for 3D)
- 12.6.2 AI-Driven Real-Time Rendering Optimization (Adaptive Sampling, Predictive LOD)
- 12.6.3 Neural Super-Sampling & Intelligent Image Enhancement
- 12.6.4 Synthetic Training Data Generation from Graphics
- 12.6.5 World Models & Generative World Simulation (Sora / Genie Direction)

### 12.7 Metaverse & Spatial Computing
- 12.7.1 Cross-Platform Spatial Anchors & Persistent Worlds
- 12.7.2 Real-Time Global 3D Reconstruction & Sharing
- 12.7.3 Spatial Audio Rendering (Spatial Audio / HRTF / Ambisonics)
- 12.7.4 3D Asset Interoperability Standards (OpenUSD / glTF Ecosystem)
- 12.7.5 Light Field / Holographic Communication (3D Video Calls / Telepresence)

---

## Appendix A · Major Conferences & Journals
- A.1 ACM SIGGRAPH / SIGGRAPH Asia
- A.2 Eurographics (EG)
- A.3 Symposium on Interactive 3D Graphics and Games (I3D)
- A.4 High Performance Graphics (HPG)
- A.5 Eurographics Symposium on Rendering (EGSR)
- A.6 ACM SIGGRAPH Symposium on Computer Animation (SCA)
- A.7 Symposium on Geometry Processing (SGP)
- A.8 IEEE Visualization (VIS)
- A.9 ACM Transactions on Graphics (TOG)
- A.10 Computer Graphics Forum (CGF)
- A.11 IEEE Transactions on Visualization and Computer Graphics (TVCG)
- A.12 Journal of Computer Graphics Techniques (JCGT)

## Appendix B · Landmark Papers & Works
- B.1 Phong (1975) — Empirical Illumination Model
- B.2 Blinn (1977) — Blinn-Phong Reflection & Bump Mapping
- B.3 Whitted (1980) — Recursive Ray Tracing
- B.4 Cook & Torrance (1981) — Microfacet BRDF
- B.5 Kajiya (1986) — The Rendering Equation
- B.6 Loren Carpenter (1980s) — Reyes Rendering Architecture (RenderMan)
- B.7 Debevec & Malik (1997) — HDR Image Capture & Image-Based Modeling
- B.8 Veach & Guibas (1997) — Metropolis Light Transport
- B.9 Kajiya & Kay (1989) — Hair Rendering
- B.10 Perlin (1985) — Noise Functions
- B.11 Catmull & Clark (1978) — Subdivision Surfaces
- B.12 Garland & Heckbert (1997) — QEM Mesh Simplification
- B.13 Möller & Trumbore (1997) — Fast Ray-Triangle Intersection
- B.14 Loop (1987) — Triangle Subdivision Surfaces
- B.15 Kajiya & Von Herzen (1984) — Ray Marching in Volume Rendering
- B.16 Veach (1997 PhD) — Path Integral Framework & MIS
- B.17 Jensen (1996) — Photon Mapping
- B.18 Müller et al. — MPM in Graphics
- B.19 Mildenhall et al. (2020) — NeRF
- B.20 Kerbl et al. (2023) — 3D Gaussian Splatting

## Appendix C · Important International Standards
- C.1 Khronos: OpenGL, Vulkan, OpenCL, SPIR, glTF, WebGL, WebGPU, OpenXR
- C.2 ISO/IEC JTC 1/SC 24: CGM, VRML/X3D, SEDRIS
- C.3 MPEG: 3D Mesh Coding, Video-based Point Cloud Compression (V-PCC)
- C.4 SMPTE: Color-Related Standards (ST 2084/PQ, ST 2086, ST 2094 Dynamic Metadata)
- C.5 ITU-R: Color Space Standards (BT.709, BT.2020, BT.2100)
- C.6 IEEE: Floating-Point Standard (754), Display Standards
- C.7 CIE: Colorimetry Standards (CIE 1931, CIE 1976, CIECAM02/16)
- C.8 OpenUSD Alliance: USD Ecosystem Standards

---

*This document aims to provide a comprehensive overview of the computer graphics knowledge landscape, spanning from foundational mathematics to cutting-edge research. Each entry represents an independent topic or technical direction, serving as a reference index for curriculum design, self-study roadmaps, or technical research.*

---

**Author: Xx1899**
