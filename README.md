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

*This chapter covers how virtual worlds are encoded — from classical polygon meshes to cutting-edge neural representations. Each concept is linked to its CG use via `▸ CG use:` annotations.*

> 💡 **Top-Level References:**
> - [ssloy/tinyrenderer](https://github.com/ssloy/tinyrenderer) ![Stars](https://img.shields.io/github/stars/ssloy/tinyrenderer?style=flat) — Build a renderer from scratch (learns mesh loading, rasterization, geometry processing)
> - [libigl/libigl](https://github.com/libigl/libigl) ![Stars](https://img.shields.io/github/stars/libigl/libigl?style=flat) — Swiss-army-knife geometry processing library
> - [graphdeco-inria/gaussian-splatting](https://github.com/graphdeco-inria/gaussian-splatting) ![Stars](https://img.shields.io/github/stars/graphdeco-inria/gaussian-splatting?style=flat) — Original 3DGS implementation (the reference for modern point-based geometry)

---

### 2.1 Polygon Meshes & Mesh Data Structures

#### 2.1.1 Mesh Representations
- 2.1.1.1 Face-Vertex List (Simplest: List of Vertex Positions + List of Face Index Triplets); OBJ Format
  - ▸ *CG use:* The default interchange format; every DCC tool imports/exports OBJ; GPU vertex/index buffers
- 2.1.1.2 Winged-Edge Structure (Baumgart 1972): Per-Edge: Two Faces, Two Vertices, Four Adjacent Edges
  - ▸ *CG use:* Historical significance; foundation for topology queries in early CAD systems
- 2.1.1.3 Half-Edge Structure (Mäntylä 1988): Directed Edges; Each Edge = Two Half-Edges (Opposite Directions); Constant-Time Adjacency Queries
  - ▸ *CG use:* THE standard for mesh processing libraries (OpenMesh, CGAL Polyhedron); supports edge flip, collapse, split operations
- 2.1.1.4 Directed-Edge (Campagna et al. 1998): Storage-Efficient Variant; Single Integer Index Per Half-Edge
  - ▸ *CG use:* Used in geometry compression and GPU-friendly mesh data layouts (mesh shaders)
- 2.1.1.5 Corner Table (Rossignac et al. 2001): Implicit Connectivity via Corner-to-Corner Mapping; Extremely Compact (≈2 integers per triangle)
  - ▸ *CG use:* Efficient GPU traversal; basis for several geometry image and compression schemes

#### 2.1.2 Mesh Topology & Quality
- 2.1.2.1 Manifold Condition: Every Point Has Neighborhood Homeomorphic to Disk (2-Manifold) or Half-Disk (2-Manifold with Boundary)
  - ▸ *CG use:* Non-manifold edges (shared by >2 faces) and vertices break most geometry processing algorithms; must detect and repair
- 2.1.2.2 Euler Characteristic χ = V − E + F = 2 − 2g − b (g = Genus, b = Boundary Loops); Gauss-Bonnet Connection
  - ▸ *CG use:* Topology verification; guarantees for simplification algorithms; genus detection for shape retrieval
- 2.1.2.3 Mesh Quality Metrics: Aspect Ratio, Skewness, Jacobian Determinant, Minimum/Maximum Angle, Condition Number of Element Jacobian
  - ▸ *CG use:* FEM simulation quality directly depends on mesh quality (sliver elements → singular stiffness matrices); remeshing targets
- 2.1.2.4 Vertex Normals: Uniform Weighted (Fast, Poor Quality), Area Weighted (Better for Non-Uniform Tessellation), Angle Weighted (Best — Thürmer-Wüthrich 1998)
  - ▸ *CG use:* Smooth shading normal computation; angle-weighted formula = most accurate for arbitrary triangulation
- 2.1.2.5 Mesh Formats Deep-Dive:
  - OBJ: ASCII, simple but verbose; MTL for materials; no animation
  - PLY: Binary/ASCII, extensible per-vertex/face properties (Stanford format)
  - STL: Binary or ASCII, no topology info; de-facto 3D printing standard
  - FBX: Autodesk proprietary binary; scene hierarchy, animation, materials, embedded textures
  - glTF 2.0: "JPEG of 3D"; JSON + binary buffers; PBR materials; Draco compression; web-friendly
  - USD (Universal Scene Description): Pixar's composition engine; Hydra rendering framework; industry standard for VFX pipelines
  - Alembic: Geometry caching; efficient animated mesh streaming (HDF5-based)

#### 2.1.3 Mesh Operations & GPU Geometry Pipeline
- 2.1.3.1 Local Topological Operations: Edge Flip (2→2 Triangles), Edge Collapse (2→0, Simplification), Edge Split (2→4, Refinement), Vertex Removal
  - ▸ *CG use:* Remeshing operations; progressive mesh construction; adaptive LOD transitions
- 2.1.3.2 GPU Vertex Pipeline: Vertex Shader → (Tessellation Control → Tessellator → Tessellation Evaluation) → Geometry Shader → Primitive Assembly → Rasterizer
  - ▸ *CG use:* Modern tessellation allows GPU-side geometry amplification (displacement mapping, adaptive subdivision)
- 2.1.3.3 Mesh Shaders (Turing/Ampere+): Replace Vertex→Tessellation→Geometry with Task Shader (Work Distribution) + Mesh Shader (Output Primitives Directly)
  - ▸ *CG use:* Nanite-style GPU-driven rendering; meshlet-based culling and LOD selection; up to 3× geometry throughput
- 2.1.3.4 Meshlet Representation: Small Mesh Chunks (Typically 64-128 Triangles) with Local Index Buffer; Optimized for GPU Mesh Shader Output
  - ▸ *CG use:* UE5 Nanite virtualized geometry; GPU-driven rendering pipelines; fine-grained culling

> 📚 **GitHub Repos:**
> - [libigl/libigl](https://github.com/libigl/libigl) ![Stars](https://img.shields.io/github/stars/libigl/libigl?style=flat) — Half-edge ops, normals, topology queries in C++/Python
> - [alecjacobson/geometry-processing](https://github.com/alecjacobson/geometry-processing) — Course: mesh data structures, simplification, parameterization
> - [hhoppe/mesh_simplification](https://github.com/hhoppe/mesh_simplification) — Progressive meshes & LOD examples
>
> 📖 **Textbooks:** *Polygon Mesh Processing* — Botsch, Kobbelt, Pauly, Alliez, Lévy; *Computer Graphics: Principles and Practice* — Hughes et al. (Ch. 12-14)

---

### 2.2 Parametric Curves & Surfaces

#### 2.2.1 Polynomial & Bézier Curves
- 2.2.1.1 Lagrange Interpolation: Given n+1 Points, Unique Degree-n Polynomial; Prone to Runge Oscillations for High Degree
  - ▸ *CG use:* Camera path interpolation (low degree); Hermite interpolation (specify value + derivative at endpoints)
- 2.2.1.2 Bézier Curves: Bernstein Basis B_i^n(t) = C(n,i) t^i (1−t)^{n−i}; Affine Invariance; Convex Hull Property; Variation Diminishing
  - ▸ *CG use:* Font rendering (TrueType=Quadratic Bézier, PostScript/OpenType=Cubic Bézier); animation path smoothing; curve editing in all DCC tools
- 2.2.1.3 de Casteljau Algorithm: Repeated Linear Interpolation (Stable, Geometric); Subdivision at Parameter t Generates Two Bézier Segments
  - ▸ *CG use:* GPU tessellation of Bézier patches; adaptive rendering via recursive subdivision
- 2.2.1.4 Degree Elevation (Exact Representation Change), Degree Reduction (Approximation); Bernstein-Bézier-to-Power Basis Conversion
  - ▸ *CG use:* Degree compatibility in CAD exchange; efficient evaluation via Horner's method for power basis

#### 2.2.2 B-Splines & NURBS
- 2.2.2.1 B-Spline Basis Functions N_{i,k}(t): Cox-de Boor Recurrence; Defined by Knot Vector [t₀, t₁, ..., t_{n+k}]; Local Support (Span Only k Intervals); C^{k−m} Continuity at Knot Multiplicity m
  - ▸ *CG use:* Local control (moving one control point affects only k spans — unlike Bézier where all change)
- 2.2.2.2 Knot Vector Types: Uniform (Equally Spaced), Open Uniform (Repeated End Knots → Interpolates Endpoints), Non-Uniform; Knot Insertion (Boehm's Algorithm — Refines Without Changing Shape)
  - ▸ *CG use:* Adding detail in specific regions without global change; interactive curve editing
- 2.2.2.3 NURBS: Rational Extension R_i(t) = w_i N_{i,k}(t) / Σ w_j N_{j,k}(t); Weights Provide Exact Conic Section Representation (Circle, Ellipse, Hyperbola)
  - ▸ *CG use:* CAD industry backbone (CATIA, SolidWorks, Rhino); exact circle representation (weight = cos(θ/2) for arc); IGES/STEP exchange
- 2.2.2.4 NURBS Surface Fitting: Least-Squares Fit to Point Cloud; Smoothness Regularization; Parameter Correction (Iterative); B-spline Surface Skinning
  - ▸ *CG use:* Reverse engineering from 3D scans to CAD; automotive/aerospace surface reconstruction

#### 2.2.3 Advanced Parametric Representations
- 2.2.3.1 T-Splines (Sederberg 2003): Allow T-Junctions in Control Grid; Local Refinement Without Global Knot Insertion; 2011 Acquisition by Autodesk (Fusion 360)
  - ▸ *CG use:* Gap-free merging of NURBS patches; organic-to-mechanical surface transitions in CAD
- 2.2.3.2 Subdivision Surfaces as Parametric Surfaces: Catmull-Clark and Loop Produce Limit Surfaces Expressible as Bi-Cubic B-Splines (Regular Regions); Irregular Patches Require Eigen-Analysis
  - ▸ *CG use:* Pixar's RenderMan uses Catmull-Clark subdivision surfaces as its primary geometry primitive; OpenSubdiv library
- 2.2.3.3 Coons Patches (1967): Interpolate Four Boundary Curves; Gordon Surfaces: Interpolate Network of Curves (Bi-Directional Coons)
  - ▸ *CG use:* Lofting between profile curves (aircraft fuselage design); filling holes with G¹ continuity

> 📚 **GitHub Repos:**
> - [NURBS-Python (geomdl)](https://github.com/orbingol/NURBS-Python) ![Stars](https://img.shields.io/github/stars/orbingol/NURBS-Python?style=flat) — Pure Python NURBS library with visualization
> - [PixarAnimationStudios/OpenSubdiv](https://github.com/PixarAnimationStudios/OpenSubdiv) ![Stars](https://img.shields.io/github/stars/PixarAnimationStudios/OpenSubdiv?style=flat) — Production Catmull-Clark subdivision (used in RenderMan)
>
> 📖 **Textbooks:** *The NURBS Book* — Piegl & Tiller (The definitive reference); *Curves and Surfaces for CAGD* — Gerald Farin (Classic foundation)

---

### 2.3 Subdivision Surfaces

#### 2.3.1 Approximating Schemes
- 2.3.1.1 Catmull-Clark (1978): Quad-Dominant; Face Point + Edge Point + Vertex Point; Generalizes Bi-Cubic B-Spline to Arbitrary Topology; C² Everywhere Except C¹ at Extraordinary Vertices
  - ▸ *CG use:* Film-quality character modeling; Pixar's subdivision surfaces since *Geri's Game* (1997); OpenSubdiv in real-time engines
- 2.3.1.2 Loop Subdivision (1987): Triangle Meshes; Edge Split (1→4) + Vertex Smoothing with Weight β(n) for Valence-n Vertices; C² Except C¹ at Irregular Vertices
  - ▸ *CG use:* Triangle-mesh-based modeling workflows; topology-preserving refinement for FEM
- 2.3.1.3 Doo-Sabin (1978): Generalizes Bi-Quadratic B-Spline; Face-Centered Refinement; Produces Only Quadrilateral Faces
  - ▸ *CG use:* Less common than Catmull-Clark; useful for quad-remeshing applications

#### 2.3.2 Interpolating & Specialized Schemes
- 2.3.2.1 Butterfly Subdivision (Dyn et al. 1990): Interpolating (Original Vertices Unchanged); 8-Point Stencil for Interior; Modified Butterfly (Zorin 1996) for Boundaries
  - ▸ *CG use:* When exact interpolation of control points is required (landmark preservation in medical modeling)
- 2.3.2.2 √3 Subdivision (Kobbelt 2000): Face Split (1→3); Rotates Edge Directions Each Step; Slower Refinement Rate
  - ▸ *CG use:* Adaptive refinement with natural triangle hierarchy; geometric multigrid solvers
- 2.3.2.3 Semi-Sharp Creases (DeRose et al. 1998): Tagged Edges with Sharpness Parameter s; Infinitely Sharp (s=∞) = Hard Edge, s=0 = Smooth; Fractional s = Semi-Sharp
  - ▸ *CG use:* Character modeling (sharp eyelids, lips, fingernails on otherwise smooth skin); Pixar's *Geri's Game* and every subsequent film

#### 2.3.3 Theory & Analysis
- 2.3.3.1 Subdivision Matrix Eigen-Analysis: Limit Position = Eigenvector for λ=1; Limit Tangent = Eigenvectors for Subdominant λ; C¹ Condition: 1 = λ₀ > λ₁ = λ₂ > |λ₃|
  - ▸ *CG use:* Mathematical guarantee of smoothness; automatically satisfied by Catmull-Clark and Loop
- 2.3.3.2 Exact Evaluation at Arbitrary Parameter (Stam 1998): Eigen-Decomposition of Subdivision Matrix → Closed-Form Evaluation; Removes Need for Recursive Subdivision
  - ▸ *CG use:* Direct limit surface evaluation for ray tracing and displacement mapping; RenderMan REYES→RIS transition
- 2.3.3.3 Adaptive Subdivision: Refine Only Where Needed (Silhouettes, High Curvature, Creases); View-Dependent Refinement
  - ▸ *CG use:* Real-time tessellation on GPU; save geometry bandwidth for flat, distant regions

> 📚 **GitHub Repos:**
> - [PixarAnimationStudios/OpenSubdiv](https://github.com/PixarAnimationStudios/OpenSubdiv) ![Stars](https://img.shields.io/github/stars/PixarAnimationStudios/OpenSubdiv?style=flat) — Production Catmull-Clark with semi-sharp creases, GPU tessellation
>
> 📖 **Textbooks:** *Subdivision Methods for Geometric Design* — Warren & Weimer; *Computer Graphics: Principles and Practice* — Hughes et al. (Ch. 22)

---

### 2.4 Implicit Representations & Signed Distance Fields

#### 2.4.1 Classical Implicit Methods
- 2.4.1.1 Algebraic Surfaces: Polynomial Equations f(x,y,z)=0; Quadrics (Sphere, Ellipsoid, Cylinder, Cone, Paraboloid, Hyperboloid); Torus (Quartic)
  - ▸ *CG use:* Exact inside/outside testing; analytical ray intersection (sphere, quadric); CSG primitives
- 2.4.1.2 Isosurface Extraction: Marching Cubes (Lorensen & Cline 1987) — 256 Cases (15 Unique by Symmetry); Marching Tetrahedra (Topologically Correct); Dual Contouring (Ju et al. 2002 — Sharp Features)
  - ▸ *CG use:* Converting implicit/imaged data to triangle meshes; CT/MRI visualization; SDF→mesh conversion
- 2.4.1.3 Metaballs (Blinn 1982): Sum of Radial Density Functions φ_i(r) = exp(−a r²); Isosurface at Iso-value; Organic Blobby Shapes
  - ▸ *CG use:* Particle-based fluid surface reconstruction; organic modeling; special effects (T-1000 in Terminator 2)
- 2.4.1.4 Function Representation (F-Rep): Complex Object as Single Real-Valued Function; R-Functions for Exact Boolean Operations (Union, Intersection, Difference with C^n Continuity)
  - ▸ *CG use:* HyperFun/Pasko framework; procedurally defined infinite-detail geometry; CAD/CAE integration

#### 2.4.2 Signed Distance Fields (SDF)
- 2.4.2.1 SDF Definition: f(x) = Signed Distance to Closest Surface Point (Negative Inside, Positive Outside); ‖∇f‖=1 (Eikonal Equation) Almost Everywhere
  - ▸ *CG use:* Sphere tracing (Hart 1996) for robust ray-marching SDFs; guaranteed convergence with Lipschitz bound
- 2.4.2.2 SDF Operations: Union min(d₁,d₂), Intersection max(d₁,d₂), Difference max(d₁,−d₂); Smooth Blend (Quilez — Polynomial Smooth min); Elongation, Rounding, Onion (Shell)
  - ▸ *CG use:* Shadertoy/Inigo Quilez style modeling; real-time ray-marched visuals (dreams, clayxels)
- 2.4.2.3 SDF to Mesh: Marching Cubes on Adaptive Grid; Octree Refinement Near Surface; Feature-Sensitive Sampling
  - ▸ *CG use:* 3D printing from SDF; game engine SDF→mesh baking (UE5 mesh distance fields)
- 2.4.2.4 Mesh to SDF: Signed Distance Computation via Closest Point Query; BVH-Accelerated; Pseudo-Normal Sign Determination for Open Meshes; Fast Sweeping/Winding Number Methods
  - ▸ *CG use:* Collision detection proxy generation; level set simulation initialization; ambient occlusion baking

#### 2.4.3 Advanced Implicit Techniques
- 2.4.3.1 Radial Basis Functions (RBF) Interpolation: f(x) = Σ w_i φ(‖x−c_i‖) + P(x); Global (Thin-Plate, Multiquadric) vs. Compact Support (Wendland); Exact Interpolation of Point+Normal Constraints
  - ▸ *CG use:* Implicit surface reconstruction from oriented point clouds; HRBF (Hermite RBF) for Hermite data
- 2.4.3.2 Moving Least Squares (MLS) Implicit: Locally Weighted Least-Squares Fit of Algebraic Surface; MLS Surface Definition (Levin 2003); Point Set Surfaces (Alexa et al. 2001)
  - ▸ *CG use:* Smooth surface definition from raw point clouds without explicit connectivity; denoising via MLS projection
- 2.4.3.3 Partition of Unity Implicits (Ohtake et al. 2003): Blend Local Quadratic Approximations via Weight Functions; Handle Large-Scale and Sparse Data
  - ▸ *CG use:* Multi-scale implicit surface reconstruction; adaptive detail handling (fine features on large smooth regions)
- 2.4.3.4 Fractals: Iterated Function Systems (IFS); Mandelbrot/Julia Sets; Fractal Landscapes (Midpoint Displacement, Diamond-Square)
  - ▸ *CG use:* Procedural terrain generation; infinite detail for background environments; artistic visual effects

> 📚 **GitHub Repos:**
> - [Interactive Computer Graphics (Cem Yuksel)](https://github.com/cem-yuksel) — Mesh processing and SDF course resources
> - [SDF-Lib](https://github.com/nv-tlabs/sdf-lib) — NVIDIA's SDF utilities and signed distance computation
>
> 📖 **Textbooks:** *Level Set Methods and Dynamic Implicit Surfaces* — Osher & Fedkiw; *Implicit Objects in Computer Graphics* — Velho, Gomes, de Figueiredo

---

### 2.5 Neural Implicit Representations

#### 2.5.1 Coordinate-Based Neural Representations
- 2.5.1.1 Occupancy Networks (Mescheder et al. 2019): f_θ(x) → Occupancy Probability ∈ [0,1]; Decision Boundary = Surface; Conditioned on Shape Latent Code
  - ▸ *CG use:* Implicit 3D shape representation; continuous surface at infinite resolution; shape completion
- 2.5.1.2 DeepSDF (Park et al. 2019): f_θ(x,z) → Signed Distance; Autodecoder Architecture (Latent Code z per Shape); Regularized Latent Space → Shape Interpolation
  - ▸ *CG use:* Shape space learning; interpolation between chairs/tables/cars; single-view 3D reconstruction
- 2.5.1.3 SIREN (Sitzmann et al. NeurIPS 2020): Sinusoidal Activation Functions = sin(Wx+b); Networks as Continuous Signals; Derivatives Are Also Networks (Smooth Normals!)
  - ▸ *CG use:* Implicit surface with analytical gradient → ∇f gives normals; wave propagation simulation; audio synthesis
- 2.5.1.4 Fourier Features (Tancik et al. NeurIPS 2020): γ(x) = [cos(2πBx), sin(2πBx)] with Random Gaussian B ∼ N(0,σ²); Controls Spectral Bias (Low σ→Smooth, High σ→High-Freq)
  - ▸ *CG use:* NeRF positional encoding is a special case with log-spaced frequencies; controls detail level of neural representations

#### 2.5.2 Multi-Resolution & Hybrid Representations
- 2.5.2.1 Instant NGP (Müller et al. SIGGRAPH 2022): Multi-Resolution Hash Encoding; L Levels × T Hash Table Size × F Features; Fast Training (Seconds!) via Tiny-CUDA-NN
  - ▸ *CG use:* Real-time NeRF training; SDF from point clouds in seconds; the backbone of modern neural graphics
- 2.5.2.2 TensoRF (Chen et al. ECCV 2022): Factorize 3D Grid into CP or VM Decomposition; Dense Grid = Σ Vectors ⊗ Matrices; Equivalent Quality to NGP with Fewer Parameters
  - ▸ *CG use:* Compact radiance field representation; explicit decomposition enables analysis and editing
- 2.5.2.3 Triplane Representation (EG3D, Chan et al. 2022): Three Axis-Aligned 2D Feature Planes (XY, XZ, YZ); Decoder MLP Queries Three 2D Features + Aggregation
  - ▸ *CG use:* Efficient 3D-aware GANs; fast feed-forward 3D reconstruction (LRM family); balance of memory vs. quality
- 2.5.2.4 NeuS (Wang et al. NeurIPS 2021): Volume Rendering of SDF with Unbiased Weight Function; Weight = α(ρ(t)) · T(t) Where α Derived from SDF-to-Density Transform
  - ▸ *CG use:* High-quality surface reconstruction from multi-view images; watertight surfaces from NeRF-like optimization

#### 2.5.3 Large-Scale & Editable Neural Representations
- 2.5.3.1 Block-NeRF (Tancik et al. 2022): City-Scale NeRF via Tiling; Block Boundary Blending via Appearance Embedding Overlap; Waymo/Google Street View Data
  - ▸ *CG use:* Autonomous driving simulation; city-scale novel view synthesis; digital twin captures
- 2.5.3.2 NeRF in the Wild (NeRF-W, Martin-Brualla et al. 2021): Per-Image Appearance Embedding; Transient Object Handling via Uncertainty; Works on Internet Photo Collections
  - ▸ *CG use:* Tourist landmark reconstruction from Flickr; removes pedestrians/cars automatically
- 2.5.3.3 Editable NeRF: Object Removal/Insertion via Compositional NeRF (Yang et al. 2021); NeRF-Editing (Yuan et al. 2022) — Explicit Surface Proxy for Intuitive Deformation
  - ▸ *CG use:* Scene editing for VFX; product visualization with background replacement
- 2.5.3.4 UNISURF (Oechsle et al. 2021): Unified Surface and Volume Rendering; Smooth Transition from NeRF Volume to Explicit Surface; No Discrete Occupancy Threshold
  - ▸ *CG use:* Bridges gap between volumetric NeRF and surface-based rendering; enables level-of-detail

> 📚 **GitHub Repos:**
> - [NVlabs/instant-ngp](https://github.com/NVlabs/instant-ngp) ![Stars](https://img.shields.io/github/stars/NVlabs/instant-ngp?style=flat) — Multi-resolution hash encoding + SDF/NeRF training
> - [vincentsitzmann/siren](https://github.com/vincentsitzmann/siren) ![Stars](https://img.shields.io/github/stars/vincentsitzmann/siren?style=flat) — Periodic activations for implicit neural representations
> - [apchenstu/TensoRF](https://github.com/apchenstu/TensoRF) ![Stars](https://img.shields.io/github/stars/apchenstu/TensoRF?style=flat) — VM-decomposition tensor radiance fields
> - [autonomousvision/sdfstudio](https://github.com/autonomousvision/sdfstudio) ![Stars](https://img.shields.io/github/stars/autonomousvision/sdfstudio?style=flat) — Unified framework for neural implicit surface reconstruction
>
> 📖 **Textbooks:** No dedicated textbook yet — area moves too fast; see NeurIPS/SIGGRAPH proceedings for NeRF, SIREN, Instant NGP, NeuS papers

---

### 2.6 3D Gaussian Splatting & Point-Based Geometry

#### 2.6.1 3D Gaussian Splatting (3DGS) — The 2023 Revolution
- 2.6.1.1 3DGS Core (Kerbl et al. SIGGRAPH 2023): Anisotropic 3D Gaussians G(x) = exp(−½(x−μ)ᵀΣ⁻¹(x−μ)); Σ = RSSᵀRᵀ (Decomposed into Rotation R + Scale S); Differentiable Tile-Based Rasterizer
  - ▸ *CG use:* Real-time novel view synthesis at 1080p 30+ FPS; quality matching or exceeding NeRF; training in minutes
- 2.6.1.2 Adaptive Density Control: Clone (Small Gradients + Small Gaussians → Fill Under-Reconstructed Regions); Split (Large Gradients + Large Gaussians → Split into Two Smaller)
  - ▸ *CG use:* Automatic geometric detail level; fewer Gaussians on smooth surfaces, many on detailed regions
- 2.6.1.3 3DGS as Geometry Representation: Each Gaussian is a 3D Position + Covariance (Oriented Ellipsoid) + Opacity + Spherical Harmonics Color (48 coeffs)
  - ▸ *CG use:* Explicit geometry unlike NeRF — can extract point clouds, meshes; editable in 3D software
- 2.6.1.4 SuGaR (Guédon & Lepetit 2023): Extract Mesh from 3DGS via Poisson Reconstruction on Gaussian-Aligned Points; Regularization for Flat Gaussians on Surface
  - ▸ *CG use:* Convert Gaussian splats to standard meshes for traditional rendering pipelines; texture baking

#### 2.6.2 3DGS Variants & Extensions
- 2.6.2.1 2D Gaussian Splatting (Huang et al. SIGGRAPH 2024): "Flat" Gaussians (Surfels) — One Dimension Collapsed; Better Surface Normal Reconstruction; SDF Extraction
  - ▸ *CG use:* Superior geometry recovery; direct normal map rendering; multi-view stereo quality
- 2.6.2.2 Dynamic 3DGS: 4D Gaussian Splatting (Luiten et al. 2024) — Time-Varying Position + Rotation + SH; Deformable 3DGS (Yang et al. 2024) — MLP Predicts Per-Frame Deformation
  - ▸ *CG use:* Real-time dynamic scene rendering from multi-view video; sports replay; volumetric video
- 2.6.2.3 Compact/Compressed 3DGS: Scalar Quantization + Entropy Coding (Niedermayr et al. 2024); LightGaussian; EAGLES (Efficient 3DGS)
  - ▸ *CG use:* Streaming 3DGS on web/mobile; 10-50× compression with minimal quality loss
- 2.6.2.4 SLAM with 3DGS: GS-SLAM; SplaTAM; MonoGS (Single RGB Camera!)
  - ▸ *CG use:* Real-time dense 3D reconstruction from moving camera; AR/VR mapping; robot navigation

#### 2.6.3 Traditional Point-Based Graphics
- 2.6.3.1 Point Splatting (Grossman & Dally 1998; Zwicker et al. 2001): Render Points as Elliptical Discs; EWA (Elliptical Weighted Average) Filtering for Anti-Aliasing; Surfels (Surface Elements = Point + Normal + Radius)
  - ▸ *CG use:* QSplat (Rusinkiewicz & Levoy 2000) — Progressive point-based rendering for large models; historical significance
- 2.6.3.2 Point Set Surfaces (Alexa et al. 2001): MLS Surface Definition from Points; Polynomial Fit in Local Neighborhood → Projection Operator
  - ▸ *CG use:* Smooth surface definition from noisy LiDAR scans without meshing; denoising by MLS projection
- 2.6.3.3 Point Cloud Registration Classic: ICP (Iterative Closest Point — Besl & McKay 1992); Variants: Point-to-Point (Classic), Point-to-Plane (Faster Convergence), Generalized ICP (Segal et al. 2009 — Probabilistic Framework)
  - ▸ *CG use:* Scan alignment for 3D reconstruction; SLAM loop closure; multi-sensor calibration

> 📚 **GitHub Repos:**
> - [graphdeco-inria/gaussian-splatting](https://github.com/graphdeco-inria/gaussian-splatting) ![Stars](https://img.shields.io/github/stars/graphdeco-inria/gaussian-splatting?style=flat) — Original 3DGS (the reference implementation)
> - [nerfstudio-project/nerfstudio](https://github.com/nerfstudio-project/nerfstudio) ![Stars](https://img.shields.io/github/stars/nerfstudio-project/nerfstudio?style=flat) — Unified NeRF/3DGS training framework
> - [PointCloudLibrary/pcl](https://github.com/PointCloudLibrary/pcl) ![Stars](https://img.shields.io/github/stars/PointCloudLibrary/pcl?style=flat) — Comprehensive point cloud processing library
>
> 📖 **Textbooks:** *Point-Based Graphics* — Gross & Pfister (The classic reference); 3DGS related: Read Kerbl et al. SIGGRAPH 2023 paper directly

---

### 2.7 Voxels, Grids & Discrete Representations

#### 2.7.1 Voxel Data Structures
- 2.7.1.1 Uniform Grid: Simple 3D Array of Values; O(n³) Memory; Direct Index Access; GPU-Friendly (3D Texture)
  - ▸ *CG use:* GPU-based fluid simulation (MAC grid); medical CT/MRI volume rendering; SDF storage for collision queries
- 2.7.1.2 Sparse Voxel Octree (SVO): 8-Child Pointer Tree; Only Refine Non-Empty Regions; Memory = O(surface_area × log resolution) Instead of O(volume); Morton Code Linearization
  - ▸ *CG use:* UE5 sparse volume textures; NVIDIA GVDB; high-resolution SDF representation; voxel cone tracing GI
- 2.7.1.3 OpenVDB (DreamWorks, now Academy Software Foundation): Hierarchical Grid of Blocks (Typically 8³ Voxels); B+ Tree Structure on Blocks; Fast Random Access + Iteration + Sparse Storage
  - ▸ *CG use:* Film-quality volumetric effects (smoke, fire, clouds) in all major VFX studios; level set fluid simulation; geometry processing
- 2.7.1.4 Clipmaps (Tanner et al. 1998): Mipmap of Nested Toroidal Grids; Coarser Levels Cover Larger Area; Updates Only at Boundary; Virtual Texture Analogy for Geometry
  - ▸ *CG use:* Large terrain heightfield rendering; GPU geometry clipmaps (Hoppe 2004); planetary-scale rendering

#### 2.7.2 Volume Representations & Applications
- 2.7.2.1 Adaptively Sampled Distance Fields (ADFs — Frisken et al. 2000): K-d Tree Subdivision of Distance Field; Finer Subdivision Near Surface; C⁰ Discontinuities at Cell Boundaries (Refined)
  - ▸ *CG use:* Font representation (character SDF stored as ADF); collision detection acceleration
- 2.7.2.2 VDB File Format & Tools: NanoVDB (GPU-Optimized, Header-Only C++ Library); OpenVDB Points (Particle Storage); OpenVDB AX (Expression Language for Volume Processing)
  - ▸ *CG use:* Houdini volume exchange; Arnold/Mantra/RenderMan volume rendering; Universal Scene Description volume binding
- 2.7.2.3 Signed Distance Field Voxelization: Windowing Number for Robust Inside/Outside; Sweep Algorithm; GPU Parallel (Atomic Min for Distance); Multi-Pass Refinement
  - ▸ *CG use:* Ray-traced soft shadows (UE5 distance field shadows); SDF-based ambient occlusion; conservative collision detection

> 📚 **GitHub Repos:**
> - [AcademySoftwareFoundation/openvdb](https://github.com/AcademySoftwareFoundation/openvdb) ![Stars](https://img.shields.io/github/stars/AcademySoftwareFoundation/openvdb?style=flat) — Industry-standard sparse volume library
> - [NVIDIAGameWorks/nanovdb](https://github.com/NVIDIAGameWorks/nanovdb) ![Stars](https://img.shields.io/github/stars/NVIDIAGameWorks/nanovdb?style=flat) — GPU-optimized VDB subset (header-only)
>
> 📖 **Textbooks:** *Fluid Simulation for Computer Graphics* — Bridson (Voxel/Particle methods); *OpenVDB Cookbook* — online documentation

---

### 2.8 Constructive Solid Geometry (CSG)

#### 2.8.1 CSG Foundations
- 2.8.1.1 CSG Tree: Binary Tree of Boolean Operations on Solid Primitives; Each Leaf = Primitive (Cube, Sphere, Cylinder, Cone, Torus, Extrusion); Each Internal Node = Boolean Op (∪, ∩, \, Δ); Root = Final Solid
  - ▸ *CG use:* CAD modeling paradigm (SolidWorks feature tree); rapid prototyping of mechanical parts; real-time CSG via SDF in Shadertoy
- 2.8.1.2 Boundary Evaluation: Convert CSG Tree to B-Rep (Boundary Representation); Classify Each Primitive Face Against Other Primitives (Inside/Outside/On); Compute Intersection Curves; Trim and Sew Faces
  - ▸ *CG use:* CAD kernel core operation (Parasolid, ACIS); manufacturing-format export (STEP, IGES from CSG)
- 2.8.1.3 Point Membership Classification (PMC): For Any Point x, Determine if x is IN, OUT, or ON the CSG Solid; Recursive Evaluation Down CSG Tree; Ray Casting Method (Count Intersections)
  - ▸ *CG use:* Collision detection with complex assemblies; virtual machining simulation; 3D printing slicer

#### 2.8.2 CSG on Contemporary Representations
- 2.8.2.1 SDF CSG: Boolean Operations Exact on SDF (min/max Operations); Smooth Blend via Polynomial Smooth Minimum (Quilez); Multiple Material IDs via Composed Fields
  - ▸ *CG use:* Real-time CSG rendering via ray marching; Shadertoy demoscene art; procedural game level generation
- 2.8.2.2 Mesh CSG: Triangle Mesh Boolean via BSP-Assisted Computation; Robustness Challenges (Coplanar Faces, Near-Degenerate Intersections); Exact Arithmetic Solutions (CGAL Nef Polyhedra)
  - ▸ *CG use:* 3D modeling software Boolean tools (Blender Boolean modifier); digital sculpting boolean operations
- 2.8.2.3 Hybrid SDF-Mesh CSG: Convert Mesh to SDF → Perform SDF Boolean → Marching Cubes Back to Mesh; Loss of Sharp Features Without Dual Contouring
  - ▸ *CG use:* Robust Boolean for 3D printing mesh repair; game engine procedural destruction (subtract sphere SDF from building mesh)

> 📚 **GitHub Repos:**
> - [elalish/manifold](https://github.com/elalish/manifold) ![Stars](https://img.shields.io/github/stars/elalish/manifold?style=flat) — Fast, robust mesh Boolean library (3D printing focused)
> - [CGAL/cgal](https://github.com/CGAL/cgal) ![Stars](https://img.shields.io/github/stars/CGAL/cgal?style=flat) — Nef Polyhedra for exact CSG
>
> 📖 **Textbooks:** *Geometric and Solid Modeling* — Christoph Hoffmann; *An Introduction to Solid Modeling* — Mäntylä

---

### 2.9 Procedural & Generative Modeling

#### 2.9.1 Noise Functions — The Building Blocks of Proceduralism
- 2.9.1.1 Perlin Noise (1985, Academy Award 1997): Lattice Gradient Noise; Smoothstep Interpolation; Octave Summation → fBm
  - ▸ *CG use:* Texturing (marble, wood, clouds); terrain height generation; vertex displacement for organic surfaces
- 2.9.1.2 Simplex Noise (Perlin 2001): Lower Computational Complexity in High Dimensions (O(n²) vs Perlin's O(2^n)); No Directional Artifacts; Improved Gradient Distribution
  - ▸ *CG use:* GPU-efficient noise (fewer samples per dimension); 3D/4D noise for animated textures
- 2.9.1.3 Worley (Voronoi/Cellular) Noise (1996): Distance to Nearest Feature Point; Closest (F1), Second-Closest (F2); Domain Warping of Feature Points
  - ▸ *CG use:* Stone/crack textures; cell-like organic patterns; water caustics approximation; Gabor noise for anisotropic textures
- 2.9.1.4 Curl Noise (Bridson et al. 2007): ∇ × (Vector Noise Field); Guaranteed Divergence-Free; Incompressible Flow Approximation
  - ▸ *CG use:* Fluid velocity fields for cheap smoke/fire simulation; particle advection in games; hair/wind motion

#### 2.9.2 Grammar-Based & Structural Modeling
- 2.9.2.1 L-Systems (Lindenmayer 1968): Parallel String Rewriting System; Turtle Graphics Interpretation (Move, Rotate, Push/Pop); Stochastic, Parametric, Context-Sensitive Extensions
  - ▸ *CG use:* Plant and tree generation (SpeedTree, XFrog); fractal modeling; biological structure simulation
- 2.9.2.2 Shape Grammars (Stiny & Gips 1971): Replacement Rules on Labeled Shapes; Subdivision-Based Derivation; Parameterized for Variation
  - ▸ *CG use:* Procedural architecture (CityEngine — entire cities from rules); building facade generation; video game level generation
- 2.9.2.3 Wave Function Collapse (WFC — Gumin 2016): Constraint Satisfaction via Tile Adjacency Rules; Superposition → Observation → Propagation Cycle; Produces Locally-Similar Output to Exemplar
  - ▸ *CG use:* Texture synthesis with structural constraints (platformer level tiles); procedural building interiors; map generation (Caves of Qud, Townscaper)
- 2.9.2.4 Diffusion-Limited Aggregation (DLA): Random Walkers Stick on Contact; Generates Fractal Tree/Coral-Like Structures
  - ▸ *CG use:* Lightning bolt generation; dendritic crystal growth; frost/ice pattern synthesis

#### 2.9.3 Terrain & Landscape Generation
- 2.9.3.1 Fractal Terrain: Diamond-Square (Midpoint Displacement) Algorithm; fBm Heightfield = Σ octavesⁿ × noise(2ⁱ x, 2ⁱ y); Erosion Simulation (Hydraulic + Thermal)
  - ▸ *CG use:* Game terrain generation (Minecraft, Horizon Zero Dawn); film landscape creation; flight simulator terrain
- 2.9.3.2 Particle-Based Erosion: SPH-Style Water Particles Advect Over Heightfield; Dissolve, Transport, Deposit Sediment; Realistic Ridge/Crater Formation
  - ▸ *CG use:* High-quality terrain for offline rendering; World Machine, Gaea, Houdini Heightfield Erode
- 2.9.3.3 Data-Driven Terrain: Train GAN/Diffusion Model on Real DEM (Digital Elevation Model) Data; Generate Realistic Novel Heightfields; Control via Sketch + Elevation Constraints
  - ▸ *CG use:* Infinite realistic game worlds; film environment generation; geographic training data augmentation

> 📚 **GitHub Repos:**
> - [Auburn/FastNoise2](https://github.com/Auburn/FastNoise2) ![Stars](https://img.shields.io/github/stars/Auburn/FastNoise2?style=flat) — High-performance noise generation library (SIMD-optimized)
> - [mxgmn/WaveFunctionCollapse](https://github.com/mxgmn/WaveFunctionCollapse) ![Stars](https://img.shields.io/github/stars/mxgmn/WaveFunctionCollapse?style=flat) — Reference WFC implementation
>
> 📖 **Textbooks:** *Texturing and Modeling: A Procedural Approach* — Ebert, Musgrave, Peachey, Perlin, Worley (The procedural bible); *The Algorithmic Beauty of Plants* — Prusinkiewicz & Lindenmayer (Free online)

---

### 2.10 Data-Driven & AI-Powered Modeling

#### 2.10.1 Acquisition-Based Modeling
- 2.10.1.1 Photogrammetry Pipeline: Image Capture → Feature Extraction (SIFT) → Feature Matching → SfM (COLMAP) → Dense MVS (PMVS/PatchMatch) → Depth Fusion → Mesh Extraction → Texture Projection
  - ▸ *CG use:* Reality capture for VFX (environments, props); cultural heritage digitization; game asset creation from real objects (Quixel Megascans)
- 2.10.1.2 Depth Sensor Fusion: TSDF Volume (Curless & Levoy 1996) — Weighted Running Average of Signed Distance; KinectFusion (Newcombe et al. 2011) — Real-Time GPU TSDF
  - ▸ *CG use:* Real-time 3D scanning; AR occlusion and physics; robot environment mapping
- 2.10.1.3 Semantic & Instance Segmentation for Modeling: PointNet/PointerNet for Per-Point Classification; Mask3D/PartNet for Part Decomposition; 3D Scene Graph Construction
  - ▸ *CG use:* Scan-to-BIM (Building Information Modeling); autonomous vehicle HD map generation; digital twin creation

#### 2.10.2 AI-Generated 3D Content (3D AIGC)
- 2.10.2.1 Text-to-3D via Score Distillation: DreamFusion (Poole et al. 2022) — SDS Loss ∇_θ = 𝔼[w(t)(ϵ̂−ϵ)∂x/∂θ] Using Frozen 2D Diffusion; ProlificDreamer (Wang et al. 2023) — VSD for Improved Quality and Diversity
  - ▸ *CG use:* Rapid 3D prototyping from text prompts; game asset ideation; creative concept exploration
- 2.10.2.2 Image-to-3D (Feed-Forward): Large Reconstruction Models (LRM — Hong et al. 2024): Transformer Predicts Triplane NeRF/3DGS from Single Image in < 5 Seconds; Instant3D, LGM, GRM, CRM
  - ▸ *CG use:* E-commerce 3D from product photos; game asset from concept art; real-time AR content creation from camera
- 2.10.2.3 Multi-View Diffusion for 3D: Zero123 (Liu et al. 2023) — View-Conditioned Diffusion; MVDream (Shi et al. 2024) — Multi-View Consistent Generation; SyncDreamer — Simultaneous Novel View Synthesis
  - ▸ *CG use:* Consistent multi-view images for reconstruction; reduced 3D generation failures (Janus/multi-face problem)
- 2.10.2.4 3D Generative Models: 3D GANs (EG3D, GET3D); Diffusion on Latent 3D Representations (DiffTF, NFD); Autoregressive Mesh Generation (PolyGen, MeshGPT — Pre-Trained Transformer Generates Triangle Meshes Token-by-Token)
  - ▸ *CG use:* Direct 3D asset generation; style-controllable shape synthesis; game content population

#### 2.10.3 Learning-Based Geometry Processing
- 2.10.3.1 Neural Mesh Simplification: Train Neural Network to Predict Edge Collapse Priority/Cost; Generalizes Across Model Categories
  - ▸ *CG use:* Content-aware LOD generation (preserve eyes on face, ignore flat back of head); streaming-optimized simplification
- 2.10.3.2 Point Cloud Upsampling: PU-Net, PU-GCN, PU-GAN — Learn to Generate Dense Uniform Points from Sparse Input; Feature-Aware Sampling
  - ▸ *CG use:* LiDAR scan enhancement; low-cost depth sensor quality improvement; scan-to-print pipeline
- 2.10.3.3 Shape Completion: PointTr (Transformer for Point Completion); PCN (Point Completion Network); Diffusion-Based Completion (Conditional DDPM on Partial Scans)
  - ▸ *CG use:* 3D scanning hole filling; robotic grasp planning on partial views; archaeological fragment reconstruction

> 📚 **GitHub Repos:**
> - [openai/shap-e](https://github.com/openai/shap-e) ![Stars](https://img.shields.io/github/stars/openai/shap-e?style=flat) — OpenAI text/image-to-3D generative model
> - [threestudio-project/threestudio](https://github.com/threestudio-project/threestudio) ![Stars](https://img.shields.io/github/stars/threestudio-project/threestudio?style=flat) — Unified text-to-3D framework (DreamFusion, MVDream, ProlificDreamer)
> - [autonomousvision/mipnerf](https://github.com/google/mipnerf) ![Stars](https://img.shields.io/github/stars/google/mipnerf?style=flat) — Anti-aliased NeRF for multi-scale reconstruction
>
> 📖 **Textbooks:** *Deep Learning for 3D Data* — survey papers; area moves fast — follow SIGGRAPH/NeurIPS proceedings

---

### 2.11 Scene Graphs & Hierarchical Organization

#### 2.11.1 Scene Graph Architecture
- 2.11.1.1 Tree-Structured Transform Hierarchy: Parent → Child Spatial Relationship; Local Transform (Relative to Parent) + Global Transform (Concatenated from Root)
  - ▸ *CG use:* Every game engine and DCC tool uses scene graphs for object organization; transform dirty-flag propagation
- 2.11.1.2 Entity-Component-System (ECS): Entity = ID; Component = Data (Transform, Mesh, Material); System = Logic (RenderSystem, PhysicsSystem); Cache-Friendly Contiguous Component Storage (Archetype/Chunk-Based)
  - ▸ *CG use:* Unity DOTS; Unreal Mass Entity; high-performance game object management (10K+ entities); data-oriented design
- 2.11.1.3 Spatial Partitioning in Scene Graphs: BVH per-Node; Octree/K-d Tree Scene Subdivision; Portal/Cell Systems for Indoor; Occlusion Query-Driven Dynamic Structure Updates
  - ▸ *CG use:* Culling efficiency — transform scene graph spatial queries from O(n) to O(log n); GPU-driven culling with draw-indirect

#### 2.11.2 Level of Detail (LOD) Systems
- 2.11.2.1 Discrete LOD: Precompute Meshes at Multiple Resolutions; Switch at Distance/Pixel-Size Thresholds; Geomorph Transitions (Vertex Morphing Between LODs)
  - ▸ *CG use:* GPU instancing with per-instance LOD selection; CPU or GPU (mesh shader) driven
- 2.11.2.2 Continuous LOD (CLOD): Progressive Meshes (Hoppe 1996) — Any Resolution via Edge Collapse/Split Sequence; View-Dependent Refinement (Hoppe 1997) — Finer Near Silhouette, Coarser in Distance
  - ▸ *CG use:* Terrain rendering (ROAM, GeoMipMaps); large CAD model visualization; mesh streaming over network
- 2.11.2.3 Virtual Geometry (Nanite — UE5): Software Rasterizer for Micro-Triangles; Hierarchical LOD Cluster Tree (Group Triangles → Simplify → Group → Simplify...); On-Demand Streaming from Disk
  - ▸ *CG use:* Film-quality assets directly in-game without manual LOD creation; automatic geometric LOD; pixel-sized triangle culling
- 2.11.2.4 Impostors & Billboard Clouds: Render Complex Object to Texture → Display as Camera-Facing Billboard; Refresh When Camera Moves Significantly; Octahedral Impostor Mapping
  - ▸ *CG use:* Distant trees/crowds in games; VR performance optimization; mobile rendering complexity reduction

#### 2.11.3 Large-Scale World Management
- 2.11.3.1 World Streaming: Tile-Based World Partition; Load/Unload Based on Camera Proximity; Priority-Based Async Loading; Precomputed Visibility Data (PVS)
  - ▸ *CG use:* Open-world games (GTA, Zelda BotW, Horizon); UE5 World Partition system; seamless player experience
- 2.11.3.2 Floating-Point Precision Handling: 32-bit Float = ~7 Digits → 1mm Precision at 10km Distance; Camera-Relative Rendering (Origin at Camera); Double Precision for Simulation; Multi-Origin (Floating Origin Shift)
  - ▸ *CG use:* Kerbal Space Program, Star Citizen (planet-to-space transitions); large-scale open world rendering
- 2.11.3.3 USD Composition (Pixar USD): Layers (SubLayer, Reference, Payload); Variant Sets (Switch Between Asset Variants); Inherits/Specializes; Opinions (Strongest Wins); Composition Arcs (Non-Destructive Overrides)
  - ▸ *CG use:* VFX pipeline collaboration (hundreds of artists on same shot); game engine interchange (UE5, Unity USD plug-in); NVIDIA Omniverse

> 📚 **GitHub Repos:**
> - [PixarAnimationStudios/USD](https://github.com/PixarAnimationStudios/USD) ![Stars](https://img.shields.io/github/stars/PixarAnimationStudios/USD?style=flat) — Universal Scene Description (the industry standard)
> - [AcademySoftwareFoundation/MaterialX](https://github.com/AcademySoftwareFoundation/MaterialX) ![Stars](https://img.shields.io/github/stars/AcademySoftwareFoundation/MaterialX?style=flat) — Standard material definition (companion to USD)
>
> 📖 **Textbooks:** *Game Engine Architecture* — Jason Gregory (Ch. 12-13 on scene management, streaming); *Real-Time Rendering* — Akenine-Möller et al. (Ch. 14 on acceleration algorithms)

---

### 2.12 Spatial Data Structures for Geometry Query

#### 2.12.1 Hierarchical Spatial Indices
- 2.12.1.1 Bounding Volume Hierarchy (BVH) — Geometry Perspective: Construction Strategies (SAH, Binned SAH, LBVH on GPU); Bottom-Up vs. Top-Down; Refit for Animated Geometry; Wide BVH (SIMD-Friendly)
  - ▸ *CG use:* Ray tracing acceleration for complex geometry; collision detection broad phase; frustum culling; nearest neighbor for mesh processing
- 2.12.1.2 k-d Trees for Geometry: Axis-Aligned Space Partition; Split at Object Medians for Balanced Tree; Nearest Neighbor & Range Search in O(log n); Ray Intersection
  - ▸ *CG use:* Photon mapping (photon kd-tree); point cloud nearest-neighbor queries; ICP correspondence search
- 2.12.1.3 Octrees & Quadtrees (Geometric Applications): Recursive 8/4-Way Subdivision; Adaptive Depth (Refine Where Data Exists); Morton (Z-Order) Codes for Linear Storage
  - ▸ *CG use:* Sparse voxel grids (OpenVDB); GPU particle neighbor search; adaptive distance field storage; frustum culling

#### 2.12.2 Proximity & Neighborhood Queries
- 2.12.2.1 Nearest Neighbor Search: k-d Tree (Exact, O(log n) Average), HNSW (Approximate, Graph-Based, State-of-the-Art Speed/Recall Trade-off), LSH (Locality Sensitive Hashing — Sublinear for High Dimensions)
  - ▸ *CG use:* Point cloud registration (nearest neighbor correspondence); texture synthesis (patch matching); geometry repair (nearest valid vertex)
- 2.12.2.2 Range Search & Radius Queries: Fixed-Radius Near Neighbors (FRNN); SPH Kernel Support Radius Query; BVH/Grid Acceleration
  - ▸ *CG use:* Fluid simulation neighbor search (SPH kernel radius); collision detection (check only nearby objects); mesh smoothing (vertex neighborhood)
- 2.12.2.3 Spatial Joins & Self-Collision Detection: Bounding Volume Traversal Tree (BVTT) for Pairwise Proximity; Sweep-and-Prune (Sort and Sweep) for AABB Overlap Pairs
  - ▸ *CG use:* Cloth self-collision detection; deformable body contact resolution; multi-body physics broad phase

#### 2.12.3 GPU-Accelerated Spatial Query
- 2.12.3.1 GPU BVH Construction (PLOC, LBVH): Morton Code Sort + Hierarchy Extraction → O(n log n) on GPU; HLBVH (Hybrid: Top-Level LBVH + Per-Leaf SAH); PLOC (Parallel Locally-Ordered Clustering)
  - ▸ *CG use:* Real-time ray tracing BVH builds for dynamic geometry (DXR/Vulkan RT — TLAS/BLAS two-level model)
- 2.12.3.2 Spatial Hashing on GPU: Infinite Grid Hash; Lock-Free Concurrent Insertion via Atomic CAS; Spatial Coherence Exploitation
  - ▸ *CG use:* Instant NGP multi-resolution hash; GPU particle simulation (neighbor lists); real-time cloth self-collision
- 2.12.3.3 Learned Spatial Indices: Neural Network as Bounding Volume; Occupancy/SDF Proxy for Conservative Culling; Reinforcement Learning for Traversal Policy
  - ▸ *CG use:* Next-gen ray tracing acceleration (neural BVH research — SIGGRAPH 2024); learned LOD selection

> 📚 **GitHub Repos:**
> - [embree/embree](https://github.com/embree/embree) ![Stars](https://img.shields.io/github/stars/embree/embree?style=flat) — World-class BVH construction and traversal kernels
> - [nmslib/hnswlib](https://github.com/nmslib/hnswlib) ![Stars](https://img.shields.io/github/stars/nmslib/hnswlib?style=flat) — Fast approximate nearest neighbor (HNSW)
> - [CGAL/cgal](https://github.com/CGAL/cgal) ![Stars](https://img.shields.io/github/stars/CGAL/cgal?style=flat) — k-d tree, octree, AABB tree spatial searching
>
> 📖 **Textbooks:** *Real-Time Collision Detection* — Christer Ericson (Essential spatial structures for games); *Foundations of Multidimensional and Metric Data Structures* — Hanan Samet (Exhaustive reference)

---


## Chapter 3 · Appearance, Materials & Textures

*How light interacts with matter — the complete theory of surface and volume appearance. From classical radiometry to neural materials. `▸ CG use:` links each concept to practice.*

> 💡 **Top-Level References:**
> - [PBR Book v4 (Free Online)](https://pbr-book.org/) — Definitive reference for physically-based appearance and light transport
> - [google/filament](https://github.com/google/filament) ![Stars](https://img.shields.io/github/stars/google/filament?style=flat) — Production PBR material system with detailed documentation
> - [AcademySoftwareFoundation/MaterialX](https://github.com/AcademySoftwareFoundation/MaterialX) ![Stars](https://img.shields.io/github/stars/AcademySoftwareFoundation/MaterialX?style=flat) — Industry-standard material definition and interchange

---

### 3.1 Radiometry & Light Measurement

#### 3.1.1 Fundamental Radiometric Quantities
- 3.1.1.1 Radiant Flux (Power) Φ [W = J/s]: Total Energy Emitted/Received Per Second by a Light Source or Surface
  - ▸ *CG use:* Light source power specification (e.g., "100W incandescent bulb"); total energy budget in light transport
- 3.1.1.2 Irradiance E = dΦ/dA [W/m²]: Radiant Flux Incident Per Unit Surface Area; Radiosity B = dΦ_out/dA: Flux Exiting Per Unit Area
  - ▸ *CG use:* Light map values stored as irradiance; diffuse surface response is proportional to irradiance; sensor pixel response
- 3.1.1.3 Radiant Intensity I = dΦ/dω [W/sr]: Flux Per Unit Solid Angle (Point Source Approximation); Isotropic Point Source: I = Φ/(4π)
  - ▸ *CG use:* Point light intensity specification; IES profile-based light sources in architectural rendering
- 3.1.1.4 Radiance L = d²Φ/(dA⊥ dω) [W/(m²·sr)]: THE Central Quantity — Flux Per Unit Projected Area Per Unit Solid Angle; Invariant Along Ray in Vacuum
  - ▸ *CG use:* Every light transport quantity is radiance; what cameras measure; what displays emit; what the rendering equation solves for
- 3.1.1.5 Spectral Radiometry: Per-Wavelength Quantities L_λ, Φ_λ; Color Matching Functions Convert Spectrum → RGB; Spectral Rendering vs. RGB Rendering
  - ▸ *CG use:* Spectral rendering for accurate dispersion (prisms, rainbows), fluorescence, and metamerism; RGB rendering is a 3-sample approximation

#### 3.1.2 Measurement & Units in Practice
- 3.1.2.1 Photometric Units (Human-Visual-System-Weighted): Luminous Flux (Lumen lm), Illuminance (Lux lx = lm/m²), Luminance (cd/m² = nit)
  - ▸ *CG use:* Display brightness specification (500 nits SDR, 1000+ nits HDR); architectural lighting standards (500 lux for office)
- 3.1.2.2 Solid Angle: dω = dA/r² = sin θ dθ dφ; Projected Solid Angle dω⊥ = cos θ dω; Integrals Over Hemisphere ∫_{H²} dω = 2π, ∫_{H²} cos θ dω = π
  - ▸ *CG use:* BRDF integration; irradiance from environment map = ∫ L_i cos θ dω; normalization constants in shading models
- 3.1.2.3 Radiometric Image Formation: Pixel Value ∝ ∫_{Pixel} ∫_{Exposure} L(x,ω,t) · W(x,ω,t) dω dt dA; Camera Response Function (CRF) Maps Irradiance → Pixel Value
  - ▸ *CG use:* HDR capture (recover L from pixel values via inverse CRF); physically-based camera model in rendering

> 📚 **GitHub Repos:**
> - [PBR Book v4](https://pbr-book.org/) — Complete radiometry chapter with interactive visualizations
> - [colour-science/colour](https://github.com/colour-science/colour) ![Stars](https://img.shields.io/github/stars/colour-science/colour?style=flat) — Spectral-to-RGB conversion, illuminants, CMFs
>
> 📖 **Textbooks:** *Physically Based Rendering* — Pharr, Jakob, Humphreys (Ch. 5: Color and Radiometry); *Principles of Digital Image Synthesis* — Andrew Glassner

---

### 3.2 BRDF Theory & Microfacet Models

#### 3.2.1 BRDF Fundamentals
- 3.2.1.1 BRDF Definition f_r(ω_i, ω_o) = dL_o(ω_o) / dE_i(ω_i) = dL_o(ω_o) / (L_i(ω_i) cos θ_i dω_i) [sr⁻¹]; BRDF Relates Incoming Irradiance to Outgoing Radiance
  - ▸ *CG use:* The core abstraction for surface appearance; every shading operation evaluates f_r for given light and view directions
- 3.2.1.2 Physical Plausibility Requirements: Non-Negativity f_r ≥ 0; Helmholtz Reciprocity f_r(ω_i,ω_o) = f_r(ω_o,ω_i); Energy Conservation ∫_{H²} f_r(ω_i,ω_o) cos θ_o dω_o ≤ 1 ∀ ω_i
  - ▸ *CG use:* Energy-conserving BRDFs prevent unnaturally bright surfaces; reciprocity enables bidirectional path tracing
- 3.2.1.3 Isotropic vs. Anisotropic: Isotropic: f_r(θ_i,φ_i,θ_o,φ_o) = f_r(θ_i,θ_o,|φ_i−φ_o|) (Depends Only on Relative Azimuth); Anisotropic: Depends on Absolute Orientation
  - ▸ *CG use:* Brushed metal, hair, carbon fiber → anisotropic BRDF with tangent-direction-dependent roughness
- 3.2.1.4 BRDF Parameterization: Rusinkiewicz Coordinates (Half-Angle θ_h, φ_h + Difference θ_d, φ_d) vs. Standard (θ_i,φ_i,θ_o,φ_o); Factorized BRDFs
  - ▸ *CG use:* Rusinkiewicz parameterization reveals BRDF structure; better for analysis, measurement, and compression

#### 3.2.2 Diffuse & Simple Models
- 3.2.2.1 Lambertian BRDF: f_r = ρ/π (Constant, Perfectly Diffuse); Reflectance ρ = ∫ f_r cos θ_o dω_o ∈ [0,1]; Albedo = ρ; Radiosity L_o = (ρ/π) ∫_{H²} L_i cos θ_i dω_i = ρ E/π
  - ▸ *CG use:* The default diffuse model; simplest form of energy conservation; albedo texture maps directly usable
- 3.2.2.2 Oren-Nayar (1994): Rough Diffuse Model; Microfacet Diffuse (V-Cavities with Lambertian Walls); Accounts for View-Dependent Darkening at Grazing Angles; Parameter: Surface Roughness σ
  - ▸ *CG use:* Moon surface rendering (no specular → all roughness effect); clay, sand, rough paper; Mars rover image calibration
- 3.2.2.3 Disney Diffuse (Burley 2012): Empirical Model with Fresnel-Inspired Falloff; f_diffuse = (ρ/π)(1+(F_D90−1)(1−cos θ_i)⁵)(1+(F_D90−1)(1−cos θ_o)⁵) with F_D90 = 0.5+2α cos²θ_d
  - ▸ *CG use:* Part of the Disney Principled BSDF; smooth transition between diffuse at normal and retro-reflective at grazing

#### 3.2.3 Microfacet Theory — The Modern Standard
- 3.2.3.1 Microfacet BRDF: f_r = F(ω_i·ω_h) · D(ω_h) · G(ω_i,ω_o) / (4 |ω_i·n| |ω_o·n|); F = Fresnel, D = NDF, G = Geometry; Derivation via Distribution of Visible Normals (VNDF)
  - ▸ *CG use:* Cook-Torrance (1981) introduced this; the dominant model for all modern PBR pipelines
- 3.2.3.2 Normal Distribution Function (NDF) D(ω_h): Statistical Distribution of Microfacet Normals; Must Satisfy ∫_{H²} D(ω_h) cos θ_h dω_h = 1 (Projected Area Normalization)
  - Beckmann: D(θ_h) = exp(−tan²θ_h/α²) / (π α² cos⁴ θ_h) — Gaussian Slope Distribution
  - GGX / Trowbridge-Reitz: D(θ_h) = α² / (π cos⁴ θ_h (α²+tan²θ_h)²) — Longer Tail (Hyperbolic Distribution); Better Matches Real-World Materials!
  - GTR (Generalized Trowbridge-Reitz): D = c / ((α² cos²θ_h+sin²θ_h)^γ); γ Controls Tail Falloff; GGX = GTR(γ=2), Beckmann ≈ GTR(γ→∞)
  - ▸ *CG use:* GGX is the de-facto standard NDF in games and film; captures the "glow" around specular highlights better than Beckmann
- 3.2.3.3 Shadowing-Masking (Geometry) Function G(ω_i,ω_o): Accounts for Microfacet Self-Occlusion; Must Be ≤1 and Satisfy Reciprocity
  - Smith G: G(ω) = 1/(1+Λ(ω)) where Λ(ω) = ½(erf(a)−1+(a√π)⁻¹exp(−a²)), a = 1/(α tan θ); Height-Correlated Smith G₂(ω_i,ω_o) = χ⁺/(1+Λ(ω_i)+Λ(ω_o))
  - Heitz (2014): Demonstrated Height-Correlated G₂ is Essential for Accurate Energy Conservation; Separable G = G₁(ω_i)G₁(ω_o) Over-Darkens at Grazing
  - ▸ *CG use:* Always use height-correlated Smith G₂; separable G₁G₁ produces visible dark rings at silhouette (most engines corrected post-2014)
- 3.2.3.4 Fresnel Reflectance F(cos θ): Fraction of Light Reflected vs. Transmitted at Interface; Depends on Complex IOR η+ik
  - Full Fresnel (Polarized): r_∥ = (η₂ cos θ_i − η₁ cos θ_t)/(η₂ cos θ_i + η₁ cos θ_t); r_⊥ = (η₁ cos θ_i − η₂ cos θ_t)/(η₁ cos θ_i + η₂ cos θ_t); R = ½(r_∥²+r_⊥²)
  - Schlick Approximation (1994): F(θ) = F₀ + (1−F₀)(1−cos θ)⁵; F₀ = ((η₁−η₂)/(η₁+η₂))² (Normal Incidence)
  - ▸ *CG use:* Schlick is the dominant approximation in real-time; full Fresnel for offline (metals have complex η → colored F₀)
- 3.2.3.5 Multiple-Scattering Microfacet: Single-Scattering Microfacet Loses Energy at High Roughness (Darkening); Multi-Scatter Compensation via Precomputed LUT (Furnace Test → Energy-Preserving Normalization); Heitz et al. (2016) Stochastic Evaluation
  - ▸ *CG use:* UE5 and Filament use multi-scatter LUTs; roughness-dependent albedo scaling to recover lost energy

#### 3.2.4 Specialized BRDF Models
- 3.2.4.1 Ashikhmin-Shirley (2000): Anisotropic Phong-Based Microfacet; Explicit Anisotropy Parameters α_u, α_v (Perpendicular Roughness Directions)
  - ▸ *CG use:* Brushed metal rendering; anisotropic specular highlights on machined surfaces
- 3.2.4.2 Ward BRDF (1992): Gaussian Slope Distribution; Isotropic and Anisotropic Variants; Physically Plausible but Simpler than Full Microfacet
  - ▸ *CG use:* Historical significance; still used in some real-time applications for simplicity
- 3.2.4.3 Hair BSDF Models: Kajiya-Kay (1989) — Tangent-Space Specular Cylinder (Diffuse + Specular Scattering); Marschner et al. (2003) — Full 3D Scattering Model (R, TT, TRT Paths); d'Eon et al. (2011) — Energy-Conserving; Chiang et al. (2016) — Practical Implementation
  - ▸ *CG use:* Film-quality digital humans and creatures; game hair rendering (TressFX, HairWorks); Pixar's *Brave* and *Coco*

> 📚 **GitHub Repos:**
> - [google/filament](https://github.com/google/filament) ![Stars](https://img.shields.io/github/stars/google/filament?style=flat) — Production PBR: GGX, multi-scatter, clear coat, anisotropy
> - [brentburley/brdf](https://github.com/brentburley/brdf) — Disney Principled BRDF exploration and reference
>
> 📖 **Textbooks:** *Physically Based Rendering* — Pharr et al. (Ch. 8: Reflection Models); *Real-Time Rendering* — Akenine-Möller et al. (Ch. 9: Physically Based Shading)

---

### 3.3 BTDF, BSDF & Layered Materials

#### 3.3.1 Transmission & Refraction
- 3.3.1.1 Snell's Law: η₁ sin θ₁ = η₂ sin θ₂; Total Internal Reflection when η₁ sin θ₁/η₂ > 1 (θ₂ = arcsin > 90° → All Light Reflected); Critical Angle θ_c = arcsin(η₂/η₁)
  - ▸ *CG use:* Glass, water, gemstone rendering; TIR creates the bright edges in water droplets and diamond sparkle
- 3.3.1.2 BTDF (Bidirectional Transmission Distribution Function): f_t(ω_i,ω_o) = dL_o(ω_o) / dE_i(ω_i); Refracted Radiance Given Incident Irradiance; Fresnel Controls Transmission Amount F_T = 1−F_R
  - ▸ *CG use:* Dielectric BSDF = BRDF (Reflection) + BTDF (Transmission); glass, water, plastic all use BSDF
- 3.3.1.3 Microfacet BTDF (Walter et al. 2007): Same Microfacet Framework Extended to Transmission; Refracted Half-Vector ω_{ht} Follows Snell's Law; Modified Jacobian for Solid Angle Compression at Interface
  - ▸ *CG use:* Rough glass (frosted glass, ice); GGX BTDF for consistent roughness in both reflection and transmission

#### 3.3.2 Layered Material Models
- 3.3.2.1 Clear Coat Model: Base BRDF + Thin Transparent Layer on Top (Car Paint, Varnished Wood, Phone Screen); Second BRDF for Coating with Separate Fresnel + Absorption
  - ▸ *CG use:* UE5 Clear Coat shading model; automotive rendering (metallic base + clear gloss coat); Filament material model
- 3.3.2.2 Adding-Doubling Method (van de Hulst 1980): Exact Solution for Multiple Scattering in Layered Slabs; Propagate Scattering (S) and Transmission (T) Matrices Layer-by-Layer; Gold Standard for Layered Material Simulation
  - ▸ *CG use:* Skin rendering (epidermis + dermis layers); paint appearance; accurate thin-film interference stacks
- 3.3.2.3 Belcour (2018) Layered BSDF: Statistical Model via Random Walk in Layer; Shadowing-Masking Extended to Layer Interface; GPU-Friendly Approximation for Real-Time
  - ▸ *CG use:* Real-time layered material rendering; car paint with metallic flakes under clear coat
- 3.3.2.4 Thin-Film Interference: Wave Optics → Constructive/Destructive Interference at Thin Layers (Soap Bubbles, Oil Slicks, Insect Wings); Iridescence via Wavelength-Dependent Reflectance
  - ▸ *CG use:* Butterfly wing rendering; soap bubble shader; pearlescent car paint; beetle iridescence in photorealistic rendering

> 📚 **GitHub Repos:**
> - MaterialX Layered BSDF nodes — Standard layered material definition
> - [pbrt-v4](https://github.com/mmp/pbrt-v4) ![Stars](https://img.shields.io/github/stars/mmp/pbrt-v4?style=flat) — Full BSDF/BTDF implementation including layered models
>
> 📖 **Textbooks:** *Physically Based Rendering* — Pharr et al. (Ch. 9: Materials); *Real-Time Rendering* — Ch. 9

---

### 3.4 Subsurface Scattering & BSSRDF

#### 3.4.1 BSSRDF Theory
- 3.4.1.1 BSSRDF S(x_i,ω_i; x_o,ω_o): Generalization of BRDF; Light Enters at Point x_i, Scatters Inside, Exits at x_o ≠ x_i; Units [m⁻² sr⁻¹]
  - ▸ *CG use:* Skin, marble, milk, jade, wax — any material where light enters, bounces inside, and exits elsewhere
- 3.4.1.2 Radiative Transfer Equation (RTE) Inside Medium: (ω·∇)L(x,ω) = −σ_t L + σ_s ∫_{S²} p(ω,ω')L(x,ω') dω' + Q; Same as Volume Rendering but with Boundary Conditions
  - ▸ *CG use:* The full volumetric light transport equation; solved for accurate SSS via Monte Carlo or diffusion approximation
- 3.4.1.3 Diffusion Approximation: When σ_s ≫ σ_a (Scattering-Dominated) and Far from Source, Radiance ≈ Isotropic + Small Anisotropic Component; Reduces RTE to Poisson Equation ∇²φ − σ_a/D φ = −Q₀
  - ▸ *CG use:* Basis for real-time SSS models (dipole, multipole, directional dipole)

#### 3.4.2 Practical SSS Models
- 3.4.2.1 Dipole Model (Jensen et al. 2001): Place Positive (Real) and Negative (Virtual) Point Sources at z_r = 1/σ_t' and z_v = −(1+4A/3)/σ_t' Below Surface; Diffuse Reflectance Profile R_d(r) = Sum of Two Dipole Contributions
  - ▸ *CG use:* First practical real-time SSS (GPU Gems 3, Chapter 14); skin rendering breakthrough (Pixar's *Geri's Game*, *Finding Nemo*)
- 3.4.2.2 Multipole Model (Donner & Jensen 2005): Cylindrical Geometry Requires Infinite Sum of Dipole Reflections; More Accurate for Thin Objects (Ears, Fingers)
  - ▸ *CG use:* Accurate thin translucent geometry; ear and finger rendering in digital humans
- 3.4.2.3 Directional Dipole (Frisvad et al. 2007): Incorporate Directional Component; Better Near Light Entry Point; Bridge Between Dipole and Full Monte Carlo
  - ▸ *CG use:* Improved close-up skin rendering; light-source-dependent scattering direction
- 3.4.2.4 Texture-Space Diffusion (d'Eon et al. 2007, NVIDIA): Unwrap Mesh to Texture Space → Blur Irradiance Texture with Diffusion Profile (Gaussian Sum); → Look Up Blurred Value via UV → Screen-Space Rendering
  - ▸ *CG use:* Real-time skin rendering in games (Uncharted 4, Call of Duty); efficient GPU diffusion via separable Gaussian convolution in texture space
- 3.4.2.5 Burley Normalized Diffusion (Disney 2015): f(r) = (e^(−r/d) + e^(−r/(3d))) / (8π d r); Single Parameter d = Scattering Distance; Normalized to Unit Integral; Fitted to Monte Carlo Ground Truth
  - ▸ *CG use:* Disney Hyperion renderer; simple, artist-friendly, energy-conserving; adopted widely in production

#### 3.4.3 Path-Space BSSRDF & Advanced Models
- 3.4.3.1 Path Integral BSSRDF Formulation: Integrate Over All Subsurface Paths; Monte Carlo Sampling of Entry-Exit Point Pairs; Bidirectional Scattering Distribution Ray Tracing (BSSRDF Sampling)
  - ▸ *CG use:* Production rendering (Arnold, RenderMan, V-Ray) uses MC SSS; handles complex geometry and heterogeneous media
- 3.4.3.2 Quantized Diffusion (d'Eon & Irving 2011): Full Radiative Transfer Solution via Spectral Decomposition; Captures Anisotropy and Short-Path Effects Beyond Diffusion
  - ▸ *CG use:* Gold standard for skin appearance; accounts for both shallow (epidermal) and deep (dermal) scattering
- 3.4.3.3 Heterogeneous SSS via Neural Methods: Train Neural Network on MC-Reference to Predict SSS in Heterogeneous Media; NeRF-Style Volume → BSSRDF Representation
  - ▸ *CG use:* Next-gen digital humans with spatially-varying SSS (freckles, scars, tattoos with different scattering properties)

> 📚 **GitHub Repos:**
> - [PBR Book v4 SSS Chapter](https://pbr-book.org/4ed/Subsurface_Scattering) — Complete BSSRDF implementation
> - Filament SSS implementation — Real-time Burley diffusion
>
> 📖 **Textbooks:** *Physically Based Rendering* — Pharr et al. (Ch. 15: Subsurface Scattering); *Digital Modeling of Material Appearance* — Dorsey, Rushmeier, Sillion

---

### 3.5 Participating Media & Volumetric Appearance

#### 3.5.1 Optical Properties of Participating Media
- 3.5.1.1 Absorption Coefficient σ_a(x) [m⁻¹]: Probability of Photon Absorption Per Unit Distance; Determines Material Color (e.g., Red Wine Absorbs Blue/Green)
  - ▸ *CG use:* Colored glass, tinted fog, wine, tea; spectral σ_a(λ) for accurate color
- 3.5.1.2 Scattering Coefficient σ_s(x) [m⁻¹]: Probability of Scattering Event Per Unit Distance; Determines Cloudiness/Turbidity
  - ▸ *CG use:* Milk (high σ_s), clouds (very high σ_s), mist (moderate σ_s), clear air (low σ_s)
- 3.5.1.3 Extinction Coefficient σ_t = σ_a + σ_s; Albedo α = σ_s/σ_t (Fraction Scattered vs. Absorbed at Interaction); Mean Free Path = 1/σ_t (Average Distance Between Interactions)
  - ▸ *CG use:* σ_t controls medium density; α controls brightness (α=1 pure scattering, α=0 pure absorption)
- 3.5.1.4 Phase Function p(ω→ω'): Angular Distribution of Scattered Light; Normalization ∫_{S²} p(ω,ω') dω' = 1; Asymmetry Parameter g = ∫ p(cos θ) cos θ dω
  - Isotropic p = 1/(4π); Rayleigh p ∝ 1+cos²θ (Molecular, λ⁻⁴ Wavelength Dependence → Blue Sky); Mie (Hazy, Forward-Peaked); Henyey-Greenstein p(cos θ) = (1−g²)/(4π(1+g²−2g cos θ)^{3/2}) (Analytic Single-Parameter)
  - ▸ *CG use:* HG phase is the default for clouds/smoke/fog; Mie for water droplets (fog, clouds); Rayleigh for atmospheric scattering

#### 3.5.2 Volume Rendering Equation
- 3.5.2.1 Radiative Transfer Equation (RTE — Full Form): (ω·∇ + σ_t(x)) L(x,ω) = σ_s(x) ∫_{S²} p(ω',ω) L(x,ω') dω' + Q(x,ω) (Emission Term)
  - ▸ *CG use:* The fundamental equation for all volumetric light transport; solved via MC path tracing or deterministic methods
- 3.5.2.2 Transmittance T(x,y) = exp(−∫_x^y σ_t(s) ds): Fraction of Light Surviving Path from x to y Without Absorption/Scattering; Optical Depth τ = −ln(T) = ∫ σ_t ds
  - ▸ *CG use:* Beer-Lambert law for absorption-only media; attenuation factor in volume rendering integral
- 3.5.2.3 Volume Rendering Integral: L(x,ω) = ∫_0^∞ T(x,x_t) [σ_s(x_t) ∫ p L_i dω' + Q(x_t)] dt; Solution via Ray Marching with Step Size Δt: L += T_accum · (emission + scattering_contribution) · Δt
  - ▸ *CG use:* Every volumetric path tracer evaluates this integral; GPU ray marching (clouds, god rays, volumetric fog)

#### 3.5.3 Natural Phenomena Appearance
- 3.5.3.1 Atmospheric Scattering: Rayleigh (λ⁻⁴, Blue Sky, Red Sunset), Mie (Aerosols, Hazy Horizon), Ozone Absorption; Precomputed via Bruneton et al. (2008)
  - ▸ *CG use:* Outdoor environment rendering; flight simulators; game sky systems; UE5 Sky Atmosphere component
- 3.5.3.2 Cloud Rendering: Volumetric Path Tracing with High Albedo (>0.999); Lorenz-Mie Scattering by Water Droplets (Exact via Mie Theory or Tabulated); Multi-Scattering Dominates Appearance
  - ▸ *CG use:* Film-quality cloud rendering; real-time volumetric clouds (UE5, Horizon Forbidden West); Houdini cloud simulations
- 3.5.3.3 Smoke, Fire & Explosions: Emissive + Absorbing + Scattering Medium; Black-Body Radiation for Fire Color; Temperature Field → Emission Spectrum
  - ▸ *CG use:* VFX explosions (Houdini, EmberGen); game particle effects; thermal imaging simulation
- 3.5.3.4 Ocean & Water Appearance: Volume Scattering + Absorption for Underwater Color; Chlorophyll and CDOM Absorption Spectra; Jerlov Water Types (I, IA, IB, II, III — Clear to Turbid)
  - ▸ *CG use:* Submarine/snorkeling simulation; underwater photography color correction; ocean rendering

> 📚 **GitHub Repos:**
> - [PBR Book v4 Volumetric Scattering](https://pbr-book.org/4ed/Volume_Scattering) — Full volumetric path tracing implementation
> - [ebruneton/precomputed_atmospheric_scattering](https://github.com/ebruneton/precomputed_atmospheric_scattering) — Bruneton atmospheric model reference
>
> 📖 **Textbooks:** *Physically Based Rendering* — Pharr et al. (Ch. 11: Volume Scattering); *Fluid Simulation for Computer Graphics* — Bridson

---

### 3.6 Texture Mapping & Filtering Theory

#### 3.6.1 Texture Fundamentals
- 3.6.1.1 Texture Mapping Paradigm: Surface Parameterization (u,v) → Texture Domain [0,1]² → Lookup Texture Color T(u,v) → Modulate Surface Appearance (Albedo, Roughness, Normal, etc.)
  - ▸ *CG use:* PBR material parameter maps (base color, metallic, roughness, normal, AO, height); every rendered surface uses textures
- 3.6.1.2 UV Parameterization for Textures: Seam Minimization; Chart Packing Efficiency; Distortion (Stretch, Shear) Minimization; UDIM (U-Dimension) Tiling for High-Resolution Multi-Tile Textures
  - ▸ *CG use:* UV unwrapping is a core DCC task; UDIM for film-quality textures (Mari, Substance Painter)
- 3.6.1.3 Ptex (Per-Face Texture — Disney 2008): Eliminates UVs Entirely; Each Face Stores Its Own Texture (No Seams!); Filtering Across Face Boundaries via Adjacency Data
  - ▸ *CG use:* Disney/Pixar film production (no UV unwrapping!); RenderMan native texture format

#### 3.6.2 Texture Filtering — The Theory
- 3.6.2.1 Nyquist Theory Applied to Textures: Texture Signal Must Be Bandlimited to Avoid Aliasing When Minified (Many Texels → One Pixel); Antialiasing via Prefiltering (Mipmapping)
  - ▸ *CG use:* All real-time rendering relies on mipmapping for texture antialiasing; without it → moiré patterns, flickering
- 3.6.2.2 Mipmapping (Williams 1983): Power-of-Two Image Pyramid; Each Level = Previous Level Downsampled 2×; d = log₂(max(|du/dx|,|dv/dy|)) → Sample from Level d; Trilinear Filtering = Bilinear Sampling on Two Mip Levels + Linear Blend
  - ▸ *CG use:* GPU hardware texture units; O(log n) lookup vs O(n); storage overhead only 1/3 extra (1+¼+1/16+...=4/3)
- 3.6.2.3 Anisotropic Filtering: When Texture is Stretched in One Direction (e.g., Floor at Grazing Angle); EWA (Elliptical Weighted Average — Heckbert 1989) → Filter Along Stretched Axis
  - ▸ *CG use:* GPU anisotropic filtering (2×, 4×, 8×, 16×); samples multiple mip-level taps along anisotropic axis; critical for ground/floor textures
- 3.6.2.4 Reconstruction Kernels for Textures: Nearest-Neighbor (Aliasing + Pixelation), Bilinear (Smooth but Blurry), Bicubic (Sharper, Ringing Artifacts), Lanczos (Windowed Sinc — Best Quality but More Taps); Mitchell-Netravali (Two-Parameter Family — Free Parameters B, C)
  - ▸ *CG use:* GPU hardware: bilinear (free, hardware-accelerated); bicubic requires manual fetch; film rendering uses Lanczos for quality
- 3.6.2.5 Virtual Textures / MegaTextures (Tanner et al. 1998; id Tech 5 — Carmack): Indirection Table Maps Virtual Pages → Physical Pages; On-Demand Streaming from Disk; Only Load Visible Texels
  - ▸ *CG use:* RAGE (id Software); UE5 Virtual Texture; sparse/resident textures in D3D12/Vulkan; planetary-scale terrain texturing

#### 3.6.3 Advanced Texture Representations
- 3.6.3.1 Compressed GPU Textures: BC1 (DXT1 — RGB, 4bpp), BC3 (DXT5 — RGBA, 8bpp), BC5 (Normal Maps, 8bpp), BC6H (HDR FP16), BC7 (High-Quality RGBA, 8bpp); ASTC (Adaptive Scalable — Variable Block Size, Modern Mobile)
  - ▸ *CG use:* Every game texture is stored in BCn/ASTC; GPU hardware decompression (no CPU cost); critical for memory bandwidth
- 3.6.3.2 Sparse Textures / Tiled Resources: Hardware Virtual Texture via GPU Page Tables; Partially Resident Texture (PRT); Shader Can Check if Page is Resident Before Sampling
  - ▸ *CG use:* Virtual texture without CPU feedback loop; streaming open worlds without texture pop-in
- 3.6.3.3 Bindless Textures (NVIDIA ARB_bindless_texture, Vulkan Descriptor Indexing): Shader Can Access All Textures via Flat Index (No Binding Per Draw Call); GPU-Driven Material System
  - ▸ *CG use:* GPU-driven rendering (no CPU per-material binding); material variety without draw call explosion

> 📚 **GitHub Repos:**
> - [GPUOpen-LibrariesAndSDKs/TextureCompression](https://github.com/GPUOpen-LibrariesAndSDKs) — BCn/ETC/ASTC tools and samples
> - [Ptex (Disney)](https://github.com/wdas/ptex) ![Stars](https://img.shields.io/github/stars/wdas/ptex?style=flat) — Per-face texture mapping library
>
> 📖 **Textbooks:** *Real-Time Rendering* — Akenine-Möller et al. (Ch. 6: Texturing); *GPU Gems 2* — Ch. Lefohn et al. (Virtual Textures)

---

### 3.7 PBR Material Models & Workflows

#### 3.7.1 The PBR Material Revolution
- 3.7.1.1 What is PBR?: Physics-Based Shading Grounded in Microfacet Theory; Energy Conservation Enforced; Dielectrics (IOR→F₀) vs. Conductors (Complex IOR→Colored Reflectance); No Ad-Hoc Specular Power Parameters
  - ▸ *CG use:* Industry-wide standardization since ~2014; consistent material appearance across lighting conditions and renderers
- 3.7.1.2 Metalness-Roughness Workflow (Most Common): Parameters: BaseColor (RGB), Metalness [0=Diel, 1=Metal], Roughness [0=Smooth, 1=Rough]; F₀ = lerp(0.04, BaseColor, Metalness); DiffuseColor = BaseColor × (1−Metalness)
  - ▸ *CG use:* Unreal Engine, Unity HDRP, glTF 2.0, Substance Painter default; artist-friendly (few parameters, physically constrained)
- 3.7.1.3 Specular-Glossiness Workflow: Parameters: DiffuseColor (RGB), SpecularColor (RGB — Direct F₀ Control), Glossiness [0=Rough, 1=Smooth]; Full Artistic Control but Easy to Break Energy Conservation
  - ▸ *CG use:* Older pipelines; glTF 2.0 extension; still available in Substance Painter for legacy compatibility
- 3.7.1.4 Disney Principled BSDF (Burley 2012): 11 Parameters: baseColor, subsurface, metallic, specular, specularTint, roughness, anisotropic, sheen, sheenTint, clearcoat, clearcoatGloss; Monolithic Shader Covering 95% of Real-World Materials
  - ▸ *CG use:* The basis for Blender Principled BSDF, Unreal layered material, Arnold Standard Surface; single shader for nearly everything

#### 3.7.2 PBR Extensions & Special Materials
- 3.7.2.1 Sheen: Additional Microfiber Lobe (fabric appearance); Tinted Fresnel at Grazing; Typically Combined with Base Metallic-Roughness
  - ▸ *CG use:* Velvet, felt, peach fuzz, certain fabrics; Disney and Filament sheen models
- 3.7.2.2 Clear Coat: Extra Layer with Separate Roughness (Usually Low for Glossy Coating); Fresnel at Air-Coating Interface; Two-Lobe Normal Distribution (Base Layer + Coating)
  - ▸ *CG use:* Car paint (metallic base + high-gloss clear); varnished wood; glossy phone screens; metallic paint with clear lacquer
- 3.7.2.3 Thin-Film (Iridescence): Wavelength-Dependent Reflectance via Optical Path Difference 2ηd cos θ_t; Airy Summation Formula for Infinite Bounces; Spectrum → XYZ → RGB Conversion
  - ▸ *CG use:* Soap bubbles, oil slicks, insect cuticle, pearl, dichroic glass; UE5 Filament implementation
- 3.7.2.4 Anisotropy: Direction-Dependent Roughness α_u ≠ α_v; Tangent/Bitangent Direction Defines Anisotropy Axis; Brushed Microfacet Normal Distribution D_aniso
  - ▸ *CG use:* Brushed metals (stainless steel appliances), hair, carbon fiber, machined aluminum, grooved surfaces

#### 3.7.3 Material Representation Standards
- 3.7.3.1 MaterialX (ASWF): XML-Based Material Definition; Node Graph → Platform-Agnostic Shader Generation; OSL/GLSL/MDL/HLSL Code Generation; Standard Library (PBR Nodes, Math, Textures)
  - ▸ *CG use:* USD Material Binding; VFX pipeline interchange; NVIDIA Omniverse uses MaterialX as default; cross-engine material portability
- 3.7.3.2 MDL (NVIDIA Material Definition Language): C-Like DSL for Materials; Physically Based by Default; Supports Measured BSDF; Compiles to Diverse Backends (OSL, PTX, GLSL)
  - ▸ *CG use:* Iray, mental ray, vMaterials library; NVIDIA Omniverse rendering; automotive and industrial design visualization
- 3.7.3.3 OpenPBR: Joint Standard by Autodesk + Adobe + NVIDIA + Epic; Unified Surface-Shading Model; Intended to Replace Proprietary Shader Fragmentation
  - ▸ *CG use:* Emerging standard (2024+); aims to unify Metalness-Roughness + Specular-Glossiness + Disney under one model
- 3.7.3.4 UsdShade: USD's Material Binding System; Shader Graph (Node Network); Connects Shaders to Geometry via Material Assignment API
  - ▸ *CG use:* VFX pipeline: define material once → consistent across modeling, layout, animation, lighting, rendering

> 📚 **GitHub Repos:**
> - [AcademySoftwareFoundation/MaterialX](https://github.com/AcademySoftwareFoundation/MaterialX) ![Stars](https://img.shields.io/github/stars/AcademySoftwareFoundation/MaterialX?style=flat) — Industry-standard material definition
> - [google/filament](https://github.com/google/filament) ![Stars](https://img.shields.io/github/stars/google/filament?style=flat) — Complete PBR material system (Metalness-Roughness, ClearCoat, Sheen, Anisotropy)
> - [NVIDIA/MDL-SDK](https://github.com/NVIDIA/MDL-SDK) ![Stars](https://img.shields.io/github/stars/NVIDIA/MDL-SDK?style=flat) — NVIDIA Material Definition Language SDK
>
> 📖 **Textbooks:** *Real-Time Rendering* — Ch. 9 (Physically Based Shading); *Physically Based Rendering* — Ch. 9 (Materials)

---

### 3.8 Measured, Data-Driven & Neural Materials

#### 3.8.1 Measured BRDF Databases & Fitting
- 3.8.1.1 MERL BRDF Database (Matusik et al. 2003): 100 Isotropic BRDFs Measured via Spherical Gantry; Dense (θ_h, θ_d, φ_d) Sampling (90×90×180); De-Facto Benchmark for BRDF Models
  - ▸ *CG use:* Ground truth for BRDF fitting evaluation; still the most widely used measured BRDF dataset; available at merl.com
- 3.8.1.2 EPFL Material Database (Dupuy & Jakob 2018): High-Resolution Anisotropic BSDF Measurements; Includes Transmission and Retroflection Components; Raw Measurement Data + Fitted Model Parameters
  - ▸ *CG use:* Anisotropic reflectance validation; BSDF research evaluation; physically accurate material reproduction
- 3.8.1.3 BRDF Fitting Techniques: Nonlinear Least Squares (Levenberg-Marquardt) to Fit Model Parameters to Measured Data; BRDF Explorer (Disney 2012); Isotropic → GGX Fitting (α, F₀ per Color Channel)
  - ▸ *CG use:* Convert measured data to PBR pipeline parameters; automate material capture workflows
- 3.8.1.4 SVBRDF (Spatially-Varying BRDF) Measurement: Per-Texel BRDF via Camera+Flash Photography; Photometric Stereo for Surface Orientation; Aittala et al. (2015) — Single Image SVBRDF via Neural Network
  - ▸ *CG use:* Quixel Megascans material capture; smartphone material scanning (Adobe Capture, Unity MARS); game texture generation

#### 3.8.2 Neural Material Representations
- 3.8.2.1 Neural BRDF: MLP f_θ(ω_i, ω_o) → RGB Reflectance; Train on Measured BRDF Data; Autoencoder Architecture: Encode BRDF to Latent Vector → Decode Specific Query Directions
  - ▸ *CG use:* Compact BRDF representation (few KB vs traditional tabulation's MB); fast evaluation; interpolation between measured materials
- 3.8.2.2 Neural BTF (Bidirectional Texture Function): 6D Function BTF(x,ω_i,ω_o) — Appearance Depends on Surface Position and Light/View Directions; Captures Meso-Scale Detail (Fabric Weave, Leather Grain)
  - ▸ *CG use:* Film-quality fabric rendering; car interior materials with visible weave; close-up surface detail beyond bump mapping
- 3.8.2.3 Neural SVBRDF Recovery from Images: Given Single or Few Photos → Neural Network Predicts Per-Pixel Albedo, Normal, Roughness, Metallic; Deschaintre et al. (2018), Li et al. (2018)
  - ▸ *CG use:* Material creation from smartphone photos; game asset material authoring from reference images
- 3.8.2.4 Diffusion-Based Material Generation: Stable Diffusion Fine-Tuned on SVBRDF Maps; Text Prompt → 4-Map Output (Albedo, Normal, Roughness, Metallic); MatFuse, ControlMat, DreamMat (SIGGRAPH 2024)
  - ▸ *CG use:* AI-assisted texture/material creation; rapid prototyping; filling material libraries with diverse variations

#### 3.8.3 Light Transport & Appearance Capture
- 3.8.3.1 Light Stage (Debevec et al. 2000): Hemispherical LED Array; Controlled Lighting Patterns; Separate Diffuse + Specular + Normal from Multi-Light Images; Spherical Harmonic Gradient Illumination
  - ▸ *CG use:* Digital human face capture; film-quality reflectance field acquisition; USC ICT Light Stage used in Avatar, Blade Runner 2049, etc.
- 3.8.3.2 Reflectance Field: 8D Function R(x_c,y_c,θ,φ,x_p,y_p) — Appearance for Every Camera Pixel, Every Projector Pixel; Spatially-Varying Reflectance + Global Illumination Effects
  - ▸ *CG use:* Relighting real scenes from photographs; movie set relighting; museum artifact digitization
- 3.8.3.3 OLAT (One-Light-at-a-Time) & Neural Relighting: Capture Scene Under Individual Light Directions → Train Network to Predict Appearance Under Any Lighting; Neural Radiance Cache (NRC — Müller 2021) for Real-Time Relighting
  - ▸ *CG use:* Product visualization (change lighting interactively); architectural walkthroughs; e-commerce 3D viewers

> 📚 **GitHub Repos:**
> - [MERL BRDF Database](https://www.merl.com/brdf) — 100 measured isotropic BRDFs
> - [EPFL Realistic Graphics Lab](https://rgl.epfl.ch/) — High-quality BSDF measurement data
> - [NVlabs/nrc](https://github.com/NVlabs/nrc) ![Stars](https://img.shields.io/github/stars/NVlabs/nrc?style=flat) — Neural Radiance Cache for real-time relighting
>
> 📖 **Textbooks:** *Digital Modeling of Material Appearance* — Dorsey, Rushmeier, Sillion (Comprehensive reference); *High Dynamic Range Imaging* — Reinhard et al.

---

### 3.9 Procedural & Neural Textures

#### 3.9.1 Procedural Texture Generation
- 3.9.1.1 Noise-Based Procedurals: fBm (fractal Brownian motion) for terrain, clouds, marble veining; Turbulence (abs(noise)) for fire, marble; Domain Warping for organic patterns
  - ▸ *CG use:* Infinite-resolution textures without storage cost; ShaderToy art; procedural planets (No Man's Sky)
- 3.9.1.2 Pattern-Based Procedurals: Tiled/Wang Tiles for seamless aperiodic textures; Reaction-Diffusion (Turing Patterns → Zebra Stripes, Leopard Spots); Voronoi → Stone, Cells, Soap Bubbles
  - ▸ *CG use:* Material graph nodes in Substance Designer; game environment texturing without repetition artifacts
- 3.9.1.3 GPU Noise Libraries: FastNoise2 (SIMD-Optimized); Psrdnoise (Tiling Simplex with Derivatives); Curl Noise Generators
  - ▸ *CG use:* Real-time procedural effects in shaders; terrain generation at runtime; VFX particle noise fields

#### 3.9.2 Neural Texture Synthesis & Super-Resolution
- 3.9.2.1 Example-Based Texture Synthesis (Efros & Leung 1999; Wei & Levoy 2000): Non-Parametric; Grow Texture Pixel-by-Pixel Matching Neighborhoods; Image Quilting (Efros & Freeman 2001) — Minimum Error Boundary Cut for Patch Blending
  - ▸ *CG use:* Texture expansion (make a small sample into a large texture); game texture authoring (start from photo, expand to needed size)
- 3.9.2.2 Neural Style Transfer for Textures (Gatys et al. 2015): CNN Feature Space Optimization; Content Loss (Preserve Structure) + Style Loss (Gram Matrix Statistics of Filter Responses); TextureNet, StyleGAN-2-Net
  - ▸ *CG use:* Style transfer for artistic texture generation; material variation from reference style image
- 3.9.2.3 Diffusion-Based Texture Generation: Fine-Tuned SD on PBR Map Pairs; Text Prompt → Albedo + Normal + Roughness; MatFuse (Vecchio et al. 2024), ControlNet for Guided PBR Map Generation
  - ▸ *CG use:* Text-to-PBR-material workflow; rapid material library population; concept art → production texture pipeline
- 3.9.2.4 Texture Super-Resolution: ESRGAN, Real-ESRGAN for Single-Image Upscaling; Texture-Specific SR Networks Trained on PBR Maps; Perceptual Loss (LPIPS) for Texture Detail Preservation
  - ▸ *CG use:* Upscale low-res game textures to 4K; enhance legacy assets; mobile → console port texture upgrade

> 📚 **GitHub Repos:**
> - [Auburn/FastNoise2](https://github.com/Auburn/FastNoise2) ![Stars](https://img.shields.io/github/stars/Auburn/FastNoise2?style=flat) — High-performance SIMD noise generation
> - [xinntao/Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN) ![Stars](https://img.shields.io/github/stars/xinntao/Real-ESRGAN?style=flat) — Practical image/texture super-resolution
>
> 📖 **Textbooks:** *Texturing and Modeling: A Procedural Approach* — Ebert, Musgrave, Peachey, Perlin, Worley

---

### 3.10 Wave Optics & Special Effects

#### 3.10.1 Wave Optics Foundations
- 3.10.1.1 When Geometric Optics Fails: When Feature Size ∼ Wavelength (Nanoscale Structures); Diffraction, Interference, Polarization Effects Emerge; CD/DVD Rainbow, Butterfly Wings, Holograms
  - ▸ *CG use:* Beyond the microfacet model — wave effects explain color in nature that ray optics cannot
- 3.10.1.2 Diffraction: Light Bending Around Edges (Huygens-Fresnel Principle); Fraunhofer (Far-Field) and Fresnel (Near-Field) Regimes; Diffraction Grating → Wavelength-Dependent Angular Dispersion
  - ▸ *CG use:* CD/DVD rainbow pattern; diffraction spikes on camera lens apertures (star filters); solar coronas in atmosphere rendering
- 3.10.1.3 Thin-Film Interference (Precise): Phase Difference Δφ = (2π/λ) × 2ηd cos θ_t + Δφ_reflection (Phase Shift at Interface); Constructive: Δφ = 2πm (Bright); Destructive: Δφ = 2π(m+½) (Dark); Infinite Summation via Airy Formula
  - ▸ *CG use:* Lens coatings (anti-reflection → purple/green tint); oil slicks; dichroic filters; accurate soap bubble rendering (Belcour & Barla 2017)

#### 3.10.2 Polarization
- 3.10.2.1 Stokes Vector/Mueller Calculus: 4D Stokes Vector S = (I,Q,U,V); I = Total Intensity, Q = Horizontal/Vertical, U = ±45°, V = Circular; Mueller Matrix M (4×4) Transforms Stokes Vector (Arbitrary Polarization Transform)
  - ▸ *CG use:* Polarization-aware rendering (Mitsuba 3); LCD screen/mobile phone reflections (polarized light); sunglasses rendering
- 3.10.2.2 Fresnel Polarization Split: r_∥ vs r_⊥ Different! → Dielectric Reflection is Partially Polarizing (Brewster's Angle: θ_B = arctan(η₂/η₁), r_∥ = 0 at θ_B)
  - ▸ *CG use:* Polarized highlights on water/glass (removed by polarizing filters in photography); LCD emission is linearly polarized
- 3.10.2.3 Fluorescence & Phosphorescence: Photon Absorption → Electron Excitation → Re-Emission at Longer Wavelength (Stokes Shift); Fluorescence = Prompt (<10⁻⁸s), Phosphorescence = Delayed (ms to hours)
  - ▸ *CG use:* Fluorescent materials (highlighters, neon, certain minerals, coral); blacklight rendering; spectral reradiation matrix (Glassner 1994)

#### 3.10.3 Spectral Rendering
- 3.10.3.1 Why Spectral?: RGB Rendering Cannot Reproduce Dispersion, Thin-Film Colors, Fluorescence, or Metamerism (Two Different Spectra → Same RGB); Spectral Rendering Uses Many Wavelength Samples (Typically 4-16, Hero Wavelength Sampling)
  - ▸ *CG use:* Film-quality rendering (Arnold, RenderMan spectral mode); accurate gemstone, prism, rainbow rendering; color-critical product visualization
- 3.10.3.2 Hero Wavelength Sampling (Wilkie et al. 2014): Trace Single Wavelength Per Path (Hero λ ∼ Blackbody); Compute Path Weight via MIS Over Wavelengths; Spectral-to-XYZ → RGB at Sensor
  - ▸ *CG use:* Efficient spectral rendering without tracing N wavelengths per path; production renderers use this approach
- 3.10.3.3 Spectral Upsampling: Given RGB Triplet → Recover Plausible Spectrum; RGB → Smooth Spectrum via Optimization (Smits 1999), Dictionary Learning (Jakob & Hanika 2019), or Neural Methods
  - ▸ *CG use:* Artists paint in RGB → spectral renderer needs spectrum; enabling spectral rendering in RGB-dominated pipelines

> 📚 **GitHub Repos:**
> - [mitsuba-renderer/mitsuba3](https://github.com/mitsuba-renderer/mitsuba3) ![Stars](https://img.shields.io/github/stars/mitsuba-renderer/mitsuba3?style=flat) — Full spectral + polarization rendering support
> - [colour-science/colour](https://github.com/colour-science/colour) ![Stars](https://img.shields.io/github/stars/colour-science/colour?style=flat) — Spectral manipulation, CIE standards, illuminants
>
> 📖 **Textbooks:** *Physically Based Rendering* — Pharr et al. (Ch. 5: Color and Radiometry — Spectral Representation); *Principles of Digital Image Synthesis* — Glassner

---

### 3.11 Fluorescent, Phosphorescent & Spectral Materials

#### 3.11.1 Fluorescence in Rendering
- 3.11.1.1 Reradiation Matrix (Glassner 1994): M(λ_i,λ_o) — Probability of Absorbing λ_i and Re-Emitting λ_o; Fluorescence Adds M · L_i to RTE Source Term; Matrix is Banded (λ_o > λ_i, Spectral Shift)
  - ▸ *CG use:* Fluorescent materials; security markings (passport UV patterns); coral reef appearance; highlighter pens under UV
- 3.11.1.2 Practical Fluorescence Models: Reduce Full Reradiation Matrix to Moments (Mean Shift + Width); Fitted to Measured Fluorescent Material Database (Wilkie et al. 2006)
  - ▸ *CG use:* Production spectral rendering; automotive paint with fluorescent pigments; theatrical lighting simulation
- 3.11.1.3 Phosphorescence (Glow-in-the-Dark): Delayed Emission (Seconds to Hours); Requires Time-Dependent Simulation; Charge/Discharge Model (Accumulate Energy, Release Exponentially)
  - ▸ *CG use:* Glow-in-the-dark toys/stickers; phosphorescent watch dials; emergency exit signs; phosphor persistence on old CRT monitors

#### 3.11.2 Special Optical Materials
- 3.11.2.1 Dichroic Materials: Transmit/Reflect Different Wavelengths Differently (Not Thin-Film — Selective Absorption); Polarizing Filters; Dichroic Beam Splitters in Projectors
  - ▸ *CG use:* Dichroic glass blocks; LCD projector optical path; color separation prisms in 3-CCD cameras
- 3.11.2.2 Retroreflective Materials: Light Reflected Back Toward Source Regardless of Incidence Angle; Corner-Cube Reflectors (Three Mutually Perpendicular Mirrors); Glass Beads (Cat's Eye Reflectors)
  - ▸ *CG use:* Road signs and markings at night; bicycle reflectors; motion capture markers (passive retroreflective spheres)
- 3.11.2.3 Gemstone Rendering: High IOR (Diamond 2.42, Sapphire 1.77), High Dispersion (Abbe Number V_d), Polarization via Birefringence (Calcite — Double Refraction), Inclusions and Flaws
  - ▸ *CG use:* Jewelry rendering (Tiffany, Cartier); accurate gem visualization for e-commerce; diamond grading simulation
- 3.11.2.4 Transparent Conductive Oxides (TCO): Thin Conductive Layer on Glass (Phone Screens, Solar Panels); Slight Tint (ITO = Yellow-Green, FTO = Haze); Important for Accurate Mobile Device Rendering
  - ▸ *CG use:* Product visualization for consumer electronics; architectural glass with low-E coatings

> 📖 **Textbooks:** *Digital Modeling of Material Appearance* — Dorsey, Rushmeier, Sillion; *Measuring and Modeling Fluorescent Materials* — Wilkie et al.

---

### 3.12 Material Standards, Interchange & Future Directions

#### 3.12.1 Material Ecosystem Standards
- 3.12.1.1 glTF 2.0 PBR: KHR_materials_pbrSpecularGlossiness (Legacy) + KHR_materials_metallicRoughness; Extensions: ClearCoat, Sheen, Transmission, Volume, Iridescence, Specular, Anisotropy
  - ▸ *CG use:* Web 3D standard material; every WebGL/WebGPU viewer; game engine import/export; USDZ for AR Quick Look
- 3.12.1.2 MaterialX/USD Integration: MaterialX Node Graph → USD Shader Prim → Hydra Renderer Backend; Multi-Renderer Support (Storm GL, Arnold, RenderMan, Karma, Cycles)
  - ▸ *CG use:* VFX pipeline material exchange; look development consistency across departments; real-time ↔ offline interoperability
- 3.12.1.3 OpenPBR (2024+): Community-Driven Unified Shading Model; Incorporates Disney + Autodesk Standard Surface + MDL + MaterialX; Single Parameterization for All Renderers
  - ▸ *CG use:* Goal: define material once → render consistently everywhere (games, film, AR, print); reduces current fragmentation

#### 3.12.2 Future Material Directions
- 3.12.2.1 Differentiable Material Models: BRDF Parameters Directly Optimizable via Gradient Descent; Differentiable Renderer → ∇L/∇(albedo, roughness, metallic) → Update Material to Match Photograph
  - ▸ *CG use:* Automatic material parameter estimation from photos; inverse rendering for asset creation; material optimization for target appearance
- 3.12.2.2 Generative Material AI: Diffusion Models Trained on Material Databases → Generate Novel, Physically-Plausible PBR Materials; Text-Guided Material Generation; Material Variation from Single Example
  - ▸ *CG use:* Infinite material library generation; artist tool augmentation; procedural material population for large scenes
- 3.12.2.3 Real-Time Neural Materials: Neural BRDF Evaluated in Shader via Tiny MLP (Few FLOPs); Precomputed Neural Texture (Baked MLP Weights into Texture); Neural Material LOD
  - ▸ *CG use:* Complex measured BRDFs at real-time frame rates; film-quality materials in games; mobile neural material inference
- 3.12.2.4 Appearance Capture Democratization: Smartphone-Based Material Scanning (LiDAR + RGB → PBR Maps); Cloud Processing → Material Library; AR-Ready Asset Generation
  - ▸ *CG use:* User-generated content for games; e-commerce 3D product scanning; architectural material documentation

> 📚 **GitHub Repos:**
> - [KhronosGroup/glTF](https://github.com/KhronosGroup/glTF) ![Stars](https://img.shields.io/github/stars/KhronosGroup/glTF?style=flat) — glTF specification + PBR extensions
> - [AcademySoftwareFoundation/OpenPBR](https://github.com/AcademySoftwareFoundation/OpenPBR) — Unified PBR shading model (emerging standard)
> - [google/filament](https://github.com/google/filament) ![Stars](https://img.shields.io/github/stars/google/filament?style=flat) — Complete PBR implementation + material documentation
>
> 📖 **Textbooks:** *Physically Based Rendering* — Pharr et al. (Complete pipeline); *Real-Time Rendering* — Akenine-Möller et al. (Real-time materials)

---


## Chapter 4 · Light Transport & Rendering

*The complete pipeline of image synthesis — from GPU rasterization to path tracing, global illumination, and real-time rendering techniques. `▸ CG use:` links each concept to practice.*

> 💡 **Top-Level References:**
> - [PBR Book v4 (Free Online)](https://pbr-book.org/) — Definitive rendering theory + implementation
> - [ssloy/tinyrenderer](https://github.com/ssloy/tinyrenderer) ![Stars](https://img.shields.io/github/stars/ssloy/tinyrenderer?style=flat) — Build a software rasterizer from scratch
> - [mmp/pbrt-v4](https://github.com/mmp/pbrt-v4) ![Stars](https://img.shields.io/github/stars/mmp/pbrt-v4?style=flat) — Complete PBRT v4 source code (literate programming)
> - [NVIDIAGameWorks/RTXDI](https://github.com/NVIDIAGameWorks/RTXDI) ![Stars](https://img.shields.io/github/stars/NVIDIAGameWorks/RTXDI?style=flat) — ReSTIR-based real-time direct illumination

---

### 4.1 The Graphics Pipeline Architecture

#### 4.1.1 Pipeline Overview
- 4.1.1.1 Application Stage (CPU): Scene Graph Traversal, Visibility Determination, Draw Call Generation, Resource Binding
  - ▸ *CG use:* Frustum culling, occlusion queries, LOD selection, material sorting — all before a single GPU command
- 4.1.1.2 GPU Command Processing: Command Buffer Recording (Vulkan/D3D12) → Queue Submission → GPU Command Processor → Work Distribution to SMs/CUs
  - ▸ *CG use:* Multi-threaded command recording; async compute overlap; GPU work graphs for GPU-driven command generation
- 4.1.1.3 Graphics Pipeline Stages: Input Assembler → Vertex Shader → (Tessellation → Geometry Shader) → Rasterizer → Fragment Shader → Output Merger; Fixed-Function vs. Programmable
  - ▸ *CG use:* Modern pipelines: Vertex + Fragment programmable since 2001; tessellation/geometry since ~2010; mesh shaders since 2018
- 4.1.1.4 Mesh Shader Pipeline (Turing+ / RDNA2+): Task Shader (Work Distribution) → Mesh Shader (Output Meshlets Directly); Replaces Vertex→Tessellation→Geometry Chain
  - ▸ *CG use:* UE5 Nanite; GPU-driven culling and LOD; 3× geometry throughput; eliminates draw-call overhead for micro-geometry
- 4.1.1.5 Work Graphs (GPU-Driven Pipeline): GPU Generates Work for Itself; Producer→Consumer Relationship; No CPU Round-Trip
  - ▸ *CG use:* Fully GPU-driven rendering (D3D12 Work Graphs, Vulkan Device-Generated Commands); culling→draw→post all on GPU

#### 4.1.2 Immediate vs. Tile-Based Rendering
- 4.1.2.1 Immediate-Mode Rendering (IMR): Process Primitives in Submission Order; Each Triangle Immediately Goes Through Full Pipeline; Desktop GPUs (NVIDIA, AMD Desktop)
  - ▸ *CG use:* Low latency; predictable performance; requires large cache to hide DRAM bandwidth
- 4.1.2.2 Tile-Based Deferred Rendering (TBDR): Bin Primitives into Screen Tiles; Process One Tile at a Time (On-Chip Tile Memory); Mobile GPUs (ARM Mali, Qualcomm Adreno, Apple GPU)
  - ▸ *CG use:* Dramatic bandwidth savings (no off-chip framebuffer until tile is done); enables low-power mobile GPUs; requires special handling for tessellation/geometry shaders
- 4.1.2.3 Tile-Based Immediate (NVIDIA Maxwell+): Hybrid: Tile-Binned for Rasterization + Immediate Fragment Processing
  - ▸ *CG use:* Best of both worlds; transparent to the developer

> 📖 **Textbooks:** *Real-Time Rendering* — Akenine-Möller et al. (Ch. 2-3); *GPU Zen* — Engel (Architecture deep-dives)

---

### 4.2 Geometry Processing & Transform Pipeline

#### 4.2.1 The Transform Chain
- 4.2.1.1 Model Transform: Object Space → World Space; M_model = T·R·S (TRS Decomposition); Hierarchical via Scene Graph Accumulation
  - ▸ *CG use:* Every object instance; GPU stores pre-computed world matrix or computes in vertex shader via instancing
- 4.2.1.2 View Transform: World → Camera/View Space; M_view = [R|t]⁻¹; Camera at Origin, Looking Down −Z (OpenGL) or +Z (D3D)
  - ▸ *CG use:* FPS camera → view matrix rebuilt each frame from camera position + rotation
- 4.2.1.3 Projection Transform: View → Clip Space; Perspective: x_clip = (f/aspect)·x, y_clip = f·y, z_clip = (f+n)/(f−n)·z − 2fn/(f−n); Orthographic: Identity with Scale
  - ▸ *CG use:* Perspective matrix maps frustum → cube [−1,1]³; sets up perspective division
- 4.2.1.4 Perspective Division & NDC: (x,y,z,w)_clip → (x/w, y/w, z/w, 1)_NDC; Non-Linear Depth: z_NDC ∝ 1/z_view; Reverse-Z for Better Precision (Far=0, Near=1)
  - ▸ *CG use:* Reverse-Z enabled by floating-point depth (close values have more precision near 0); industry standard since ~2017
- 4.2.1.5 Viewport Transform: NDC [−1,1]² → Screen Pixels; glViewport/D3D12_VIEWPORT; Half-Pixel Offset Convention
  - ▸ *CG use:* Maps normalized coordinates to actual framebuffer; multi-viewport for split-screen or cascaded shadow maps

#### 4.2.2 Programmable Geometry Stages
- 4.2.2.1 Vertex Shader: Per-Vertex Processing; Input: Vertex Attributes (Position, Normal, UV, Color, Bone Weights); Output: Clip-Space Position + Interpolated Attributes
  - ▸ *CG use:* Skinning (bone matrix application); morph targets; wind animation (vertex displacement by noise); all per-vertex work
- 4.2.2.2 Tessellation: Hull Shader (Control Points + Tess Factors) → Fixed-Function Tessellator (Generates Domain Points) → Domain Shader (Evaluates Surface at Each Point); Displacement Mapping
  - ▸ *CG use:* Adaptive terrain tessellation; smooth LOD transitions; detailed displacement without pre-tessellated geometry
- 4.2.2.3 Geometry Shader: Per-Primitive Processing; Can Emit/Delete Vertices; Input: Primitive (Point/Line/Triangle) → Output: Stream of Primitives
  - ▸ *CG use:* Shadow volume extrusion; billboard generation from points; cube map rendering (one pass, 6 faces); largely superseded by mesh shaders

#### 4.2.3 Primitive Assembly & Culling
- 4.2.3.1 Primitive Assembly: Vertices → Triangles (3 Vertices), Lines (2), Points (1); Triangle Strips/Fans for Compression; Index Buffer Redundancy Elimination (Post-Transform Vertex Cache)
  - ▸ *CG use:* Indexed drawing (16-bit or 32-bit indices); triangle strips reduce vertex processing by ~3× vs. triangle lists
- 4.2.3.2 Back-Face Culling: Discard Triangles Facing Away from Camera (n·view_dir > 0 → Back Face); Configurable Winding Order (CW/CCW)
  - ▸ *CG use:* Eliminates ~50% of fragments for closed surfaces; free performance; must disable for two-sided materials (cloth, leaves)
- 4.2.3.3 Frustum Culling: AABB/Sphere Against 6 Frustum Planes; Hierarchical (BVH/Octree); GPU-Based via Compute Shader Indirect Draw
  - ▸ *CG use:* Essential for any non-trivial scene; GPU-driven culling (cull → compact → draw indirect)
- 4.2.3.4 Guard Band Clipping: Hardware Clips to Larger Region than Viewport; Avoids Expensive Clipping for Triangles Just Outside; Genuine Clipping Only When Beyond Guard Band
  - ▸ *CG use:* Transparent GPU hardware optimization; developer doesn't need to think about it

> 📚 **GitHub Repos:** [ssloy/tinyrenderer](https://github.com/ssloy/tinyrenderer) ![Stars](https://img.shields.io/github/stars/ssloy/tinyrenderer?style=flat) — Complete transform chain from scratch

---

### 4.3 Rasterization & Fragment Processing

#### 4.3.1 Rasterization Algorithms
- 4.3.1.1 Line Rasterization: DDA (Digital Differential Analyzer — Floating Point, Simple), Bresenham (Integer-Only, No Division); GPU-Specific Variants
  - ▸ *CG use:* Wireframe rendering; line primitives for CAD visualization; Bresenham still taught for pedagogical value, GPU uses custom hardware
- 4.3.1.2 Triangle Rasterization — Edge Function Method (Pineda 1988): For Each Screen Pixel (x,y), Evaluate E_i(x,y) = (x−x_i)(y_{i+1}−y_i) − (y−y_i)(x_{i+1}−x_i) for i=0,1,2; All E_i ≥ 0 (or All ≤ 0) → Inside
  - ▸ *CG use:* THE algorithm used by all GPU rasterizers; trivial to parallelize; yields barycentric coordinates naturally
- 4.3.1.3 Barycentric Coordinates (α,β,γ): α = E_1/E_total, β = E_2/E_total, γ = E_3/E_total; α+β+γ=1; α,β,γ ≥ 0 Inside Triangle
  - ▸ *CG use:* Smooth attribute interpolation across triangle faces; texture coordinate, normal, color interpolation
- 4.3.1.4 Perspective-Correct Interpolation: Linear Interpolation in Screen Space is WRONG (Affine Texture Mapping Error); Must Interpolate (u/z, v/z, 1/z) in Screen Space, Then Divide: u = (u/z)/(1/z)
  - ▸ *CG use:* GPU hardware does perspective-correct interpolation automatically; classic PS1/Saturn era affine texture warping is this bug
- 4.3.1.5 Scanline vs. Tile-Based Rasterization: Scanline (Process Triangle Row-by-Row); Tile (Binned to Screen Tiles, Process Per Tile); Hierarchical (Coarse Rasterizer → Fine Rasterizer)
  - ▸ *CG use:* Modern GPUs use hierarchical rasterization: coarse test (entire tile inside/outside) → fine rasterization only for boundary tiles

#### 4.3.2 Depth, Stencil & Blending
- 4.3.2.1 Depth Buffer (Z-Buffer — Catmull 1974): Store Per-Pixel Depth; Before Shading: Test z_incoming < z_stored → Pass (Write Depth + Color); Opaque Objects: Front-to-Back Sort for Early-Z Optimization
  - ▸ *CG use:* The foundation of 3D rendering; GPU Early-Z (Hi-Z) rejects fragments before expensive fragment shader execution
- 4.3.2.2 Reverse-Z: Store 0 at Far Plane, 1 at Near; Floating-Point Depth Has More Precision Near 0 → Better Far-Plane Precision; No More Z-Fighting at Distance
  - ▸ *CG use:* Industry standard since ~2017; games with large view distances (Battlefield, open-world) require this; requires inverted depth test (Greater instead of Less)
- 4.3.2.3 Stencil Buffer: 8-Bit Per-Pixel Integer; Configurable Stencil Test + Stencil Operation (Keep/Zero/Replace/Incr/Decr/Invert); Separate Front/Back Face Stencil State
  - ▸ *CG use:* Shadow volume rendering (Carmack's Reverse); outline/highlight rendering (render selection outline via stencil); decal clipping; mirrors and portals
- 4.3.2.4 Alpha Blending: C_out = C_src · α_src + C_dst · (1−α_src); Premultiplied Alpha: C_out = C_src + C_dst·(1−α_src) (Correct Filtering + Compositing); Blend Modes (Additive, Multiply, Screen, Overlay)
  - ▸ *CG use:* Transparent objects; particle effects; UI compositing; premultiplied alpha avoids edge artifacts in mipmapped textures
- 4.3.2.5 Order-Independent Transparency (OIT): Weighted Blended OIT: C_accum += α · C · weight(z,α), α_accum += α; Final: C_final = C_accum/α_accum · (1−α_first); Moment-Based OIT; Per-Pixel Linked Lists
  - ▸ *CG use:* Real-time transparency without expensive object sorting; glass buildings, holograms, particle systems

#### 4.3.3 Fragment Shader Programming
- 4.3.3.1 Fragment Shader Input: Interpolated Attributes (UV, Normal, World Position, Color); Output: One or More Color Values (Multiple Render Targets — MRT)
  - ▸ *CG use:* G-Buffer in deferred shading (each render target = one material property); up to 8 MRTs on modern GPUs
- 4.3.3.2 Early Fragment Tests: Early-Z (Before Shader — Reject If Occluded), Early-Stencil; Can Be Disabled (discard in Shader, Writing gl_FragDepth, Alpha-to-Coverage)
  - ▸ *CG use:* Opaque pass: enable Early-Z for maximum performance; transparent pass: Early-Z disabled
- 4.3.3.3 Conservative Rasterization (D3D12/Vulkan): Generate Fragment for ANY Pixel Touched by Triangle (Not Just Center-Covered); Overestimation (Outer Conservative) vs. Underestimation (Inner Conservative)
  - ▸ *CG use:* Voxelization (guarantee no holes); occlusion culling (conservative depth rendering); collision detection on GPU; light culling tile classification

> 📚 **GitHub Repos:** [ssloy/tinyrenderer](https://github.com/ssloy/tinyrenderer) ![Stars](https://img.shields.io/github/stars/ssloy/tinyrenderer?style=flat) — Triangle rasterization, z-buffer, perspective correction from scratch

---

### 4.4 Anti-Aliasing Theory & Practice

#### 4.4.1 Aliasing Fundamentals
- 4.4.1.1 Nyquist-Shannon in Rendering: Geometry Edges, Texture Details, Specular Highlights All Create Frequencies Above Pixel Nyquist (0.5 cycles/pixel); Result: Jaggies, Moiré, Flickering, Crawling Edges
  - ▸ *CG use:* Aliasing is the single most visible rendering artifact; every AA technique addresses some aspect of this
- 4.4.1.2 Prefiltering vs. Postfiltering: Prefilter = Bandlimit Signal Before Sampling (Mipmapping, Analytic AA); Postfilter = Reconstruct from Higher-Rate Samples (MSAA, SSAA, TAA)
  - ▸ *CG use:* Mipmapping is the prefilter solution for textures; geometric edges require spatial supersampling (MSAA) or temporal accumulation (TAA)

#### 4.4.2 Spatial Anti-Aliasing
- 4.4.2.1 Supersampling (SSAA / FSAA): Render at Higher Resolution → Downsample with Reconstruction Filter; 2× = 4× Pixel Count; Perfect Quality but Prohibitively Expensive
  - ▸ *CG use:* Screenshot/offline rendering; not practical for real-time games; VR requires supersampling for clarity
- 4.4.2.2 Multisample Anti-Aliasing (MSAA): Multiple Coverage/Raster Samples per Pixel, Single Shader Evaluation; Only Edge Pixels Get Multiple Samples; 2×/4×/8× MSAA
  - ▸ *CG use:* Standard AA for forward rendering; doesn't anti-alias shader aliasing (specular, normal map noise); inactive in deferred (G-Buffer resolves before MSAA)
- 4.4.2.3 Coverage Sampling AA (CSAA / EQAA): More Coverage Samples Than Color/Z Samples; CSAA 16×Q = 4 Color/Z + 16 Coverage; Better Edge Quality at Lower Cost Than MSAA with Same C/Z Count
  - ▸ *CG use:* NVIDIA Maxwell/Pascal era; largely superseded by TAA in modern pipelines
- 4.4.2.4 Morphological AA (MLAA, SMAA, FXAA, CMAA): Post-Process Edge Detection + Blur Along Edges; No Extra Samples (Cheap); Cannot Recover Sub-Pixel Detail; May Blur Text
  - ▸ *CG use:* FXAA (cheapest, most blurry); SMAA (best quality/speed balance for post-process AA); CMAA (conservative, less blur, sharper)

#### 4.4.3 Temporal Anti-Aliasing (TAA)
- 4.4.3.1 TAA Core Algorithm: For Frame n, Jitter Projection Matrix by Sub-Pixel Offset (Halton Sequence); Accumulate 4-8 Historical Frames via Exponential Moving Average; Reproject Using Motion Vectors; Reject Disoccluded/Changed Pixels
  - ▸ *CG use:* The dominant AA in modern games (UE4/UE5 TAA, Unity TAA); effectively gives SSAA quality at MSAA cost; handles shader aliasing that MSAA cannot
- 4.4.3.2 Motion Vector Computation: Per-Pixel Motion = Current Frame Screen Position − Previous Frame Screen Position (After Applying Previous Frame's Camera + Object Transform)
  - ▸ *CG use:* From vertex shader (compute current + previous clip position); stored in G-Buffer or velocity buffer
- 4.4.3.3 TAA Artifacts: Ghosting (Insufficient Rejection of Changed Pixels → Old Frame Bleed-Through); Flicker/Instability (Too-Aggressive Clamping → Temporal Information Lost → Aliasing Returns); Blur (Accumulation of Reconstruction Filter)
  - ▸ *CG use:* Modern TAA: adaptive color bounding box clamping; variance-guided temporal accumulation; DLSS/FSR as super-resolution TAA variant
- 4.4.3.4 DLSS / FSR / XeSS — Temporal Super-Resolution: Same Core as TAA but Upscales (e.g., 1080p→4K); Neural Network (DLSS/XeSS) or Analytical (FSR) Reconstruction; Frame Generation (DLSS 3/FSR 3 — Interpolate Between Rendered Frames)
  - ▸ *CG use:* DLSS 3.5 Ray Reconstruction: combined denoising + upscaling; FSR 3: open, cross-vendor; XeSS: Intel Arc optimized, DP4a fallback

#### 4.4.4 Advanced AA Techniques
- 4.4.4.1 Variable Rate Shading (VRS): Shade at Lower Rate in Low-Contrast/Peripheral Regions; Tier 1: Per-Draw Rate; Tier 2: Per-Pixel Rate via Screen-Space Image
  - ▸ *CG use:* VR foveated rendering (full res at gaze, reduced at periphery); content-adaptive shading (sky, flat walls → 2×2 coarse shading)
- 4.4.4.2 Subpixel Morphological AA: For RGB Subpixel Layout (LCD Screens); Exploit Individual R,G,B Subpixel Positions for 3× Horizontal Resolution
  - ▸ *CG use:* Font rendering (ClearType, FreeType); UI text sharpness; limited to LCD displays

> 📚 **GitHub Repos:** [NVIDIAGameWorks/DLSS](https://github.com/NVIDIA/DLSS) — DLSS Super Resolution SDK; [GPUOpen-Effects/FidelityFX-FSR2](https://github.com/GPUOpen-Effects/FidelityFX-FSR2) ![Stars](https://img.shields.io/github/stars/GPUOpen-Effects/FidelityFX-FSR2?style=flat) — FSR 2 open-source
>
> 📖 **Textbooks:** *Real-Time Rendering* — Ch. 5 (Visual Appearance), Ch. 21 (Post-Processing)

---

### 4.5 Shading Models & Image-Based Lighting

#### 4.5.1 Real-Time Shading Techniques
- 4.5.1.1 Deferred Shading: Geometry Pass (G-Buffer: Albedo, Normal, Roughness/Metalness, Depth) → Lighting Pass (Full-Screen Quad: For Each Light, Sample G-Buffer, Compute BRDF); Decouples Geometry Complexity from Lighting
  - ▸ *CG use:* Dominant for scenes with many dynamic lights; G-Buffer bandwidth is the bottleneck; transparent objects require separate forward pass
- 4.5.1.2 Forward+ (Tiled Forward Shading): Screen Divided into Tiles (e.g., 16×16 pixels); Compute Shader: Per-Tile Light List (Test Light AABB Against Tile Depth Range) → Store in Light Grid → Fragment Shader Iterates Only Visible Lights
  - ▸ *CG use:* Combines forward rendering benefits (MSAA, transparency, varied materials) with many-light support; Unity HDRP uses Clustered Forward
- 4.5.1.3 Clustered Shading: 3D Subdivision of View Frustum (Screen Tiles × Depth Slices); Light Assignment to Clusters; More Fine-Grained Culling than Forward+
  - ▸ *CG use:* Clustered Deferred (UE5) or Clustered Forward; handles very deep scenes better than 2D tiled
- 4.5.1.4 Visibility Buffer (V-Buffer): Instead of Material Properties, Store Only Triangle ID + Barycentrics; Material Evaluation Deferred via Lookup from ID; Texture Fetch in Lighting Pass Instead of G-Buffer
  - ▸ *CG use:* Reduces G-Buffer bandwidth; enables arbitrary material complexity in deferred context; UE5 Nanite uses visibility buffer

#### 4.5.2 Image-Based Lighting (IBL)
- 4.5.2.1 Environment Map Representation: Cubemap (6 Faces, Omnidirectional) or Equirectangular (2:1, HDR); Captured via 360° Camera or Rendered
  - ▸ *CG use:* Realistic outdoor lighting without explicit sky model; indoor lighting from HDR photographs; reflective object environment mapping
- 4.5.2.2 Diffuse IBL (Irradiance Map): E(n) = ∫_{H²} L_i(ω) max(n·ω, 0) dω; Precompute via Spherical Harmonics (Typically 3rd Order / 9 Coefficients = Good Enough for Diffuse); GPU: Convolve Cubemap to Generate Irradiance Map
  - ▸ *CG use:* PBR ambient term; smooth indirect lighting on all surfaces; SH representation stores irradiance in just 9 floats
- 4.5.2.3 Specular IBL (Prefiltered Environment Map): Cook-Torrance BRDF Has Two Parameters (Roughness α, View Direction Angle); Precompute at Multiple Roughness Levels (Mipmap Chain) via GGX Importance Sampling; Store in Cubemap Mip Levels
  - ▸ *CG use:* Roughness-dependent environment reflections; glossy/mirror surfaces reflect prefiltered environment
- 4.5.2.4 Split-Sum Approximation (Karís 2013, UE4): Separate ∫ L_i(l) f(l,v) cos θ_l dl ≈ (∫ L_i(l) D(l,v) dl) × (Precomputed BRDF LUT2D); LUT2D: Input (cos θ_v, Roughness) → Output (F₀ Scale, F₀ Bias)
  - ▸ *CG use:* THE real-time IBL standard; separates environment prefiltering from BRDF integration; precomputed 2D LUT fits in 128×128 RG16 texture
- 4.5.2.5 Parallax-Corrected Cubemaps: Box Projection — Reflect Ray Against Proxy Geometry (OBB around Capture Location); Corrects Local Reflections (Indoor Room Reflection Doesn't Show Sky Outside)
  - ▸ *CG use:* Interior environment reflections (mirrors in rooms); UE5 Reflection Captures with box projection

#### 4.5.3 Light Source Types
- 4.5.3.1 Analytical Light Types: Directional (Sun, Constant Direction, No Attenuation), Point/Omni (Radial Falloff 1/(d²+1) or Smoothstep), Spot (Cone with Inner/Outer Angle + Falloff), Area/Rect Lights (Most Realistic, Estimate via LTC or Monte Carlo)
  - ▸ *CG use:* Every game engine implements these; area lights approximated via Linearly Transformed Cosines (LTC — Heitz 2016) for real-time
- 4.5.3.2 IES Profiles: Illuminating Engineering Society Format; Measured Real-World Light Fixture Intensity Distribution (Tabulated); Architectural Lighting Standard
  - ▸ *CG use:* Architectural visualization; accurately reproducing real-world light fixtures in rendering
- 4.5.3.3 Many-Light Rendering: Thousands to Millions of Dynamic Lights; ReSTIR (Direct Illumination: Spatiotemporal Reservoir Resampling — Bitterli et al. 2020); Stochastic Light Selection
  - ▸ *CG use:* UE5 MegaLights (SIGGRAPH 2025); RTXDI; real-time dynamic lighting from emissive particles, neon signs, city lights

> 📚 **GitHub Repos:** [google/filament](https://github.com/google/filament) ![Stars](https://img.shields.io/github/stars/google/filament?style=flat) — Complete PBR+IBL implementation; [NVIDIAGameWorks/RTXDI](https://github.com/NVIDIAGameWorks/RTXDI) — ReSTIR-based lighting
>
> 📖 **Textbooks:** *Real-Time Rendering* — Ch. 9 (PBR), Ch. 10 (IBL); *GPU Gems 3* — Ch. 14 (Split-Sum Approximation)

---

### 4.6 Shadow Algorithms

#### 4.6.1 Shadow Mapping
- 4.6.1.1 Standard Shadow Map: Render Depth from Light's Perspective → Store in Shadow Map Texture → For Each Visible Point, Transform to Light Space, Compare z_pixel > z_map (In Shadow) or < (Lit); Depth Bias Required to Prevent Self-Shadowing (Shadow Acne)
  - ▸ *CG use:* Ubiquitous real-time shadow technique; aliasing on shadow edges is the primary artifact
- 4.6.1.2 Percentage Closer Filtering (PCF — Reeves 1987): For Each Shadow Test, Sample Multiple Texels and Filter Binary Shadow Results (Percentage of Lit Samples); Soft Shadow Edges
  - ▸ *CG use:* GPU hardware PCF (bilinear PCF on 2×2 block); softens shadow edges; noise at high filter widths
- 4.6.1.3 Percentage Closer Soft Shadows (PCSS — Fernando 2005): Estimate Blocker Distance (Average Depth of Occluders in Search Region); Map Blocker Distance → Penumbra Size; PCF with Adaptive Kernel Size (Larger = Softer Shadow)
  - ▸ *CG use:* Realistic soft shadows (narrow near contact point, wide far from contact); physically plausible penumbra
- 4.6.1.4 Cascaded Shadow Maps (CSM): Multiple Shadow Maps for Different Distance Ranges; Near Cascade: High Resolution, Small Area; Far Cascade: Low Resolution, Large Area; 2-8 Cascades
  - ▸ *CG use:* Outdoor directional light shadows (sun); every open-world game uses CSM; cascades distributed logarithmically or by PSSM (Parallel-Split Shadow Maps)
- 4.6.1.5 Variance Shadow Maps (VSM) / Exponential SM (ESM) / Moment SM (MSM): Store Statistical Moments of Depth Distribution (Not Just Single Depth); Filterable (Can Be Blurred by Standard Texture Filtering); Light Bleeding Artifact
  - ▸ *CG use:* VSM/ESM: soft shadows with standard mipmap+blur; MSM (4 moments = 128-bit): significantly reduces light bleeding; practical for production with MSM

#### 4.6.2 Advanced Shadow Techniques
- 4.6.2.1 Virtual Shadow Maps (UE5): 16K×16K Virtual Shadow Map Page Table; Per-Light Page Allocation; Only Render Pages Touched by Visible Geometry; Clipmap for Directional Light
  - ▸ *CG use:* UE5 virtual shadow maps; film-quality shadows at real-time; eliminates cascade artifacts and resolution limits
- 4.6.2.2 Ray-Traced Shadows (DXR 1.1 / Vulkan RT): Cast Shadow Ray from Surface Point Toward Light; Exact Hard Shadows; Soft Shadows via Multiple Random Rays (Stochastic Sampling) + Denoising
  - ▸ *CG use:* Accurate contact shadows; no shadow map artifacts (no bias, no resolution limits); expensive for soft shadows
- 4.6.2.3 Shadow Volumes (Carmack's Reverse / Depth-Fail): Extrude Silhouette Edges from Light Away from Light (Shadow Volume Geometry); Stencil Buffer: Increment for Front-Facing, Decrement for Back-Facing; Stencil ≠ 0 → In Shadow
  - ▸ *CG use:* Doom 3 (2004) used this; perfect pixel-accurate hard shadows; extremely fill-rate intensive; largely historical now
- 4.6.2.4 Ambient Occlusion Shadows: SSAO (Screen-Space AO — Crytek 2007): For Each Pixel, Sample Random Points in Hemisphere Above Surface, Test Depth Buffer for Occlusion; GTAO (Ground Truth AO — Jimenez 2016): Physically-Based Formulation with Cosine Weighting and Accurate Occlusion Falloff
  - ▸ *CG use:* Contact shadows for ambient lighting; small-scale occlusion (creases, corners); complements direct shadows (which handle large occluders)

> 📚 **GitHub Repos:** [GPUOpen-Effects/FidelityFX-ShadowDenoiser](https://github.com/GPUOpen-Effects) — AMD's ray-traced shadow denoiser
>
> 📖 **Textbooks:** *Real-Time Rendering* — Ch. 7 (Shadows); *Real-Time Shadows* — Eisemann et al.

---

### 4.7 Real-Time Global Illumination

#### 4.7.1 Precomputed Methods
- 4.7.1.1 Lightmaps: Bake Static Global Illumination into Textures (Offline Path Tracing → Texture Atlas → Real-Time Lookup); Binary Radiosity Lightmaps for Color + Directional Lightmaps for Specular
  - ▸ *CG use:* Static environment lighting in virtually all games; Enlighten, Beast, and GPU Lightmass are industry-standard lightmappers
- 4.7.1.2 Light Probes & Irradiance Volumes: Scatter Spherical Harmonic Probes Throughout Scene; Interpolate Probe Values at Runtime for Dynamic Object Lighting; Tetrahedral or Trilinear Interpolation Between Probes
  - ▸ *CG use:* Dynamic character/object lighting that matches static environment; UE5 automatically places probes; Unity Light Probes
- 4.7.1.3 Precomputed Radiance Transfer (PRT — Sloan et al. 2002): Precompute Light Transport Operator T (Per-Vertex or Per-Texel) as Transfer Matrix or SH Coefficients; At Runtime: Lighting_vector · T → Outgoing Radiance; Supports Dynamic Lighting, Static Geometry
  - ▸ *CG use:* Dynamic environment lighting on static scenes; shadowed diffuse+glossy transfer; limited by precomputation time and memory
- 4.7.1.4 Reflection Probes: Capture Cubemap at Probe Location; Apply Parallax Correction (Box Projection); Blend Between Adjacent Probes for Seamless Transitions
  - ▸ *CG use:* Reflections on dynamic objects; UE5 Reflection Capture with box projection blending

#### 4.7.2 Real-Time Methods
- 4.7.2.1 Screen-Space Methods (SSAO, SSR, SSGI): Work Entirely in Screen Space Using Depth+Normal Buffer as Proxy Geometry; Fast but Cannot Handle Off-Screen Information
  - ▸ *CG use:* SSAO: ubiquitous contact shadow approximation; SSR: reflections on floors/walls from visible geometry; SSGI: diffuse bounce from visible surfaces
- 4.7.2.2 Reflective Shadow Maps (RSM — Dachsbacher & Stamminger 2005): Treat Shadow Map Texels as Virtual Point Lights (VPLs); Each Texel Emits Indirect Light in Hemisphere; Many VPLs (~Thousands) → Indirect Illumination
  - ▸ *CG use:* First-bounce indirect from dominant light source; used in real-time games for interactive GI; basis for LPV
- 4.7.2.3 Light Propagation Volumes (LPV — Kaplanyan 2009): Inject VPL Radiance into 3D Grid of SH Coefficients; Iterative Propagation (Diffusion) Through Grid Neighbors → Accumulated Indirect Light Distribution; Read SH at Object Position for Indirect
  - ▸ *CG use:* CryEngine real-time GI; dynamic bounce light (explosions, moving lights affecting environment)
- 4.7.2.4 Voxel Cone Tracing (VXGI — Crassin 2011): Voxelize Scene (Octree of Opacity+Emissive); Trace Cones (Not Rays) from Surface; Wider Cone for Diffuse (Capture More Voxels), Narrow for Specular; Mipmap Voxel Hierarchy Provides Prefiltering
  - ▸ *CG use:* NVIDIA VXGI (2015); diffuse + specular indirect at real-time; UE5 partially superseded by Lumen
- 4.7.2.5 DDGI (Dynamic Diffuse Global Illumination — Majercik et al. 2021): Probe-Based GI with Ray Tracing; Probes Store Irradiance + Depth (Visibility Info); Ray Trace from Probes to Update; Spatiotemporal Blending Between Probe Updates
  - ▸ *CG use:* RTXGI (NVIDIA SDK); real-time diffuse GI with ray tracing hardware; scales well from low to high ray budgets
- 4.7.2.6 Lumen (UE5): Hybrid GI System; Software Ray Tracing: Signed Distance Field (Mesh Distance Fields → SDF Tracing); Hardware Ray Tracing: DXR/Vulkan RT for Accuracy; Surface Cache: Cache Light on Cards (Simplified Geometry Proxy); Radiance Cache: Probe Grid for Final Gather
  - ▸ *CG use:* UE5's production real-time GI; handles dynamic geometry, emissive materials, sky changes; ~30 FPS on consoles

> 📚 **GitHub Repos:**
> - [NVIDIAGameWorks/RTXGI](https://github.com/NVIDIAGameWorks/RTXGI) ![Stars](https://img.shields.io/github/stars/NVIDIAGameWorks/RTXGI?style=flat) — DDGI reference implementation
> - [SlightlyMad/VolumetricLights](https://github.com/SlightlyMad/VolumetricLights) — Voxel-based GI experiments
>
> 📖 **Textbooks:** *Real-Time Rendering* — Ch. 11 (Global Illumination); *GPU Pro* series (multiple GI articles)

---

### 4.8 Ray Tracing Fundamentals

#### 4.8.1 Ray Generation & Intersection
- 4.8.1.1 Ray Generation: Camera Model → Primary Ray Direction Per Pixel; r(t) = o + t d (t > t_min); Pinhole Camera: Direction = normalize( (x·right + y·up) · tan(fov/2) + forward ); Orthographic: Origin Varies, Direction = −forward
  - ▸ *CG use:* Ray tracing starts here; every path tracer generates ~10⁶ to 10⁹ primary rays per frame
- 4.8.1.2 Ray-Sphere Intersection: Solve ‖o + t d − c‖² = r² → Quadratic a t² + b t + c = 0, a = d·d, b = 2 d·(o−c), c = ‖o−c‖²−r²; Discriminant < 0 → Miss; t = min(t₁,t₂) If Both > t_min
  - ▸ *CG use:* Sphere primitives; analytic analytical; bounding sphere intersection test
- 4.8.1.3 Möller-Trumbore Ray-Triangle (1997): Compute Barycentrics (u,v) + Distance t via Solving Linear System; Uses Cramer's Rule on Edge Vectors; Back-Face Culling via t < 0; Most Performant Triangle Intersection
  - ▸ *CG use:* THE algorithm — GPU RT cores implement hardware-accelerated ray-triangle intersection
- 4.8.1.4 Ray-AABB (Slab Method — Kay & Kajiya 1986): Intersect Ray with 3 Pairs of Parallel Planes (x_min, x_max, y_min, y_max, z_min, z_max); Compute t_enter = max(t_xmin, t_ymin, t_zmin), t_exit = min(t_xmax, t_ymax, t_zmax); Hit if t_enter ≤ t_exit and t_exit ≥ t_min
  - ▸ *CG use:* BVH node intersection test; GPU RT core box intersection hardware
- 4.8.1.5 Ray Marching (Sphere Tracing — Hart 1996): For Implicit Surface f(x)=0: x_{n+1} = x_n + f(x_n) · d; Distance f(x_n) is Conservative Lower Bound; Converges When f(x_n) < ε
  - ▸ *CG use:* SDF rendering (Shadertoy, Dreams); volumetric ray marching; robust for complex implicit geometry

#### 4.8.2 Whitted-Style & Distributed Ray Tracing
- 4.8.2.1 Whitted (1980): Primary Ray → Hit → Reflection Ray + Refraction Ray + Shadow Ray (to Each Light) → Recurse; Perfect Specular Reflection + Refraction + Hard Shadows; First Practical Ray Tracing Algorithm
  - ▸ *CG use:* Simple mirror+glass scenes; basis for recursive ray tracing; limited to specular transport (no diffuse interreflection)
- 4.8.2.2 Distributed Ray Tracing (Cook et al. 1984): Sample Multiple Random Rays Per Effect: Soft Shadows (N Rays Across Light Area), Glossy Reflections (N Rays Within Reflection Cone), Motion Blur (N Rays at Random Times Within Frame), Depth of Field (N Rays Through Lens Aperture)
  - ▸ *CG use:* The bridge from Whitted to path tracing; Monte Carlo sampling introduced to rendering; film-quality effects
- 4.8.2.3 Fresnel at Ray Intersection: Reflectance R via Fresnel Equations (Dielectric: Full Fresnel or Schlick, Conductor: Complex IOR → Colored); Transmission T = 1−R for Dielectrics; Russian Roulette or Branching (Choose One Path, Weight by Probability)
  - ▸ *CG use:* Glass: trace reflection OR refraction (not both — explosive recursion); Schlick for real-time, full Fresnel for offline

> 📚 **GitHub Repos:** [ssloy/tinyraytracer](https://github.com/ssloy/tinyraytracer) ![Stars](https://img.shields.io/github/stars/ssloy/tinyraytracer?style=flat) — Build a ray tracer from scratch
>
> 📖 **Textbooks:** *Physically Based Rendering* — Ch. 3-4 (Ray tracing fundamentals); *Ray Tracing Gems* — Haines & Akenine-Möller

---

### 4.9 Path Tracing & Global Illumination

#### 4.9.1 Path Tracing Core
- 4.9.1.1 Random Walk Light Transport: Each Path: Camera → Random Bounce Direction (BRDF Sampling) → Next Intersection → Repeat; Terminal via Russian Roulette (Probability q, Weight 1/(1−q)); Estimate: L = Σ_{path} weight · emission_at_hit; Unbiased
  - ▸ *CG use:* The gold standard for film/VFX rendering; converges to correct solution; noise ∝ 1/√N samples
- 4.9.1.2 Next Event Estimation (NEE / Direct Lighting): At Each Path Vertex, Explicitly Sample Light Source (Connect to Random Light Point); Shadow Ray Test Visibility;Separate Direct (Low Variance) from Indirect (High Variance)
  - ▸ *CG use:* Critical for efficient path tracing; without NEE, hitting small light sources by chance is nearly impossible
- 4.9.1.3 Bidirectional Path Tracing (BDPT — Lafortune & Willems 1993, Veach & Guibas 1994): Trace Light Subpath from Light + Camera Subpath from Camera; Connect All Vertex Pairs via Visibility Test; MIS Weights for All Connection Strategies
  - ▸ *CG use:* Better than unidirectional PT for scenes dominated by indirect light (interior with window, caustics from mirror)
- 4.9.1.4 Photon Mapping (Jensen 1996): Two-Pass: (1) Photon Tracing: Emit Photons from Lights, Store at Diffuse Hits (Photon Map = 3D Point Set + Power), (2) Rendering: PT with Radiance Estimate from Nearest Photons (Density Estimation)
  - ▸ *CG use:* Caustics (focused light patterns through glass/water — very difficult for PT alone); participating media; progressive photon mapping for consistent results

#### 4.9.2 Advanced Light Transport
- 4.9.2.1 Vertex Connection & Merging (VCM — Hachisuka et al. 2012): Unifies BDPT + Photon Mapping; Path Vertices Either Connected (If Distance > r → BDPT Contribution) or Merged (If Distance < r → Photon Map Contribution); MIS Across All Strategies
  - ▸ *CG use:* Combined strengths: BDPT for smooth indirect + photon mapping for caustics + SDS paths; production renders use VCM or variants
- 4.9.2.2 Metropolis Light Transport (MLT — Veach & Guibas 1997): MCMC Sampling of Path Space; Current Path → Mutate (Perturb Vertices, Regenerate Subpath) → Accept/Reject (Metropolis Rule); Explores Path Space Efficiently Around Important Paths
  - ▸ *CG use:* Extreme lighting scenarios (thin beam of light through keyhole illuminating room); hard to use in production (non-uniform convergence, flickering in animations)
- 4.9.2.3 Manifold Next Event Estimation (MNEE — Hanika et al. 2015, Zeltner et al. 2020): Find Specular Path Connecting Two Points on Diffuse Surfaces via Specular Vertices; Solve Constrained Optimization on Manifold of Valid Specular Paths (Newton's Method on Constraint Manifold)
  - ▸ *CG use:* Efficiently find specular-diffuse-specular (SDS) paths (underwater caustics on pool floor, light through glass onto table); production rendering caustic solution
- 4.9.2.4 Path Guiding: Learn Incident Radiance Distribution (SD-Tree or Neural Network); Use Learned Distribution for Importance Sampling at Each Bounce → Dramatically Reduce Variance; Online Learning During Rendering
  - ▸ *CG use:* Production path tracing with path guiding (Arnold, RenderMan, Cycles); neural path guiding (Müller et al. 2020) — MLP predicts sampling distribution

> 📚 **GitHub Repos:** [mmp/pbrt-v4](https://github.com/mmp/pbrt-v4) ![Stars](https://img.shields.io/github/stars/mmp/pbrt-v4?style=flat) — Complete BDPT, photon mapping, VCM, MLT implementations
>
> 📖 **Textbooks:** *Physically Based Rendering* — Pharr et al. (Ch. 13-16); *Advanced Global Illumination* — Dutré, Bekaert, Bala

---

### 4.10 Real-Time Ray Tracing Hardware & APIs

#### 4.10.1 Hardware Acceleration
- 4.10.1.1 RT Cores (NVIDIA Turing 2018 → Blackwell 2024): Fixed-Function BVH Traversal + Ray-Triangle Intersection; 1st Gen: BVH Traversal Only; 2nd Gen (Ampere): Triangle Intersection; 3rd Gen (Ada): Opacity Micromap, Displacement Micromap, SER; 4th Gen (Blackwell): Further Acceleration
  - ▸ *CG use:* Enables real-time ray tracing (RTX); each generation approximately doubles RT throughput
- 4.10.1.2 Two-Level Acceleration (TLAS + BLAS): Top-Level (TLAS): Instance-Level, References BLAS + Transform; Bottom-Level (BLAS): Per-Object Geometry, Static After Build; Build TLAS Once, Refit BLAS for Animation
  - ▸ *CG use:* DXR 1.1 / Vulkan RT standard model; animated characters: refit BLAS per frame without rebuilding TLAS
- 4.10.1.3 Shader Execution Reordering (SER — NVIDIA Ada): Reorder Divergent Ray Threads (Hit Different Materials → Different Shaders) into Coherent Groups; Avoid GPU Warp Divergence; Up to 2× Speedup for Incoherent Rays
  - ▸ *CG use:* Path tracing with varied materials (glass, diffuse, metal all in one scene); SER groups rays by material for coherent execution

#### 4.10.2 Ray Tracing APIs
- 4.10.2.1 DXR (DirectX Raytracing): DXR 1.0 (Turing): Ray Generation + Closest-Hit + Any-Hit + Miss Shaders; Shader Table (Per-Geometry Shader Binding); DXR 1.1 (Ampere): Inline Ray Tracing (No Shader Table — Manual Traversal), ExecuteIndirect for GPU-Driven Dispatch
  - ▸ *CG use:* Windows PC ray tracing; inline RT for simpler integration in existing compute pipelines
- 4.10.2.2 Vulkan Ray Tracing (VK_KHR_ray_tracing_pipeline / VK_KHR_ray_query): RT Pipeline: Similar to DXR 1.0 Shader Model; Ray Query: Inline, No Separate Shader Stages → Use Inside Any Compute/Fragment Shader; Cross-Platform (Windows, Linux, Some Android)
  - ▸ *CG use:* Steam Deck, Linux gaming, Android high-end; ray query for selective ray casting in existing shaders
- 4.10.2.3 OptiX (NVIDIA): Higher-Level API on Top of CUDA; Automatic BVH Construction, Denoiser Integration, AI Acceleration; Used by Major Renderers (Arnold, V-Ray, Octane, Cycles, Blender)
  - ▸ *CG use:* Production offline rendering; rapid prototyping; AI denoising integration
- 4.10.2.4 Metal Ray Tracing (Apple): M3+ Hardware RT Acceleration; Metal RT API (Intersection Query + Raytracing Pipeline); Integrated with Apple Silicon GPU Architecture
  - ▸ *CG use:* macOS/iOS rendering; Pro apps (Octane X, Redshift Metal); Apple Vision Pro spatial computing

> 📚 **GitHub Repos:**
> - [NVIDIAGameWorks/dxr-tutorials](https://github.com/NVIDIAGameWorks/dxr-tutorials) — DXR tutorial series
> - [SaschaWillems/Vulkan](https://github.com/SaschaWillems/Vulkan) ![Stars](https://img.shields.io/github/stars/SaschaWillems/Vulkan?style=flat) — Comprehensive Vulkan examples including ray tracing
> - [mmp/pbrt-v4](https://github.com/mmp/pbrt-v4) — GPU ray tracing backend
>
> 📖 **Textbooks:** *Ray Tracing Gems I & II* — Haines & Akenine-Möller (Practical RT techniques); *Physically Based Rendering* — GPU chapters

---

### 4.11 Denoising & Reconstruction

#### 4.11.1 Monte Carlo Denoising
- 4.11.1.1 The Denoising Problem: Path-Traced Images Have High-Frequency Noise (MC Variance); Denoiser Must Smooth Noise While Preserving Edges, Textures, and Specular Detail
  - ▸ *CG use:* 1 sample-per-pixel (1 spp) path tracing + denoising ≈ 1000 spp without denoising in visual quality
- 4.11.1.2 Spatial Denoising: Bilateral Filter (Weighted Spatial Average — Weight = spatial_distance × color_difference × normal_difference); À-Trous Wavelet (Iterative Kernel Dilation Preserves Edges); Guided Filter (Local Linear Model, O(N) Complexity)
  - ▸ *CG use:* Fast but limited (1 frame of data); blurry loss of high-frequency detail
- 4.11.1.3 Temporal Denoising: Accumulate Pixel History Over Multiple Frames; Reproject via Motion Vectors; Exponential Moving Average with Adaptive α Based on Disocclusion Detection; Temporal Lag (Ghosting) Is the Primary Artifact
  - ▸ *CG use:* Dramatically increases effective sample count (8 frame history ≈ 8× more samples); must reject disoccluded pixels to prevent ghosting
- 4.11.1.4 SVGF (Spatiotemporal Variance-Guided Filter — Schied et al. 2017): Hierarchical À-Trous Wavelet with Variance-Guided Bandwidth; Uses Temporal Color Moments (First + Second Moments) for Robust History; Fast Filtering Guided by G-Buffer
  - ▸ *CG use:* Real-time path tracing denoising; basis for many production denoisers
- 4.11.1.5 ReBlur / NRD (NVIDIA Real-Time Denoisers — 2021/2023): ReBlur: Physically-Based Blur Kernel Derived from MC Statistics; Relax: Advanced Spatial-Temporal Accumulation with Disocclusion Handling; SIGMA: Shadow-Specific Denoiser
  - ▸ *CG use:* NVIDIA RTX denoising SDK; bundled with RTXGI; used in AAA games (Cyberpunk 2077 RT Overdrive, Alan Wake 2)

#### 4.11.2 Neural Denoising
- 4.11.2.1 OptiX Denoiser (NVIDIA): CNN-Based; Input: Noisy Beauty + Albedo + Normal (Optional); 2.5D U-Net Architecture; Trained on Synthetic Data; GPU-Accelerated via Tensor Cores
  - ▸ *CG use:* Production offline rendering (Arnold, V-Ray, RenderMan); near-instant denoising of path-traced frames
- 4.11.2.2 OIDN (Intel Open Image Denoise): CPU-Optimized CNN; Input: Beauty + Albedo + Normal; Lightweight Architecture (Fast CPU Inference); Open Source
  - ▸ *CG use:* Blender Cycles denoising; cross-platform (no GPU required); fast enough for interactive rendering
- 4.11.2.3 DLSS Ray Reconstruction (NVIDIA 2023): Combined Denoising + Super-Resolution; Input: Noisy Path-Traced Image + G-Buffer Features + Motion Vectors → Transformer Network → Denoised + Upscaled Output; Trained on 5× More Data Than DLSS 3
  - ▸ *CG use:* Cyberpunk 2077 Path Tracing mode; Alan Wake 2; denoises + upscales path tracing in a single network

> 📚 **GitHub Repos:**
> - [NVIDIAGameWorks/RayTracingDenoiser](https://github.com/NVIDIAGameWorks/RayTracingDenoiser) — NRD reference implementation
> - [OpenImageDenoise/oidn](https://github.com/OpenImageDenoise/oidn) ![Stars](https://img.shields.io/github/stars/OpenImageDenoise/oidn?style=flat) — Intel's CPU neural denoiser
>
> 📖 **Textbooks:** *Ray Tracing Gems* — Denoising chapters; NRD documentation

---

### 4.12 Post-Processing, Lens Effects & Display

#### 4.12.1 Tone Mapping & HDR Display
- 4.12.1.1 Why Tone Mapping?: HDR Rendering Produces Radiance Values [0, ∞); Display Accepts [0,1] (SDR) or [0,~10000 nits] (HDR with PQ/HLG); Tone Mapping = Compressing Dynamic Range While Preserving Perceived Contrast and Color
  - ▸ *CG use:* Every rendered frame passes through a tone mapper; incorrect tone mapping destroys artistic intent
- 4.12.1.2 Reinhard (2002): L_d = L/(1+L); Global Operator; Simple, Photographically Inspired; Can Desaturate at High Luminance (Fix: Apply on Luminance Only)
  - ▸ *CG use:* Popular early HDR tone mapper; largely superseded by filmic operators
- 4.12.1.3 Filmic Tone Mapping (ACES / Uncharted 2): S-Curve Preserving Shadows and Highlights with Smooth Roll-Off; Desaturates to White at Extreme Values; ACES RRT (Reference Rendering Transform) for Film/VFX
  - ▸ *CG use:* ACES is the VFX industry standard; UE4 Filmic (Hable), Unity ACES; cinematic look out of the box
- 4.12.1.4 HDR Display Pipeline (HDR10, Dolby Vision, scRGB): Authoring: Scene-Referred Linear; Grading: Display-Referred with PQ (ST.2084 — Perceptual Quantizer) or HLG; Metadata: MaxFALL, MaxCLL, Color Volume
  - ▸ *CG use:* AAA games shipping with HDR support; Dolby Vision dynamic metadata per scene; console and PC HDR standards

#### 4.12.2 Lens & Camera Effects
- 4.12.2.1 Depth of Field (DoF): Thin Lens Model → Circle of Confusion (CoC) Radius ∝ |1/z_focus − 1/z_object|; Scatter Pixel Within CoC Disc → Physical Bokeh (Polygonal Aperture Shape via Sample Points on Polygonal Disc)
  - ▸ *CG use:* Cinematic rendering; photography simulation; scatter-as-gather vs. accumulate methods
- 4.12.2.2 Motion Blur: Camera Motion Blur (Per-Frame Velocity Vector, Scatter Along Motion Path); Object Motion Blur (Transform Object by Velocity × Random Time Within Exposure); Deformation Motion Blur (Interpolate Vertex Positions)
  - ▸ *CG use:* Film rendering at 24 FPS requires motion blur for smooth motion; game rendering at 60+ FPS → per-pixel velocity buffer
- 4.12.2.3 Bloom: Extract Bright Areas (Threshold: L > 1) → Gaussian Blur Pyramid (Multiple Sizes) → Composite Over Original; Produces Glow Around Bright Objects; Physically: Lens + Ocular Scatter
  - ▸ *CG use:* Neon signs, sunlight through trees, car headlights at night; every game uses bloom
- 4.12.2.4 Lens Flare: Ghost Reflections (Even-Order Bounces Between Lens Elements → Reflected Image of Aperture); Diffraction Spikes (Star Pattern from Aperture Blades); Veiling Glare (Scatter in Lens → Overall Contrast Reduction)
  - ▸ *CG use:* Cinematic lens flare (JJ Abrams style); physical lens simulation via ray tracing through lens model
- 4.12.2.5 Chromatic Aberration: Lateral (Transverse): Different Wavelengths Magnified Differently → Color Fringes at Image Edges; Longitudinal (Axial): Different Wavelengths Focus at Different Depths → Purple/Green Fringing in Out-of-Focus Regions
  - ▸ *CG use:* Cinematic realism; VR lens correction; often overused as stylistic effect
- 4.12.2.6 Vignette, Film Grain, Lens Distortion: Vignette (Edge Darkening — cos⁴ Law + Mechanical Vignetting); Film Grain (Perceptual Noise — Analog Film Emulation); Barrel/Pincushion Distortion
  - ▸ *CG use:* Cinematic post-processing; VR pre-distortion correction; nostalgic/period-piece aesthetics

#### 4.12.3 Color Grading & Final Output
- 4.12.3.1 Color Grading: Lift/Gamma/Gain (ASC CDL); Curves (S-Curve for Contrast); HSL (Hue/Saturation/Lightness) Adjustments; LUT (Look-Up Table — 3D LUT, Typically 33³ = 35,937 Entries, Trilinear Interpolation)
  - ▸ *CG use:* Final frame look; consistent color across shots; LUT is the standard interchange format (export from DaVinci Resolve → import into game engine)
- 4.12.3.2 Display Output: sRGB (Fragment Shader Writes Linear, Hardware Applies sRGB EOTF via Framebuffer sRGB Format); HDR10/HLG (Metadata-Driven Display Mapping); scRGB (16-Bit Linear, No EOTF — HDR Monitor Decodes)
  - ▸ *CG use:* Correct gamma handling throughout pipeline; linear-space rendering + final encode is mandatory for PBR

> 📚 **GitHub Repos:**
> - [GPUOpen-Effects/FidelityFX-Denoiser](https://github.com/GPUOpen-Effects) — AMD's denoising and post-processing effects
> - [ampas/aces-dev](https://github.com/ampas/aces-dev) — Official ACES reference implementation
>
> 📖 **Textbooks:** *Real-Time Rendering* — Ch. 8 (Post-Processing); *High Dynamic Range Imaging* — Reinhard et al. (Tone mapping, HDR display)

---


## Chapter 5 · Neural, Differentiable & Inverse Rendering

*The 2020s rendering revolution — differentiable pipelines, neural radiance fields, Gaussian splatting, and diffusion-based 3D generation. `▸ CG use:` links each technique to its practical impact.*

> 💡 **Top-Level References:**
> - [mitsuba-renderer/mitsuba3](https://github.com/mitsuba-renderer/mitsuba3) ![Stars](https://img.shields.io/github/stars/mitsuba-renderer/mitsuba3?style=flat) — Research-grade differentiable renderer (the standard)
> - [NVlabs/instant-ngp](https://github.com/NVlabs/instant-ngp) ![Stars](https://img.shields.io/github/stars/NVlabs/instant-ngp?style=flat) — Hash encoding + NeRF/SDF training in seconds
> - [graphdeco-inria/gaussian-splatting](https://github.com/graphdeco-inria/gaussian-splatting) ![Stars](https://img.shields.io/github/stars/graphdeco-inria/gaussian-splatting?style=flat) — Original 3DGS — real-time novel view synthesis
> - [nerfstudio-project/nerfstudio](https://github.com/nerfstudio-project/nerfstudio) ![Stars](https://img.shields.io/github/stars/nerfstudio-project/nerfstudio?style=flat) — Unified NeRF/3DGS training framework

---

### 5.1 Differentiable Rendering Foundations

#### 5.1.1 Why Differentiable Rendering?
- 5.1.1.1 The Inverse Problem: Given an Image, Recover Scene Parameters (Geometry, Materials, Lighting); Traditional Approach = Manual + Heuristic; Differentiable Rendering = Render → Compare to Photo → Gradient → Optimize Parameters Automatically
  - ▸ *CG use:* Automatic material estimation from photographs; 3D reconstruction from images via gradient descent; computational design optimization
- 5.1.1.2 Forward vs. Inverse Rendering: Forward: Scene → Renderer → Image (Well-Posed, Deterministic); Inverse: Image → Optimizer → Scene Parameters (Ill-Posed, Underdetermined, Requires Priors); Differentiable Renderer = Differentiable Forward Model Enabling Gradient-Based Inverse
  - ▸ *CG use:* The bridge connecting pixels to scene understanding; enables machine learning to directly optimize 3D content
- 5.1.1.3 The Gradient Challenge: Rendering Has Discontinuities (Occlusion Boundaries, Shadows, Specular Highlights); Naive Autodiff Produces Zero Gradients at Discontinuities (0 = Not Useful); Need Specialized Gradient Estimators
  - ▸ *CG use:* This is why a "simple" differentiable renderer doesn't work — requires careful handling of discontinuities

#### 5.1.2 Gradient Estimation Strategies
- 5.1.2.1 Reparameterization: Change Integration Variable to Remove Discontinuity from Integrand; Primary Sample Space (PSS): Differentiate w.r.t. Uniform Random Numbers → Discontinuity Moves to Sampling Strategy; Used in Differentiable Path Tracing
  - ▸ *CG use:* Mitsuba 3 PSDR (Primary Sample Space Differentiable Rendering); continuous gradients despite discrete visibility changes
- 5.1.2.2 Edge Sampling / Boundary Integrals (Li et al. 2018): Discontinuity Gradient = Integral Over Object Silhouettes; Sample Points on Discontinuity Boundaries × Magnitude of Jump × Change in Boundary Location; Yields Usable Gradients for Vertex Positions
  - ▸ *CG use:* Differentiable rasterization (Redner); gradient-based mesh optimization from images (soft rasterizer); inverse geometry
- 5.1.2.3 REINFORCE (Score Function / Likelihood Ratio): ∇_θ 𝔼[f(X)] = 𝔼[f(X) ∇_θ log p_θ(X)]; Unbiased but High Variance; Works on Non-Differentiable Black Box; Antithetic Sampling for Variance Reduction
  - ▸ *CG use:* Black-box differentiable rasterization (transform any rasterizer into a differentiable one — Intel I3D 2024 Best Paper); NVIDIA Warp uses REINFORCE for non-differentiable ops
- 5.1.2.4 Control Variates for REINFORCE Variance Reduction: f(X)∇ log p(X) − β(∇ log p(X) − 𝔼[∇ log p]) (Subtract Baseline); Learned Control Variates (Neural Network Predicts Baseline)
  - ▸ *CG use:* Dramatically reduces REINFORCE variance; enables practical black-box diff-rendering

> 📚 **GitHub Repos:** [mitsuba-renderer/mitsuba3](https://github.com/mitsuba-renderer/mitsuba3) ![Stars](https://img.shields.io/github/stars/mitsuba-renderer/mitsuba3?style=flat) — PSDR, edge sampling, reparameterization; [NVIDIAGameWorks/nvdiffrast](https://github.com/NVIDIAGameWorks/nvdiffrast) ![Stars](https://img.shields.io/github/stars/NVIDIAGameWorks/nvdiffrast?style=flat) — GPU differentiable rasterization
>
> 📖 **Papers:** Li et al. *Differentiable Monte Carlo Ray Tracing through Edge Sampling* (SIGGRAPH 2018); Loubet et al. *Reparameterizing Path Space* (SIGGRAPH 2019)

---

### 5.2 Differentiable Rasterization & Path Tracing

#### 5.2.1 Differentiable Rasterization
- 5.2.1.1 Soft Rasterizer (Liu et al. 2019 — SoftRas): Replace Hard Occlusion Step with Sigmoid; Probability Each Triangle Covers Each Pixel; Gradients Flow Through Coverage Probabilities; Blurry but Smooth Gradients
  - ▸ *CG use:* Single-image 3D reconstruction; deformable mesh fitting to silhouettes; shape-from-shading via gradient descent
- 5.2.1.2 Forward Rasterization (Nvdiffrast — Laine et al. 2020): Standard Hardware Rasterization → Differentiable Interpolation of Attributes; Gradients via Barycentrics; Discontinuity Gradients Manual (Edge Sampling for Silhouette Derivatives); GPU-Optimized via CUDA/OpenGL Interop
  - ▸ *CG use:* Nvdiffrec (inverse rendering: multi-view images → mesh + PBR materials); Nvdiffmodeling; 3D deep learning training with rendering in the loop
- 5.2.1.3 DIB-R (Chen et al. 2019): Differentiable Interpolation-Based Renderer; Forward Pass = Standard Rasterization; Backward Pass = Interpolate Gradients from Pixels to Vertices via Barycentric Weights; Handles Texture + Lighting
  - ▸ *CG use:* Learning-based 3D reconstruction; face model fitting; mesh prediction from images

#### 5.2.2 Differentiable Path Tracing
- 5.2.2.1 Primary Sample Space Differentiable Rendering (PSDR — Zhang et al. 2020, 2021, 2023): Differentiate w.r.t. Uniform Random Numbers (Primary Samples) → Removes Scene-Parameter Dependency from Sampler; Handle Discontinuities via MIS Over Tangent-Space Strategies
  - ▸ *CG use:* Mitsuba 3's differentiable mode (PSDR integrator); differentiable light transport for complex scenes (caustics, participating media)
- 5.2.2.2 Radiative Backpropagation (Nimier-David et al. 2020): Adjoint Method for Radiative Transfer Equation; Propagate Adjoint Radiance from Sensor Backward Through Scene; Efficient for High-Dimensional Parameter Spaces
  - ▸ *CG use:* Mitsuba 3 adjoint integrator; efficient for scenes with many parameters (e.g., per-vertex geometry optimization)
- 5.2.2.3 Warp-Area Product (Bangaru et al. 2020): Directly Compute Discontinuity Gradient as Integral Over Silhouette in Path Space; Relationship Between Silhouette Movement and Pixel Intensity Change
  - ▸ *CG use:* Unbiased gradients for geometry optimization; handles complex visibility effects (multiple bounces, participating media)

> 📚 **GitHub Repos:** [NVIDIAGameWorks/nvdiffrast](https://github.com/NVIDIAGameWorks/nvdiffrast) ![Stars](https://img.shields.io/github/stars/NVIDIAGameWorks/nvdiffrast?style=flat) — GPU differentiable rasterizer; [mitsuba-renderer/mitsuba3](https://github.com/mitsuba-renderer/mitsuba3) — PSDR + adjoint + reparameterization integrators
>
> 📖 **Papers:** Laine et al. *Modular Primitives for High-Performance Differentiable Rendering* (SIGGRAPH Asia 2020); Nimier-David et al. *Radiative Backpropagation* (SIGGRAPH 2020)

---

### 5.3 Neural Radiance Fields (NeRF) — The 2020 Breakthrough

#### 5.3.1 NeRF Core Algorithm
- 5.3.1.1 Scene Representation: MLP F_Θ: (x, y, z, θ, φ) → (RGB_σ, Density σ); 3D Position → Density (View-Independent); 3D Position + 2D View Direction → Color (View-Dependent); Continuous Implicit Representation
  - ▸ *CG use:* Novel view synthesis from posed images; the 2020 paper transformed 3D computer vision and graphics; ECCV 2020 Best Paper Honorable Mention
- 5.3.1.2 Positional Encoding γ(p) = [sin(2⁰πp), cos(2⁰πp), sin(2¹πp), cos(2¹πp), ..., sin(2^{L−1}πp), cos(2^{L−1}πp)]; L=10 for Position, L=4 for Direction; Fourier Features Enable MLP to Learn High-Frequency Detail (Tancik et al. NeurIPS 2020 — Spectral Bias Analysis)
  - ▸ *CG use:* Without PE, MLP produces blurry results (low-frequency bias of ReLU networks); PE is the "secret sauce" for NeRF detail
- 5.3.1.3 Volume Rendering Integration: C(r) = Σᵢ T_i (1 − exp(−σ_i δ_i)) c_i; T_i = exp(−Σ_{j<i} σ_j δ_j) (Accumulated Transmittance); Sample Points Along Ray via Stratified Sampling + Hierarchical Sampling (Coarse Network → Fine Network)
  - ▸ *CG use:* Differentiable volume rendering enables end-to-end training from images only; no 3D supervision needed!
- 5.3.1.4 Training: L = Σ_r ‖C_GT(r) − C_pred(r)‖²; Random Ray Batches from Training Images; Adam Optimizer; ~100K-300K Iterations (~Hours on Single GPU); No 3D Ground Truth Required
  - ▸ *CG use:* First practical neural scene representation trainable from posed photographs; spawned an entire research field

#### 5.3.2 NeRF Quality Improvements
- 5.3.2.1 Mip-NeRF (Barron et al. 2021): Replace Point Sampling with Conical Frustum Sampling (Integrated Positional Encoding — IPE); Anti-Aliased Multi-Scale Representation; Handles Variable Camera Distances/Resolutions
  - ▸ *CG use:* Sharper results at multiple resolutions; eliminates aliasing when training and testing at different scales
- 5.3.2.2 Mip-NeRF 360 (Barron et al. 2022): Contract Unbounded Scene into Bounded Ball via Coordinate Contraction; Proposal Network (Lightweight Density MLP) for Efficient Sampling; Distortion Loss Regularization; Handles Indoor/Outdoor Unbounded Scenes
  - ▸ *CG use:* Practical NeRF for real-world unbounded scenes (not just object-centric); Google's "RawNeRF" for dark scenes
- 5.3.2.3 Ref-NeRF (Verbin et al. 2022): Separate Diffuse + Specular Appearance; View Direction → Reflected Direction (via Normal) → Specular Color; Integrated Directional Encoding (IDE) for Specular; handles glossy reflections significantly better than vanilla NeRF
  - ▸ *CG use:* Glossy object rendering; specular highlights that change correctly with viewpoint

> 📚 **GitHub Repos:**
> - [bmild/nerf](https://github.com/bmild/nerf) ![Stars](https://img.shields.io/github/stars/bmild/nerf?style=flat) — Original NeRF implementation (Mildenhall et al. 2020)
> - [google-research/multinerf](https://github.com/google-research/multinerf) ![Stars](https://img.shields.io/github/stars/google-research/multinerf?style=flat) — Mip-NeRF 360 implementation (Google)
> - [nerfstudio-project/nerfstudio](https://github.com/nerfstudio-project/nerfstudio) ![Stars](https://img.shields.io/github/stars/nerfstudio-project/nerfstudio?style=flat) — Unified training framework with 20+ NeRF variants
>
> 📖 **Papers:** Mildenhall et al. *NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis* (ECCV 2020); Tancik et al. *Fourier Features Let Networks Learn High Frequency Functions in Low Dimensional Domains* (NeurIPS 2020)

---

### 5.4 NeRF Acceleration & Efficient Variants

#### 5.4.1 Grid-Based Acceleration
- 5.4.1.1 Instant NGP (Müller et al. SIGGRAPH 2022): Multi-Resolution Hash Encoding: L Levels × T=2^19 Hash Entries × F=2 Feature Dimensions; Tiny CUDA Neural Network (Fully Fused MLP — 1-2 Layer, 64 Neurons); Training: 5-15 Seconds (vs. Hours for Vanilla NeRF!)
  - ▸ *CG use:* The breakthrough that made neural rendering practical; real-time NeRF training; backbone for most subsequent work
- 5.4.1.2 TensoRF (Chen et al. ECCV 2022): Factorize 3D Density + Appearance Grid into CP (Vector) or VM (Vector-Matrix) Decomposition; Explicit 3D Grid = Σ_r v_r¹ ∘ v_r² ∘ v_r³ (CP) or Σ_r v_r ∘ M_r (VM); Compact Yet High-Quality
  - ▸ *CG use:* Interpretable factorization enables editing (modify basis vectors → edit scene); comparable quality to NGP with better compression
- 5.4.1.3 Plenoxels (Fridovich-Keil et al. 2022): Fully Explicit Voxel Grid of Spherical Harmonics; No MLP at All!; Direct Optimization of Voxel Values via SGD; Training in ~10 Minutes; Rendering via Trilinear Interpolation
  - ▸ *CG use:* Demonstrates MLP is not strictly necessary; explicit optimization is simple + interpretable; fast rendering
- 5.4.1.4 Triplane / K-Planes (Chan et al. 2022, Fridovich-Keil et al. 2023): Decompose 3D Volume into 2D (Triplane: XY, XZ, YZ) or 3×1D (HexPlane) Factorized Planes; Query via Projection + Bilinear Interpolation + Concatenation → Tiny MLP; Dense Grid Quality with Factorized Memory
  - ▸ *CG use:* EG3D (Chan et al. 2022) — 3D-aware GAN for face generation; efficient 4D representations for dynamic scenes

#### 5.4.2 Compression & Deployment
- 5.4.2.1 MERF / SMERF (Duckworth et al. 2023, 2024): Mobile/Web-Friendly NeRF; Compact Representation (Sparse Grid + Triplane); SMERF: Real-Time on Smartphones via WebGL
  - ▸ *CG use:* NeRF on the web; product configurators; real estate walkthroughs; AR viewing
- 5.4.2.2 VQ-NeRF (Takikawa et al. 2022): Vector Quantization of Feature Grid; Learned Codebook + Grid of Indices → Drastic Compression; Distillation from Larger Model
  - ▸ *CG use:* Streaming NeRF; mobile deployment; game-ready neural scene assets
- 5.4.2.3 ReRF / StreamRF (Li et al. 2023): Residual Radiance Fields; Encode Temporal Change as Compact Residual → Efficient Dynamic Scene Streaming; Progressive Refinement
  - ▸ *CG use:* Volumetric video streaming; free-viewpoint video at manageable bitrates

> 📚 **GitHub Repos:**
> - [NVlabs/instant-ngp](https://github.com/NVlabs/instant-ngp) ![Stars](https://img.shields.io/github/stars/NVlabs/instant-ngp?style=flat) — Hash encoding + real-time training
> - [apchenstu/TensoRF](https://github.com/apchenstu/TensoRF) ![Stars](https://img.shields.io/github/stars/apchenstu/TensoRF?style=flat) — VM/CP tensor decomposition
> - [sxyu/svox2](https://github.com/sxyu/svox2) ![Stars](https://img.shields.io/github/stars/sxyu/svox2?style=flat) — Plenoxels: explicit voxel grid + SH

---

### 5.5 Dynamic, Few-View & Large-Scale NeRF

#### 5.5.1 Dynamic NeRF
- 5.5.1.1 D-NeRF (Pumarola et al. 2021): Deformation Field Maps Canonical Space ↔ Deformed Space at Time t; MLP: (x_canonical, t) → (Δx, Δr) for Position + Rotation; Volume Render in Canonical Space — Always Consistent
  - ▸ *CG use:* Monocular video → dynamic 3D scene; deformable object reconstruction; virtual production
- 5.5.1.2 HyperNeRF (Park et al. 2021): Ambient Space Slice Codes for Topological Changes; Higher-Dimensional Hyperspace → Projections Handle Appearance Changes Beyond Simple Deformation
  - ▸ *CG use:* Dynamic scenes with topological changes (mouth opening, bag opening); facial performance capture
- 5.5.1.3 TiNeuVox / K-Planes 4D (Fang et al. 2022, Fridovich-Keil et al. 2023): Time-Aware Voxel Grids; HexPlane Decomposition: 3 Spatial + 1 Temporal Dimension; Fast Training + Rendering for Dynamic Scenes
  - ▸ *CG use:* Real-time dynamic view synthesis; volumetric video; sports replay
- 5.5.1.4 4D Gaussian Splatting: Dynamic 3DGS via Time-Varying Positions + Covariances + Colors; Real-Time Rendering of Dynamic Scenes from Multi-View Video
  - ▸ *CG use:* Free-viewpoint video at 30+ FPS; immersive sports broadcasting; volumetric performance capture

#### 5.5.2 Few-View & Generalizable NeRF
- 5.5.2.1 PixelNeRF (Yu et al. 2021): Image-Conditioned NeRF; CNN Encodes Input Images → Per-Point Features → Input to NeRF MLP Along with (x,y,z,d); Generalizes Across Scenes (Train on Many, Test on New Without Per-Scene Optimization)
  - ▸ *CG use:* Single/few-view 3D reconstruction; no per-scene training needed; feed-forward reconstruction
- 5.5.2.2 MVSNeRF (Chen et al. 2021): MVS Cost Volume → 3D Feature Volume + Neural Rendering; Multi-View Stereo + NeRF Hybrid; Generalizable Across Scenes
  - ▸ *CG use:* Few-shot view synthesis; camera array capture; drone photogrammetry enhancement
- 5.5.2.3 FreeNeRF / RegNeRF (Yang et al. 2023, Niemeyer et al. 2022): Regularization Strategies for Sparse-View NeRF; Depth Smoothness + Appearance Regularization; Can Reconstruct from as Few as 3 Views!
  - ▸ *CG use:* Casual capture (3 phone photos → 3D); practical NeRF for non-experts
- 5.5.2.4 Zero-1-to-3 / Zero123 (Liu et al. 2023): Diffusion Model Trained on Large 3D Dataset (Objaverse); Input: Single Image + Relative Camera Pose → Output: Novel View; Feed-Forward, No Per-Scene Optimization
  - ▸ *CG use:* Single-image novel view synthesis; 3D asset preview from product photo; AR content creation

#### 5.5.3 Large-Scale & Outdoor NeRF
- 5.5.3.1 Block-NeRF (Tancik et al. 2022): City-Scale via Tiling into Blocks; Each Block = Independently Trained NeRF; Block Boundary Blending via Appearance Embedding Overlap; Waymo/Street View Data (Millions of Images)
  - ▸ *CG use:* Autonomous driving simulation; city digital twins; Google Immersive View
- 5.5.3.2 Urban Radiance Fields (Rematas et al. 2022): Satellite + Street-Level Imagery Fusion; RGB + LiDAR Data; Multi-Scale Training (Coarse from Satellite, Fine from Street View) → Fly-Through from Any Altitude
  - ▸ *CG use:* Google Earth 3D; urban planning visualization; gaming environment capture
- 5.5.3.3 NeRF-W / NeRF in the Wild (Martin-Brualla et al. 2021): Per-Image Appearance Embedding + Transient Object (People, Cars) Handling via Uncertainty; Trained on Internet Photo Collections (Uncontrolled Lighting, Occlusions, Variable Appearance)
  - ▸ *CG use:* Tourist landmark reconstruction from Flickr; removes pedestrians automatically; cultural heritage digitization

> 📚 **GitHub Repos:**
> - [nerfstudio-project/nerfstudio](https://github.com/nerfstudio-project/nerfstudio) ![Stars](https://img.shields.io/github/stars/nerfstudio-project/nerfstudio?style=flat) — Implements most NeRF variants in a unified framework
> - [cvlab-columbia/zero123](https://github.com/cvlab-columbia/zero123) ![Stars](https://img.shields.io/github/stars/cvlab-columbia/zero123?style=flat) — Zero-1-to-3 single image → novel view

---

### 5.6 3D Gaussian Splatting — The 2023 Revolution

#### 5.6.1 3DGS Core Method
- 5.6.1.1 Primitive Representation: Anisotropic 3D Gaussian G(x) = σ · exp(−½(x−μ)ᵀΣ⁻¹(x−μ)); Σ = RSSᵀRᵀ (Rotation R + Scale S); Each Gaussian: Position μ (3D), Cov Σ (9 params → 7 after decomposition), Opacity σ, Color via SH Coefficients (48 coefficients / 16 bands per channel)
  - ▸ *CG use:* Explicit point-based representation; interpretable (unlike NeRF MLP); naturally supports editing
- 5.6.1.2 Tile-Based Differentiable Rasterizer: Sort Gaussians by Depth (Per-Tile Radix Sort); For Each Tile: Accumulate Front-to-Back via α-Blending C = Σᵢ c_i α_i Π_{j<i}(1−α_j), α_i = σ_i · G_2D(u,v); Entirely Differentiable (Gradients w.r.t. μ, Σ, σ, SH)
  - ▸ *CG use:* Fast training (minutes vs. hours for NeRF); real-time rendering (30+ FPS at 1080p); GPU-friendly (rasterization, not ray marching)
- 5.6.1.3 Adaptive Density Control: Detect Under-Reconstruction (Small Gaussians with Large Position Gradients → Clone); Detect Over-Reconstruction (Large Gaussians with Large Position Gradients → Split); Periodic Culling of Low-Opacity Gaussians
  - ▸ *CG use:* Automatic LOD — more Gaussians on detailed regions, fewer on smooth surfaces; no manual tuning needed
- 5.6.1.4 SfM Initialization: Start from COLMAP Sparse Point Cloud → Each Point = One Gaussian (Color + Covariance from 3 Nearest Neighbors); Provides Good Initialization → Faster Convergence
  - ▸ *CG use:* Standard pipeline: COLMAP SfM → 3DGS Training → Real-Time Rendering; works with any SfM input

#### 5.6.2 3DGS Quality & Efficiency Extensions
- 5.6.2.1 Mip-Splatting (Yu et al. 2023): 3D Frequency-Constrained Gaussians; Band-Limited 3DGS for Anti-Aliasing at Variable Resolutions/Zooms; 3D Smoothing Filter Applied During Training
  - ▸ *CG use:* Eliminates aliasing when rendering at different resolutions; zoom into 3DGS without artifacts
- 5.6.2.2 Compact3D / LightGaussian / EAGLES: Scalar Quantization of Gaussian Parameters (8-bit); Entropy Coding of Compressed Parameters; Learned Mask to Prune Unnecessary Gaussians; Retain Methods for Post-Training
  - ▸ *CG use:* 3DGS on mobile/web; storage reduced from GB to tens of MB; streaming Gaussian splats
- 5.6.2.3 StopThePop (Radl et al. 2024): Sort-Free Rendering via Multi-Pass Approximate Ordering; Eliminates Expensive Per-Frame Radix Sort; Up to 2× Rendering Speedup with Minimal Quality Loss
  - ▸ *CG use:* Higher FPS for real-time 3DGS; mobile deployment where radix sort is expensive
- 5.6.2.4 Scaffold-GS (Lu et al. 2023): Anchor-Based Gaussian Distribution; Sparse Voxel Grid of Anchor Points → Each Anchor Generates Local Gaussians via MLP; Better Structure, Fewer Floaters
  - ▸ *CG use:* Cleaner geometry; more structured representation; fewer artifacts in novel views

#### 5.6.3 2DGS, Surfel-Based & Hybrid Methods
- 5.6.3.1 2D Gaussian Splatting (Huang et al. SIGGRAPH 2024): "Flat" Gaussians → Surfels (One Dimension Collapsed); Surface Normal = Shortest Axis → Direct Normal Map Rendering; Better Surface Reconstruction than 3DGS
  - ▸ *CG use:* High-quality mesh extraction from Gaussian splats; surface reconstruction quality approaching MVS; direct normal for relighting
- 5.6.3.2 SuGaR (Guédon & Lepetit 2023): Regularize Gaussians to Be Flat and Aligned with Surface; Poisson Surface Reconstruction from Aligned Gaussians; Mesh Extraction from 3DGS for Traditional Rendering Pipelines
  - ▸ *CG use:* Convert 3DGS to standard mesh → import into game engines, DCC tools, physics simulation
- 5.6.3.3 GOF (Gaussian Opacity Fields — Yu et al. 2024): Replace Discrete Gaussians with Continuous Opacity Field; Ray-Marching Through Gaussian Field → Surface-Like Rendering; Direct SDF Extraction
  - ▸ *CG use:* Best-of-both: explicit efficiency of 3DGS + continuous surface quality of implicit methods

> 📚 **GitHub Repos:**
> - [graphdeco-inria/gaussian-splatting](https://github.com/graphdeco-inria/gaussian-splatting) ![Stars](https://img.shields.io/github/stars/graphdeco-inria/gaussian-splatting?style=flat) — Original 3DGS (Kerbl et al. SIGGRAPH 2023)
> - [nerfstudio-project/gsplat](https://github.com/nerfstudio-project/gsplat) ![Stars](https://img.shields.io/github/stars/nerfstudio-project/gsplat?style=flat) — Optimized CUDA Gaussian rasterizer
> - [hbb1/2d-gaussian-splatting](https://github.com/hbb1/2d-gaussian-splatting) ![Stars](https://img.shields.io/github/stars/hbb1/2d-gaussian-splatting?style=flat) — 2DGS: surfel-based surface reconstruction
>
> 📖 **Papers:** Kerbl et al. *3D Gaussian Splatting for Real-Time Radiance Field Rendering* (SIGGRAPH 2023); Huang et al. *2D Gaussian Splatting* (SIGGRAPH 2024)

---

### 5.7 Neural Surface Reconstruction

#### 5.7.1 SDF-Based Neural Methods
- 5.7.1.1 NeuS (Wang et al. NeurIPS 2021): Volume Rendering of SDF with Unbiased Weight Function w(t) = φ_s(f(p(t))) / ∫ φ_s(f(p(u))) du; φ_s(x) = se^{−sx}/(1+e^{−sx})² (Logistic Density Distribution, s→∞ → Surface); Transforms SDF to Density for Volume Rendering
  - ▸ *CG use:* High-quality surface reconstruction from multi-view images; watertight meshes; replaces traditional MVS pipeline
- 5.7.1.2 VolSDF (Yariv et al. 2021): SDF → Density via Laplace CDF σ(x) = α Ψ_β(−d(x)), Ψ_β(s) = ½(1+erf(s/β)) for s<0 else ½(1+exp(−s/β)); β Controls Surface Thickness (Learnable); Better Volume Rendering Gradients than Naive SDF-Density
  - ▸ *CG use:* More stable training than NeuS; better handling of thin structures
- 5.7.1.3 Neuralangelo (Li et al. 2023): Multi-Resolution Hash Grids + Numerical Gradient Computation for Higher-Order Smoothness; Coarse-to-Fine Optimization on Hash Grid Resolution; State-of-the-Art Surface Detail
  - ▸ *CG use:* Reconstructs fine geometric detail (brick textures, sculptures, terrain) from images; NVIDIA's flagship reconstruction method
- 5.7.1.4 BakedSDF (Yariv et al. 2023): Multi-Layer Perceptron → Bake into High-Resolution SDF Grid + Feature Grid for View-Dependent Color; Fast Real-Time Rendering After Baking; Hybrid Training + Baking Pipeline
  - ▸ *CG use:* Production-quality neural assets; precompute neural scene → render at interactive rates in game engines

#### 5.7.2 Hybrid & Real-Time Neural Surfaces
- 5.7.2.1 VoxFusion / Voxurf (Wu et al. 2023): Dense Voxel Grid + Sparse Convolution for Efficiency; Direct Mesh Extraction via Marching Cubes on Optimized Voxel Grid; No MLP at Inference Time
  - ▸ *CG use:* Fast neural surface reconstruction; direct mesh output; mobile-friendly
- 5.7.2.2 MobileNeRF (Chen et al. 2023): Bake NeRF into Textured Polygons (Surface Mesh); Polygon Mesh + View-Dependent Texture Atlas; Runs on Mobile Phones at 60 FPS via Standard GPU Rasterization
  - ▸ *CG use:* Deploy NeRF-quality views on web and mobile without specialized ML hardware; Google's Immersive View uses this
- 5.7.2.3 SMERF / MERF (Duckworth et al. 2023, 2024): Streamable Memory-Efficient Radiance Field; Distilled Sparse Voxel Representation + Triplane; Real-Time on WebGL Smartphones
  - ▸ *CG use:* Web-based immersive 3D experiences; real estate virtual tours; e-commerce 3D product viewing

> 📚 **GitHub Repos:**
> - [autonomousvision/sdfstudio](https://github.com/autonomousvision/sdfstudio) ![Stars](https://img.shields.io/github/stars/autonomousvision/sdfstudio?style=flat) — Unified neural SDF reconstruction framework
> - [NVlabs/neuralangelo](https://github.com/NVlabs/neuralangelo) ![Stars](https://img.shields.io/github/stars/NVlabs/neuralangelo?style=flat) — High-detail surface reconstruction
>
> 📖 **Papers:** Wang et al. *NeuS* (NeurIPS 2021); Li et al. *Neuralangelo* (CVPR 2023); Yariv et al. *BakedSDF* (SIGGRAPH 2023)

---

### 5.8 Neural Materials & Neural Radiance Caches

#### 5.8.1 Neural Materials
- 5.8.1.1 Neural BRDF (Rainer et al. 2019, 2020): MLP f_θ(θ_i, φ_i, θ_o, φ_o) → RGB; Autoencoder Architecture: Encoder Compresses Measured BRDF → Latent z, Decoder Evaluates Any (θ_i, φ_i, θ_o, φ_o); Compact Yet Accurate
  - ▸ *CG use:* Store complex measured BRDFs (MERL database) in few KB; fast evaluation via GPU MLP inference; material space interpolation
- 5.8.1.2 Neural BTF (Rainer et al. 2019): Captures Meso-Scale Detail (Fabric Weave, Leather Grain); 6D Function BTF(x, ω_i, ω_o) Compressed via Neural Network; View-Dependent Texture from Any Angle
  - ▸ *CG use:* Film-quality fabric/apparel rendering; car interior material realism; close-up surface detail beyond bump/normal maps
- 5.8.1.3 NeuMIP (Kužel & Sýkora 2022): Neural Multi-Resolution Material Representation; Replaces Traditional Mipmap Chain with Neural Pyramids; Handles Complex Displacement + Parallax Effects
  - ▸ *CG use:* Self-shadowing, parallax, and specular at grazing angles in real-time; video game material enhancement
- 5.8.1.4 MatFuse / DreamMat / ControlMat (2024): Diffusion Model → Generate PBR Material Maps (Albedo, Normal, Roughness, Metallic); Text/Image-Conditioned; Produce 4+ SVBRDF Maps Simultaneously
  - ▸ *CG use:* Text-to-material pipeline; rapid material library creation; material variation from single sample

#### 5.8.2 Neural Radiance Cache & Light Transport Learning
- 5.8.2.1 Neural Radiance Cache (NRC — Müller et al. 2021): Train Tiny MLP Online to Cache Path-Traced Radiance; MLP Input: (x, θ, φ) → Radiance L_o; Faster Than Re-Tracing, More Accurate Than Irradiance Caching; Real-Time Path Tracing Acceleration
  - ▸ *CG use:* RTXGI NRC; real-time path tracing with full global illumination at interactive rates
- 5.8.2.2 Neural Incident Radiance Field (Boss et al. 2021): Learn Directional Incident Radiance as Neural Network; Query Incident Light at Any Surface Point in Any Direction → Use for Relighting; Fast Evaluation (No Path Tracing at Runtime)
  - ▸ *CG use:* Dynamic scene relighting; product visualization with interactive lighting changes
- 5.8.2.3 Neural Light Transport (Chen et al. 2020): Learn 4D Light Transport Matrix Between Camera Pixels and Projector Pixels; Neural Network Factorization → Compact Representation
  - ▸ *CG use:* Projector-camera systems; computational illumination; relightable photography
- 5.8.2.4 Real-Time Neural Appearance Models (Müller et al. 2023): Neural BRDF + Neural Radiance Cache + Neural Importance Sampling All Running in Real-Time; Tensor-Core-Accelerated MLP Inference in Shader
  - ▸ *CG use:* DLSS/RTX neural rendering pipeline; film-quality materials + lighting in real-time games

> 📚 **GitHub Repos:**
> - [NVlabs/nrc](https://github.com/NVlabs/nrc) ![Stars](https://img.shields.io/github/stars/NVlabs/nrc?style=flat) — Neural Radiance Cache for real-time GI
> - [mitsuba-renderer/mitsuba3](https://github.com/mitsuba-renderer/mitsuba3) — Neural BRDF integrator plugins

---

### 5.9 Diffusion Models for 3D Generation

#### 5.9.1 Score Distillation Sampling (SDS)
- 5.9.1.1 DreamFusion (Poole et al. 2022): Text-to-3D via Frozen 2D Diffusion Model (Imagen); SDS Loss: ∇_θ L_SDS = 𝔼_{t,ϵ} [w(t)(ϵ̂_φ(x_t, y, t) − ϵ) ∂x/∂θ]; Gradient of 2D Diffusion w.r.t. 3D Representation Parameters; No 3D Training Data Required!
  - ▸ *CG use:* First practical text-to-3D; "a corgi riding a bicycle" → 3D model; spawned text-to-3D field
- 5.9.1.2 Variational Score Distillation (VSD — ProlificDreamer, Wang et al. 2023): SDS Suffers from Over-Smoothing and Mode-Seeking (Low Diversity); VSD: Learn Particle-Based Variational Inference via Wasserstein Gradient Flow; Finetune LoRA on Current Render → More Detailed, Diverse Results
  - ▸ *CG use:* High-quality text-to-3D; sharper geometry, more texture detail, less "blobby" results
- 5.9.1.3 Magic3D / Fantasia3D (Lin et al. 2023, Chen et al. 2023): Two-Stage: Coarse NeRF → Fine Mesh (DMTet); SDS on DMTet (Differentiable Mesh Representation) → High-Resolution Geometry + Texture
  - ▸ *CG use:* Production-quality text-to-3D meshes; directly importable into DCC tools and game engines

#### 5.9.2 Multi-View Diffusion & 3D-Consistent Generation
- 5.9.2.1 MVDream (Shi et al. 2024): Multi-View Consistent Diffusion Model; Generate 4 Views (Front, Right, Back, Left) Simultaneously; Attention Across Views Ensures 3D Consistency; Eliminates Janus/Multi-Face Problem
  - ▸ *CG use:* Reliable multi-view generation → feed into NeRF/3DGS reconstruction → consistent 3D model
- 5.9.2.2 SyncDreamer (Liu et al. 2023): Synchronized Multi-View Diffusion via 3D-Aware Feature Volume; Generate 16 Views from Single Image with 3D Consistency
  - ▸ *CG use:* Single image → consistent 3D preview; rapid asset generation
- 5.9.2.3 ImageDream (Wang et al. 2024): Image-Conditioned 3D Generation; More Control than Text (Composition, Style, Specific Object); Guidance from Reference Image + Text for Details
  - ▸ *CG use:* 3D from concept art; product 3D from photograph; style-preserving 3D generation
- 5.9.2.4 3D Diffusion Models: DiffTF (Cao et al. 2023) — Diffusion on Triplane Latent Representation; NFD (Shue et al. 2023) — Neural Field Diffusion; Direct 3D Diffusion (Not 2D Distillation) → Better 3D Structure
  - ▸ *CG use:* Native 3D generation (not via 2D proxy); more 3D-coherent; fewer artifacts than SDS

> 📚 **GitHub Repos:**
> - [threestudio-project/threestudio](https://github.com/threestudio-project/threestudio) ![Stars](https://img.shields.io/github/stars/threestudio-project/threestudio?style=flat) — Unified text-to-3D framework (DreamFusion, MVDream, ProlificDreamer)
> - [ashawkey/stable-dreamfusion](https://github.com/ashawkey/stable-dreamfusion) ![Stars](https://img.shields.io/github/stars/ashawkey/stable-dreamfusion?style=flat) — DreamFusion with Stable Diffusion
>
> 📖 **Papers:** Poole et al. *DreamFusion* (arXiv 2022); Wang et al. *ProlificDreamer* (NeurIPS 2023); Shi et al. *MVDream* (arXiv 2024)

---

### 5.10 Feed-Forward 3D Reconstruction

#### 5.10.1 Large Reconstruction Models (LRM)
- 5.10.1.1 LRM (Hong et al. 2024): Transformer Architecture; Input: Single Image (or Few Views) Patches → Image Tokens; Predict Triplane NeRF Representation in Single Forward Pass (< 5 Seconds); Trained on Objaverse (800K+ 3D Models) with Rendering Supervision
  - ▸ *CG use:* Instant 3D from single photo; e-commerce product digitization; AR content creation pipeline
- 5.10.1.2 Instant3D (Li et al. 2024): Feed-Forward Text/Image → 3D Triplane; Multi-View Diffusion as Teacher; Text-to-3D in < 10 Seconds (vs. Hours for DreamFusion optimization)
  - ▸ *CG use:* Real-time text-to-3D; rapid prototyping; game asset ideation
- 5.10.1.3 LGM (Tang et al. 2024): LRM that Predicts 3DGS Instead of NeRF; Direct 3D Gaussian Splat from Single Image; Real-Time Rendering After Prediction
  - ▸ *CG use:* Single image → animatable 3DGS in seconds; real-time 3D preview
- 5.10.1.4 CRM / GRM (Wang et al. 2024, Xu et al. 2024): Convolutional Reconstruction Model; U-Net Architecture + Cross-Attention to Image Features → Triplane; Even Faster Than Transformer LRM
  - ▸ *CG use:* Mobile/edge deployment of feed-forward reconstruction; real-time 3D on device

#### 5.10.2 Multi-View Reconstruction Networks
- 5.10.2.1 DUSt3R (Wang et al. 2024): End-to-End Dense Stereo from Unposed Image Pairs; Transformer Predicts Dense 3D Pointmaps (Per-Pixel XYZ) for Both Images; No Camera Pose Required (!); Foundation Model for 3D Vision
  - ▸ *CG use:* Drop-in replacement for SfM + MVS; casual 3D capture without calibration; 3D reconstruction at scale
- 5.10.2.2 Spann3R (Kasten et al. 2024): Streaming Dense Reconstruction from Video; Incremental Frame-by-Frame Pointmap Prediction; No Global Optimization (Unlike SfM); Real-Time
  - ▸ *CG use:* Real-time 3D mapping from smartphone video; AR/VR scene understanding; robot navigation
- 5.10.2.3 CAT3D (Gao et al. 2024): Generate Many Consistent Views from Few Input Images via Diffusion; Reconstruct 3D Scene from Generated Views; Few-Shot Scene Reconstruction
  - ▸ *CG use:* 3D from 3-5 photos; fills in missing viewpoints automatically; democratizing 3D capture

> 📚 **GitHub Repos:**
> - [openai/shap-e](https://github.com/openai/shap-e) ![Stars](https://img.shields.io/github/stars/openai/shap-e?style=flat) — Text/image-to-3D feed-forward
> - [naver/dust3r](https://github.com/naver/dust3r) ![Stars](https://img.shields.io/github/stars/naver/dust3r?style=flat) — Dense unposed stereo reconstruction

---

### 5.11 Inverse Rendering

#### 5.11.1 Joint Estimation of Geometry, Materials & Lighting
- 5.11.1.1 Nvdiffrec (Munkberg et al. 2022): Multi-View Images → Optimize Mesh + PBR Materials (Albedo, Roughness, Metallic) + Environment Map via Differentiable Rasterization + Path Tracing; Regularization Priors (Smoothness, Minimal Specular)
  - ▸ *CG use:* Turn photo set into game-ready PBR asset (mesh + textures + materials) automatically
- 5.11.1.2 NeRFactor (Zhang et al. 2021): NeRF Pre-Training → Extract Surface + View-Dependent Appearance → Factor into Albedo + Normal + Roughness + Lighting (SH) via MLP; Relightable Neural Representation
  - ▸ *CG use:* Relightable 3D from photos; change lighting after capture; consistent material editing
- 5.11.1.3 TensoIR (Jin et al. 2023): TensoRF-Based Inverse Rendering; VM Factorization for Geometry + Materials + Visibility + Indirect Illumination; Joint Optimization via Differentiable Rendering; Relightable + Editable
  - ▸ *CG use:* Inverse rendering with editable materials; scene decomposition; VFX integration
- 5.11.1.4 GS-IR (Liang et al. 2024): 3DGS for Inverse Rendering; Decompose Gaussian Colors into Material Parameters + Lighting; Normal Estimation from Gaussians; Relightable Gaussian Splatting
  - ▸ *CG use:* Real-time relightable 3DGS; change environment map in real-time on Gaussian scenes

#### 5.11.2 Specialized Inverse Problems
- 5.11.2.1 Photometric Stereo (Differentiable): Known Lighting Directions → Recover Surface Normals via Differentiable BRDF Optimization → Integrate Normals → Height Map/3D Surface
  - ▸ *CG use:* High-frequency surface detail (pores, scratches) from multi-light photography; museum artifact digitization
- 5.11.2.2 Inverse Path Tracing: Jointly Estimate Emitter Distribution and Reflectance from Photographs; Gradient Through Full Light Transport; Underdetermined → Strong Priors Required
  - ▸ *CG use:* Room lighting estimation; architectural daylight analysis; forensic image analysis
- 5.11.2.3 Differentiable Volume Reconstruction: Tomographic Reconstruction with Differentiable Forward Model; Replace Traditional Filtered Back-Projection with Learned/Iterative Reconstruction; Application: CT, Cryo-EM, Neutron Imaging
  - ▸ *CG use:* Medical imaging; materials science; industrial non-destructive testing

> 📚 **GitHub Repos:**
> - [NVlabs/nvdiffrec](https://github.com/NVlabs/nvdiffrec) ![Stars](https://img.shields.io/github/stars/NVlabs/nvdiffrec?style=flat) — Joint inverse rendering (mesh + PBR from images)
> - [Haian-Jin/TensoIR](https://github.com/Haian-Jin/TensoIR) ![Stars](https://img.shields.io/github/stars/Haian-Jin/TensoIR?style=flat) — TensoRF-based inverse rendering
>
> 📖 **Papers:** Munkberg et al. *Extracting Triangular 3D Models, Materials, and Lighting From Images* (CVPR 2022); Zhang et al. *NeRFactor* (SIGGRAPH Asia 2021)

---

### 5.12 Differentiable Rendering Frameworks & Ecosystem

#### 5.12.1 Research Frameworks
- 5.12.1.1 Mitsuba 3 (Jakob et al. 2022): Retargetable Differentiable Renderer; Python-Driven + JIT Compilation (Dr.Jit → LLVM/CUDA); Multiple Integrators: PSDR, Adjoint, Reparameterization; Spectral + Polarization; Research Standard
  - ▸ *CG use:* Academic research in differentiable rendering; new integrator prototyping; benchmark for inverse methods
- 5.12.1.2 Redner (Li et al. 2018): Python-Based Differentiable Renderer; Implements Edge Sampling for Mesh Gradients; Production Use via PyTorch Integration; Reference Implementation for Discontinuity Handling
  - ▸ *CG use:* Single-image 3D reconstruction; material estimation; shape-from-shading research
- 5.12.1.3 Nvdiffrast (Laine et al. 2020): NVIDIA's GPU Differentiable Rasterizer; OpenGL/CUDA Interop; Fast (Hardware Rasterization + CUDA Gradients); Modular: Use with Any Deep Learning Framework
  - ▸ *CG use:* Nvdiffrec, Nvdiffmodeling; training 3D deep learning models with rendering in the loop; texture optimization
- 5.12.1.4 PSDR-CUDA (Zhang et al. 2023): GPU-Optimized Primary Sample Space Diff-Renderer; Wavefront Path Tracing on GPU; Handles Complex Lighting (Caustics, Participating Media); Production-Grade Performance
  - ▸ *CG use:* Large-scale inverse rendering; film-quality scene parameter estimation

#### 5.12.2 Production & DSL Approaches
- 5.12.2.1 Slang.D (Bangaru, He et al. 2023): Automatic Differentiation Compiler for Shading Languages; Write Renderer in Slang → Automatically Get Forward + Backward Passes; No Manual Gradient Code; Differentiable Path Tracer in < 1000 Lines
  - ▸ *CG use:* Rapid prototyping of differentiable rendering algorithms; production renderer differentiation
- 5.12.2.2 Taichi (Hu et al. 2019): Differentiable Programming Language for Physical Simulation; Python Frontend + LLVM/CUDA Backend; Automatic Differentiation of Entire Simulation Loop
  - ▸ *CG use:* DiffTaichi (differentiable physics); ∇-Sim; differentiable MPM/FEM for inverse design
- 5.12.2.3 Warp (NVIDIA — Macklin et al. 2022): Python Framework for High-Performance Simulation + Differentiable Rendering; JIT-Compiled CUDA Kernels from Python; Automatic Differentiation via Source Transformation
  - ▸ *CG use:* Differentiable physics + rendering for robotics; inverse design; reinforcement learning with rendering in loop

#### 5.12.3 Emerging Standards & Convergence
- 5.12.3.1 Unified Differentiable Rendering API (Proposed): Common Interface Across Mitsuba/Redner/Nvdiffrast/Warp; Standard Scene Description → Any Backend; Reduces Fragmentation
  - ▸ *CG use:* Easier comparison between methods; plug-and-play backend switching
- 5.12.3.2 Neural + Classical Hybrid Pipelines: Differentiable Renderer as Component in Larger Neural System; Render → Neural Network → Loss → Gradient Through Both; End-to-End Trainable Visual Computing
  - ▸ *CG use:* Inverse graphics; AI-assisted content creation; robot vision training; autonomous vehicle perception
- 5.12.3.3 Real-Time Differentiable Rendering (Emerging): GPU-Optimized + Sparse Gradient Computation; Interactive Inverse Rendering; Enables Artist-in-the-Loop Optimization
  - ▸ *CG use:* Real-time material fitting with visual feedback; interactive scene reconstruction

> 📚 **GitHub Repos:**
> - [mitsuba-renderer/mitsuba3](https://github.com/mitsuba-renderer/mitsuba3) ![Stars](https://img.shields.io/github/stars/mitsuba-renderer/mitsuba3?style=flat) — Research standard differentiable renderer
> - [NVIDIAGameWorks/nvdiffrast](https://github.com/NVIDIAGameWorks/nvdiffrast) ![Stars](https://img.shields.io/github/stars/NVIDIAGameWorks/nvdiffrast?style=flat) — GPU differentiable rasterizer
> - [NVIDIA/warp](https://github.com/NVIDIA/warp) ![Stars](https://img.shields.io/github/stars/NVIDIA/warp?style=flat) — Python differentiable simulation + rendering
> - [taichi-dev/taichi](https://github.com/taichi-dev/taichi) ![Stars](https://img.shields.io/github/stars/taichi-dev/taichi?style=flat) — Differentiable programming for physics
>
> 📖 **Papers:** Jakob et al. *Mitsuba 3* (SIGGRAPH 2022); Laine et al. *Nvdiffrast* (SIGGRAPH Asia 2020); Bangaru et al. *Slang.D* (SIGGRAPH 2023)

---


## Chapter 6 · Animation & Physics Simulation

*From keyframes to physics-based simulation — the complete theory of motion, deformation, and dynamics. `▸ CG use:` links each technique to practice.*

> 💡 **Top-Level References:**
> - [dilevin/CSC2549](https://github.com/dilevin/CSC2549) — Physics-based animation course (University of Toronto)
> - [InteractiveComputerGraphics/PositionBasedDynamics](https://github.com/InteractiveComputerGraphics/PositionBasedDynamics) ![Stars](https://img.shields.io/github/stars/InteractiveComputerGraphics/PositionBasedDynamics?style=flat) — PBD/XPBD reference implementation
> - [taichi-dev/taichi](https://github.com/taichi-dev/taichi) ![Stars](https://img.shields.io/github/stars/taichi-dev/taichi?style=flat) — Differentiable physics simulation framework

---

### 6.1 Keyframe Animation & Interpolation

#### 6.1.1 Keyframe Fundamentals
- 6.1.1.1 Keyframe Paradigm: Artist Specifies Key Poses at Discrete Times; Computer Interpolates Between Keys; Separates Creative Control (What) from Mathematical Interpolation (How)
  - ▸ *CG use:* Every animation in games, film, and interactive media; Maya/Blender curve editor is the artist interface
- 6.1.1.2 Interpolation Types: Linear (Constant Velocity, C⁰, Jerky at Keys), Bézier/Spline (C¹/C² Smooth, Adjustable Tangents), Step (Hold Pose Until Next Key — Used for Pose-to-Pose Blocking)
  - ▸ *CG use:* DCC curve editor: Linear for mechanical motion, Spline for organic, Step for blocking
- 6.1.1.3 Easing Functions (Penner 2002): Ease-In (Slow→Fast), Ease-Out (Fast→Slow), Ease-In-Out (Slow→Fast→Slow); Cubic, Quintic, Exponential, Elastic, Bounce, Back; t' = f(t) where t ∈ [0,1]
  - ▸ *CG use:* UI animation (CSS easing); camera transitions; game object tweening; every motion graphics tool
- 6.1.1.4 Arc-Length Parameterization: Constant Arc-Length Speed; Reparameterize Curve by s = ∫‖γ'(u)‖du → s⁻¹(t); Avoids Speed Distortion from Control Point Distribution
  - ▸ *CG use:* Camera fly-through (constant speed regardless of control point spacing); character path following

#### 6.1.2 Advanced Keyframe Techniques
- 6.1.2.1 Time Remapping: Animate Time Variable Independently; t_map = f(t_global); Slow Motion: Stretch Time; Fast Motion: Compress Time; Reverse: Negative Slope
  - ▸ *CG use:* Cinematic time manipulation (bullet time, speed ramps); retiming mocap data
- 6.1.2.2 Additive Animation Layers: Base Animation + Offset Animation = Combined; Offset Can Be Applied Selectively (Upper Body Only); Non-Destructive Workflow
  - ▸ *CG use:* Game animation blending (base locomotion + aim offset on upper body); film animation layering
- 6.1.2.3 Animation Curves as Signals: Filter Keyframe Data (Smooth Noisy Mocap); Frequency Analysis to Identify Jitter; Butterworth Low-Pass Filter for Denoising
  - ▸ *CG use:* Motion capture cleanup; removing high-frequency noise from tracked data while preserving intention

> 📖 **Textbooks:** *The Animator's Survival Kit* — Richard Williams (The classic); *Computer Animation: Algorithms and Techniques* — Rick Parent

---

### 6.2 Skeletal Animation

#### 6.2.1 Skeleton Structure & Forward Kinematics
- 6.2.1.1 Skeleton Hierarchy: Joint = Pivot Point with Parent-Child Relationship; Bone = Segment Between Two Joints; Root Joint = Origin (Typically Pelvis); Chain: Root→Spine→Shoulder→Elbow→Wrist→Finger
  - ▸ *CG use:* Character rigging standard; USD/USD Skeleton; glTF skinning; every game engine
- 6.2.1.2 Local vs. Global Transforms: T_global(i) = T_global(parent) · T_local(i); Local: Joint Orientation Relative to Parent (Animator Edits); Global: World-Space Transform (For Rendering)
  - ▸ *CG use:* Animation data stored as local transforms (rotation quaternions); rendering computes global transforms via hierarchy traversal
- 6.2.1.3 Forward Kinematics (FK): Given Joint Angles θ, Compute End-Effector Position x = f(θ); Unique Solution; Simple to Compute via Matrix Chain; Animator Directly Rotates Each Joint
  - ▸ *CG use:* FK is the standard animation mode; animator poses skeleton by rotating individual joints

#### 6.2.2 Inverse Kinematics (IK)
- 6.2.2.1 IK Problem: Given End-Effector Target Position x_target, Find Joint Angles θ Such That f(θ) = x_target; Underdetermined (Many Solutions for Multi-Joint Chains); Requires Numerical Optimization
  - ▸ *CG use:* Foot placement on uneven terrain; hand grabbing objects; character interaction with environment
- 6.2.2.2 CCD (Cyclic Coordinate Descent): Iteratively Rotate Each Joint (From End to Root) to Bring End-Effector Closer to Target; Simple, Robust, but Can Produce Unnatural Poses; O(n) Per Iteration
  - ▸ *CG use:* Fast IK solver in game engines; real-time procedural animation (foot IK)
- 6.2.2.3 Jacobian IK: Linearize f(θ+Δθ) ≈ f(θ) + J Δθ; Δx = J Δθ → Δθ = J⁺ Δx (Pseudo-Inverse) or Damped Least Squares Δθ = (JᵀJ + λ²I)⁻¹Jᵀ Δx; Smooth Motion but Computationally Heavier
  - ▸ *CG use:* DCC tools (Maya, Blender IK solver); high-quality animation; DLS avoids singularity at full extension
- 6.2.2.4 FABRIK (Forward And Backward Reaching IK — Aristidou 2011): Two-Phase: Forward (Root→Tip: Position Each Joint at Distance from Previous), Backward (Tip→Root: Pull Toward Target); Fast, Natural-Looking, No Matrix Computation
  - ▸ *CG use:* Real-time IK for games; naturally handles joint limits; outperforms CCD and Jacobian for many problems
- 6.2.2.5 Full-Body IK: IK with Multiple End-Effectors + Balance Constraints; Prioritized IK (Higher Priority Tasks Solved First, Lower Priority in Null Space); Center of Mass Constraint
  - ▸ *CG use:* Character grabbing ledge while keeping feet planted; procedural animation adapting to environment

#### 6.2.3 Skinning & Deformation
- 6.2.3.1 Linear Blend Skinning (LBS / Skeletal Subspace Deformation): v' = Σ w_i · M_i · v (Weighted Sum of Bone Transforms); Weights w_i ≥ 0, Σ w_i = 1 (Partition of Unity); GPU Vertex Shader Implementation
  - ▸ *CG use:* Universal real-time skinning; candy-wrapper artifact at joints (elbows, wrists collapse volume when twisted ~180°)
- 6.2.3.2 Dual Quaternion Skinning (DQS — Kavan et al. 2008): Replace Linear Blend of Matrices with Dual Quaternion Blend + Normalization; Eliminates Candy-Wrapper — Volume Preservation at Joints; Slightly Higher GPU Cost (~10-20%)
  - ▸ *CG use:* Higher quality skinning in modern games; UE5 supports DQS; joint deformation without volume loss
- 6.2.3.3 Pose Space Deformation (PSD / Corrective Blend Shapes): Learn Residual Deformation as Function of Joint Angles; RBF Interpolation: w_k = RBF(‖θ − θ_k‖); Correct LBS/DQS Artifacts (Muscle Bulge, Shoulder Collapse)
  - ▸ *CG use:* Film-quality character deformation; Disney/Pixar character rigging; game cinematics
- 6.2.3.4 Delta Mush (Mancewicz et al. 2014): Apply Laplacian Smoothing to LBS Result → Compute Delta (Original − Smoothed) → Re-Apply Delta to Restore Detail; Automatic Smoothing of LBS Artifacts
  - ▸ *CG use:* Production rigging smoothing; reduces need for manual corrective shapes; Disney Hyperion renderer
- 6.2.3.5 Bounded Biharmonic Weights (BBW — Jacobson et al. 2011): Automatic Skinning Weight Computation via Biharmonic Equation; Minimize Δ²w Subject to Constraints; Artist Places Sparse Handle Points; No Manual Weight Painting!
  - ▸ *CG use:* Rapid rigging prototyping; weight painting replacement for simple characters; Blender auto-weights

> 📚 **GitHub Repos:** [PixarAnimationStudios/OpenSubdiv](https://github.com/PixarAnimationStudios/OpenSubdiv) — Subdivision + skinning; [libigl/libigl](https://github.com/libigl/libigl) — BBW implementation
>
> 📖 **Textbooks:** *Computer Animation: Algorithms and Techniques* — Rick Parent; *Game Engine Architecture* — Jason Gregory (Ch. 11)

---

### 6.3 Deformation Techniques

#### 6.3.1 Mesh-Based Deformation
- 6.3.1.1 Free-Form Deformation (FFD — Sederberg & Parry 1986): Embed Object in 3D Lattice of Control Points; Deform Lattice → Object Follows (Bernstein Polynomial Blending); Hierarchical FFD for Progressive Detail
  - ▸ *CG use:* Non-skeletal deformation; squash-and-stretch cartoon effects; modeling tool (3ds Max FFD modifier)
- 6.3.1.2 As-Rigid-As-Possible (ARAP — Sorkine & Alexa 2007): Minimize Σ ‖(v_i' − v_j') − R_i(v_i − v_j)‖²; R_i = Per-Vertex Rotation (Polar Decomposition of Local Neighborhood); Alternating: Fix R → Solve Positions → Fix Positions → Update R
  - ▸ *CG use:* Natural-looking deformation preserving local rigidity; mesh editing with handle manipulation; shape interpolation
- 6.3.1.3 Laplacian Mesh Editing: Encode Geometry via Differential Coordinates δ_i = v_i − (1/d_i) Σ_{j∈N(i)} v_j (Laplacian); Edit via Constraints + Reconstruct Positions (Least Squares); Detail-Preserving Deformation
  - ▸ *CG use:* Pose transfer; detail-preserving mesh editing; surface deformation transfer between characters

#### 6.3.2 Cage-Based & Advanced Deformation
- 6.3.2.1 Cage-Based Deformation: Coarse Cage Encloses Detailed Mesh; Deform Cage → Mesh Follows via Generalized Barycentric Coordinates; Mean Value Coordinates (MVC — Ju et al. 2005): Smooth, Always Defined; Harmonic Coordinates (Joshi et al. 2007): Non-Negative, Cage-Conforming; Green Coordinates (Lipman et al. 2008): Conformal in Limit, Shape-Preserving
  - ▸ *CG use:* Character deformation with coarse control; film-quality shape editing (Pixar Presto)
- 6.3.2.2 Blend Shapes / Morph Targets: Linear Combination of Predefined Shapes: v = v_base + Σ w_k · Δv_k; Weights Typically ∈ [0,1]; Facial Animation Standard (FACS — Facial Action Coding System); Corrective Blend Shapes for Skeletal Deformation Artifacts
  - ▸ *CG use:* Facial animation in all media; character expression library; PCA compression of blend shape space
- 6.3.2.3 Example-Based Deformation (Sumner et al. 2005): Artist Provides Example Pairs (Rest Pose → Deformed Pose); Learn Deformation Model to Interpolate/Extrapolate Examples; Handle Unseen Poses via Weighted Combination of Nearest Examples
  - ▸ *CG use:* Consistent deformation across a character animation space; reduce artist workload

---

### 6.4 Rigid Body Simulation

#### 6.4.1 Dynamics & Time Integration
- 6.4.1.1 Newton-Euler Equations: F = m a (Linear); τ = I α + ω × (I ω) (Angular); State = (x, q, v, ω); I_local → I_world = R I_local Rᵀ
  - ▸ *CG use:* Every physics engine; rigid body solver core; Bullet, PhysX, Havok
- 6.4.1.2 Time Stepping: Explicit Euler: x_{n+1}=x_n + v_n Δt (Simple, Unstable for Stiff Systems); Semi-Implicit Euler: v_{n+1}=v_n + a_n Δt, x_{n+1}=x_n + v_{n+1} Δt (Symplectic = Energy-Conserving for Conservative Systems); Verlet: x_{n+1}=2x_n − x_{n-1} + a_n Δt² (Velocity-Free, Time-Reversible)
  - ▸ *CG use:* Game physics = Semi-Implicit Euler (good trade-off); Verlet for cloth/particles (position-based constraint enforcement)
- 6.4.1.3 Adaptive Time Stepping: Δt_{n+1} = Δt_n · (tol / error)^(1/(p+1)); Reduce Δt When Error Large (Collision, High Acceleration), Increase When Error Small; Error Estimate via Embedded RK Pair (Fehlberg, Dormand-Prince)
  - ▸ *CG use:* Offline simulation accuracy; game physics typically uses fixed Δt for determinism

#### 6.4.2 Collision Detection & Response
- 6.4.2.1 Broad Phase: Sweep and Prune (Sort AABB Min/Max Projections on Axis → Overlap List); Spatial Hashing (Infinite Grid + Hash, GPU-Friendly); Dynamic BVH (Bottom-Up Refit for Moving Objects); O(n) to O(n log n)
  - ▸ *CG use:* Reduce O(n²) all-pairs collision to near-linear; PhysX, Bullet all use broad phase
- 6.4.2.2 Narrow Phase — GJK (Gilbert-Johnson-Keerthi): Compute Minkowski Difference A⊖B = {a−b}; Distance = min ‖point in A⊖B‖; Iteratively Refine Simplex Inside A⊖B; Returns Closest Distance + Closest Points; EPA (Expanding Polytope Algorithm): Extends GJK to Compute Penetration Depth + Contact Normal
  - ▸ *CG use:* THE standard convex collision algorithm in every physics engine; GJK + EPA handles all convex shapes
- 6.4.2.3 Collision Response: Impulse-Based: Instantaneous Velocity Change via Conservation of Momentum; j = −(1+e)(v_rel·n) / (1/m_A + 1/m_B + n·(I_A⁻¹(r_A×n))×r_A + ...); e = Coefficient of Restitution (0=Plastic, 1=Elastic); Friction via Coulomb Model (Static μ_s > Kinetic μ_k)
  - ▸ *CG use:* Game physics collision response; impulse-based is fast and stable for most cases

---

### 6.5 Soft Body & Cloth Simulation

#### 6.5.1 Mass-Spring & PBD/XPBD
- 6.5.1.1 Mass-Spring: Forces = Σ k_s (‖x_i−x_j‖−L₀)·(x_i−x_j)/‖x_i−x_j‖ (Spring) + k_d (v_j−v_i) (Damping); Structural + Shear + Bend Springs (Provot 1995 Cloth Model)
  - ▸ *CG use:* Simple cloth/hair; game physics; limited accuracy (stiffness-dependent time step)
- 6.5.1.2 Position-Based Dynamics (PBD — Müller et al. 2007): Directly Manipulate Positions to Satisfy Constraints; For Each Constraint: Project Positions to Constraint Manifold; C(x+Δx)→0 via Newton Step; Gauss-Seidel Iteration Over All Constraints
  - ▸ *CG use:* Real-time cloth, hair, fluids in games; NVIDIA FleX; Unity/Unreal built-in physics; stable at large time steps
- 6.5.1.3 XPBD (Extended PBD — Macklin et al. 2016): Add Compliance Parameter α = 1/k (Stiffness Inverse) to Lagrange Multiplier Update; λ_{n+1} = (−C − α̃ λ_n) / (∇CᵀM⁻¹∇C + α̃); Correct Stiffness Behavior Independent of Iteration Count; Converges to True Physics as Iterations→∞
  - ▸ *CG use:* Fixes PBD's stiffness-dependence-on-iteration problem; NVIDIA PhysX 5; production cloth simulation

#### 6.5.2 Finite Element Method (FEM) for Deformables
- 6.5.2.1 Corotational FEM: Decompose Deformation Gradient F = R S (Polar Decomposition: R = Rotation, S = Stretch); Remove Rotation R Before Computing Strain → Geometric Nonlinearity Without Material Nonlinearity; Fast (Small Deformation in Local Frame + Global Rotation)
  - ▸ *CG use:* Real-time deformable objects; game destructible environments; medical simulation
- 6.5.2.2 Hyperelastic Models: Neo-Hookean Ψ = μ/2 (tr(C)−3) − μ ln J + λ/2 (ln J)² (Stable Under Compression, Doesn't Invert); St. Venant-Kirchhoff (Simple but Unstable Under Compression — Avoid); Mooney-Rivlin (Better Rubber Modeling)
  - ▸ *CG use:* Neo-Hookean is the default for production FEM simulation; handles large deformation without element inversion
- 6.5.2.3 Projective Dynamics (Bouaziz et al. 2014): Reformulate Implicit Euler as Optimization: min_x ½‖x−y‖²_M + Δt² E(x); E(x) = Σ w_i ‖A_i x − B_i p_i‖² (Element-Wise Quadratic); Alternating: Fix p (Local Projection) → Solve for x (Global Quadratic); Each Step is Fast + Parallel
  - ▸ *CG use:* Real-time FEM in games and VR; GPU-accelerated via Cholesky prefactorization; Adobe's animation tools

---

### 6.6 Fluid Simulation

#### 6.6.1 Grid-Based (Eulerian) Methods
- 6.6.1.1 Navier-Stokes: ∂u/∂t + (u·∇)u = −(1/ρ)∇p + ν∇²u + f; ∇·u = 0 (Incompressibility); Advection + Pressure + Diffusion + External Forces
  - ▸ *CG use:* Smoke, fire, water simulation; Stable Fluids (Stam 1999) introduced semi-Lagrangian advection to graphics
- 6.6.1.2 Staggered (MAC) Grid: Velocity Stored at Cell Faces (Not Centers); Pressure at Cell Centers; Natural Divergence-Free Discretization; Avoids Checkerboard Pressure Instability
  - ▸ *CG use:* Standard grid layout for incompressible flow; pressure solve yields exactly divergence-free velocities on faces
- 6.6.1.3 Pressure Projection: Solve Poisson Equation ∇²p = ∇·u* (Divergence of Intermediate Velocity); u^{n+1} = u* − Δt ∇p; Result is Divergence-Free; Solve via Conjugate Gradient / Multigrid (AMG for Performance)
  - ▸ *CG use:* The computational bottleneck of grid-based fluids; multigrid preconditioned CG for real-time

#### 6.6.2 Particle-Based (Lagrangian) Methods
- 6.6.2.1 SPH (Smoothed Particle Hydrodynamics): A(x) ≈ Σ m_j A_j/ρ_j W(‖x−x_j‖, h); Density ρ_i = Σ m_j W_{ij}; Pressure Force via p_i = κ(ρ_i−ρ₀); WCSPH, IISPH (Implicit Incompressible), DFSPH (Divergence-Free)
  - ▸ *CG use:* Free-surface water; splash/spray/foam; real-time fluid in games (NVIDIA FleX); film VFX
- 6.6.2.2 FLIP / PIC / APIC: PIC (Particle-In-Cell): Transfer Particle Velocity → Grid → Solve Pressure → Transfer Grid Velocity Back → Advect Particles (Smooth but Overly Diffusive); FLIP: Transfer Velocity Change (Δv) Not Full Velocity Back to Particles (Preserves Detail but Noisy); APIC (Affine): Transfer Affine Velocity Field per Particle (Best of Both — Smooth + Detailed)
  - ▸ *CG use:* APIC is state-of-the-art for film-quality fluid; Disney's Moana water; Houdini flip solver

#### 6.6.3 Material Point Method (MPM)
- 6.6.3.1 MPM: Particles Carry Full Deformation Gradient F (Not Just Position); Transfer Particle → Grid (Mass + Momentum) → Solve on Grid (FEM) → Transfer Grid → Particles (Update F, v); Handles Large Deformation, Fracture, History-Dependent Materials Naturally
  - ▸ *CG use:* Snow simulation (Disney's Frozen — Stomakhin et al. 2013); sand, mud, viscoplastic materials; the "swiss army knife" of simulation
- 6.6.3.2 MLS-MPM (Hu et al. 2018): Moving Least Squares Shape Functions Replace B-Spline; Faster Than Classic MPM (~2×); Simpler Implementation; AFMPC (Affine Particle-In-Cell) Unification
  - ▸ *CG use:* Real-time MPM in Taichi; GPU-accelerated snow/sand/granular materials; game physics research

---

### 6.7 Character Animation & Motion Synthesis

#### 6.7.1 Motion Matching & Graphs
- 6.7.1.1 Motion Graph (Kovar et al. 2002): Nodes = Frames of Mocap Data; Edges = Valid Transitions (Similar Pose + Velocity); Shortest Path for Desired Motion; Post-Process for Smoothness
  - ▸ *CG use:* Character navigation from mocap library; dynamic motion synthesis
- 6.7.1.2 Motion Matching (Clavet 2016 — For Honor, Last of Us Part II): Per-Frame: Query Database for Best Matching Frame Given Current Pose + Desired Future Trajectory; Match on: Joint Positions, Velocities, Future Path; PCA on Pose Features for Efficient Search; No Precomputed Graph
  - ▸ *CG use:* State-of-the-art game character animation; smooth, responsive, no manual transition authoring; UE5 Motion Matching
- 6.7.1.3 Learned Motion Matching (Holden et al. 2020): Neural Network Replaces Database Query; Input: Current Pose + Trajectory, Output: Next Pose; Learns Deformation + Foot IK Implicitly; Dramatically Smaller Memory than Database
  - ▸ *CG use:* Mobile/console animation memory reduction; smoother motion than database lookup; ML-based animation

#### 6.7.2 Physics-Based Character Animation
- 6.7.2.1 DeepMimic (Peng et al. 2018): Deep RL Agent Trained to Imitate Reference Mocap; Physics Simulation + Neural Network Policy; Reward = Pose Matching + Velocity Matching + End-Effector Matching; Produces Physically Plausible Motion
  - ▸ *CG use:* Character that reacts to pushes/obstacles naturally; physically valid animation from mocap
- 6.7.2.2 Adversarial Motion Priors (AMP — Peng et al. 2021): Discriminator Learns Realistic Motion Manifold from Mocap; Generator (Policy) Tries to Produce Realistic Motion While Achieving Task; Style Reward from Discriminator
  - ▸ *CG use:* Natural-looking motion without per-motion reward engineering; general-purpose physics-based animation
- 6.7.2.3 ASE (Adversarial Skill Embeddings — Peng et al. 2022): Learn Latent Skill Space from Mocap; High-Level Controller Selects Skill; Low-Level Policy Executes Skill; Composable and Reusable Motor Skills
  - ▸ *CG use:* Hierarchical character control; complex behaviors from simple skill combinations

> 📚 **GitHub Repos:**
> - [InteractiveComputerGraphics/PositionBasedDynamics](https://github.com/InteractiveComputerGraphics/PositionBasedDynamics) ![Stars](https://img.shields.io/github/stars/InteractiveComputerGraphics/PositionBasedDynamics?style=flat) — PBD/XPBD implementation
> - [dilevin/CSC2549](https://github.com/dilevin/CSC2549) — Physics-based animation course (FEM, MPM, fluids)
> - [taichi-dev/taichi](https://github.com/taichi-dev/taichi) ![Stars](https://img.shields.io/github/stars/taichi-dev/taichi?style=flat) — Differentiable MPM, FEM, fluid simulation
> - [NVIDIAGameWorks/PhysX](https://github.com/NVIDIAGameWorks/PhysX) ![Stars](https://img.shields.io/github/stars/NVIDIAGameWorks/PhysX?style=flat) — Production physics engine
>
> 📖 **Textbooks:**
> - *Computer Animation* — Rick Parent; *Fluid Simulation for Computer Graphics* — Bridson
> - *Physics-Based Animation* — Erleben et al.; *Game Physics Engine Development* — Ian Millington

---


## Chapter 7 · Geometry Processing & Shape Analysis

*The algorithms that manipulate, analyze, and optimize 3D geometry — simplification, smoothing, parameterization, reconstruction, and shape understanding. `▸ CG use:` links each technique.*

> 💡 **Top-Level References:**
> - [libigl/libigl](https://github.com/libigl/libigl) ![Stars](https://img.shields.io/github/stars/libigl/libigl?style=flat) — Swiss-army-knife geometry processing library
> - [geometry-central/geometry-central](https://github.com/nmwsharp/geometry-central) ![Stars](https://img.shields.io/github/stars/nmwsharp/geometry-central?style=flat) — DEC, geodesics, parameterization in C++
> - [alecjacobson/geometry-processing](https://github.com/alecjacobson/geometry-processing) — Graduate course: mesh processing algorithms

---

### 7.1 Mesh Data Structures & Topological Operations

#### 7.1.1 Representations in Depth
- 7.1.1.1 Half-Edge: Each Edge = Two Directed Half-Edges; Each Half-Edge Stores: Next, Prev, Twin, Vertex (Target), Face, Edge; O(1) Adjacency: Vertex→Ring, Face→Boundary, Edge Flips
  - ▸ *CG use:* OpenMesh, CGAL Polyhedron_3, libigl; the standard for geometry processing
- 7.1.1.2 Directed Edge: Single Integer Index per Half-Edge; Implicit Adjacency via Index Arithmetic; More Memory-Efficient than Half-Edge; Used in GPU Geometry Processing
  - ▸ *CG use:* Geometry shader adjacency; mesh shader meshlet construction
- 7.1.1.3 Corner Table (Rossignac 2001): Corner = (Vertex, Face) Association; V[c] = Vertex Idx, O[c] = Opposite Corner, N[c] = Next Corner Around Face; Extremely Compact (2 ints per corner)
  - ▸ *CG use:* GPU-friendly mesh traversal; geometry compression (Edgebreaker); lightweight processing

#### 7.1.2 Topological Operations
- 7.1.2.1 Edge Flip: Swap Diagonal of Two Adjacent Triangles; Maintains Genus and Boundary; Used in Delaunay Triangulation (Lawson Flip) and Remeshing
  - ▸ *CG use:* Delaunay mesh generation; isotropic remeshing; improving element quality
- 7.1.2.2 Edge Collapse (Simplification): Merge Two Vertices into One; Remove Degenerate Triangles; Key Operation in QEM Simplification (Garland-Heckbert 1997)
  - ▸ *CG use:* Progressive mesh LOD; mesh decimation; adaptive simplification
- 7.1.2.3 Edge Split (Refinement): Split Edge at Midpoint, Split Adjacent Triangles; Increases Mesh Resolution; Key Operation in Subdivision and Adaptive Refinement
  - ▸ *CG use:* Subdivision surfaces; adaptive tessellation; mesh refinement for FEM

---

### 7.2 Mesh Simplification & Level of Detail

#### 7.2.1 Quadric Error Metric (QEM) Simplification
- 7.2.1.1 QEM (Garland & Heckbert 1997): Per-Vertex Error Quadric Q_v = Σ_{faces f ∋ v} K_f (4×4 Matrix); K_f Encodes Distance to Face Plane; Edge Collapse Cost: v̄ᵀ (Q_i+Q_j) v̄; Optimal New Position: Solve (Q_i+Q_j) v̄ = (0,0,0,1)ᵀ
  - ▸ *CG use:* The standard mesh simplification algorithm; fast, quality-preserving, widely implemented
- 7.2.1.2 Appearance-Preserving Simplification: Extend QEM with Texture Coordinate Error; Attribute Quadrics for Color, Normal, UV Preservation; Image-Driven Simplification (Render and Compare)
  - ▸ *CG use:* Game asset LOD generation; preserve texture seams and material boundaries

#### 7.2.2 Progressive Meshes & LOD
- 7.2.2.1 Progressive Meshes (Hoppe 1996): Store Base Mesh + Sequence of Vertex Splits (Inverse of Edge Collapses); Any Resolution by Applying Subset of Splits; Geomorph Transitions Between LODs (Vertex Morphing)
  - ▸ *CG use:* Continuous LOD; geometry streaming over network; adaptive terrain rendering
- 7.2.2.2 View-Dependent LOD (Hoppe 1997): Refine Mesh Non-Uniformly: Finer Near Viewer + Silhouette, Coarser in Distance; Vertex Hierarchy (Forest of Binary Trees); Active Nodes Determined Per-Frame by View Parameters
  - ▸ *CG use:* Large terrain rendering; CAD model visualization; VR high-quality foveated rendering

---

### 7.3 Mesh Smoothing, Fairing & Denoising

#### 7.3.1 Classical Smoothing
- 7.3.1.1 Laplacian Smoothing: v_i ← v_i + λ Σ_{j∈N(i)} w_{ij} (v_j−v_i); w=uniform (Umbrella Operator — Fast, Shrinkage), w=cotangent (Scale-Invariant, Shape-Preserving); Repeated Application → Mean Curvature Flow ∂x/∂t = −H n
  - ▸ *CG use:* Noise removal; mesh fairing; excessive iterations cause volume shrinkage
- 7.3.1.2 Taubin Smoothing (λ/μ Scheme — 1995): Alternate Positive λ (Smooth) and Negative μ (Inflate — Undo Shrinkage); μ < −λ, |μ| > λ for Low-Pass Filter; Preserves Volume Better than Pure Laplacian
  - ▸ *CG use:* Mesh denoising without volume loss; standard pipeline for scan cleanup
- 7.3.1.3 Bilateral Mesh Filtering: Filter Vertex Positions Using Spatial + Normal Weights; Spatial: Distance on Surface (Geodesic), Range: Normal Difference; Preserves Sharp Edges While Smoothing Flat Regions
  - ▸ *CG use:* Feature-preserving denoising; 3D scan processing; photogrammetry mesh cleanup

#### 7.3.2 Optimization-Based Methods
- 7.3.2.1 L₀ / L₁ Sparsity-Prior Denoising: Minimize Data Term + λ · ‖Lv‖₀ (Number of Non-Zero Laplacians) or λ · ‖Lv‖₁ (Sparse Laplacian); L₀ Better Preserves Flat Regions + Sharp Creases
  - ▸ *CG use:* CAD model denoising (sharp edges are important); architectural mesh processing
- 7.3.2.2 Guided Normal Filtering (Zhang et al. 2015): Filter Face Normals (Not Positions); Bilateral/Guided Filter on Normal Field → Update Vertex Positions to Match Filtered Normals via Poisson Reconstruction
  - ▸ *CG use:* State-of-the-art feature-preserving mesh denoising; handles large noise while preserving edges
- 7.3.2.3 Non-Local Means for Meshes: For Each Face/Patch, Find Similar Patches Elsewhere on Surface; Average with Similarity Weights; Exploits Self-Similarity for Superior Denoising
  - ▸ *CG use:* High-quality denoising of noisy scans; texture-like geometric detail recovery

---

### 7.4 Mesh Parameterization & UV Mapping

#### 7.4.1 Conformal & Distortion-Minimizing Methods
- 7.4.1.1 Least Squares Conformal Maps (LSCM — Lévy et al. 2002): Minimize Conformal Energy E = Σ_T ‖∇u − [0 −1; 1 0] ∇v‖²; Fixed Two Vertices to Pin Translation+Rotation; Linear System (Sparse); Angle-Preserving
  - ▸ *CG use:* Blender UV unwrap (Smart UV Project variant); texture mapping for organic models
- 7.4.1.2 ARAP Parameterization (Liu et al. 2008): As-Rigid-As-Possible in 2D; Minimize Σ_T ‖J_T − R_T‖²_F (Jacobian Should Be Rotation); Local/Global Alternating Optimization; Area + Angle Preserving
  - ▸ *CG use:* High-quality UV unwrapping; minimal distortion; Blender's Unwrap uses LSCM, ARAP available as plug-in
- 7.4.1.3 Angle-Based Flattening (ABF — Sheffer & de Sturler 2001): Optimize Angles Directly (Not Positions); Constraint: Angles Sum to 2π Around Interior Vertices; Produces Valid (No Triangle Flip) Parameterization; ABF++ for Free Boundaries
  - ▸ *CG use:* Guaranteed valid UV maps; no triangle flips; slower than LSCM but guaranteed quality

#### 7.4.2 Global & Seamless Parameterization
- 7.4.2.1 Globally Smooth Parameterization: Cone Singularities (Gaussian Curvature Concentrators); Integer-Valued Transition Functions Across Cut Graph; Quadrangulation via Parameterization → Extract Integer Grid Lines
  - ▸ *CG use:* Quad meshing; cross-field guided remeshing; texture atlas generation
- 7.4.2.2 Atlas Generation: Seam-Guided Segmentation (Minimize Seam Length + Distortion); Chart Packing into Unit Square; UDIM Multi-Tile Layout for Film Resolution Textures
  - ▸ *CG use:* Production UV atlases (Mari, Substance Painter); multi-tile texture workflows

---

### 7.5 Surface Reconstruction from Point Clouds

#### 7.5.1 Implicit Reconstruction
- 7.5.1.1 Poisson Surface Reconstruction (Kazhdan et al. 2006): Solve Δχ = ∇·V (Indicator Function χ from Oriented Points); V = Filtered Normal Field; Multigrid Poisson Solver; Extract Isosurface via Marching Cubes; Watertight Output
  - ▸ *CG use:* The gold standard for point cloud → mesh; Meshlab, CloudCompare, COLMAP all implement Poisson
- 7.5.1.2 Screened Poisson (Kazhdan & Hoppe 2013): Add Data Term: χ(x_i) ≈ 0.5 (Point at Surface); Balances Gradient Fit + Point Interpolation; Sharper Features than Classic Poisson
  - ▸ *CG use:* Higher quality scans; better preservation of sharp edges and fine detail
- 7.5.1.3 RBF Reconstruction (Carr et al. 2001): f(x) = Σ w_i φ(‖x−c_i‖) + P(x); Add Off-Surface Points (Normal Offset) for Sign; Global Support RBF (Thin-Plate, Bi-Harmonic) → Solve Dense Linear System; Fast Multipole Method for Scalability
  - ▸ *CG use:* Scattered data reconstruction; medical imaging surface extraction; offline high-quality reconstruction

#### 7.5.2 Volumetric & Learning-Based Methods
- 7.5.2.1 TSDF Fusion (Curless & Levoy 1996): D(x) = Σ w_i d_i(x) / Σ w_i (Weighted Running Average); Each Depth Map → SDF Sample; Fuse Multiple Depth Maps into Single Volume; Extract via Marching Cubes; KinectFusion (Newcombe et al. 2011) = Real-Time GPU TSDF
  - ▸ *CG use:* Real-time 3D scanning; RGB-D reconstruction; AR environmental understanding
- 7.5.2.2 Neural Surface Reconstruction: Occupancy Networks, DeepSDF, NeuS, Neuralangelo (See Ch. 5 for full treatment); Implicit Neural Representations Learn Smooth Priors from Data
  - ▸ *CG use:* State-of-the-art reconstruction from images/point clouds; handles missing data naturally

---

### 7.6 Shape Analysis & Descriptors

#### 7.6.1 Spectral Shape Analysis
- 7.6.1.1 Laplace-Beltrami Spectrum: Δφ_k = λ_k φ_k; Spectrum {λ_k} is Isometry-Invariant; ShapeDNA: Use First N Eigenvalues as Shape Fingerprint; Functional Maps: Express Correspondence as Map Between Function Spaces C(M) → C(N)
  - ▸ *CG use:* Non-rigid shape matching; shape retrieval; deformation analysis; medical shape classification
- 7.6.1.2 Heat Kernel Signature (HKS — Sun et al. 2009): h_t(x) = K_t(x,x) = Σ_k e^{−λ_k t} φ_k²(x); Multi-Scale Descriptor (Small t = Local Geometry, Large t = Global Shape); Intrinsic (Bending-Invariant); Wave Kernel Signature (WKS — Aubry et al. 2011): Band-Pass Filter → Better Feature Separation
  - ▸ *CG use:* Point correspondence in non-rigid shapes; shape segmentation; feature point detection

#### 7.6.2 Geometric Features & Segmentation
- 7.6.2.1 Shape Diameter Function (SDF — Shapira et al. 2008): For Each Surface Point, Average Ray Length Inside Volume Along Opposite Normal Direction; Captures Local Thickness; Pose-Invariant
  - ▸ *CG use:* Shape segmentation (thin limbs vs. thick torso); skeleton extraction; part-based shape retrieval
- 7.6.2.2 Mesh Segmentation: Curvature-Based (Watershed on Mean/Gaussian Curvature), Spectral Clustering (Eigenvectors of Laplacian as Embedding → K-Means), Randomized Cuts (Golovinskiy & Funkhouser 2008), Shape Diameter + Graph Cut
  - ▸ *CG use:* Part-based modeling; texture atlas generation; shape correspondence pre-processing

---

### 7.7 Shape Correspondence & Registration

#### 7.7.1 Rigid & Non-Rigid Registration
- 7.7.1.1 ICP (Iterative Closest Point — Besl & McKay 1992): For Each Source Point, Find Nearest Target Point (Correspondence) → Solve Procrustes for Optimal Rigid Transform → Repeat; Point-to-Plane Variant: Minimize Distance to Target Tangent Plane (Faster Convergence)
  - ▸ *CG use:* Scan alignment; 3D reconstruction loop closure; quality inspection (CAD vs. scan)
- 7.7.1.2 Non-Rigid ICP: Allow Per-Vertex Deformation (ARAP or Laplacian Regularization); E-Step: Find Nearest Points on Target; M-Step: Deform Source to Minimize Distance + Regularization; Embedded Deformation Graph for Efficiency
  - ▸ *CG use:* Facial expression transfer; body shape fitting (SMPL to scan); animation retargeting
- 7.7.1.3 Coherent Point Drift (CPD — Myronenko & Song 2010): Probabilistic Framework: GMM Centroid = Source Points, Target = Data; Maximize Likelihood via EM; Coherent Motion Prior (GMM Components Move Together); Outperforms ICP for Non-Rigid Cases
  - ▸ *CG use:* Medical image registration; point set alignment with noise/outliers; motion capture marker matching

#### 7.7.2 Functional Maps Framework
- 7.7.2.1 Functional Maps (Ovsjanikov et al. 2012): Represent Correspondence as Linear Operator C: F(M,ℝ) → F(N,ℝ); Truncate to k Leading Eigenfunctions → C is Small k×k Matrix; Optimize C for Descriptor Preservation + Operator Commutativity
  - ▸ *CG use:* State-of-the-art shape correspondence; scalable to large shape collections; basis for many follow-up works
- 7.7.2.2 Deep Functional Maps (Litany et al. 2017): Learn Feature Descriptors via Neural Network → Compute Functional Map from Learned Features → Supervise with Geodesic Error; End-to-End Differentiable; Generalizes Across Shape Categories
  - ▸ *CG use:* Automatic shape matching; learned correspondence without handcrafted descriptors

---

### 7.8 Mesh Repair, Remeshing & Compression

#### 7.8.1 Mesh Repair
- 7.8.1.1 Common Defects: Non-Manifold Edges/Vertices, Self-Intersections, Degenerate Faces (Zero Area), Inconsistent Normals, Holes, Duplicate Vertices, Isolated Components
  - ▸ *CG use:* 3D printing requires watertight, manifold, non-self-intersecting meshes; every scan→print pipeline needs repair
- 7.8.1.2 Hole Filling: Minimum Area Triangulation (Liepa 2003), Advancing Front (Fill from Hole Boundary Inward, Maintain Smoothness), Context-Based (Learn Hole Geometry from Surrounding Surface — Neural Methods); Fairing for Smooth Blending
  - ▸ *CG use:* Scan post-processing; incomplete archaeological artifact reconstruction

#### 7.8.2 Isotropic & Anisotropic Remeshing
- 7.8.2.1 Isotropic Remeshing: Uniform Edge Length + Regular Vertex Valence (6 Interior, 4 Boundary); Centroidal Voronoi Tessellation + Lloyd Relaxation → Even Point Distribution → Delaunay Triangulation; Botsch & Kobbelt (2004) Framework
  - ▸ *CG use:* FEM mesh generation (uniform quality); shape modeling subdivision
- 7.8.2.2 Anisotropic Remeshing: Edge Length Varies with Principal Curvature (Shorter Along High Curvature Direction); Mesh Aligned with Curvature Directions; Better Approximation with Fewer Triangles
  - ▸ *CG use:* CAD model meshing; CFD boundary layer meshing; curvature-adaptive LOD

#### 7.8.3 Geometry Compression
- 7.8.3.1 Draco (Google): Edgebreaker Connectivity Compression + Predictive Vertex Position Coding + Entropy Coding; 10-100× Compression for Meshes and Point Clouds; KTX 2.0 for Textures; glTF Extension
  - ▸ *CG use:* Web 3D delivery; game asset streaming; AR asset compression; Google Earth 3D tiles
- 7.8.3.2 Corto / Open3DGC: Lightweight Alternative to Draco; Optimized for Real-Time Decode on Mobile; Progressive Decoding (Base Mesh → Refinement)
  - ▸ *CG use:* Mobile 3D streaming; WebGL progressive mesh loading

> 📚 **GitHub Repos:**
> - [libigl/libigl](https://github.com/libigl/libigl) ![Stars](https://img.shields.io/github/stars/libigl/libigl?style=flat) — Simplification, smoothing, parameterization, reconstruction
> - [geometry-central/geometry-central](https://github.com/nmwsharp/geometry-central) ![Stars](https://img.shields.io/github/stars/nmwsharp/geometry-central?style=flat) — DEC, geodesics, vector fields
> - [google/draco](https://github.com/google/draco) ![Stars](https://img.shields.io/github/stars/google/draco?style=flat) — Production mesh compression
> - [PointCloudLibrary/pcl](https://github.com/PointCloudLibrary/pcl) ![Stars](https://img.shields.io/github/stars/PointCloudLibrary/pcl?style=flat) — Comprehensive point cloud processing
>
> 📖 **Textbooks:**
> - *Polygon Mesh Processing* — Botsch, Kobbelt, Pauly, Alliez, Lévy (The definitive reference)
> - *Geometric Modeling* — Mortenson; *Curves and Surfaces for CAGD* — Farin

---


## Chapter 8 · 3D Vision, Reconstruction & Computational Photography

*From camera geometry to dense reconstruction and smartphone photography — how the physical world becomes digital 3D. `▸ CG use:` links each technique.*

> 💡 **Top-Level References:**
> - [colmap/colmap](https://github.com/colmap/colmap) ![Stars](https://img.shields.io/github/stars/colmap/colmap?style=flat) — State-of-the-art SfM + MVS pipeline
> - [naver/dust3r](https://github.com/naver/dust3r) ![Stars](https://img.shields.io/github/stars/naver/dust3r?style=flat) — Dense stereo from unposed images (2024 breakthrough)
> - [nerfstudio-project/nerfstudio](https://github.com/nerfstudio-project/nerfstudio) ![Stars](https://img.shields.io/github/stars/nerfstudio-project/nerfstudio?style=flat) — Neural reconstruction framework

---

### 8.1 Camera Models & Projective Geometry

#### 8.1.1 Camera Geometry
- 8.1.1.1 Pinhole Camera Model: x = K [R|t] X; K = [f_x s c_x; 0 f_y c_y; 0 0 1] (Intrinsic Matrix: Focal Length, Skew, Principal Point); [R|t] = Extrinsic Matrix; 3×4 Projection Matrix P Maps 3D World → 2D Image
  - ▸ *CG use:* Every SfM/SLAM/3D reconstruction pipeline; camera calibration; CG rendering projection
- 8.1.1.2 Radial & Tangential Distortion (Brown-Conrady): x_d = x(1 + k₁r² + k₂r⁴ + k₃r⁶) + [2p₁xy + p₂(r²+2x²); p₁(r²+2y²) + 2p₂xy]; k₁,k₂,k₃ = Radial, p₁,p₂ = Tangential; Undistort Before Processing
  - ▸ *CG use:* Lens distortion correction; photogrammetry pre-processing; OpenCV calibrateCamera
- 8.1.1.3 Light Field / Plenoptic Function: L(x,y,z,θ,φ,λ,t) — 7D Function; 4D Light Field (Two-Plane Parameterization — Levoy & Hanrahan 1996): L(u,v,s,t); Refocus After Capture (Synthetic Aperture), Change Viewpoint
  - ▸ *CG use:* Lytro camera; post-capture refocus; VR light field rendering; neural radiance fields approximate plenoptic function

#### 8.1.2 Multi-View Geometry
- 8.1.2.1 Epipolar Geometry: Epipolar Plane (Camera Centers + 3D Point); Epipolar Line (Intersection of Epipolar Plane with Image Plane); All Correspondences Lie on Epipolar Line; Fundamental Matrix F Encodes Epipolar Geometry (Uncalibrated), Essential Matrix E (Calibrated)
  - ▸ *CG use:* Stereo matching (reduce 2D search to 1D along epipolar line); visual odometry; SfM initialization
- 8.1.2.2 Essential Matrix: E = [t]× R (3×3, Rank 2, 5 DOF); x₂ᵀ E x₁ = 0 (Normalized Image Coordinates); 8-Point Algorithm (Longuet-Higgins 1981), 5-Point Algorithm (Nistér 2004 — Minimal Solver, RANSAC)
  - ▸ *CG use:* Relative camera pose estimation; SfM initial pair selection; Visual SLAM initialization
- 8.1.2.3 Fundamental Matrix: F = K₂⁻ᵀ E K₁⁻¹ (3×3, Rank 2, 7 DOF); p₂ᵀ F p₁ = 0 (Pixel Coordinates); 8-Point + Normalization (Hartley 1997), 7-Point Algorithm
  - ▸ *CG use:* Uncalibrated stereo; image matching verification; outlier rejection in SfM
- 8.1.2.4 Homography: Plane-Induced Mapping H (3×3); p₂ ≅ H p₁; 4 Point Correspondences (DLT); Decompose H → R,t,n (Faugeras & Lustman 1988)
  - ▸ *CG use:* Planar scene reconstruction; panorama stitching; augmented reality marker tracking

---

### 8.2 Structure from Motion (SfM)

#### 8.2.1 SfM Pipeline
- 8.2.1.1 Incremental SfM (COLMAP style): Feature Extraction (SIFT — Scale-Invariant Feature Transform) → Feature Matching (GPU Brute-Force + Lowe's Ratio Test) → Geometric Verification (Fundamental/Homography Estimation → RANSAC) → Initial Image Pair (Wide Baseline + Many Inliers) → Incremental Registration (PnP for New Cameras → Triangulate New Points → Bundle Adjustment) → Global Bundle Adjustment
  - ▸ *CG use:* COLMAP is the standard open-source SfM; most 3D reconstruction and NeRF pipelines start with COLMAP poses
- 8.2.1.2 Global SfM: Simultaneously Estimate All Camera Rotations (Rotation Averaging on SO(3)) + Translations (Translation Averaging); Single Global Optimization Instead of Incremental; More Scalable, Less Robust to Outliers
  - ▸ *CG use:* Large-scale reconstruction (city-scale); Theia, OpenMVG global pipelines
- 8.2.1.3 Bundle Adjustment (BA): Jointly Optimize Camera Parameters + 3D Point Positions; min_{C_i, X_j} Σ ‖π(C_i, X_j) − x_{ij}‖² (Reprojection Error); Sparse Levenberg-Marquardt (Schur Complement Trick: Marginalize Points → Solve Cameras → Back-Substitute Points)
  - ▸ *CG use:* The computational core of SfM and SLAM; Ceres Solver, g2o, GTSAM are the standard BA libraries

#### 8.2.2 Feature Extraction & Matching
- 8.2.2.1 SIFT (Lowe 2004): Scale-Space Extrema (DoG Pyramid) → Keypoint Localization (Subpixel Refinement) → Orientation Assignment (Gradient Histogram) → 128D Descriptor (Gradient Histograms in 4×4 Grid); Rotation + Scale Invariant; Patent Expired 2020
  - ▸ *CG use:* The gold standard feature for SfM; robust to viewpoint, illumination, scale changes
- 8.2.2.2 Modern Learned Features: SuperPoint (DeTone et al. 2018 — CNN Keypoint + Descriptor), SuperGlue (Sarlin et al. 2020 — GNN Attention Matching), LoFTR (Sun et al. 2021 — Transformer Dense Matching Without Keypoints), LightGlue (Lindebaum et al. 2023 — Faster SuperGlue)
  - ▸ *CG use:* Learned features outperform SIFT in challenging conditions (night, weather, textureless); SuperGlue+LightGlue are standard in modern pipelines
- 8.2.2.3 DUSt3R (Wang et al. 2024): Dense Pointmap Prediction Directly from Image Pair (No Keypoints!); Transformer Architecture Predicts Per-Pixel 3D for Both Images Simultaneously; Align Pointmaps via Procrustes (No Explicit Pose Estimation!); Foundation Model for 3D Vision
  - ▸ *CG use:* Replaces SfM + MVS pipeline; 3D reconstruction from uncalibrated images; democratizes 3D capture

---

### 8.3 Multi-View Stereo (MVS) & Depth Estimation

#### 8.3.1 Classical MVS
- 8.3.1.1 PatchMatch Stereo (Bleyer et al. 2011, PMVS — Furukawa & Ponce 2010): Random Initialization + Spatial Propagation (Good Disparities Propagate to Neighbors) + Random Refinement + View Propagation; Handles Slanted Surfaces (Per-Pixel 3D Plane); GPU Real-Time Variants
  - ▸ *CG use:* COLMAP MVS; high-quality depth maps; widely used in photogrammetry pipelines
- 8.3.1.2 Semi-Global Matching (SGM — Hirschmüller 2008): Mutual Information Cost + 8-Path Dynamic Programming Smoothness Term; 1D DP Along Multiple Directions → Approximate 2D MRF; Fast, Parallelizable; Built into Many Industrial Stereo Cameras
  - ▸ *CG use:* Real-time stereo on embedded systems; drone obstacle avoidance; automotive stereo

#### 8.3.2 Learned Depth Estimation
- 8.3.2.1 Learned Stereo Matching: PSMNet (Chang & Chen 2018 — 3D Cost Volume + Stacked Hourglass), RAFT-Stereo (Lipson et al. 2021 — Iterative 2D Correlation + GRU Update, Inspired by RAFT Optical Flow), CREStereo (Li et al. 2022 — Recurrent Refinement with Cascaded Resolution)
  - ▸ *CG use:* State-of-the-art stereo depth; generation of training data for NeRF/3DGS
- 8.3.2.2 Monocular Depth Estimation: MiDaS (Ranftl et al. 2020 — Transformer, Trained on Mixed Datasets → Zero-Shot Generalization); Depth Anything (Yang et al. 2024 — Large-Scale Unlabeled Data Training via Teacher-Student, DINOv2 Backbone → State-of-the-Art)
  - ▸ *CG use:* Single-image depth for AR; depth prior for sparse-view NeRF; robotics visual navigation
- 8.3.2.3 Multi-View Stereo Networks: MVSNet (Yao et al. 2018 — Differentiable Homography Warping + 3D UNet Cost Volume Regularization), CasMVSNet (Gu et al. 2020 — Cascade from Coarse to Fine), PatchMatchNet (Wang et al. 2021 — Learned PatchMatch)
  - ▸ *CG use:* Learned MVS reconstruction; faster than classical while maintaining quality

---

### 8.4 SLAM (Simultaneous Localization and Mapping)

#### 8.4.1 Visual & Visual-Inertial SLAM
- 8.4.1.1 ORB-SLAM3 (Campos et al. 2020): Three Parallel Threads: Tracking (ORB Features → Pose from PnP + Relocalization), Local Mapping (Keyframe Management + Local BA), Loop Closing (Bag-of-Words Place Recognition + Pose Graph Optimization + Full BA); Monocular/Stereo/RGB-D; Atlas Multi-Map System
  - ▸ *CG use:* The standard visual SLAM system; AR/VR tracking; robotics; autonomous driving
- 8.4.1.2 DSO (Direct Sparse Odometry — Engel et al. 2018): Direct Method: Optimize Photometric Error (Not Feature Reprojection); Sparse Gradient Points (High Image Gradient Regions); Joint Optimization of Pose + Depth + Camera Parameters; No Feature Descriptors!
  - ▸ *CG use:* High-precision odometry in feature-sparse environments; complements feature-based methods
- 8.4.1.3 VINS-Mono (Qin et al. 2018): Tightly-Coupled Visual-Inertial Odometry; IMU Pre-Integration Between Keyframes + Visual Feature Constraints + Sliding Window Optimization; Robust Initialization (Visual-Inertial Alignment); Loop Closure with Pose Graph
  - ▸ *CG use:* Drone navigation; handheld AR (ARKit/ARCore use VIO); fast camera motion where pure visual fails

#### 8.4.2 Dense & Neural SLAM
- 8.4.2.1 KinectFusion (Newcombe et al. 2011): Real-Time Dense TSDF Volume via GPU; ICP Frame-to-Model Tracking; Raycasting from Volume for Rendering; The First Real-Time Dense SLAM
  - ▸ *CG use:* Real-time 3D scanning; HoloLens spatial mapping; AR environmental mesh
- 8.4.2.2 ElasticFusion (Whelan et al. 2015): Surfel-Based Map (Not Volume); Non-Rigid Deformation for Loop Closure (Deform Map to Close Loops); Real-Time; Handles Room-Scale Environments
  - ▸ *CG use:* Room-scale real-time reconstruction; AR persistent mapping
- 8.4.2.3 NeRF-SLAM / 3DGS-SLAM: Neural Implicit Map Representation (Hash Grid + Tiny MLP); RGB + Depth → Jointly Optimize Pose + Neural Map; Dense Photorealistic Reconstruction; SplaTAM, MonoGS (Single RGB Camera → 3DGS Map!)
  - ▸ *CG use:* Photorealistic AR mapping; dense 3D reconstruction from monocular video; robotics perceptual mapping

---

### 8.5 Computational Photography

#### 8.5.1 HDR & Image Fusion
- 8.5.1.1 HDR Capture (Debevec & Malik 1997): Multiple Exposures → Recover Camera Response Function g(Z_{ij}) = ln E_i + ln Δt_j via Linear Least Squares; Weighted Fusion of Exposures → Radiance Map; Tone Map for Display
  - ▸ *CG use:* IBL light probe capture; smartphone HDR mode; every camera pipeline
- 8.5.1.2 Multi-Frame Fusion: Align + Merge Multiple Frames (Handheld Burst); Reduces Noise (√N Reduction) + Increases Dynamic Range; Google HDR+ (Hasinoff et al. 2016) — Tile-Based Alignment + Wiener Fusion; Apple Deep Fusion (Neural Network-Based)
  - ▸ *CG use:* Smartphone photography; low-light enhancement; surveillance camera quality

#### 8.5.2 Panorama, Video & Computational Effects
- 8.5.2.1 Panorama Stitching: Feature Matching → Homography Estimation → Bundle Adjustment (Global Alignment) → Seam Cutting (Graph Cut on Overlap) → Multi-Band Blending (Burt & Adelson 1983 — Blend Low Freq Over Large Area, High Freq Over Small Area); Cylindrical/Spherical Projection for Wide Angles
  - ▸ *CG use:* Smartphone panorama mode; VR 360° capture; Google Street View
- 8.5.2.2 Portrait Mode: Stereo Depth (Dual Camera) or Dual-Pixel PDAF Depth or Learned Monocular Depth → Synthetic Bokeh via Scatter Disk Rendering; Segmentation + Depth Map → Layer Separation; Defocus Map = f(1/depth − 1/focus_depth)
  - ▸ *CG use:* Every modern smartphone; computational bokeh approaches optical quality
- 8.5.2.3 Super-Resolution: Classical (Multi-Frame: Subpixel Shift → Higher Resolution via L1/L2 Reconstruction); Learned (SRCNN, ESRGAN, Real-ESRGAN, SwinIR); Diffusion-Based (Stable Diffusion Upscale, Cascaded Diffusion — State-of-the-Art)
  - ▸ *CG use:* 4K from 1080p; enhancing legacy game textures; medical imaging enhancement; satellite imagery

> 📚 **GitHub Repos:**
> - [colmap/colmap](https://github.com/colmap/colmap) ![Stars](https://img.shields.io/github/stars/colmap/colmap?style=flat) — SfM + MVS pipeline; [naver/dust3r](https://github.com/naver/dust3r) ![Stars](https://img.shields.io/github/stars/naver/dust3r?style=flat) — Unposed stereo reconstruction
> - [opencv/opencv](https://github.com/opencv/opencv) ![Stars](https://img.shields.io/github/stars/opencv/opencv?style=flat) — Camera calibration, stereo, SfM tools
> - [PointCloudLibrary/pcl](https://github.com/PointCloudLibrary/pcl) ![Stars](https://img.shields.io/github/stars/PointCloudLibrary/pcl?style=flat) — Point cloud processing, ICP, feature extraction
> - [xinntao/Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN) ![Stars](https://img.shields.io/github/stars/xinntao/Real-ESRGAN?style=flat) — Practical super-resolution
>
> 📖 **Textbooks:**
> - *Multiple View Geometry in Computer Vision* — Hartley & Zisserman (The bible)
> - *Computer Vision: Algorithms and Applications* — Szeliski; *Photogrammetric Computer Vision* — Förstner & Wrobel

---


## Chapter 9 · Graphics Systems, Hardware & Engineering

*The engineering backbone of computer graphics — GPU architectures, graphics APIs, shader languages, rendering engines, and data interchange. `▸ CG use:` links each system to production practice.*

> 💡 **Top-Level References:**
> - [SaschaWillems/Vulkan](https://github.com/SaschaWillems/Vulkan) ![Stars](https://img.shields.io/github/stars/SaschaWillems/Vulkan?style=flat) — Comprehensive Vulkan examples
> - [google/filament](https://github.com/google/filament) ![Stars](https://img.shields.io/github/stars/google/filament?style=flat) — Production PBR renderer with complete documentation
> - [KhronosGroup/glTF](https://github.com/KhronosGroup/glTF) ![Stars](https://img.shields.io/github/stars/KhronosGroup/glTF?style=flat) — glTF 2.0 specification and tools

---

### 9.1 GPU Architecture

#### 9.1.1 GPU Compute Model
- 9.1.1.1 SIMT Execution: Single Instruction, Multiple Threads; Warp (NVIDIA 32 Threads) / Wavefront (AMD 64 Threads) / Subgroup (Vulkan/D3D12); Threads in Warp Execute Same Instruction — Divergence Causes Serialization
  - ▸ *CG use:* Understanding warp occupancy and divergence is critical for shader optimization; avoid per-thread branching on divergent conditions
- 9.1.1.2 Streaming Multiprocessor (SM / CU): Warp Schedulers (4/SM on Ampere), Register File (64K 32-bit/SM), Shared Memory / LDS (Up to 164 KB on Ampere — Configurable L1/SMEM Split), Tensor Cores (FP16/BF16/INT8/FP8 Matrix Multiply), RT Cores (BVH Traversal + Triangle Intersection)
  - ▸ *CG use:* Shader performance is fundamentally limited by SM resources: register pressure, shared memory usage, and warp occupancy
- 9.1.1.3 Memory Hierarchy: Global Memory (HBM2/GDDR6X — 1-2 TB/s, High Latency ~600 cycles), L2 Cache (40-96 MB on Ada/Blackwell), L1/SMEM (~30 cycles latency), Register File (0 cycles); Coalesced Memory Access: Adjacent Threads → Adjacent Addresses → Single Transaction (128 Bytes)
  - ▸ *CG use:* Non-coalesced global memory access = 8-10× bandwidth penalty; texture cache (optimized for 2D locality) for random access
- 9.1.1.4 Compute Shader Model: Dispatch Thread Groups (3D Grid of Thread Blocks); Each Thread Block Mapped to SM; Within Thread Block: Shared Memory + Barrier Synchronization; Across Blocks: No Synchronization Guarantee
  - ▸ *CG use:* Particle systems, post-processing, culling, light culling, GPU skinning — all use compute shaders

#### 9.1.2 Modern GPU Features
- 9.1.2.1 Mesh Shaders (Turing+): Replace Vertex → Tessellation → Geometry Pipeline with Task Shader (Optional, Work Amplification) + Mesh Shader (Output Meshlets Directly to Rasterizer); No Fixed-Function Primitive Assembly; GPU-Driven Geometry Pipeline
  - ▸ *CG use:* UE5 Nanite; geometry culling on GPU; procedural geometry generation; reduces draw call count
- 9.1.2.2 Work Graphs (D3D12 / Vulkan Device-Generated Commands): GPU Generates Work for Itself; Producer Node → Consumer Node Execution; No CPU Round-Trip for Dependent Work; Material Shading, Classification, GPU Particle Emission
  - ▸ *CG use:* Fully GPU-driven rendering; culling → draw → compute post-processing → present all on GPU
- 9.1.2.3 Sampler Feedback & Texture-Space Shading: GPU Reports Which Texture Regions Were Sampled → CPU/GPU Only Shades Those Regions; Shade Texture Once, Reuse Across Frames (Sparse Shading); VRS Tier 2
  - ▸ *CG use:* Reducing shading cost; texture-space irradiance caching; dynamic resolution without visible blur

---

### 9.2 Modern Graphics APIs

#### 9.2.1 Vulkan — Explicit GPU Control
- 9.2.1.1 Core Concepts: Physical Device → Logical Device → Queues (Graphics, Compute, Transfer, Sparse Binding); Command Buffers (Multi-Threaded Recording); Pipeline State Objects (PSO — Precompiled Pipeline, No Runtime State Changes); Descriptor Sets (Bindless via Descriptor Indexing); Timeline Semaphores (Monotonically Increasing Counters)
  - ▸ *CG use:* Low-overhead API for high-performance rendering; explicit memory management (VMA); async compute overlap
- 9.2.1.2 Synchronization: Pipeline Barriers (Transition Image Layout + Flush/Invalidate Caches); Subpass Dependencies (Implicit Sync Within Render Pass); Events (Fine-Grained GPU-GPU Sync Within Command Buffer); Fences (GPU→CPU Signal); Semaphores (Queue → Queue Signal)
  - ▸ *CG use:* Correct synchronization is the hardest part of Vulkan; validation layers catch errors
- 9.2.1.3 Vulkan Ray Tracing: Acceleration Structure (TLAS + BLAS build via compute); Shader Binding Table (SBT — Shader Records per Geometry); Ray Generation → Traversal → Hit/Miss Shaders; Ray Query (Inline in Any Shader)
  - ▸ *CG use:* Cross-platform RT (Windows, Linux, Android); Steam Deck; game console emulators

#### 9.2.2 D3D12, Metal & WebGPU
- 9.2.2.1 D3D12: Similar to Vulkan (Explicit); Root Signatures (Descriptor Layout); State Objects (Graphics/Compute/RT Pipeline State); Resource Barriers with Automatic Subresource State Tracking (Enhanced Barriers in Agility SDK); DXR for Ray Tracing; Work Graphs (New in Agility SDK 2024); DirectSR (Super Resolution API Abstraction)
  - ▸ *CG use:* Windows/Xbox rendering; PC AAA games; professional visualization
- 9.2.2.2 Metal (Apple): Command Queue → Command Buffer → Command Encoder (Render/Compute/Blit/Parallel); Argument Buffers (GPU-Writable Descriptors); Indirect Command Buffers (GPU-Recorded Rendering Commands); Tile Shaders (Programmable Blend in Tile Memory); MetalFX (Temporal/Spatial Upscaling)
  - ▸ *CG use:* macOS/iOS/visionOS rendering; Apple Silicon unified memory → zero-copy CPU-GPU data; Vision Pro passthrough
- 9.2.2.3 WebGPU: Next-Gen Web Graphics API; Designed for Native Web Performance (Avoids WebGL's OpenGL ES Legacy); WGSL Shading Language; Compute + Render Pipeline; Bind Groups; Explicit Barriers; Cross-Platform via Dawn (Chromium) or wgpu (Firefox/Rust)
  - ▸ *CG use:* Web 3D rendering; ML inference in browser (WebGPU compute); cross-platform 3D without native builds

---

### 9.3 Shader Programming & Compilation

#### 9.3.1 Shader Languages
- 9.3.1.1 GLSL (OpenGL / Vulkan via SPIR-V): C-Like; Built-in Vector/Matrix Types (vec3, mat4); Limited Compile-Time Features; Compile to SPIR-V via glslang; Legacy but Still Widespread
  - ▸ *CG use:* Shadertoy; prototyping; OpenGL compatibility; Vulkan via glslang→SPIR-V
- 9.3.1.2 HLSL (D3D12 / Vulkan via DXC): C++-Like with Templates, Interfaces, Operator Overloading; SM 6.x Features: Wave Intrinsics, 16-Bit Types, Ray Tracing Intrinsics, Mesh Shaders; Compile to DXIL (D3D12) or SPIR-V (Vulkan via DXC); Dominant in AAA Games
  - ▸ *CG use:* Unreal Engine, Unity (HLSL→SPIR-V), AAA game development; DirectX ecosystem
- 9.3.1.3 Slang (NVIDIA): Superset of HLSL; Adds Generics, Interfaces with Associated Types, Automatic Differentiation (Slang.D); Compile to Multiple Targets (DXIL, SPIR-V, CUDA, C++, Metal); Production at NVIDIA
  - ▸ *CG use:* Differentiable rendering (Slang.D); cross-platform shader development; NVIDIA Omniverse
- 9.3.1.4 WGSL (WebGPU): Rust-Inspired Syntax; Designed for Security (No Raw Pointers, Bounds-Checked); Struct Types, Uniform/Storage Buffer Bindings; Compiler in Browser
  - ▸ *CG use:* WebGPU shaders; browser-based 3D; web ML inference

#### 9.3.2 Shader Compilation & Intermediate Representations
- 9.3.2.1 SPIR-V (Vulkan/OpenCL Standard IR): Binary Intermediate Representation; SSA-Based (Static Single Assignment); Supports All Shader Stages + Compute + Ray Tracing; Extensible via Capabilities/Extensions; spirv-opt (Optimizer), spirv-cross (SPIR-V→GLSL/HLSL/MSL)
  - ▸ *CG use:* Vulkan's shader format; enables cross-compilation ecosystem; validation and reflection
- 9.3.2.2 DXIL (DirectX Intermediate Language): LLVM Bitcode-Based IR; Signed, Validated by D3D Runtime; DXC Compiles HLSL→DXIL; Driver Compiles DXIL→ISA (GPU-Specific); Enables Shader Debugging (PIX) and Optimization
  - ▸ *CG use:* D3D12 shader pipeline; PIX shader debugging; game console shader compilation (Xbox uses DXIL variant)

---

### 9.4 Rendering Engine Architecture

#### 9.4.1 Frame Graph & Render Graph
- 9.4.1.1 Render Graph: Declarative Pass Specification (Input Resources → Pass → Output Resources); Automatic Resource Lifetime Management (Aliasing, Barrier Insertion, Memory Reuse); Execution Order Optimization; Async Compute Overlap Detection
  - ▸ *CG use:* UE5 RDG (Render Dependency Graph); Frostbite Frame Graph; Unity SRP Render Graph; simplifies complex multi-pass rendering
- 9.4.1.2 GPU-Driven Rendering Pipeline: CPU: Minimal Per-Frame Work (Resource Streaming, UI, Game Logic); GPU: Culling → Classification (Material Binning) → Indirect Draw Generation → Execute Indirect → Post-Processing; Persistent Shader Thread + GPU Work Submission
  - ▸ *CG use:* UE5 Nanite (GPU-driven geometry); GPU Work Graphs; reducing CPU draw call overhead to near-zero

#### 9.4.2 Multi-Threaded Rendering
- 9.4.2.1 Threading Model: Game Thread (Logic, Physics, AI) → Render Thread (Command Recording, Resource Upload, Draw Call Preparation) → GPU (Async Execution, Frames in Flight via Fences); Pipelined Parallelism (3 Frames Overlapping)
  - ▸ *CG use:* AAA game engine standard; maximize CPU/GPU utilization; typically 2-3 frames of latency
- 9.4.2.2 Parallel Command Recording: Vulkan Secondary Command Buffers (Record per-Thread → Execute in Primary); D3D12 Bundles (Similar Concept); Multi-Threaded Command List Generation; Deferred Contexts for Resource Creation
  - ▸ *CG use:* Reduce single-thread recording bottleneck; scalable to many CPU cores

---

### 9.5 Performance Optimization & Profiling

#### 9.5.1 Profiling Tools
- 9.5.1.1 GPU Profilers: NVIDIA Nsight Graphics (Frame Debugger, Shader Profiler, GPU Trace, Range Profiling); AMD Radeon GPU Profiler (RGP — Hardware Thread Trace, Event Timing); PIX for Windows (D3D12, Timing Captures, GPU Memory, Shader Debugging); RenderDoc (Cross-Platform, Open Source, Frame Capture + Replay)
  - ▸ *CG use:* Frame analysis; bottleneck identification (ALU vs. Bandwidth vs. Fill vs. Latency); shader optimization
- 9.5.1.2 Performance Counters: ALU Utilization (Occupancy), Texture L1/L2 Hit Rates, Memory Bandwidth Utilization, ROP Throughput, Primitive Culling Rate; Occupancy Limiter: Registers Per Thread × Threads Per Block vs. Register File Size
  - ▸ *CG use:* Diagnose why a shader is slow: register spilling? texture cache misses? warp divergence? each has different solutions

#### 9.5.2 Key Optimization Techniques
- 9.5.2.1 Draw Call Optimization: Instancing (Draw Many Copies of Same Mesh), Indirect Draw (GPU-Generated Draw Counts), GPU-Driven Draw Generation; Bundle Similar Materials, Merge Static Meshes, Texture Atlas
  - ▸ *CG use:* Draw calls are the most expensive CPU operation; target < 1000 per frame for 60 FPS on modern hardware
- 9.5.2.2 Bandwidth Optimization: Texture Compression (BCn/ASTC — Saves 4-8× vs. RGBA8), Delta Color Compression (Lossless — GPU Hardware Compression of Render Target Data), Tile-Based Rendering (Mobile — Only Write Tile to DRAM Once); Z-Prepass (Write Depth First → Fragment Shader Only for Visible Pixels)
  - ▸ *CG use:* Memory bandwidth is often the limiting factor, not ALU; reduce texture resolution, use compressed formats, minimize render targets

---

### 9.6 Data Formats & Interchange Standards

#### 9.6.1 3D Formats
- 9.6.1.1 glTF 2.0 (Khronos): "JPEG of 3D"; JSON Scene + Binary Buffer + Textures; PBR Material (Metalness-Roughness + Extensions); Draco Compression Extension; Animation, Skinning, Morph Targets; KTX 2.0 Texture; USDZ Variant (Apple AR)
  - ▸ *CG use:* Web 3D standard; game engine interchange; Sketchfab, Facebook 3D Posts, Google AR
- 9.6.1.2 USD (Universal Scene Description — Pixar): Stage (Scene Composition), Layers (SubLayer, Reference, Payload, VariantSet), Prims (Hierarchical Elements), Attributes (Typed Values + Time Samples), Composition Arcs (Non-Destructive Overrides); Hydra (Render Delegate Framework)
  - ▸ *CG use:* Film/VFX standard; NVIDIA Omniverse; UE5/USD interoperability; Apple USDZ for AR; USD is becoming the universal 3D interchange
- 9.6.1.3 MaterialX (ASWF): XML-Based Material Graph Definition; Platform-Agnostic Node Graph → Generated Shader Code for OSL/GLSL/MDL/HLSL; Standard PBR Node Library; Tightly Integrated with USD (UsdShade)
  - ▸ *CG use:* Cross-renderer material exchange; consistent look across modeling, animation, lighting, rendering

#### 9.6.2 Image, Texture & Shader Formats
- 9.6.2.1 HDR Formats: OpenEXR (Half Float, Multi-Layer, Deep, Tiled, Mipmapped — VFX Industry Standard); Radiance HDR (.hdr — Simple, Legacy); JPEG-XL HDR, AVIF HDR (Web-Deliverable HDR)
  - ▸ *CG use:* Production rendering output; environment maps; texture storage for PBR; deep compositing
- 9.6.2.2 KTX 2.0 (Khronos Texture Container): Basis Universal (ETC1S/UASTC Super-Compression), Transcoding to GPU Format at Load Time; Universal Textures (Cross-Platform); Zstd Compression for Metadata; glTF Standard Texture Format
  - ▸ *CG use:* glTF ecosystem; web streaming; reduces GPU texture format fragmentation

> 📚 **GitHub Repos:**
> - [SaschaWillems/Vulkan](https://github.com/SaschaWillems/Vulkan) ![Stars](https://img.shields.io/github/stars/SaschaWillems/Vulkan?style=flat) — Comprehensive Vulkan example suite
> - [GPUOpen-LibrariesAndSDKs](https://github.com/GPUOpen-LibrariesAndSDKs) — AMD open-source graphics tools
> - [PixarAnimationStudios/USD](https://github.com/PixarAnimationStudios/USD) ![Stars](https://img.shields.io/github/stars/PixarAnimationStudios/USD?style=flat) — USD ecosystem
> - [AcademySoftwareFoundation/MaterialX](https://github.com/AcademySoftwareFoundation/MaterialX) ![Stars](https://img.shields.io/github/stars/AcademySoftwareFoundation/MaterialX?style=flat) — Material standard
> - [RenderDoc/renderdoc](https://github.com/RenderDoc/renderdoc) ![Stars](https://img.shields.io/github/stars/RenderDoc/renderdoc?style=flat) — Cross-platform graphics debugger
>
> 📖 **Textbooks:**
> - *Vulkan Programming Guide* — Sellers & Kessenich; *Real-Time Rendering* — Akenine-Möller et al. (Ch. 3: GPU, Ch. 4: Transforms)
> - *GPU Zen* — Engel (Advanced GPU optimization); *Game Engine Architecture* — Jason Gregory

---


## Chapter 10 · Display, Interaction & Professional Practice

*How graphics reaches the human — display technologies, VR/AR/MR, 3D interaction, and real-world application domains. `▸ CG use:` links each topic to industry practice.*

> 💡 **Top-Level References:**
> - [KhronosGroup/OpenXR-SDK-Source](https://github.com/KhronosGroup/OpenXR-SDK-Source) ![Stars](https://img.shields.io/github/stars/KhronosGroup/OpenXR-SDK-Source?style=flat) — OpenXR standard for VR/AR
> - [ValveSoftware/openvr](https://github.com/ValveSoftware/openvr) ![Stars](https://img.shields.io/github/stars/ValveSoftware/openvr?style=flat) — SteamVR API
> - [EpicGames/UnrealEngine](https://github.com/EpicGames/UnrealEngine) — Access to UE source (registered developers)

---

### 10.1 Display Technologies

#### 10.1.1 Display Hardware
- 10.1.1.1 LCD: Liquid Crystal Modulates Backlight Polarization; IPS (Wide View Angle, Lower Contrast), VA (High Contrast, Narrower Angle), TN (Fast Response, Poor Color/View Angle); LED Backlight (Edge-Lit or Full-Array Local Dimming — FALD for HDR)
  - ▸ *CG use:* Consumer monitors and TVs; color accuracy critical for content creation (IPS preferred)
- 10.1.1.2 OLED: Self-Emissive Pixels (No Backlight → True Blacks, Infinite Contrast); WRGB (LG) or Pentile (Samsung AMOLED); Burn-In Risk (Static UI Elements); Faster Response than LCD (< 0.1ms vs. 1-5ms)
  - ▸ *CG use:* HDR mastering monitors; VR headsets (low persistence, high contrast); premium smartphones; gaming displays
- 10.1.1.3 Micro-LED (Emerging): Inorganic LED per Pixel; OLED-Like Contrast + No Burn-In + Higher Brightness (10,000+ nits); Currently Very Expensive (Large Displays Only); Future of HDR
  - ▸ *CG use:* Future cinema displays; VR (micro-displays with high brightness for optical efficiency); digital signage
- 10.1.1.4 HDR Standards: HDR10 (Static Metadata, 1000 nits Max, 10-bit, Rec.2020), Dolby Vision (Dynamic Metadata Per Scene/Frame, 12-bit, up to 10,000 nits), HLG (Hybrid Log-Gamma — Backwards Compatible with SDR, Broadcast Standard), HDR10+ (Samsung — Dynamic Metadata, Royalty-Free)
  - ▸ *CG use:* Game/film HDR delivery; content creation workflow: author in scRGB or ACES → grade in HDR via PQ → deliver with metadata

#### 10.1.2 Display Interfaces & Sync
- 10.1.2.1 V-Sync / Adaptive Sync: V-Sync: Wait for Vertical Blank → Tear-Free but Input Lag + Stutter if Missed Frame; Adaptive Sync (G-Sync / FreeSync / VRR): Display Refresh Matches GPU Frame Rate Dynamically → Smooth, No Tear, Low Lag; HDMI 2.1 VRR, DisplayPort Adaptive-Sync
  - ▸ *CG use:* Gaming (VRR is essential); media playback (match to 24/30/60 Hz); reducing perceived stutter
- 10.1.2.2 Color Calibration: ICC Profile (Display Characterization); Colorimeter/Photospectrometer Hardware Calibration; Calibrate to Target White Point (D65), Gamma (2.2 SDR, PQ HDR), Gamut (sRGB/DCI-P3/Rec.2020); 3D LUT for Hardware Calibration
  - ▸ *CG use:* Color-critical work (VFX, print, medical imaging); consistent appearance across displays
- 10.1.2.3 Multi-Display & CAVE Systems: Bezel Correction, Color Matching Across Displays; CAVE (Cave Automatic Virtual Environment — Projection on Walls/Floor); Large-Scale Tiled Displays
  - ▸ *CG use:* Simulation training; architectural walkthrough; scientific visualization; immersive art installations

---

### 10.2 Virtual Reality (VR)

#### 10.2.1 VR Rendering
- 10.2.1.1 Stereoscopic Rendering: Render Left + Right Eye Views with IPD Offset (Interpupillary Distance ~63mm); Vergence-Accommodation Conflict (Eyes Focus at Fixed Screen Distance, Converge at Varying Depths → Eye Strain); Varifocal Displays (Future: Dynamically Adjust Focus)
  - ▸ *CG use:* Every VR application renders stereo; single-pass stereo (render both eyes in one draw call via instancing or multiview)
- 10.2.1.2 Lens Distortion Correction: VR Lenses Magnify and Distort Display; Pre-Distort Rendered Image (Barrel Distortion) → Cancel Lens Distortion (Pincushion); Chromatic Aberration Correction (Separate R,G,B Distortion); Hardware- Accelerated via Compositor
  - ▸ *CG use:* OpenVR/OpenXR compositor handles distortion automatically; developer renders undistorted
- 10.2.1.3 Asynchronous Time Warp (ATW) / Space Warp (ASW): ATW: Reproject Last Frame Using Latest Head Pose → Reduces Motion-to-Photon Latency; ASW: Generate Intermediate Frame via Motion Estimation (Optical Flow) → Maintain FPS When App Drops Frames
  - ▸ *CG use:* Critical for VR comfort; reduces motion sickness; Oculus/Meta pioneered ASW 2.0 with depth-based reprojection
- 10.2.1.4 Foveated Rendering: Full Resolution Only at Gaze Point (Fovea Centralis ~2° Visual Angle → ~5% of Pixels!); Reduced Resolution in Periphery; Eye Tracking Required (~120Hz Gaze Update); VRS Tier 2 Per-Pixel Shading Rate (Quadrant or 2×2)
  - ▸ *CG use:* PSVR2 (Tobii eye tracking + foveated rendering); Quest Pro; dramatically reduces shading cost in VR

#### 10.2.2 VR Interaction & Tracking
- 10.2.2.1 6DOF Tracking: Inside-Out (Cameras on Headset → SLAM + Hand Tracking — Quest, Vision Pro), Outside-In (External Base Stations → Lighthouse — Valve Index, HTC Vive); IMU + Visual Fusion for Low Latency (~1ms IMU, ~10ms Visual Correction)
  - ▸ *CG use:* Room-scale VR; accurate hand presence; controller-free interaction
- 10.2.2.2 Hand & Body Tracking: Camera-Based Skeletal Tracking (MediaPipe, Quest Hand Tracking, Ultraleap); EMG Wristbands (Meta Orion — Neural Interface Research); Full-Body via External Cameras or IMU Suits (Xsens, Rokoko)
  - ▸ *CG use:* Natural interaction in VR; social VR avatars; motion capture democratization

---

### 10.3 Augmented & Mixed Reality (AR/MR)

#### 10.3.1 AR Rendering
- 10.3.1.1 Video See-Through (VST): Camera Feed + Virtual Objects Rendered on Top (Quest 3/Pro, Apple Vision Pro, Smartphone AR); Low Latency Critical (< 20ms Photon-to-Photon); Real-World Occlusion via Depth Sensor (LiDAR/ToF)
  - ▸ *CG use:* Apple Vision Pro passthrough; ARKit/ARCore smartphone AR; Meta Quest mixed reality
- 10.3.1.2 Optical See-Through (OST): Transparent Display (HoloLens, Magic Leap); Virtual Objects Added to Real-World Light; Real World Always Visible (No Latency); Dark Virtual Objects Appear Transparent (Additive Light Only); Limited Field of View (~50° vs. 120°+ VST)
  - ▸ *CG use:* Enterprise AR (manufacturing, field service, medical); lightweight glasses form factor
- 10.3.1.3 Lighting Estimation: Environment Probe Capture (Cubemap or SH from Camera); Light Direction + Intensity Estimation; Real-Time Shadow from Estimated Light; Reflection of Real World on Virtual Objects; IBL with Real Environment
  - ▸ *CG use:* AR object placement realism; ARKit/ARCore light estimation; Google ARCore Environmental HDR

#### 10.3.2 Spatial Mapping & Anchoring
- 10.3.2.1 Plane Detection: ARKit/ARCore: Horizontal + Vertical Plane Detection from Sparse Point Cloud; Anchor Virtual Content to Detected Planes; Mesh Generation (LiDAR Scanner on iPad Pro/iPhone Pro → Real-Time 3D Mesh of Environment); Scene Understanding (Semantic Labeling — Floor, Wall, Table, Door)
  - ▸ *CG use:* AR furniture placement (IKEA Place); AR measuring tools; game level generation from real room
- 10.3.2.2 Persistent Anchors / Spatial Anchors: Save Anchor to Cloud, Share Across Devices; Azure Spatial Anchors, ARCloud; Cross-Platform (iOS + Android); GPS + Visual Feature Fusion for Outdoor Large-Scale AR
  - ▸ *CG use:* Multi-player AR games; persistent AR content (leave notes in real locations); Niantic Lightship (Pokémon GO infrastructure)

---

### 10.4 3D Interaction & User Interfaces

#### 10.4.1 3D Picking & Manipulation
- 10.4.1.1 Ray-Based Picking: Cast Ray from Cursor/Controller into Scene; Intersect with Geometry (BVH Acceleration); Select Closest Hit; Highlight (Outline, Glow, Color Change); VR Controller Ray (Curved Ray via Bezier for Distant Objects)
  - ▸ *CG use:* Every 3D editor and VR application; selection precision for dense geometry
- 10.4.1.2 Gizmo Manipulation: Translation, Rotation, Scale Handles with Constraint Axes; Arcball Rotation (Quaternion Map from Mouse Drag); Screen-Space Manipulation; VR Direct Manipulation (Grab Object with Virtual Hand Controller)
  - ▸ *CG use:* DCC tool interaction (Blender, Maya, UE Editor); CAD modeling; VR creative tools

#### 10.4.2 Camera Control & Navigation
- 10.4.2.1 Camera Controllers: Orbit (Arcball/Turntable — Rotate Around Target Point, Pinch to Zoom), FPS (WASD + Mouse Look), Trackball (Shoemake 1992 — Quaternion-Based Rotation), Fly-Through (Cinematic, Path-Following)
  - ▸ *CG use:* Every 3D application implements camera control; teleport in VR for comfort
- 10.4.2.2 Gaze-Based Interaction: Dwell Time (Look at Object for N Seconds → Select); Eye Tracking + Confirmation Gesture (Pinch); Gaze + Pinch (Apple Vision Pro Primary Interaction — "Look and Pinch"); Voice + Gaze Hybrid
  - ▸ *CG use:* Hands-free AR interaction; accessibility; Apple Vision Pro UX paradigm

---

### 10.5 Application Domains — Games, Film & VFX

#### 10.5.1 Real-Time Games
- 10.5.1.1 AAA Rendering Pipeline: Forward+ or Clustered Deferred, PBR Materials, ReSTIR DI/GI, Ray-Traced Reflections/Shadows/AO, DLSS/FSR Upscaling, Denoising (NRD/DLSS-RR), V-Sync/Variable Rate Shading; PS5/Xbox Series: ~10 TFLOPS GPU, Hardware RT, SSD Streaming
  - ▸ *CG use:* Cyberpunk 2077 RT Overdrive; Alan Wake 2; UE5 Lumen + Nanite titles
- 10.5.1.2 Indie & Stylized Rendering: NPR Methods (Cel Shading, Outline Rendering, Halftone); Low-Poly Aesthetic; Pixel Art Rendering (3D→2D Pixelation); Hand-Painted Texture Workflow
  - ▸ *CG use:* Genshin Impact (anime cel shading); Return of the Obra Dinn (1-bit dithering); Minecraft (voxel aesthetic)
- 10.5.1.3 Mobile Rendering: TBDR Architecture (Tile-Based Deferred Rendering); ASTC Texture Compression; Vulkan/Metal; Multi-View Rendering (VR/AR); Energy-Aware Frame Pacing (Avoid Thermal Throttling)
  - ▸ *CG use:* Genshin Impact, PUBG Mobile, Fortnite Mobile; mobile VR (Quest standalone); smartphone AR

#### 10.5.2 Film, VFX & Animation
- 10.5.2.1 Production Renderers: Path Tracing with Global Illumination (Arnold — Autodesk, RenderMan — Pixar, V-Ray — Chaos, Cycles — Blender, Redshift — Maxon, Karma — SideFX, MoonRay — DreamWorks); Spectral Rendering (Accurate Dispersion, Thin-Film); Deep Image Output (Per-Pixel Depth Samples for Compositing)
  - ▸ *CG use:* Every VFX and animated film uses these; render times: hours to days per frame (render farms); denoising critical
- 10.5.2.2 Virtual Production: LED Wall (StageCraft — ILM): Real-Time UE Rendering on Massive LED Display Behind Actors → In-Camera Final Pixel; Camera Tracking + Real-Time Perspective Correction; Volumetric Capture (Multiple Cameras → 3D Performance)
  - ▸ *CG use:* The Mandalorian, The Batman, Thor: Love and Thunder; reduces post-production time significantly
- 10.5.2.3 Digital Humans: MetaHuman (UE — Cloud-Based Character Creator); Light Stage Capture (USC ICT — Pore-Level Facial Detail); Facial Rig (FACS Blend Shapes + Wrinkle Maps); Subsurface Scattering, Hair (Curve-Based), Eye Model; Real-Time Performance (UE5 MetaHuman Animator — iPhone Video → Facial Animation)
  - ▸ *CG use:* Game characters; film digital doubles; virtual influencers; video game cutscenes

---

### 10.6 Application Domains — Science, Industry & Autonomy

#### 10.6.1 Scientific & Medical Visualization
- 10.6.1.1 Volume Rendering: Transfer Function (Scalar Value → Color + Opacity); Direct Volume Rendering (Ray Marching Through 3D Texture), Maximum Intensity Projection (MIP — Radiography), Isosurface Rendering (Marching Cubes)
  - ▸ *CG use:* CT/MRI visualization; confocal microscopy; seismic data; fluid dynamics post-processing
- 10.6.1.2 Flow Visualization: Streamlines (Tangent to Velocity Field), Pathlines, Streaklines, Timelines; Line Integral Convolution (LIC — Cabral & Leedom 1993 — Texture-Based Dense Flow Visualization); Tensor Field Visualization (DTI — Diffusion Tensor Imaging for Brain White Matter)
  - ▸ *CG use:* Aerodynamic simulation; ocean currents; blood flow; weather visualization

#### 10.6.2 CAD, CAM & Digital Twins
- 10.6.2.1 CAD/CAE/CAM Visualization: B-Rep Rendering + CSG + Parametric Modeling; FEM Post-Processing (Stress, Strain, Deformation Colormaps); VR/AR for Design Review; GPU-Accelerated Ray Tracing for Realistic Product Rendering (NVIDIA Iray, KeyShot)
  - ▸ *CG use:* Automotive design; aerospace engineering; consumer product design; architectural BIM visualization
- 10.6.2.2 Digital Twin: Real-Time 3D Replica of Physical System; IoT Sensor Data → Real-Time Status Visualization; Predictive Maintenance Overlay; Simulation Integration (What-If Analysis on Live Data)
  - ▸ *CG use:* Factory monitoring (NVIDIA Omniverse); smart city management; wind farm optimization; Formula 1 race strategy

#### 10.6.3 Autonomous Driving & Robotics Simulation
- 10.6.3.1 Sensor Simulation: RGB Cameras (Physically-Based, HDR), LiDAR (Ray Casting with Realistic Noise Model, Material-Dependent Reflectance), Radar (Doppler + Range + Cross-Section), Ultrasonic; Synchronized Multi-Sensor Data Streams
  - ▸ *CG use:* Training perception models (domain randomization → sim-to-real transfer); safety validation (edge case generation)
- 10.6.3.2 Synthetic Data Engines: NVIDIA DRIVE Sim / Omniverse Replicator, CARLA, AirSim, Isaac Sim; Domain Randomization (Texture, Lighting, Weather, Occlusion Variation); Auto-Labeled Ground Truth (Depth, Semantics, Instance ID, 3D Bounding Box — Free!); Photorealistic Rendering with RTX
  - ▸ *CG use:* Training data generation replaces expensive manual labeling; generating rare/dangerous scenarios for safety testing

---

### 10.7 Cloud Rendering, Streaming & Future Directions

#### 10.7.1 Cloud & Edge Rendering
- 10.7.1.1 Cloud Gaming: Game Runs on Cloud GPU, Streams Video to Client (GeForce Now, Xbox Cloud Gaming, Amazon Luna); Encoder: H.264/H.265/AV1 Low-Latency Mode; Client: Video Decode + Input Upload; < 30ms Total Latency (Network + Encode + Decode) Target
  - ▸ *CG use:* AAA gaming on low-end devices; instant play without downloads; cross-platform continuity
- 10.7.1.2 Pixel Streaming (UE5): Server-Side Rendering → WebRTC Video Stream to Browser; Client Sends Mouse/Keyboard Input; No Plugins, No Install; Scalable via GPU Instances
  - ▸ *CG use:* Remote design review; interactive configurators; virtual events; cloud-based DCC tools

#### 10.7.2 Metaverse, Spatial Computing & AIGC
- 10.7.2.1 Spatial Computing (Apple Vision Pro Paradigm): Apps Exist in 3D Space Around User; Shared Spatial Anchors for Multi-User; Passthrough as Primary Mode (Not VR Immersion); Gaze + Pinch Interaction; Environments (Immersive Backgrounds with varying Immersion Levels)
  - ▸ *CG use:* Next-gen computing platform; productivity, entertainment, communication all spatial; Unity/PolySpatial + RealityKit development
- 10.7.2.2 AI-Generated Content (AIGC) for 3D: Text/Image → 3D Models (DreamFusion, LRM, MVDream); Text → PBR Materials (MatFuse, ControlMat); Text → Animation (MDM — Motion Diffusion Model); AI-Assisted Level Design (Procedural + AI Variation)
  - ▸ *CG use:* Democratizing 3D content creation; rapid prototyping; user-generated content; game asset pipelines of the future
- 10.7.2.3 Real-Time Neural Rendering: DLSS/FSR/XeSS (Super-Resolution + Frame Generation); Neural Radiance Cache (NRC — Real-Time GI); Neural Materials (MLP Evaluated in Shader); Neural Compression (Learned Texture/Geometry Compression); World Models (Generative Simulation — Sora/Genie Direction)
  - ▸ *CG use:* The convergence of neural networks and real-time rendering; film-quality graphics at game frame rates; AI-native game engines

> 📚 **GitHub Repos:**
> - [KhronosGroup/OpenXR-SDK-Source](https://github.com/KhronosGroup/OpenXR-SDK-Source) ![Stars](https://img.shields.io/github/stars/KhronosGroup/OpenXR-SDK-Source?style=flat) — OpenXR standard
> - [EpicGames/UnrealEngine](https://github.com/EpicGames/UnrealEngine) — UE5 source access
> - [carla-simulator/carla](https://github.com/carla-simulator/carla) ![Stars](https://img.shields.io/github/stars/carla-simulator/carla?style=flat) — Autonomous driving simulator
> - [isl-org/Open3D](https://github.com/isl-org/Open3D) ![Stars](https://img.shields.io/github/stars/isl-org/Open3D?style=flat) — 3D data processing and visualization
> - [AcademySoftwareFoundation/OpenColorIO](https://github.com/AcademySoftwareFoundation/OpenColorIO) ![Stars](https://img.shields.io/github/stars/AcademySoftwareFoundation/OpenColorIO?style=flat) — Color management for VFX
>
> 📖 **Textbooks:**
> - *Game Engine Architecture* — Jason Gregory; *Real-Time Rendering* — Akenine-Möller et al.
> - *The VR Book: Human-Centered Design for Virtual Reality* — Jason Jerald
> - *3D User Interfaces: Theory and Practice* — LaViola et al.

---


**Author: Xx1899**
