# A Comprehensive Knowledge Map of Computer Graphics

**Author: Xx1899**

> 🇨🇳 [中文版本 (Chinese Version)](./计算机图形学知识体系目录.md)

---


## Chapter 1 · Mathematical & Physical Foundations

> 💡 **Comprehensive References:**
> - [ericjang/awesome-graphics](https://github.com/ericjang/awesome-graphics) ![Stars](https://img.shields.io/github/stars/ericjang/awesome-graphics?style=flat) — Curated list of CG tutorials, books, math & programming resources
> - [ssloy/tinyrenderer](https://github.com/ssloy/tinyrenderer) ![Stars](https://img.shields.io/github/stars/ssloy/tinyrenderer?style=flat) — Learn CG math by building a software rasterizer from scratch (~500 lines C++)
> - [mml-book/mml-book.github.io](https://github.com/mml-book/mml-book.github.io) ![Stars](https://img.shields.io/github/stars/mml-book/mml-book.github.io?style=flat) — *Mathematics for Machine Learning* — comprehensive modern math foundation
> - [PBR Book v4](https://pbr-book.org/) — Definitive reference connecting math to rendering theory
> - [3b1b/manim](https://github.com/3b1b/manim) ![Stars](https://img.shields.io/github/stars/3b1b/manim?style=flat) — 3Blue1Brown's math animation engine for visual intuition

> 🎯 **How to Use:** Each concept is linked to its direct CG application via `▸ CG use:` annotations.

---

### 1.1 Linear Algebra & Tensor Methods

#### 1.1.1 Vector Spaces & Fundamental Operations
- 1.1.1.1 Vector Spaces, Span, Linear Independence, Basis, Dimension, Change of Basis
  - ▸ *CG use:* Coordinate frame transforms; barycentric coordinates for triangle interpolation
- 1.1.1.2 Inner Products, Norms (ℓ₁, ℓ₂, ℓₚ, Frobenius, Nuclear), Metric Spaces
  - ▸ *CG use:* ℓ₂ for least-squares (geometry registration, IK); Nuclear norm for low-rank light field/BRDF completion
- 1.1.1.3 Outer Product, Tensor Product ⊗, Kronecker Product, Khatri-Rao Product
  - ▸ *CG use:* Rank-1 BRDF factorization (outer product); structured light transport (Kronecker)
- 1.1.1.4 Linear Maps, Range, Nullspace, Fundamental Theorem of Linear Algebra
  - ▸ *CG use:* Nullspace of constraint Jacobians in PBD/XPBD; range of light transport matrix for inverse rendering

#### 1.1.2 Matrix Decompositions
- 1.1.2.1 LU, Cholesky (SPD), LDLᵀ — Direct Linear Solvers
  - ▸ *CG use:* Cholesky for real-time FEM (projective dynamics); mass matrix inversion
- 1.1.2.2 QR Decomposition (Gram-Schmidt, Householder, Givens)
  - ▸ *CG use:* Camera extrinsic calibration; orthonormal tangent space frames
- 1.1.2.3 Eigenvalue Decomposition: Spectral Theorem, Rayleigh Quotient, Gershgorin Circles
  - ▸ *CG use:* Spectral clustering for mesh segmentation; principal curvature directions; vibration modes (sound rendering)
- 1.1.2.4 Singular Value Decomposition (SVD): Full, Thin, Truncated; Eckart-Young-Mirsky Optimal Low-Rank
  - ▸ *CG use:* PCA for 3DMM face models; R=UVᵀ polar decomposition for stable ARAP; camera matrix factorization
- 1.1.2.5 Polar Decomposition A=UP; Schur Decomposition; Generalized Eigenvalue (Av=λBv)
  - ▸ *CG use:* ARAP rotation extraction; modal FEM analysis; constrained dynamics (λMx=Kx)

#### 1.1.3 Special Matrices & Sparsity
- 1.1.3.1 Symmetric, Skew-Symmetric [ω]×, Orthogonal, Projection Matrices
  - ▸ *CG use:* Angular velocity via skew-symmetric; perspective/orthographic projection matrices
- 1.1.3.2 Sparse, Banded, Block-Diagonal/Tridiagonal; CSR/CSC/BCSR Storage Formats
  - ▸ *CG use:* FEM stiffness/mass matrices; GPU SpMV for projective dynamics; mesh Laplacian
- 1.1.3.3 Toeplitz, Circulant, Hankel — FFT-Based Fast Matrix-Vector Product
  - ▸ *CG use:* Fast convolution filtering (circulant); constant-velocity motion blur (Toeplitz)
- 1.1.3.4 Condition Number κ(A), Ill-Posedness, Tikhonov (Ridge) ‖Ax−b‖²+λ‖Γx‖²; Truncated SVD Regularization
  - ▸ *CG use:* Stable inverse rendering; robust normal estimation from noisy point clouds
- 1.1.3.5 Moore-Penrose Pseudoinverse A⁺; Least-Squares minₓ‖Ax−b‖₂ & Minimum-Norm Solutions
  - ▸ *CG use:* Blend shape weight computation; camera resectioning (DLT algorithm)

#### 1.1.4 Geometry of Transformations
- 1.1.4.1 2D/3D Rigid Transformations: SO(n), Matrix Exponential/Logarithm, Scaling, Shear, Reflection
  - ▸ *CG use:* Scene graph transforms; camera animation on SE(3)
- 1.1.4.2 Homogeneous Coordinates (ℙⁿ): Unified Affine & Projective via 4×4 Matrices
  - ▸ *CG use:* Entire GPU vertex pipeline; hardware perspective division
- 1.1.4.3 Graphics Viewing Pipeline: Model→World→View→Clip→NDC→Screen
  - ▸ *CG use:* Every frame; reverse-Z for infinite far plane
- 1.1.4.4 Camera Models: Pinhole K[R|t]; Orthographic; Weak-Perspective
  - ▸ *CG use:* SfM; multi-view stereo projection matrix decomposition

#### 1.1.5 Quaternions & Rotations
- 1.1.5.1 Quaternion Algebra (S³ Group): Hamilton Product, Norm, Conjugate, Inverse; Unit q = Rotation
  - ▸ *CG use:* Compact (4 floats vs 9), no gimbal lock, GPU-friendly interpolation
- 1.1.5.2 Rotation p'=qpq⁻¹; Axis-Angle Conversion; Double Cover q≡−q of SO(3)
  - ▸ *CG use:* Skeletal joint rotations; arcball camera
- 1.1.5.3 SLERP (Constant ω), SQUAD (Cubic on S³), NLERP; Quaternion Averaging (Karcher Mean on SO(3))
  - ▸ *CG use:* Keyframe rotation blending; multi-view rotation averaging in global SfM
- 1.1.5.4 Dual Quaternions: 8D Entity Encodes Rigid Transform (R+t); Screw Motion Theory
  - ▸ *CG use:* DQS skinning eliminates candy-wrapper; unified rigid body state

#### 1.1.6 Lie Groups & Lie Algebras
- 1.1.6.1 Lie Group: Smooth Manifold + Group; Lie Algebra 𝔤=T_eG; SO(3), SE(3), Sim(3)
  - ▸ *CG use:* Consistent rotation/pose in optimization; bundle adjustment on SE(3)
- 1.1.6.2 exp: 𝔤→G, log: G→𝔤; BCH Formula (Non-commutative Addition)
  - ▸ *CG use:* Small pose updates in Gauss-Newton; camera trajectory interpolation
- 1.1.6.3 so(3): 3×3 Skew-Symmetric↭3-Vector via ∧/∨; Basis Generators; se(3): 6D Twist (v,ω); Adjoint Ad_{[R|t]}
  - ▸ *CG use:* Rigid body angular velocity integration; robot kinematics; character animation
- 1.1.6.4 Derivatives on SO(3)/SE(3): Jacobians w.r.t. Lie Algebra (Tangent Space) Parameters
  - ▸ *CG use:* Gauss-Newton pose optimization; differentiable articulated rendering

#### 1.1.7 Tensor Methods for Compact Representation
- 1.1.7.1 Tensor Decompositions: CP (CANDECOMP/PARAFAC), Tucker (HOSVD), Tensor Train (TT), Tensor Ring
  - ▸ *CG use:* TensoRF (CP+VM→100× radiance field compression); TT for neural BRDF compression
- 1.1.7.2 Tensor Contraction (Einstein Summation), Mode-n Product, Matricization/Unfolding
  - ▸ *CG use:* GPU tensor cores accelerate contractions (cuBLAS, Triton); neural renderer forward ops
- 1.1.7.3 Low-Rank Tensor Completion: Nuclear Norm Minimization; Riemannian Optimization on Tensor Manifolds
  - ▸ *CG use:* Compressive light transport (4D/6D light fields from sparse measurements)
- 1.1.7.4 VM (Vector-Matrix) Decomposition for Factorized Feature Grids
  - ▸ *CG use:* TensoRF (Chen et al. ECCV 2022); Instant NGP-style factorization; factorized neural SDF

#### 1.1.8 Randomized & Approximate Linear Algebra
- 1.1.8.1 Randomized SVD: Random Projection+QR+Power Iteration — O(mn log k)
  - ▸ *CG use:* Fast PCA on million-vertex meshes; rapid SVBRDF material decomposition
- 1.1.8.2 Random Sketching: JL Lemma, CountSketch, SRHT; Nyström Approximation (Landmark-Based Low-Rank)
  - ▸ *CG use:* Light transport matrix sketching; scalable GP for radiance field interpolation
- 1.1.8.3 Randomized Kaczmarz & Stochastic Iterative Methods for Overdetermined LS
  - ▸ *CG use:* Fast CT/mesh reconstruction; real-time projector-camera calibration

#### 1.1.9 Group Theory & Equivariance (Geometric DL Foundations)
- 1.1.9.1 Group Theory: Groups, Subgroups, Cosets, Group Actions, Orbits, Stabilizers
  - ▸ *CG use:* SE(3)-equivariant point cloud networks; symmetry-aware texture synthesis
- 1.1.9.2 Group Representations: Linear Representations, Irreducible Representations (Irreps), Characters, Schur's Lemma
  - ▸ *CG use:* Spherical CNNs (SO(3) irreps); Tensor Field Networks for molecular/point cloud data
- 1.1.9.3 Wigner D-Matrices: Rotation of SH; Clebsch-Gordan Tensor Product for Combining Irreps
  - ▸ *CG use:* SE(3)-transformers; equivariant 3D reconstruction; rotation-invariant shape descriptors
- 1.1.9.4 Steerable Filters & Gauge-Equivariant CNNs on Meshes (GEM-CNN)
  - ▸ *CG use:* MeshCNN on curved surfaces; gauge-equivariant 3D shape learning

> 📚 **GitHub Repos:**
> - [MIT 18.06 & 18.065 (Gilbert Strang)](https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/) — Classic LA + Matrix Methods for Data, Signal & ML
> - [fastai/numerical-linear-algebra](https://github.com/fastai/numerical-linear-algebra) ![Stars](https://img.shields.io/github/stars/fastai/numerical-linear-algebra?style=flat) — Randomized SVD, Krylov solvers, PCA in Jupyter+PyTorch
> - [kenjihiranabe/The-Art-of-Linear-Algebra](https://github.com/kenjihiranabe/The-Art-of-Linear-Algebra) ![Stars](https://img.shields.io/github/stars/kenjihiranabe/The-Art-of-Linear-Algebra?style=flat) — Visual graphic notes of all key matrix-vector operations
> - [QBobWatson/gt-linalg](https://github.com/QBobWatson/gt-linalg) ![Stars](https://img.shields.io/github/stars/QBobWatson/gt-linalg?style=flat) — Interactive linear algebra textbook with Jupyter notebooks
> - [TensoRF Project Page](https://apchenstu.github.io/TensoRF/) — Tensor decomposition for radiance fields
>
> 📖 **Textbooks:**
> - *Linear Algebra and Its Applications* — Gilbert Strang (Intuition-first classic)
> - *Matrix Computations* — Golub & Van Loan (The definitive numerical LA reference)
> - *Numerical Linear Algebra* — Trefethen & Bau (Concise, elegant, computation-driven)
> - *3D Math Primer for Graphics and Game Development* — Dunn & Parberry (Practical CG-focused)
> - *Mathematics for 3D Game Programming and Computer Graphics* — Eric Lengyel (Rigorous CG math)

---

### 1.2 Calculus, Automatic Differentiation & Analysis

#### 1.2.1 Foundations of Real Analysis
- 1.2.1.1 Limits, Continuity, Lipschitz (‖f(x)−f(y)‖≤L‖x−y‖); ϵ-δ Formalism
  - ▸ *CG use:* Lipschitz SDF guarantees sphere-tracing convergence; neural field smoothness bounds
- 1.2.1.2 Differentiability: Fréchet (Total) Derivative, Gâteaux (Directional) Derivative
  - ▸ *CG use:* Variational image processing; rendering equation operator analysis
- 1.2.1.3 Gradient ∇f, Divergence ∇·F, Curl ∇×F, Laplacian Δf — Geometric & Physical Meanings
  - ▸ *CG use:* Curl noise for incompressible flow; Laplacian mesh smoothing; Poisson image editing
- 1.2.1.4 Jacobian J_f, Hessian H=∇²f; Vector-Jacobian (VJP) & Jacobian-Vector Products (JVP)
  - ▸ *CG use:* VJPs/JVPs are THE fundamental ops of autodiff (PyTorch backward() = VJP accumulation)
- 1.2.1.5 Taylor's Theorem: f(x+h)=f(x)+∇f·h+½hᵀHh+O(‖h‖³); Lagrange & Integral Remainders
  - ▸ *CG use:* Trust-region IK; Newton convergence analysis; FEM integration error bounds
- 1.2.1.6 Implicit Function Theorem: F(x,y)=0⇒y=g(x) with g'(x)=−[∂F/∂y]⁻¹∂F/∂x
  - ▸ *CG use:* Implicit layer differentiation (DEQ); constraint forces in physics simulation
- 1.2.1.7 Integration: Riemann, Lebesgue; Fubini; Change of Variables (Jacobian Determinant)
  - ▸ *CG use:* Path integral formulation of light transport; BRDF IS transform method (uniform→target PDF)

#### 1.2.2 Automatic Differentiation — Engine of Modern Graphics
- 1.2.2.1 Computational Graph: Primal Ops, Adjoint Ops; Topological Reverse-Order Traversal
  - ▸ *CG use:* All modern differentiable renderers built on AD
- 1.2.2.2 Forward-Mode AD: Dual Numbers (a+bε, ε²=0); JVP; Cost∝#Inputs
  - ▸ *CG use:* Gauss-Newton Jacobians (small input→forward mode); directional derivatives for specular paths
- 1.2.2.3 Reverse-Mode AD: Adjoint Sensitivity; VJP Chain; Wengert Tape; Cost∝#Outputs
  - ▸ *CG use:* Gradient of scalar loss w.r.t. millions of scene params in NeRF/3DGS training
- 1.2.2.4 Checkpointing: Compute-Memory Trade-off; Binomial Optimal Schedule
  - ▸ *CG use:* Training 3DGS with millions of Gaussians under GPU memory limits
- 1.2.2.5 Higher-Order: HVP via Forward-over-Reverse
  - ▸ *CG use:* 2nd-order optimization for camera+geometry; Laplace approximation for rendering uncertainty
- 1.2.2.6 Discontinuity Handling: Dirac Gradients at Visibility Boundaries; Edge Sampling; Reparameterization (Path→Primary Sample Space); Warp-Area
  - ▸ *CG use:* THE core challenge of diff-rendering; Li et al. 2018, Loubet et al. 2019
- 1.2.2.7 REINFORCE (Score-Function) Estimator ∇_θ𝔼_{x~p_θ}[f(x)]=𝔼[f(x)∇_θ log p_θ]; Unbiased, High Variance
  - ▸ *CG use:* Black-box differentiable rasterization; NeRF coarse sampling gradient
- 1.2.2.8 Reparameterization Trick: ∇_θ𝔼_{x~p_θ}[f(x)]=∇_θ𝔼_{z~q}[f(T(z,θ))]; Lower Variance When T Exists
  - ▸ *CG use:* VAE texture latents; 3DGS (sampling≈reparameterization of 2D Gaussians)
- 1.2.2.9 Adjoint State Method for ODE/PDE-Constrained Optimization; Continuous vs. Discrete Adjoint
  - ▸ *CG use:* Differentiable fluid simulation (∇-Sim, PhiFlow); gradient-based design optimization

#### 1.2.3 Integral Transforms & Spherical Harmonics
- 1.2.3.1 Fourier Series (Real & Complex), Parseval; Gibbs Phenomenon, Dirichlet Kernel
  - ▸ *CG use:* FFT ocean surface; periodic texture synthesis; antialiasing theory
- 1.2.3.2 Fourier Transform (1D,2D,nD): Shift, Convolution (ℱ{f∗g}=ℱ{f}·ℱ{g}), Scaling, Derivative Theorems
  - ▸ *CG use:* Fast convolution filtering; frequency-domain BRDF analysis
- 1.2.3.3 DFT & FFT (Cooley-Tukey Radix-2): O(N log N); GPU via cuFFT/rocFFT
  - ▸ *CG use:* Ocean wave simulation; frequency-space fluids; fast convolution via FFT
- 1.2.3.4 Laplace Transform, Z-Transform: LTI ODE/Difference Equation Solving
  - ▸ *CG use:* Viscoelastic material relaxation; character animation control theory
- 1.2.3.5 Spherical Harmonics Yₗᵐ: Complete Orthonormal Basis on S²; Legendre Pₗᵐ; Real SH Basis
  - ▸ *CG use:* IBL irradiance (SH projection); PRT; ambient occlusion SH (Ramamoorthi 2001)
- 1.2.3.6 SH Rotation (Wigner D), SH Product (Clebsch-Gordan), Triple Product (Gaunt)
  - ▸ *CG use:* Rotating environment maps without re-projection; fast SH-based glossy BRDF
- 1.2.3.7 Zonal Harmonics, Anisotropic Spherical Gaussians (ASG), Bingham
  - ▸ *CG use:* Compact specular models; real-time anisotropic environment lighting
- 1.2.3.8 Wavelet Transform (CWT,DWT): Haar, Daubechies, Mallat Algorithm, Subband Coding
  - ▸ *CG use:* JPEG 2000; geometry images; à-trous wavelet MC denoising

#### 1.2.4 Variational Calculus, PDEs & SDEs
- 1.2.4.1 Euler-Lagrange ∂L/∂f−d/dx(∂L/∂f')=0; Natural BCs; First & Second Variation
  - ▸ *CG use:* Geodesic computation; minimal surface generation; Mumford-Shah segmentation
- 1.2.4.2 Weak Formulations, Sobolev Hᵏ, Lax-Milgram; Galerkin
  - ▸ *CG use:* FEM for elastic solids; Poisson surface reconstruction
- 1.2.4.3 Elliptic (Laplace, Poisson), Parabolic (Heat), Hyperbolic (Wave, Transport) PDEs
  - ▸ *CG use:* Harmonic deformation; heat method geodesics; fluid advection; sound propagation
- 1.2.4.4 Heat Kernel K_t=Σe^{−λₖt}φₖ(x)φₖ(y); Connection to Laplace-Beltrami
  - ▸ *CG use:* HKS for shape matching; geodesic distance via short-time heat (Crane et al. 2013)
- 1.2.4.5 Stochastic Differential Equations: Itô Process dX=μdt+σdW; Fokker-Planck; Generator
  - ▸ *CG use:* Score-based 3D generation (reverse SDE=denoising); Langevin MCMC for PT; stochastic texture
- 1.2.4.6 Neural Tangent Kernel (NTK): Infinite-Width Limit; Gradient Descent in Function Space
  - ▸ *CG use:* Understanding NeRF/SIREN training dynamics; implicit regularization in coordinate MLPs

> 📚 **GitHub Repos:**
> - [google/jax](https://github.com/google/jax) ![Stars](https://img.shields.io/github/stars/google/jax?style=flat) — Composable autodiff+JIT; backbone of modern diff-rendering
> - [EnzymeAD/Enzyme](https://github.com/EnzymeAD/Enzyme) ![Stars](https://img.shields.io/github/stars/EnzymeAD/Enzyme?style=flat) — LLVM-level AD through GPU kernels and simulation codes
> - [greenw07/spherical-harmonics](https://github.com/greenw07/spherical-harmonics) — Practical SH: rotation, projection, product
> - [lab-cosmo/sphericart](https://github.com/lab-cosmo/sphericart) ![Stars](https://img.shields.io/github/stars/lab-cosmo/sphericart?style=flat) — High-performance spherical harmonics in C++/Python/CUDA
> - [3Blue1Brown (YouTube)](https://www.youtube.com/@3blue1brown) — Visual intuition for calculus, Fourier, DEs
>
> 📖 **Textbooks:**
> - *Calculus* — James Stewart (Standard comprehensive calculus reference)
> - *Advanced Calculus: A Geometric View* — James Callahan (Geometric intuition for multivariable)
> - *Inside Interesting Integrals* — Paul Nahin (Contour integration, special functions)
> - *A Student's Guide to Fourier Transforms* — J.F. James (Accessible FT introduction)

---

### 1.3 Differential Geometry & Manifold Theory

#### 1.3.1 Classical Curve & Surface Theory
- 1.3.1.1 Curves: Arc-Length s=∫‖γ'‖du; Frenet-Serret {T,N,B}; Curvature κ, Torsion τ
  - ▸ *CG use:* Uniform path sampling; camera path smoothing; sweep surface generation
- 1.3.1.2 Surfaces: Parameterized x(u,v); Tangent Basis {x_u,x_v}; Normal n
  - ▸ *CG use:* Tangent space for texture/normal mapping; displacement along normals
- 1.3.1.3 First Fundamental Form I=E du²+2F du dv+G dv² (Metric g); Intrinsic Geometry
  - ▸ *CG use:* Length/area/angle on surfaces; texture distortion metrics; bending-invariant geometry
- 1.3.1.4 Second Fundamental Form II; Shape Operator S=I⁻¹II (Weingarten Map)
  - ▸ *CG use:* Surface curvature for segmentation/features; NPR suggestive contours
- 1.3.1.5 Principal κ₁,κ₂ (Eigenvalues of S); Gaussian K=κ₁κ₂; Mean H=(κ₁+κ₂)/2
  - ▸ *CG use:* Mean curvature flow smoothing; Gaussian curvature type classification (elliptic/hyperbolic/parabolic)
- 1.3.1.6 Gauss Theorema Egregium (K Intrinsic); Gauss-Bonnet ∫KdA+∫κ_g ds=2πχ(M)
  - ▸ *CG use:* Developable surface flattening (K=0); topology verification
- 1.3.1.7 Geodesics ∇_γ'γ'=0; Exponential Map; Minimal Surfaces H≡0
  - ▸ *CG use:* Heat method geodesics; stretch-minimizing parameterization; surface fairing

#### 1.3.2 Riemannian Geometry & Manifolds
- 1.3.2.1 Smooth Manifolds, Charts/Atlases, Tangent Bundle TM; Induced Metric
  - ▸ *CG use:* SO(3)/SE(3) manifold optimization; shape spaces for statistical analysis
- 1.3.2.2 Riemannian Metric g_p; Covariant Derivative ∇_XY; Levi-Civita Connection; Christoffels Γᵏ_{ij}
  - ▸ *CG use:* Anisotropic meshing (prescribed metric); parallel transport for direction fields
- 1.3.2.3 Riemann Curvature R(X,Y)Z; Sectional, Ricci, Scalar; Parallel Transport & Holonomy
  - ▸ *CG use:* Ricci flow mesh processing; N-RoSy direction field design

#### 1.3.3 Hodge Theory & Exterior Calculus
- 1.3.3.1 k-Forms, Wedge ∧, Exterior d (d²=0), de Rham Complex
  - ▸ *CG use:* Helmholtz-Hodge decomposition for fluid simulation (any field = curl-free + div-free + harmonic)
- 1.3.3.2 Hodge Star ⋆, Codifferential δ=⋆d⋆, Hodge Laplacian Δ=dδ+δd; Harmonic Forms
  - ▸ *CG use:* DEC for structure-preserving fluid; Hodge decomposition on meshes
- 1.3.3.3 Discrete Exterior Calculus (DEC): Discrete k-Forms; Discrete d & ⋆
  - ▸ *CG use:* Robust geometric PDE solving on meshes; exact divergence-free fluid constraint
- 1.3.3.4 Laplace-Beltrami Δ=−div_M∘∇_M; Δφ_k=λ_kφ_k (Manifold Fourier Basis)
  - ▸ *CG use:* ShapeDNA; spectral mesh compression; functional maps for shape correspondence

#### 1.3.4 Discrete Differential Geometry (DDG) on Meshes
- 1.3.4.1 Discrete Gaussian Curvature: K(v_i)=2π−Σⱼθᵢⱼ (Angle Deficit); Discrete Gauss-Bonnet
  - ▸ *CG use:* Mesh quality metrics; feature detection; curvature-driven remeshing
- 1.3.4.2 Discrete Mean Curvature (Cotangent): Hn_i=(1/2A_i)Σⱼ(cotα+cotβ)(v_j−v_i)
  - ▸ *CG use:* Mean curvature flow smoothing; Laplacian mesh editing; discrete shell bending
- 1.3.4.3 Cotangent Laplacian L_{ij}=½(cotα+cotβ); Mass M; Lφ=λMφ (Generalized Eigenproblem)
  - ▸ *CG use:* Heat method geodesics; spectral mesh filtering; functional maps
- 1.3.4.4 Discrete Conformal Maps: Circle Patterns, CETM, LSCM (Lévy 2002)
  - ▸ *CG use:* High-quality UV unwrapping; surface flattening
- 1.3.4.5 Discrete Shells (Grinspun 2003): Bending via Dihedral Change; N-RoSy Direction Fields; Spin Transforms
  - ▸ *CG use:* Cloth with bending; quad remeshing; seamless global parameterization; NPR orientation

#### 1.3.5 Optimal Transport Geometry
- 1.3.5.1 Monge→Kantorovich Relaxation; Wasserstein-p W_p; Earth Mover's (W₁); Metric on ℙ
  - ▸ *CG use:* BRDF IS via OT map; shape interpolation; point set registration
- 1.3.5.2 Entropic OT: Sinkhorn O(n² log n) GPU; Fully Differentiable
  - ▸ *CG use:* Differentiable point cloud registration; neural rendering OT-regularized losses
- 1.3.5.3 Semidiscrete OT: Power/Laguerre Diagrams; Newton on Weights; Sliced Wasserstein
  - ▸ *CG use:* Blue noise (de Goes 2012); geometry compression quantization; NPR stippling

> 📚 **GitHub Repos:**
> - [geometry-central/geometry-central](https://github.com/nmwsharp/geometry-central) ![Stars](https://img.shields.io/github/stars/nmwsharp/geometry-central?style=flat) — DEC, geodesics, vector fields, parameterization in C++
> - [libigl/libigl](https://github.com/libigl/libigl) ![Stars](https://img.shields.io/github/stars/libigl/libigl?style=flat) — Cotan Laplacian, curvature, geodesics, parameterization
> - [CMU DDG (Keenan Crane)](https://www.cs.cmu.edu/~kmcrane/Projects/DDG/) — Free notes, slides, videos — the gold standard
> - [Peyré/Cuturi — Computational OT](https://github.com/Peyre/bookOT) — Standard OT reference with Python notebooks
> - [Directional Field Design (SIGGRAPH Course)](https://github.com/avaxman/DirectionalFieldDesign) — N-RoSy fields, parameterization, quad meshing
>
> 📖 **Textbooks:**
> - *Differential Geometry of Curves and Surfaces* — Manfredo do Carmo (The classic DG text)
> - *Discrete Differential Geometry: An Applied Introduction* — Keenan Crane et al. (Free online)
> - *A Sampler of Useful Computational Tools for Applied Geometry* — CGAL project (Practical geometry tools)

---

### 1.4 Computational Geometry & Spatial Acceleration

#### 1.4.1 Convexity & Triangulations
- 1.4.1.1 Convex Hull 2D: Graham O(n log n), Jarvis O(nh), Chan O(n log h); 3D: QuickHull
  - ▸ *CG use:* GJK collision detection; V-HACD convex decomposition; alpha shapes
- 1.4.1.2 Delaunay Triangulation: Empty Circumcircle (Max-Min Angle)↭Voronoi Duality; Bowyer-Watson O(n log n)
  - ▸ *CG use:* High-quality mesh generation; terrain triangulation; natural neighbor interpolation
- 1.4.1.3 CDT, Ruppert Quality Meshing; Voronoi, Power Diagram, CVT (Lloyd Relaxation), CCVT
  - ▸ *CG use:* CAD meshing; blue noise; fracture fragments; 3D printing toolpath; optimal stippling

#### 1.4.2 Spatial Data Structures
- 1.4.2.1 BVH: SAH C=C_T+(SA(L)/SA(R))·C; Binned SAH O(n log n), HLBVH, PLOC
  - ▸ *CG use:* THE dominant RT structure (DXR/Vulkan/OptiX); collision broad phase
- 1.4.2.2 BVH Traversal: Stack/Stackless, Wide BVH (4/8/16 SIMD), Quantized Nodes; TLAS+BLAS; SER
  - ▸ *CG use:* DXR 1.1/Vulkan RT; embree kernel-level traversal; animated scenes (refit BLAS)
- 1.4.2.3 k-d Trees, Octrees (Morton/SVO), BSP Trees
  - ▸ *CG use:* Photon kd-tree; OpenVDB SVO; Quake-style PVS
- 1.4.2.4 Spatial Hashing: Infinite Grid+Hash; Lock-Free GPU Hash; Learned Spatial Indices (Neural BVH, SDF Proxy)
  - ▸ *CG use:* Instant NGP multi-res hash; GPU particle neighbors; neural scene traversal

#### 1.4.3 Intersection & Proximity
- 1.4.3.1 Ray-Triangle: Möller-Trumbore (Barycentric+Distance); Ray-AABB (Slab)
  - ▸ *CG use:* GPU RT core hardware; most-executed instruction in modern rendering
- 1.4.3.2 GJK+EPA (Convex Distance & Penetration); SAT (Convex Polytopes)
  - ▸ *CG use:* Bullet, PhysX collision; continuous collision for convex shapes
- 1.4.3.3 Bentley-Ottmann Segment Intersection O((n+k)log n); Polygon Clipping (Sutherland-Hodgman, Vatti)
  - ▸ *CG use:* 2D Boolean; planar maps; UI clipping; CSG for CAD

#### 1.4.4 Robustness & Exact Computation
- 1.4.4.1 Adaptive Precision (Shewchuk): Filter+Interval+Exact; SoS Symbolic Perturbation
  - ▸ *CG use:* Robust Delaunay (CGAL/TetGen); exact orient/incircle tests
- 1.4.4.2 Exact Geometric Computation (EGC): GMP/MPFR; CGAL Cartesian+Exact Kernel; GPU Radix Sort, ANN (HNSW, LSH)
  - ▸ *CG use:* CGAL gold standard; real-time BVH on GPU; HNSW photon lookup

> 📚 **GitHub Repos:**
> - [CGAL/cgal](https://github.com/CGAL/cgal) ![Stars](https://img.shields.io/github/stars/CGAL/cgal?style=flat) — Robust Delaunay, arrangements, Boolean, exact arithmetic
> - [embree/embree](https://github.com/embree/embree) ![Stars](https://img.shields.io/github/stars/embree/embree?style=flat) — Intel world-class BVH traversal kernels
> - [nmslib/hnswlib](https://github.com/nmslib/hnswlib) ![Stars](https://img.shields.io/github/stars/nmslib/hnswlib?style=flat) — Fast HNSW approximate NN
> - [Habrador/Computational-geometry](https://github.com/Habrador/Computational-geometry) ![Stars](https://img.shields.io/github/stars/Habrador/Computational-geometry?style=flat) — Unity/C# 2D/3D algorithms with interactive demos
>
> 📖 **Textbooks:**
> - *Computational Geometry: Algorithms and Applications* — de Berg, Cheong, van Kreveld, Overmars (The golden textbook)
> - *Geometric Tools for Computer Graphics* — Schneider & Eberly (Practical algorithms for CG practitioners)
> - *Real-Time Collision Detection* — Christer Ericson (The bible for game physics intersection)

---

### 1.5 Probability Theory & Stochastic Processes

#### 1.5.1 Foundations
- 1.5.1.1 Probability Space (Ω,ℱ,ℙ); CDF/PDF/PMF; Transform Y=g(X) (Change of Variables)
  - ▸ *CG use:* THE basis for ALL Monte Carlo rendering; IS transform method
- 1.5.1.2 Expectation, Variance, Covariance; Law of Total Expectation; Conditional Variance
  - ▸ *CG use:* MIS weight derivation; adaptive sampling variance analysis
- 1.5.1.3 Concentration: Markov, Chebyshev, Chernoff, Hoeffding, Bernstein, McDiarmid; Exponential Family; MGF
  - ▸ *CG use:* Certified MC error bounds; adaptive termination criteria; unified rendering distributions
- 1.5.1.4 Key Distributions: Gaussian, Exponential, Gamma, Beta, Dirichlet, Wishart, von Mises-Fisher (Spherical)
  - ▸ *CG use:* GGX NDF≈Beta; vMF for spherical BRDF lobe

#### 1.5.2 Monte Carlo Integration for Rendering
- 1.5.2.1 Classical MC: Î=(1/N)Σf(X_i)/p(X_i); Unbiased; Var=σ²_f/N; CLT; Error∝1/√N
  - ▸ *CG use:* Path tracing estimator; O(1/√N) is the fundamental rendering limitation
- 1.5.2.2 Importance Sampling: Optimal q*∝|f|; BRDF IS (GGX VNDF); Light IS; Environment Map IS
  - ▸ *CG use:* Every path tracer BRDF sample uses IS
- 1.5.2.3 Multiple IS (MIS): Balance Heuristic w_s∝N_s p_s; Power Heuristic (β=2); One-Sample MIS
  - ▸ *CG use:* BSDF+light combo in VCM; standard in every production renderer
- 1.5.2.4 RIS & ReSTIR: Reservoir Sampling+Spatiotemporal Reuse; Generalized Resampling
  - ▸ *CG use:* ReSTIR DI/GI/PT (SIGGRAPH 2020-2024); NVIDIA RTXDI — millions of lights in real-time
- 1.5.2.5 QMC: Low-Discrepancy (Halton, Sobol', Faure); Koksma-Hlawka; Owen Scrambling (RQMC)
  - ▸ *CG use:* Production PT (V-Ray, Arnold, Cycles) uses QMC for O(logᵈN/N) convergence

#### 1.5.3 MCMC for Rendering
- 1.5.3.1 Markov Chains: Transition Kernel, Stationary π=πP; Detailed Balance; Ergodicity & Mixing
  - ▸ *CG use:* MCMC rendering→path integral measure π(X̄)∝f(X̄)
- 1.5.3.2 MH: α=min(1,π(y)q(x|y)/(π(x)q(y|x))); HMC (Leapfrog+NUTS); Langevin MC
  - ▸ *CG use:* MLT (1997); PSSMLT (2002); MNEE manifold exploration for specular paths
- 1.5.3.3 MLT Mutations: Bidirectional, Perturbation, Lens Subpath; Handling SDS Paths
  - ▸ *CG use:* Renders caustics & SDS impossible for standard PT

#### 1.5.4 SDEs & Diffusion Generative Models
- 1.5.4.1 Brownian Motion, Itô Integral, Itô's Lemma: df=(f_t+μf_x+½σ²f_{xx})dt+σf_xdW
  - ▸ *CG use:* Foundation for diffusion-based 3D generation
- 1.5.4.2 Forward SDE: VP-SDE dX=−½β(t)Xdt+√βdW; VE-SDE dX=√(d[σ²]/dt)dW
  - ▸ *CG use:* DDPM=VP-SDE discretization; Score-based (Song 2021)=continuous SDE
- 1.5.4.3 Reverse SDE: dX=[μ−σ²∇_x log p_t]dt+σdŴ (Anderson 1982); Score Function Must Be Learned
  - ▸ *CG use:* The magic: learn score→reverse SDE→generate samples
- 1.5.4.4 Score Matching: DSM (Vincent 2011), Sliced, Implicit; DDPM: ϵ-Prediction Parametrization
  - ▸ *CG use:* 3D asset gen (3DGS+Score Distillation); text-to-texture
- 1.5.4.5 Flow Matching, Rectified Flow, Stochastic Interpolants; Score Distillation (SDS), VSD
  - ▸ *CG use:* Next-gen 3D generation (faster than DDPM); DreamFusion text→3D; ProlificDreamer

#### 1.5.5 Bayesian Inference, GPs & Random Fields
- 1.5.5.1 Bayes Theorem; Conjugate Priors; VI (ELBO, Mean-Field, Reparameterization); GP (RBF/Matérn, Kriging, Sparse)
  - ▸ *CG use:* Bayesian BRDF; GP-NeRF; geometry interpolation; Bayesian Optimization (rendering params, materials, cameras)
- 1.5.5.2 MRF, CRF, Graph Cuts (α-Expansion, αβ-Swap); Noise Spectrum Engineering (White, Blue, Pink, Brown)
  - ▸ *CG use:* Texture synthesis; segmentation; stereo; Perlin/Simplex noise; blue noise dithering; fBm terrain

> 📚 **GitHub Repos:**
> - [probml/pml-book](https://github.com/probml/pml-book) ![Stars](https://img.shields.io/github/stars/probml/pml-book?style=flat) — Exhaustive probability+ML (Murphy)
> - [CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers](https://github.com/CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers) ![Stars](https://img.shields.io/github/stars/CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers?style=flat) — MCMC+Bayesian from scratch+PyMC
> - [yang-song/score_sde](https://github.com/yang-song/score_sde) ![Stars](https://img.shields.io/github/stars/yang-song/score_sde?style=flat) — Score-based SDEs: theoretical foundation
> - [huggingface/diffusers](https://github.com/huggingface/diffusers) ![Stars](https://img.shields.io/github/stars/huggingface/diffusers?style=flat) — SOTA diffusion (DDPM, SD, Flow Matching)
> - [chi-feng/mcmc-demo](https://github.com/chi-feng/mcmc-demo) ![Stars](https://img.shields.io/github/stars/chi-feng/mcmc-demo?style=flat) — Interactive browser MCMC visualization (MH, HMC, NUTS)
> - [ctgk/PRML](https://github.com/ctgk/PRML) ![Stars](https://img.shields.io/github/stars/ctgk/PRML?style=flat) — Bishop PRML Python implementations (all chapters, Jupyter)
>
> 📖 **Textbooks:**
> - *Probabilistic Machine Learning* — Kevin Murphy (Exhaustive, graphics-relevant probability+ML)
> - *Pattern Recognition and Machine Learning* — Christopher Bishop (Classic Bayesian ML text)
> - *Monte Carlo Statistical Methods* — Robert & Casella (Theoretical MC foundations)
> - *Physically Based Rendering* — Pharr, Jakob, Humphreys (Free at pbr-book.org, MC rendering bible)

---

### 1.6 Information Theory & Statistical Learning

*Essential for neural rendering, geometry compression, perceptual metrics, and generative graphics.*

#### 1.6.1 Core Information Measures
- 1.6.1.1 Shannon Entropy H(X)=−Σp log p; Differential Entropy h(X)=−∫f log f; Maximum Entropy Principle
  - ▸ *CG use:* Entropy-constrained quantization (Draco mesh compression); BRDF measurement uncertainty
- 1.6.1.2 KL Divergence D_KL(P‖Q); Cross-Entropy; f-Divergences (TV, Hellinger, χ², JS)
  - ▸ *CG use:* VAE training (KL term); GAN training (JS vs W); perceptual loss in neural rendering
- 1.6.1.3 Mutual Information I(X;Y)=D_KL(P_XY‖P_X P_Y); Data Processing Inequality; MINE (Belghazi 2018)
  - ▸ *CG use:* Viewpoint selection (max MI camera↔scene); InfoNCE for view-consistent scenes; CLIP-based 3D generation

#### 1.6.2 Rate-Distortion Theory & Neural Compression
- 1.6.2.1 R(D)=min_{Q:𝔼[d]≤D} I(X;X̂); Blahut-Arimoto; Lossy Coding (Lloyd-Max, LBG, DCT→JPEG, Wavelet→JP2K)
  - ▸ *CG use:* BCn/ASTC GPU texture compression; vertex quantization (Draco)
- 1.6.2.2 Entropy Coding: Huffman, Arithmetic, ANS (Zstd, Draco); Neural Compression (Analysis/Synthesis+Quant+Entropy; Hyperprior; RD λ)
  - ▸ *CG use:* Draco bitstream; neural radiance field compression; 3DGS compression (quant+entropy+pruning)

#### 1.6.3 Statistical Learning Theory
- 1.6.3.1 PAC Learning, VC Dimension, Rademacher Complexity; Generalization Gap
  - ▸ *CG use:* When does NeRF overfit? Sample complexity: how many views needed?
- 1.6.3.2 Bias-Variance Trade-off; Double Descent (Modern Overparameterized); Regularization (L₁/Lasso, L₂/Ridge, Elastic Net, Early Stopping)
  - ▸ *CG use:* Neural field capacity; sparse 3DGS; smoothness prior (Eikonal loss for neural SDF)
- 1.6.3.3 Model Selection: AIC, BIC, MDL; Cross-Validation; Information Bottleneck min I(X;Z)−βI(Z;Y)
  - ▸ *CG use:* BRDF lobe count; 3DGS Gaussian count; compact latent scene representations

> 📚 **GitHub Repos:**
> - [Cover & Thomas — Elements of Information Theory](http://staff.ustc.edu.cn/~cgong821/Wiley.Interscience.Elements.of.Information.Theory.Jul.2006.eBook-DDU.pdf) — Canonical textbook
> - [google/draco](https://github.com/google/draco) ![Stars](https://img.shields.io/github/stars/google/draco?style=flat) — Production 3D mesh compression with entropy coding
> - [Understanding Deep Learning (Prince)](https://udlbook.github.io/udlbook/) — Modern text covering learning theory + info theory for DL
> - [YannDubs/InfoNCE](https://github.com/YannDubs/InfoNCE) — Practical InfoNCE & contrastive loss implementations
>
> 📖 **Textbooks:**
> - *Elements of Information Theory* — Cover & Thomas (The canonical info theory text, freely available online)
> - *Information Theory, Inference, and Learning Algorithms* — David MacKay (Free online, beautifully written)

---

### 1.7 Numerical Analysis & Scientific Computing

#### 1.7.1 Floating-Point & Error Analysis
- 1.7.1.1 IEEE 754: Binary32/64; FP16, BF16 (Same Range as FP32!), TF32; Subnormals, Inf, NaN
  - ▸ *CG use:* Every GPU shader; BF16 for stable NeRF training; TF32→2× speedup on tensor cores
- 1.7.1.2 Forward/Backward Error (Wilkinson); Condition Number; Catastrophic Cancellation
  - ▸ *CG use:* Robust geometric predicates; stable cross-product normal; compensated summation (Kahan) for PT radiance

#### 1.7.2 Numerical Linear Algebra
- 1.7.2.1 Krylov Subspace: CG (SPD), MINRES, GMRES(m), BiCGSTAB
  - ▸ *CG use:* CG for Poisson pressure; GMRES for radiosity; BiCGSTAB for advection-diffusion
- 1.7.2.2 Multigrid (GMG, AMG): Smoothing+V/W/F-Cycles; AMG as Black-Box Preconditioner
  - ▸ *CG use:* State-of-the-art Poisson solver for fluid pressure
- 1.7.2.3 Sparse Direct: Minimum Degree, Nested Dissection, Multifrontal (PARDISO/MUMPS); Preconditioning (Jacobi, ILU, AMG, SPAI, Schur)
  - ▸ *CG use:* FEM stiffness factorization; good preconditioner→CG in ~20 iters vs 2000

#### 1.7.3 Function Approximation, Interpolation & Integration
- 1.7.3.1 Polynomial (Lagrange, Newton, Barycentric), Spline (Cubic, Catmull-Rom, TCB), RBF (Gaussian, Thin-Plate, Wendland), MLS, Bézier (de Casteljau), B-Spline (Cox-de Boor), NURBS
  - ▸ *CG use:* Keyframes; MLS point surfaces; font rendering; CAD modeling
- 1.7.3.2 1D Gauss-Legendre (2n−1), Adaptive Gauss-Kronrod; Multidimensional Sparse Grids/Smolyak; Triangle Cubature (Dunavant); Romberg/Richardson
  - ▸ *CG use:* FEM element integration; spherical quadrature for environment map; subsurface scattering moments

#### 1.7.4 Numerical ODEs & PDEs
- 1.7.4.1 Explicit ODE (Euler, RK4, DOPRI5); Symplectic (Verlet, Leapfrog, Implicit Midpoint) for Hamiltonian
  - ▸ *CG use:* Particle advection (RK4); stable molecular dynamics (Verlet); game physics
- 1.7.4.2 Implicit for Stiff Systems (BDF, Radau IIA); FEM (Galerkin, Shape Fn, Assembly); FVM (Godunov, MUSCL, WENO, MAC); SPH, MPM, FLIP/PIC/APIC, MLS-MPM
  - ▸ *CG use:* Cloth (BDF-2); FEM solids; fluid (Stam 1999); snow (Disney Frozen MPM)
- 1.7.4.3 Neural Operators: DeepONet, FNO (Spectral Conv), PINNs (Collocation Residual); Randomized SVD, Sketch-and-Solve
  - ▸ *CG use:* Real-time fluid surrogate; learned cloth; fast PCA on massive meshes

> 📚 **GitHub Repos:**
> - [SciML/DifferentialEquations.jl](https://github.com/SciML/DifferentialEquations.jl) ![Stars](https://img.shields.io/github/stars/SciML/DifferentialEquations.jl?style=flat) — Julia ODE/PDE/SDE/DDE solvers
> - [scipy/scipy](https://github.com/scipy/scipy) ![Stars](https://img.shields.io/github/stars/scipy/scipy?style=flat) — linalg, sparse.linalg, integrate, interpolate
> - [taichi-dev/taichi](https://github.com/taichi-dev/taichi) ![Stars](https://img.shields.io/github/stars/taichi-dev/taichi?style=flat) — Differentiable physics (MPM, FEM, fluid)
> - [lululxvi/deepxde](https://github.com/lululxvi/deepxde) ![Stars](https://img.shields.io/github/stars/lululxvi/deepxde?style=flat) — PINNs, DeepONet, FNO for forward/inverse PDEs
> - [YLiu-5/numerical_linear_algebra_notebooks](https://github.com/YLiu-5/numerical_linear_algebra_notebooks) — Trefethen & Bau textbook companion (Jupyter)
>
> 📖 **Textbooks:**
> - *Numerical Linear Algebra* — Trefethen & Bau (Concise, elegant, the standard)
> - *Scientific Computing: An Introductory Survey* — Michael Heath (Well-rounded intro)
> - *Numerical Recipes 3rd Edition* — Press et al. (Practical, code-heavy reference, free online)

---

### 1.8 Signal Processing & Harmonic Analysis

#### 1.8.1 Classical Signal Processing
- 1.8.1.1 LTI Systems: Impulse Response, Convolution, Transfer Function, BIBO Stability
  - ▸ *CG use:* Image filtering=convolution; motion blur=box filter along motion vector
- 1.8.1.2 Nyquist-Shannon f_s>2f_max; Aliasing; Antialiasing via Prefilter+Supersample
  - ▸ *CG use:* MSAA/SSAA/TAA; mipmapping (prefiltered downsampling); texture minification
- 1.8.1.3 Reconstruction Kernels: Sinc (Ideal), Box, Tent, Mitchell-Netravali (B=1/3,C=1/3), Lanczos
  - ▸ *CG use:* Texture filtering (bilinear=tent); GPU hardware texture units
- 1.8.1.4 Filter Design: FIR (Linear Phase), IIR; Window (Hamming, Blackman, Kaiser); Remez Exchange
  - ▸ *CG use:* Audio DSP for game sound; procedural audio

#### 1.8.2 Multi-Resolution & Wavelet Analysis
- 1.8.2.1 Filter Banks: Analysis(LP+HP→↓2)→Synthesis(↑2+LP+HP→Sum); Perfect Reconstruction; QMF/CQF
  - ▸ *CG use:* JPEG 2000; geometry image compression; à-trous wavelet MC denoising
- 1.8.2.2 DWT: Mallat Cascade; Haar, Daubechies, Symlets; Lifting (Predict+Update, Integer-to-Integer Lossless)
  - ▸ *CG use:* Wavelet radiance caching; progressive mesh transmission; multiresolution editing
- 1.8.2.3 Laplacian/Gaussian Pyramids; Burt-Adelson (1983) Multiresolution Spline Blending
  - ▸ *CG use:* Mipmap chains; seamless image stitching; multiscale tone mapping
- 1.8.2.4 Steerable Pyramids, Gabor, Complex Wavelets, Curvelets, Contourlets
  - ▸ *CG use:* Edge-aware processing; anisotropic texture synthesis; directional NPR noise

#### 1.8.3 Image Processing Core
- 1.8.3.1 Edge Detection: Sobel, Prewitt, Scharr; LoG (Marr-Hildreth); Canny (Gaussian+NMS+Hysteresis); HED (Deep)
  - ▸ *CG use:* NPR contour rendering; depth discontinuity for DoF; image-based mesh extraction
- 1.8.3.2 Edge-Preserving Smoothing: Bilateral (Spatial+Range), Guided Filter O(N), Domain Transform
  - ▸ *CG use:* MC denoising (SVGF, BMFR); base-detail texture decomposition; tone mapping
- 1.8.3.3 NLM & BM3D (Collaborative Filtering); TV Regularization (ROF, Chambolle-Pock Primal-Dual)
  - ▸ *CG use:* Denoising benchmarks; MC denoising inspiration; mesh smoothing; inverse rendering regularization
- 1.8.3.4 Morphological Ops (Dilation, Erosion, Opening, Closing, Watershed, Distance Transform)
  - ▸ *CG use:* SDF from binary masks; hole detection in meshes; particle separation

#### 1.8.4 Harmonic Analysis on Manifolds & Neural Representations
- 1.8.4.1 Spectral Graph Theory: Graph Laplacian L=D−W; Spectrum; Graph Fourier Transform (GFT)
  - ▸ *CG use:* Mesh spectral filtering; spectral clustering segmentation; functional maps
- 1.8.4.2 Fourier Feature Networks (Tancik et al. 2020); Multi-Res Hash Encoding (Instant NGP, Müller 2022); SIREN (Sitzmann 2020)
  - ▸ *CG use:* NeRF positional encoding; learned feature grids; continuous neural SDF/radiance fields
- 1.8.4.3 Neural Fields as Universal Signal Learners: Occupancy, SDF, Radiance, BRDF Fields
  - ▸ *CG use:* Unified view: all neural rendering=learning a continuous signal from sparse pixel/ray samples

> 📚 **GitHub Repos:**
> - [scikit-image/scikit-image](https://github.com/scikit-image/scikit-image) ![Stars](https://img.shields.io/github/stars/scikit-image/scikit-image?style=flat) — Python image processing with tutorials
> - [NVlabs/instant-ngp](https://github.com/NVlabs/instant-ngp) ![Stars](https://img.shields.io/github/stars/NVlabs/instant-ngp?style=flat) — Hash encoding: learned features as signals
> - [vincentsitzmann/siren](https://github.com/vincentsitzmann/siren) ![Stars](https://img.shields.io/github/stars/vincentsitzmann/siren?style=flat) — Periodic activations for implicit neural reps
> - [opencv/opencv](https://github.com/opencv/opencv) ![Stars](https://img.shields.io/github/stars/opencv/opencv?style=flat) — Industry-standard CV: filtering, FFT, edge detection
> - [AllenDowney/ThinkDSP](https://github.com/AllenDowney/ThinkDSP) ![Stars](https://img.shields.io/github/stars/AllenDowney/ThinkDSP?style=flat) — Interactive book: signals, FFT, convolution, filters in Python
>
> 📖 **Textbooks:**
> - *Discrete-Time Signal Processing* — Oppenheim & Schafer (The DSP bible)
> - *A Wavelet Tour of Signal Processing* — Stéphane Mallat (Definitive wavelet reference)
> - *Digital Image Processing* — Gonzalez & Woods (Comprehensive image processing)

---

### 1.9 Optimization Theory

#### 1.9.1 First-Order Methods
- 1.9.1.1 GD: Convex O(1/k), Strongly-Convex Linear; Nesterov Accelerated O(1/k²); Heavy-Ball Momentum
  - ▸ *CG use:* Workhorse for all gradient-based graphics optimization
- 1.9.1.2 SGD: Mini-batching, Variance Reduction (SVRG, SAGA, SPIDER); Adam/AdamW (Decoupled Weight Decay), LAMB
  - ▸ *CG use:* NeRF/3DGS training (Adam dominates); convergence theory for adaptive methods
- 1.9.1.3 Subgradient; Proximal Gradient (ISTA/FISTA); Forward-Backward Splitting
  - ▸ *CG use:* ℓ₁-sparse compressed sensing BRDF/light transport

#### 1.9.2 Second-Order & Quasi-Newton
- 1.9.2.1 Newton (Local Quadratic); Gauss-Newton, Levenberg-Marquardt (Nonlinear LS)
  - ▸ *CG use:* Bundle adjustment (SfM); IK solving; material parameter fitting
- 1.9.2.2 Quasi-Newton: BFGS; L-BFGS (Double-Loop, Sherman-Morrison)
  - ▸ *CG use:* Dominates large-scale smooth optimization (geometry processing, texture optimization)
- 1.9.2.3 Natural Gradient (Fisher-Rao); K-FAC, TENGraD (Approximations)
  - ▸ *CG use:* Distribution-space optimization (BRDF, policy gradient in character control)

#### 1.9.3 Constrained, Riemannian & Structured Optimization
- 1.9.3.1 Convex: KKT, Slater, Duality; LP (Simplex, IP), QP, SOCP, SDP
  - ▸ *CG use:* Geometry convex formulations; OT as LP; ARAP as SOCP
- 1.9.3.2 ALM & ADMM; Projected Gradient, Frank-Wolfe; Active Set, IP (Barrier+Central Path)
  - ▸ *CG use:* ADMM for inverse problems (deconvolution, inpainting); constrained physics (contact, volume preservation)
- 1.9.3.3 Riemannian Optimization: Stiefel, Grassmann; Riemannian SGD, Trust-Region, L-BFGS; pymanopt, geoopt
  - ▸ *CG use:* Rotation averaging SO(3); camera pose SE(3); subspace tracking; dictionary learning

#### 1.9.4 Bilevel, Global & Derivative-Free Optimization
- 1.9.4.1 Bilevel: Hypergradient via IFT; Implicit Differentiation (Adjoint, Neumann, CG); DEQ
  - ▸ *CG use:* MAML few-shot BRDF; inverse graphics (diff-render as inner loop); implicit neural rendering layers
- 1.9.4.2 Global: Evolutionary (GA, CMA-ES, DE), Simulated Annealing, PSO, Nelder-Mead, Powell, COBYLA/BOBYQA
  - ▸ *CG use:* Material fitting; procedural gen; camera placement; black-box renderer optimization

#### 1.9.5 Graphics-Specific Optimization
- 1.9.5.1 Projective Dynamics: Element-wise Quadratic+Gauss-Seidel→Real-Time FEM
- 1.9.5.2 PBD/XPBD: Nonlinear Gauss-Seidel Constraint Projection→Game Physics
- 1.9.5.3 Chambolle-Pock Primal-Dual for TV→Mesh Smoothing, Denoising, Inverse Rendering
- 1.9.5.4 Differentiable Physics (∇-Sim, DiffTaichi, Warp)→Gradient-Based Design & Control

> 📚 **GitHub Repos:**
> - [epfml/OptML_course](https://github.com/epfml/OptML_course) ![Stars](https://img.shields.io/github/stars/epfml/OptML_course?style=flat) — EPFL: convex, SGD, ADMM, Quasi-Newton
> - [cvxpy/cvxpy](https://github.com/cvxpy/cvxpy) ![Stars](https://img.shields.io/github/stars/cvxpy/cvxpy?style=flat) — Python convex: LP, QP, SOCP, SDP
> - [jaxopt/jaxopt](https://github.com/google/jaxopt) ![Stars](https://img.shields.io/github/stars/google/jaxopt?style=flat) — Differentiable optimization: implicit diff, bilevel, QP
> - [pymanopt/pymanopt](https://github.com/pymanopt/pymanopt) ![Stars](https://img.shields.io/github/stars/pymanopt/pymanopt?style=flat) — Riemannian optimization
> - [scipy/scipy](https://github.com/scipy/scipy) ![Stars](https://img.shields.io/github/stars/scipy/scipy?style=flat) — scipy.optimize: L-BFGS, SLSQP, trust-region, global methods
> - [cvxgrp/cvx_short_course](https://github.com/cvxgrp/cvx_short_course) — Stanford convex optimization short course (Boyd & Vandenberghe)
>
> 📖 **Textbooks:**
> - *Convex Optimization* — Boyd & Vandenberghe (The bible, freely available online)
> - *Numerical Optimization* — Nocedal & Wright (Comprehensive algorithms reference)
> - *Optimization for Machine Learning* — Sra, Nowozin, Wright (Advanced, ML-focused)

---

### 1.10 Topology for Graphics

#### 1.10.1 Algebraic Topology
- 1.10.1.1 Simplicial/Cell/CW-Complexes; Homology Hₖ (Betti βₖ); Cohomology Hᵏ, Cup Product; π₁, Covering Spaces
  - ▸ *CG use:* Hole/tunnel detection; topology-preserving simplification; vector field design (cohomology); global parameterization
- 1.10.1.2 Morse Theory: Critical Points, Morse-Smale Complex, Reeb Graphs, Contour Trees
  - ▸ *CG use:* Shape feature detection; topological skeletonization; isosurface topology in sci-viz

#### 1.10.2 Persistent Homology & TDA
- 1.10.2.1 Filtration (Vietoris-Rips, Čech, Alpha), Persistence Diagram/Barcode, Bottleneck/Wasserstein Distance
  - ▸ *CG use:* Topological feature lifetime → noise vs signal; 3D shape classification
- 1.10.2.2 Persistence Landscapes/Images (ML Vectorization); Mapper; Merge Trees
  - ▸ *CG use:* Shape skeletonization; ML-compatible topological shape features
- 1.10.2.3 Discrete Morse: Gradient Fields, Cancelation; Morse-Smale Meshes→Quadrangulation
  - ▸ *CG use:* Vector field topology-driven quad meshing; flow-guided remeshing

> 📚 **GitHub Repos:**
> - [Ripser/ripser](https://github.com/Ripser/ripser) ![Stars](https://img.shields.io/github/stars/Ripser/ripser?style=flat) — Ultrafast Vietoris-Rips persistence in C++
> - [giotto-ai/giotto-tda](https://github.com/giotto-ai/giotto-tda) ![Stars](https://img.shields.io/github/stars/giotto-ai/giotto-tda?style=flat) — High-performance TDA with Mapper
> - [Stanford CS468: Topology for Graphics](https://graphics.stanford.edu/courses/cs468-12-spring/) — Course notes & papers
> - [scikit-tda/scikit-tda](https://github.com/scikit-tda/scikit-tda) — Python ecosystem for topological data analysis
>
> 📖 **Textbooks:**
> - *Computational Topology: An Introduction* — Edelsbrunner & Harer (The standard reference)
> - *Algebraic Topology* — Allen Hatcher (Free online, classic algebraic topology text)

---

### 1.11 Geometric & Clifford Algebra

#### 1.11.1 Foundations
- 1.11.1.1 Exterior (Grassmann) Algebra: k-vectors, Wedge ∧, Grade, k-blades
  - ▸ *CG use:* Oriented area/volume; Plücker line coordinates
- 1.11.1.2 Clifford Algebra Cl(p,q,r): Geometric Product ab=a·b+a∧b; Multivectors; Graded Structure
  - ▸ *CG use:* Unified framework replacing separate vector+quaternion+matrix code
- 1.11.1.3 Rotors RxR̃; Versors: All Orthogonal Transforms as Versor Products (Cartan-Dieudonné)
  - ▸ *CG use:* Rotation, reflection, translation as single algebraic entity

#### 1.11.2 PGA — Cl(3,0,1) & CGA — Cl(4,1)
- 1.11.2.1 PGA: Points/Lines/Planes as k-vectors; Join ∧ (Span), Meet ∨ (Intersection); Motor (Rigid Motion)
  - ▸ *CG use:* Entire camera pipeline in one algebra; ray-triangle via meet; rigid body=motor
- 1.11.2.2 CGA: Spheres/Circles/Point Pairs/Tangents as Basis; Conformal Versors (Möbius, Spherical Inversion)
  - ▸ *CG use:* Sphere packing; IK (joint limits as spheres); Möbius texture distortion; lens correction

> 📚 **GitHub Repos:**
> - [bivector/Liber-Demysthen](https://github.com/bivector/Liber-Demysthen) — Interactive intro to GA for CG
> - [enkimute/ganja.js](https://github.com/enkimute/ganja.js) ![Stars](https://img.shields.io/github/stars/enkimute/ganja.js?style=flat) — GA for JavaScript with visualizations
> - [projectivegeometricalgebra.org](https://projectivegeometricalgebra.org/) — PGA reference + cheat sheets
> - [bivector.net](https://bivector.net) — Community hub: tutorials, tools, papers for GA/CGA/PGA
>
> 📖 **Textbooks:**
> - *Geometric Algebra for Computer Science* — Dorst, Fontijne, Mann (Definitive GA-for-CG reference)
> - *Linear and Geometric Algebra* — Alan Macdonald (Accessible introduction)

---

### 1.12 Color Science & Visual Perception

#### 1.12.1 Photometry & Colorimetry
- 1.12.1.1 Radiometry→Photometry (lm, cd, lx, nit); CIE V(λ); CIE 1931 XYZ (x̄ȳz̄ CMFs); CIE xy Chromaticity
  - ▸ *CG use:* Display calibration; spectral rendering→XYZ→display encoding; gamut visualization
- 1.12.1.2 CIE LAB (L*a*b*, ΔE*₀₀), LCh; OKLab/OKLCH (Improved Uniformity & Hue Linearity)
  - ▸ *CG use:* Perceptually-uniform color difference metrics; gradient-domain ops in perceptual space

#### 1.12.2 Color Spaces & Encoding
- 1.12.2.1 sRGB (Rec.709 Primaries, D65, ~γ2.2); DCI-P3/Display P3; Adobe RGB; ProPhoto RGB
  - ▸ *CG use:* Default framebuffer; texture storage; wide-gamut HDR displays
- 1.12.2.2 Rec.2020 (UHD), Rec.2100 (HDR: PQ ST.2084 + HLG); ACES (ACES2065-1, ACEScg, ACEScct)
  - ▸ *CG use:* HDR10/Dolby Vision; scRGB; film/VFX industry standard pipeline (ACES RRT+ODT)
- 1.12.2.3 Gamma/EOTF/OETF; Scene-Referred vs. Display-Referred; Linear Workflow (Linearize→Compute→Encode)
  - ▸ *CG use:* Correct texture sampling; HDR tone mapping chain

#### 1.12.3 Visual Perception
- 1.12.3.1 HVS: Cones L/M/S (Trichromatic), Rods (Scotopic); Opponent Color; CSF (Mannos & Sakrison, Daly VDP)
  - ▸ *CG use:* Foveated rendering exploits cone falloff; blue noise dithering shaped to CSF; JND for adaptive quality
- 1.12.3.2 Visual Masking: Luminance (Weber-Fechner ΔL/L≈const), Contrast, Texture, Temporal (Flicker~60Hz)
  - ▸ *CG use:* Perceptual metrics (SSIM, MS-SSIM, HDR-VDP); rendering noise visibility prediction
- 1.12.3.3 Modern Perceptual Losses: LPIPS (AlexNet Features), DISTS (Structure+Texture), ST-LPIPS (Spatiotemporal)
  - ▸ *CG use:* Neural rendering loss functions; GAN training; NeRF/3DGS quality evaluation
- 1.12.3.4 Visual Attention (Saliency): Itti-Koch, DeepGaze; Foveated/Gaze-Contingent Rendering
  - ▸ *CG use:* Adaptive sample budget allocation; VR eye-tracking quality optimization

#### 1.12.4 HDR Imaging
- 1.12.4.1 HDR Capture: Debevec & Malik 1997 (CRF Recovery via LS); Multi-Exposure Fusion; Ghost Removal
  - ▸ *CG use:* IBL environment map capture; light probe HDR stitching
- 1.12.4.2 HDR Formats: OpenEXR (Half Float, Multi-Layer, Deep), Radiance .hdr, JPEG-XL HDR, AVIF HDR
  - ▸ *CG use:* Production rendering output; PBR texture storage
- 1.12.4.3 Tone Mapping: Reinhard (Photographic), Filmic (UE4 ACES), Hable, Gran Turismo; Display Mapping
  - ▸ *CG use:* HDR→SDR for consumer displays; artistic look development

> 📚 **GitHub Repos:**
> - [PBR Book v4 (Color & Radiometry Chapters)](https://pbr-book.org/) — Definitive CG reference
> - [colour-science/colour](https://github.com/colour-science/colour) ![Stars](https://img.shields.io/github/stars/colour-science/colour?style=flat) — Comprehensive Python color science library
> - [richzhang/PerceptualSimilarity](https://github.com/richzhang/PerceptualSimilarity) ![Stars](https://img.shields.io/github/stars/richzhang/PerceptualSimilarity?style=flat) — LPIPS perceptual metric (standard for neural rendering)
> - [ACES Documentation](https://acescentral.com/) — Academy Color Encoding System specs
> - [ampas/aces-dev](https://github.com/ampas/aces-dev) ![Stars](https://img.shields.io/github/stars/ampas/aces-dev?style=flat) — Official ACES reference implementation
>
> 📖 **Textbooks:**
> - *Color Science: Concepts and Methods* — Wyszecki & Stiles (The definitive color science reference)
> - *Digital Color Management* — Giorgianni & Madden (Practical color encoding workflows)
> - *Vision Science: Photons to Phenomenology* — Stephen Palmer (Comprehensive perception textbook)

---




## Chapter 2 · Geometry & Shape Representation

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


---

## Chapter 3 · Appearance, Materials & Textures

*This chapter covers the theoretical foundations of how light interacts with matter — radiometry, BRDF/BSDF theory, materials, and the rendering equation — the "what" before the "how" of rendering.*

*This chapter covers the theoretical foundations of how light interacts with matter — radiometry, BRDF/BSDF theory, materials, and the rendering equation — the "what" before the "how" of rendering.*

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

---


---

## Chapter 4 · Light Transport & Rendering


### 4.1 Rasterization Rendering

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

---


---

## Chapter 5 · Neural, Differentiable & Inverse Rendering


### 5.1 Differentiable Rendering
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

### 5.2 Neural Rendering
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


---

## Chapter 6 · Animation & Physics Simulation

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


---

## Chapter 7 · Geometry Processing & Shape Analysis

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


---

## Chapter 8 · 3D Vision, Reconstruction & Computational Photography


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


---

## Chapter 9 · Graphics Systems, Hardware & Engineering


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


---

## Chapter 10 · Display, Interaction & Professional Practice


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
