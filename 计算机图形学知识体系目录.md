# 计算机图形学知识体系完整目录

**作者：Xx1899**

---

## 第一章 · 数学基础

### 1.1 线性代数
- 1.1.1 标量、向量与向量空间
- 1.1.2 向量运算（点积、叉积、张量积、混合积）
- 1.1.3 矩阵与矩阵运算（加法、乘法、转置、逆、伪逆）
- 1.1.4 行列式与秩
- 1.1.5 线性变换（缩放、旋转、剪切、镜像、投影）
- 1.1.6 齐次坐标与仿射空间
- 1.1.7 特征值与特征向量
- 1.1.8 奇异值分解（SVD）
- 1.1.9 主成分分析（PCA）
- 1.1.10 四元数（定义、运算、插值、与旋转矩阵的转换）
- 1.1.11 对偶数四元数（Dual Quaternion）
- 1.1.12 旋转群 SO(3)、SE(3) 与李代数
- 1.1.13 张量代数基础
- 1.1.14 稀疏矩阵与迭代求解

### 1.2 微积分
- 1.2.1 极限、连续性与可导性
- 1.2.2 一元/多元函数的导数与偏导数
- 1.2.3 梯度、散度、旋度
- 1.2.4 雅可比矩阵与海森矩阵
- 1.2.5 链式法则与自动微分（前向/反向模式）
- 1.2.6 泰勒展开与函数逼近
- 1.2.7 定积分、不定积分
- 1.2.8 重积分（二重、三重）
- 1.2.9 线积分与面积分
- 1.2.10 积分变换（傅里叶级数、傅里叶变换、拉普拉斯变换）
- 1.2.11 球谐函数（Spherical Harmonics）
- 1.2.12 小波变换基础
- 1.2.13 变分法与函数空间
- 1.2.14 微分形式与外代数基础

### 1.3 微分几何
- 1.3.1 曲线论：弧长参数化、Frenet 标架（切向量、法向量、副法向量）
- 1.3.2 曲线论：曲率与挠率
- 1.3.3 曲面论：第一基本形式（度量张量）
- 1.3.4 曲面论：第二基本形式（形状算子）
- 1.3.5 曲面论：法曲率、主曲率、高斯曲率、平均曲率
- 1.3.6 测地线与测地距离
- 1.3.7 等距变换、共形映射
- 1.3.8 曲面上的拉普拉斯算子（Laplace-Beltrami）
- 1.3.9 流形（Manifold）基本概念
- 1.3.10 黎曼度量与黎曼几何基础
- 1.3.11 外微分与斯托克斯定理
- 1.3.12 离散微分几何（DDG）

### 1.4 计算几何
- 1.4.1 凸包（Convex Hull）：Graham Scan、QuickHull
- 1.4.2 三角剖分（Delaunay Triangulation）
- 1.4.3 约束 Delaunay 三角剖分（CDT）
- 1.4.4 沃罗诺伊图（Voronoi Diagram）
- 1.4.5 多边形剖分（Ear Clipping、梯形分解）
- 1.4.6 布尔运算（多边形裁剪、多面体布尔）
- 1.4.7 包围盒层次结构（AABB、OBB、包围球、k-DOP）
- 1.4.8 空间划分：BVH、k-d Tree、八叉树（Octree）、BSP 树
- 1.4.9 最近邻搜索与范围查询
- 1.4.10 点到几何体的距离计算
- 1.4.11 几何求交：线段、平面、三角形、多面体
- 1.4.12 扫描线算法与平面扫描法
- 1.4.13 鲁棒性几何计算（浮点误差处理、精确算术）

### 1.5 概率论与统计学
- 1.5.1 概率空间与随机变量
- 1.5.2 常见分布（均匀、正态、泊松、指数、Beta、Gamma）
- 1.5.3 条件概率与贝叶斯公式
- 1.5.4 期望、方差、协方差
- 1.5.5 马尔可夫链与马尔可夫随机场（MRF）
- 1.5.6 高斯过程
- 1.5.7 蒙特卡洛方法（重要性采样、分层采样、拉丁超立方）
- 1.5.8 马尔可夫链蒙特卡洛（MCMC）与 Metropolis-Hastings
- 1.5.9 拟蒙特卡洛方法（Quasi-Monte Carlo, QMC）
- 1.5.10 多重要性采样（Multiple Importance Sampling, MIS）
- 1.5.11 重采样重要性采样（RIS / ReSTIR）
- 1.5.12 信息论基础：熵、KL 散度、互信息

### 1.6 数值分析
- 1.6.1 浮点数表示与 IEEE 754 标准
- 1.6.2 数值误差分析（舍入、截断、病态）
- 1.6.3 线性方程组求解（高斯消元、LU/Cholesky 分解）
- 1.6.4 迭代法（Jacobi、Gauss-Seidel、共轭梯度法、多重网格法）
- 1.6.5 插值（线性、多项式、样条、径向基函数 RBF）
- 1.6.6 函数逼近（最小二乘法、移动最小二乘法 MLS）
- 1.6.7 数值积分（Newton-Cotes、Gauss 求积、自适应积分）
- 1.6.8 常微分方程数值解法（Euler、Runge-Kutta、Verlet、隐式积分）
- 1.6.9 偏微分方程数值解法（有限差分 FDM、有限元 FEM、有限体积 FVM）
- 1.6.10 边界元法（BEM）与无网格法
- 1.6.11 特征值问题数值求解
- 1.6.12 稀疏线性系统的预处理子（Preconditioner）
- 1.6.13 优化基础（梯度下降、牛顿法、拟牛顿法、共轭梯度）

### 1.7 信号与图像处理
- 1.7.1 连续/离散信号与系统
- 1.7.2 采样定理（Nyquist-Shannon）
- 1.7.3 混叠（Aliasing）与反走样（Anti-aliasing）
- 1.7.4 离散傅里叶变换（DFT）与快速傅里叶变换（FFT）
- 1.7.5 滤波（低通、高通、带通、带阻）
- 1.7.6 卷积与相关
- 1.7.7 重建核（Box、Tent、Lanczos、Mitchell-Netravali、Gaussian）
- 1.7.8 多分辨率分析（图像金字塔、小波分解、Mipmap）
- 1.7.9 图像梯度（Sobel、Prewitt、Schaar）
- 1.7.10 边缘检测（Canny、Marr-Hildreth）
- 1.7.11 直方图处理与均衡化
- 1.7.12 形态学操作（膨胀、腐蚀、开/闭运算）

### 1.8 优化理论
- 1.8.1 无约束优化（梯度下降、牛顿法、L-BFGS）
- 1.8.2 约束优化（拉格朗日乘数法、KKT 条件）
- 1.8.3 线性规划与二次规划（QP）
- 1.8.4 凸优化基础
- 1.8.5 全局优化（模拟退火、遗传算法、粒子群优化）
- 1.8.6 ADMM（交替方向乘子法）
- 1.8.7 稀疏优化与压缩感知
- 1.8.8 梯度下降变体（SGD、Adam、RMSprop）

---

## 第二章 · 建模

### 2.1 显式表示

#### 2.1.1 多边形网格
- 2.1.1.1 网格数据结构（面列表、翼边结构、半边结构、有向边结构）
- 2.1.1.2 流形与非流形网格
- 2.1.1.3 网格拓扑（欧拉示性数、亏格、边界、洞）
- 2.1.1.4 顶点法线与面法线计算
- 2.1.1.5 网格格式（OBJ、PLY、STL、FBX、glTF、USD、Alembic）
- 2.1.1.6 自适应网格加密（AMR）

#### 2.1.2 参数曲线
- 2.1.2.1 多项式插值曲线（Lagrange、Hermite）
- 2.1.2.2 贝塞尔曲线（Bernstein 基、de Casteljau 算法、升阶/降阶）
- 2.1.2.3 B 样条曲线（节点向量、基函数递推、局部支撑性）
- 2.1.2.4 非均匀有理 B 样条（NURBS）：权重、有理形式、圆锥曲线表示
- 2.1.2.5 T 样条（T-Splines）
- 2.1.2.6 细分曲线（Chaikin 算法、四点法）

#### 2.1.3 参数曲面
- 2.1.3.1 张量积曲面
- 2.1.3.2 贝塞尔曲面
- 2.1.3.3 B 样条曲面（均匀、非均匀）
- 2.1.3.4 NURBS 曲面（裁剪曲面 Trimmed NURBS）
- 2.1.3.5 旋转曲面与扫掠曲面
- 2.1.3.6 Coons 曲面与 Gordon 曲面
- 2.1.3.7 填充曲面（N-Sided Patch Filling）

#### 2.1.4 细分曲面
- 2.1.4.1 Catmull-Clark 细分（四边形网格）
- 2.1.4.2 Loop 细分（三角形网格）
- 2.1.4.3 Doo-Sabin 细分
- 2.1.4.4 √3 细分
- 2.1.4.5 蝴蝶细分（插值型）
- 2.1.4.6 半尖锐折痕与边界特征处理
- 2.1.4.7 自适应细分

### 2.2 隐式表示

#### 2.2.1 传统隐式方法
- 2.2.1.1 代数曲面（多项式的零集）
- 2.2.1.2 等值面（Isosurface）
- 2.2.1.3 Blobby 模型 / 元球（Metaball）
- 2.2.1.4 函数表示（F-Rep / FRep）
- 2.2.1.5 有符号距离场（SDF）及其操作（并、交、差、平滑混合、偏移）
- 2.2.1.6 R 函数（Rvachev Functions）
- 2.2.1.7 分形（Mandelbrot 集、Julia 集、IFS 迭代函数系统）

#### 2.2.2 神经隐式表示
- 2.2.2.1 SIREN（正弦激活函数网络）
- 2.2.2.2 位置编码与傅里叶特征
- 2.2.2.3 占用网络（Occupancy Networks）
- 2.2.2.4 DeepSDF
- 2.2.2.5 神经辐射场（NeRF）及其变体
- 2.2.2.6 即时神经图形基元（Instant NGP, Multi-resolution Hash Encoding）
- 2.2.2.7 3D Gaussian Splatting（显式-隐式混合）

### 2.3 体素与离散表示
- 2.3.1 均匀栅格（Uniform Grid）
- 2.3.2 稀疏体素八叉树（Sparse Voxel Octree, SVO）
- 2.3.3 自适应采样距离场（ADFs）
- 2.3.4 自适应网格（Adaptive Mesh Refinement）
- 2.3.5 Clipmap 与虚拟纹理
- 2.3.6 有向距离场体素化
- 2.3.7 OpenVDB（稀疏分层体素数据结构）

### 2.4 点云与基于点的表示
- 2.4.1 点云获取（激光扫描 LiDAR、结构光、摄影测量、深度相机）
- 2.4.2 点云配准（ICP：点对点、点对面、广义 ICP、Go-ICP 全局配准）
- 2.4.3 点云特征（PFH、FPFH、SHOT、ISS 关键点、法线估计）
- 2.4.4 点云滤波（体素下采样、统计离群点去除、双边滤波）
- 2.4.5 点云分割与聚类（RANSAC、区域生长、欧式聚类、超体素）
- 2.4.6 基于点的渲染（点精灵 Splatting、QSplat、Surfel）
- 2.4.7 点云补全与上采样

### 2.5 构造实体几何
- 2.5.1 基本体元（Primitives）：立方体、球、圆柱、圆锥、环
- 2.5.2 布尔运算（并集 ∪、交集 ∩、差集 \、对称差）
- 2.5.3 CSG 树与求值
- 2.5.4 边界求值算法（Boundary Evaluation）
- 2.5.5 点到 CSG 模型的分类（点分类与光线投射法）

### 2.6 过程化建模
- 2.6.1 噪声函数（Perlin、Simplex、Worley/Voronoi、Curl Noise）
- 2.6.2 分形布朗运动（fBm）与湍流（Turbulence）
- 2.6.3 L-System：植物与树木建模、随机与参数化 L-System
- 2.6.4 形状语法（Shape Grammars）：建筑与城市建模
- 2.6.5 分形地形（Diamond-Square / Midpoint Displacement、侵蚀模拟）
- 2.6.6 基于图块/波函数坍缩（Wave Function Collapse, WFC）
- 2.6.7 自相似结构生成
- 2.6.8 基于物理的生长模拟（扩散限制聚集 DLA）
- 2.6.9 数据驱动过程化建模（从样例学习规则）

### 2.7 数据驱动建模
- 2.7.1 摄影测量（Photogrammetry）与运动恢复结构（SfM）
- 2.7.2 多视角立体视觉（MVS）：PMVS、PatchMatch
- 2.7.3 深度图融合（TSDF / KinectFusion、Voxel Hashing）
- 2.7.4 语义建模（从图像 / 点云到带语义的 CAD）
- 2.7.5 逆向工程与 CAD 重建
- 2.7.6 三维生成模型（3D GAN、扩散模型、自回归模型）
- 2.7.7 文本到 3D（DreamFusion, SJC, Magic3D, ProlificDreamer）
- 2.7.8 图像到 3D（单视图/多视图重建网络）

### 2.8 场景图与层次化表示
- 2.8.1 场景图数据结构（树形层次变换）
- 2.8.2 实体-组件-系统（ECS）架构
- 2.8.3 层次包围体（BVH）的构建与更新
- 2.8.4 层次细节（Level of Detail, LOD）——离散 LOD、连续 LOD、视点相关 LOD
- 2.8.5 实例化（Instancing）与间接绘制
- 2.8.6 GPU 驱动渲染的批次与合批策略
- 2.8.7 大世界坐标处理（浮点精度、相机相对渲染、多原点）

---

## 第三章 · 渲染

### 3.1 渲染方程与理论基础

#### 3.1.1 辐射度量学
- 3.1.1.1 辐射通量（Radiant Flux / Power）Φ
- 3.1.1.2 辐照度（Irradiance）E —— 入射面密度
- 3.1.1.3 辐射出射度（Radiosity / Radiant Exitance）B / M
- 3.1.1.4 辐射强度（Radiant Intensity）I —— 单位立体角
- 3.1.1.5 辐射亮度（Radiance）L —— 单位投影面积、单位立体角
- 3.1.1.6 光谱辐射度量学（Spectral Radiometry）
- 3.1.1.7 立体角与投影立体角

#### 3.1.2 BRDF / BTDF / BSDF / BSSRDF
- 3.1.2.1 BRDF（双向反射分布函数）定义与性质（非负、Helmholtz 互易性、能量守恒）
- 3.1.2.2 各向同性 BRDF vs 各向异性 BRDF
- 3.1.2.3 漫反射模型（Lambert、Oren-Nayar、Disney Diffuse）
- 3.1.2.4 镜面反射与光滑表面微面元模型（Cook-Torrance）
- 3.1.2.5 微面元理论：法线分布函数 NDF（Beckmann、GGX/Trowbridge-Reitz、GTR）
- 3.1.2.6 微面元理论：几何遮蔽函数（Smith、Cook-Torrance、Heitz 高度相关遮蔽）
- 3.1.2.7 微面元理论：菲涅尔方程（Schlick 近似、完整 Fresnel）
- 3.1.2.8 Disney Principled BRDF
- 3.1.2.9 BTDF（双向透射分布函数）与折射
- 3.1.2.10 BSDF = BRDF + BTDF
- 3.1.2.11 分层材质 BRDF（Clear Coat、Thin-film Interference）
- 3.1.2.12 波动光学 BRDF（衍射、薄膜干涉）
- 3.1.2.13 BSSRDF 与次表面散射（偶极子模型、多极子、Path-space 公式）
- 3.1.2.14 测量 BRDF / 数据驱动 BRDF（MERL、MIT CSAIL、EPFL 数据库）

#### 3.1.3 渲染方程
- 3.1.3.1 Kajiya 渲染方程（1986）
- 3.1.3.2 表面形式：发射项 + 反射项
- 3.1.3.3 面积形式
- 3.1.3.4 路径形式与路径空间公式
- 3.1.3.5 算符形式与 Neumann 级数展开
- 3.1.3.6 伴随方程与重要性函数

### 3.2 光栅化渲染

#### 3.2.1 图形管线总览
- 3.2.1.1 应用程序阶段（CPU）：场景管理、可见性判断、绘制调用
- 3.2.1.2 几何处理阶段（GPU）：顶点着色器 → 曲面细分 → 几何着色器
- 3.2.1.3 光栅化阶段：图元装配、三角形设置、三角形遍历
- 3.2.1.4 像素处理阶段：片元着色器 → 输出合并
- 3.2.1.5 固定功能管线 vs 可编程管线
- 3.2.1.6 现代 GPU 管线（Mesh Shader / Task Shader → 简化几何管线）

#### 3.2.2 几何处理
- 3.2.2.1 模型变换（Model Matrix）
- 3.2.2.2 视图变换（View Matrix / Camera Matrix）
- 3.2.2.3 投影变换：透视投影矩阵与正交投影矩阵
- 3.2.2.4 透视除法与标准化设备坐标（NDC）
- 3.2.2.5 视口变换（Viewport Transform）
- 3.2.2.6 顶点着色器（Vertex Shader）编程
- 3.2.2.7 曲面细分着色器（Tessellation Control / Evaluation Shader）
- 3.2.2.8 几何着色器（Geometry Shader）
- 3.2.2.9 图元装配（点、线、三角形、三角形带/扇）
- 3.2.2.10 背面剔除（Back-face Culling）
- 3.2.2.11 裁剪（Cohen-Sutherland、Sutherland-Hodgman、Guard Band Clipping）

#### 3.2.3 光栅化与片元处理
- 3.2.3.1 线段光栅化（DDA 算法、Bresenham 算法）
- 3.2.3.2 三角形光栅化（重心坐标、边函数法、扫描线填充）
- 3.2.3.3 透视校正插值
- 3.2.3.4 深度测试与深度缓冲（Z-Buffer、W-Buffer、Reverse-Z）
- 3.2.3.5 模板测试（Stencil Test）与模板缓冲
- 3.2.3.6 混合（Blending）：Alpha 混合、预乘 Alpha、排序与混合模式
- 3.2.3.7 多重采样抗锯齿（MSAA：2×, 4×, 8×, EQAA/CSAA）
- 3.2.3.8 超采样抗锯齿（SSAA）、覆盖采样抗锯齿（CSAA）
- 3.2.3.9 时域抗锯齿（TAA）
- 3.2.3.10 基于深度学习的抗锯齿（DLSS、FSR、XeSS）
- 3.2.3.11 形态学抗锯齿（MLAA、SMAA、FXAA、CMAA）
- 3.2.3.12 片元着色器（Fragment / Pixel Shader）编程
- 3.2.3.13 Early-Z / Hi-Z 剔除
- 3.2.3.14 可变速率着色（Variable Rate Shading, VRS）
- 3.2.3.15 保守光栅化（Conservative Rasterization）
- 3.2.3.16 图块渲染架构（Tile-based Rendering / TBDR）

#### 3.2.4 纹理映射
- 3.2.4.1 纹理坐标（UV）与参数化
- 3.2.4.2 纹理过滤：最近邻、双线性、三线性
- 3.2.4.3 各向异性过滤（Anisotropic Filtering）
- 3.2.4.4 Mipmap 生成：逐层降采样（Box、Kaiser、Lanczos 核）
- 3.2.4.5 纹理采样与寻址模式（Wrap、Mirror、Clamp、Border）
- 3.2.4.6 压缩纹理格式（BC1-BC7, ASTC, ETC2, PVRTC）
- 3.2.4.7 浮点纹理与 HDR 纹理（Half/Float、共享指数格式）
- 3.2.4.8 立方体贴图（Cubemap）与环境映射
- 3.2.4.9 凹凸贴图（Bump Mapping）：法线扰动
- 3.2.4.10 法线贴图（Normal Mapping）：切线空间与法线压缩
- 3.2.4.11 位移贴图（Displacement Mapping）：顶点位移
- 3.2.4.12 视差贴图（Parallax Mapping）、陡峭视差贴图、浮雕映射（Relief Mapping）
- 3.2.4.13 过程化纹理（棋盘格、大理石、木材、云噪点）
- 3.2.4.14 体积纹理（3D Texture）与噪声体积
- 3.2.4.15 纹理图集（Texture Atlas）与数组纹理（Array Texture）
- 3.2.4.16 虚拟纹理（Virtual Texture / MegaTexture / Tiled Resources / Sparse 纹理）
- 3.2.4.17 绑定无关纹理（Bindless Textures）
- 3.2.4.18 Ptex（Per-face Texture Mapping）

#### 3.2.5 着色模型
- 3.2.5.1 光照基础：方向光、点光源、聚光灯、面光源、环境光
- 3.2.5.2 漫反射：Lambert 着色
- 3.2.5.3 高光：Phong 反射模型
- 3.2.5.4 Blinn-Phong 反射模型（半向量近似）
- 3.2.5.5 物理基础渲染（PBR）概念：能量守恒、金属/非金属区分
- 3.2.5.6 金属工作流（Metalness-Roughness Workflow）
- 3.2.5.7 镜面反射工作流（Specular-Glossiness Workflow）
- 3.2.5.8 基于图像的光照（Image-Based Lighting, IBL）
- 3.2.5.9 预计算辐照度图（Diffuse Irradiance Map）
- 3.2.5.10 预滤波环境贴图（Prefiltered Environment Map / Specular IBL）
- 3.2.5.11 分裂和近似（Split Sum Approximation）
- 3.2.5.12 环境 BRDF 查找表（LUT: BRDF Integration Map）
- 3.2.5.13 延迟着色（Deferred Shading）：G-Buffer 布局
- 3.2.5.14 前向+着色（Forward+ Rendering / Tiled Forward Shading）
- 3.2.5.15 集群着色（Clustered Shading / Clustered Deferred / Forward）
- 3.2.5.16 可见性缓冲（Visibility Buffer）与延迟材质

#### 3.2.6 阴影
- 3.2.6.1 平面投影阴影（Projective / Planar Shadows）
- 3.2.6.2 阴影体（Shadow Volumes）：模板缓冲法（Carmack's Reverse / Depth-Fail）
- 3.2.6.3 阴影映射（Shadow Mapping）：基础原理
- 3.2.6.4 透视阴影映射（Perspective SM）
- 3.2.6.5 级联阴影映射（Cascaded Shadow Maps, CSM）
- 3.2.6.6 平行分割阴影映射（Parallel-Split SM, PSSM）
- 3.2.6.7 紧锥体裁剪（Tight Frustum Culling）
- 3.2.6.8 方差阴影映射（Variance Shadow Maps, VSM）
- 3.2.6.9 卷积阴影映射（Convolution SM, CSM）
- 3.2.6.10 指数阴影映射（Exponential SM, ESM）
- 3.2.6.11 指数方差阴影映射（EVSM）
- 3.2.6.12 矩阴影映射（Moment Shadow Maps, MSM）
- 3.2.6.13 接触硬化阴影（Percentage Closer Soft Shadows, PCSS）
- 3.2.6.14 百分比更近过滤（PCF）
- 3.2.6.15 屏幕空间阴影（Contact / Short-Range AO as shadows）
- 3.2.6.16 光线追踪阴影（Ray Traced Shadows, DXR 1.1 / Vulkan RT）
- 3.2.6.17 虚拟阴影映射（Virtual Shadow Maps, Unreal Engine 5 风格）
- 3.2.6.18 半透明阴影（Colored / Translucent Shadows）

#### 3.2.7 环境效果
- 3.2.7.1 天空渲染（天空盒、大气散射模型、Precomputed Atmospheric Scattering）
- 3.2.7.2 体积云（Volumetric Clouds）：Noise-based、Weather Texture、Ray Marching
- 3.2.7.3 雾（Fog）：线性雾、指数雾、高度雾
- 3.2.7.4 体积光（Volumetric Light / God Rays / Light Shafts）
- 3.2.7.5 体积雾与参与介质
- 3.2.7.6 雨、雪效果（粒子系统 + 屏幕空间效果）
- 3.2.7.7 水面渲染（反射、折射、焦散、波浪、泡沫、Crest）
- 3.2.7.8 水下效果（Underwater Fog / Caustics / Color Absorption）

### 3.3 光线追踪

#### 3.3.1 基础光线追踪
- 3.3.1.1 光线生成（透视相机、正交相机、针孔模型）
- 3.3.1.2 光线与几何体求交（球、平面、三角形 Möller-Trumbore、AABB slab 法）
- 3.3.1.3 光线与参数曲面求交（Newton 迭代、Bezier Clipping）
- 3.3.1.4 光线与隐式曲面求交（Ray Marching / Sphere Tracing）
- 3.3.1.5 Whitted 式光线追踪（递归反射 + 折射 + 阴影光线）
- 3.3.1.6 折射定律（Snell's Law）与全内反射
- 3.3.1.7 菲涅尔效应处理（Schlick / 精确 Fresnel）
- 3.3.1.8 分布式光线追踪（Cook et al. 1984）：软阴影、运动模糊、景深、光泽反射

#### 3.3.2 加速结构
- 3.3.2.1 包围体层次结构（BVH）：构建（SAH 扫描/分箱、HLBVH、PLOC）
- 3.3.2.2 BVH 遍历（栈 vs 无栈、压缩宽 BVH）
- 3.3.2.3 BVH 更新与重建（自上而下/自下而上重建、重拟合 Refit）
- 3.3.2.4 K-d Tree：构建（SAH、中点分割）、遍历
- 3.3.2.5 均匀栅格与层次栅格
- 3.3.2.6 八叉树加速结构
- 3.3.2.7 双边 BVH（Two-Level BVH / TLAS + BLAS, DXR/Vulkan RT 模型）
- 3.3.2.8 基于排序的加速（Shader Execution Reordering, SER）
- 3.3.2.9 加速结构的质量评估（SAH 成本模型、遍历步数、包围盒紧密度）

#### 3.3.3 路径追踪与全局光照
- 3.3.3.1 路径追踪（Kajiya 1986）基础算法
- 3.3.3.2 蒙特卡洛积分回顾与渲染应用
- 3.3.3.3 重要性采样：
  - 3.3.3.3.1 余弦加权半球采样
  - 3.3.3.3.2 BRDF 重要性采样（GGX/Beckmann VNDF 采样）
  - 3.3.3.3.3 光源重要性采样（面积采样、方向采样）
  - 3.3.3.3.4 环境贴图重要性采样
- 3.3.3.4 多重重要性采样（MIS）：Balance Heuristic、Power Heuristic
- 3.3.3.5 一重 MIS（One-sample MIS）
- 3.3.3.6 俄罗斯轮盘赌（Russian Roulette）与路径截断
- 3.3.3.7 双向路径追踪（Bidirectional Path Tracing, BDPT）
- 3.3.3.8 顶点合并与光子映射（Photon Mapping：光子发射、光子图、辐射度估计）
- 3.3.3.9 渐进光子映射（Progressive PM, PPM）
- 3.3.3.10 随机渐进光子映射（Stochastic Progressive Photon Mapping, SPPM）
- 3.3.3.11 顶点连接与合并统一（VCM / UPS / Unified Path Sampling）
- 3.3.3.12 光子束 / 光子平面（Photon Beams / Photon Planes）
- 3.3.3.13 Metropolis 光传输（MLT：Primary Sample Space MLT, Path Space MLT）
- 3.3.3.14 流形探索（Manifold Exploration / Manifold Next Event Estimation, MNEE）
- 3.3.3.15 路径空间正则化（Path Space Regularization）
- 3.3.3.16 渐进式渲染与自适应采样（Adaptive Sampling）
- 3.3.3.17 基于路径引导的采样（Practical Path Guiding, SD-tree/Quad-tree 引导）
- 3.3.3.18 神经路径引导（Neural Path Guiding）

#### 3.3.4 实时与交互式光线追踪
- 3.3.4.1 硬件加速光线追踪（NVIDIA RT Core、AMD Ray Accelerator、Intel Arc）
- 3.3.4.2 DXR（DirectX Raytracing）API 基础
- 3.3.4.3 Vulkan Ray Tracing（VK_KHR_ray_tracing_pipeline）
- 3.3.4.4 OptiX 框架
- 3.3.4.5 Metal Ray Tracing
- 3.3.4.6 降噪（Denoising）：
  - 3.3.4.6.1 空间降噪：双边滤波、导向滤波、À-Trous 小波
  - 3.3.4.6.2 时域降噪：时域累积（Temporal Accumulation）、运动向量、拒绝采样
  - 3.3.4.6.3 回归降噪（SVGF、BMFR）
  - 3.3.4.6.4 神经网络降噪（OptiX Denoiser、OIDN、NRD）
  - 3.3.4.6.5 超分辨率联合降噪（DLSS Ray Reconstruction）
- 3.3.4.7 重要性采样与路径空间滤波
- 3.3.4.8 光线追踪中的 LOD（简化的 BVH 几何、着色器替换）
- 3.3.4.9 ReSTIR（Reservoir-based Spatiotemporal Importance Resampling）
  - ReSTIR DI（直接光照）
  - ReSTIR GI（全局光照）
  - ReSTIR PT（路径追踪）
  - 广义重采样理论
- 3.3.4.10 异步光线追踪与异步计算
- 3.3.4.11 混合渲染（Raster + Ray Tracing）：混合反射、混合 AO、混合 GI

#### 3.3.5 参与介质渲染
- 3.3.5.1 体积渲染方程（Radiative Transfer Equation, RTE）
- 3.3.5.2 吸收系数 σₐ、散射系数 σₛ、消光系数 σₜ、相位函数
- 3.3.5.3 透射率（Transmittance / Optical Depth）
- 3.3.5.4 自由程采样（Free-path Sampling / Woodcock Tracking / Delta Tracking）
- 3.3.5.5 体积路径追踪（Volumetric Path Tracing）
- 3.3.5.6 体积光子映射（Volumetric Photon Mapping）
- 3.3.5.7 相位函数：各向同性、Rayleigh、Mie（Henyey-Greenstein）
- 3.3.5.8 空域与非均质介质（级联阴影栅格、自适应采样）
- 3.3.5.9 大气散射（预计算大气散射、Bruneton 模型、Hillaire 实时大气）
- 3.3.5.10 云、烟、雾、火渲染
- 3.3.5.11 次表面散射（皮肤、大理石、玉石等半透明材质）

### 3.4 实时全局光照

#### 3.4.1 预计算方法
- 3.4.1.1 光照贴图（Lightmap）：离线烘焙 + 实时纹理映射
- 3.4.1.2 光照探针（Light Probes）：球谐（SH）/ 环境光遮蔽存储
- 3.4.1.3 反射探针（Reflection Probes）：盒投影校正、混合
- 3.4.1.4 预计算辐射度传输（Precomputed Radiance Transfer, PRT）
- 3.4.1.5 辐照度体积（Irradiance Volumes）

#### 3.4.2 实时方法
- 3.4.2.1 屏幕空间环境光遮蔽（SSAO、SSAO+、HBAO、GTAO、CACAO）
- 3.4.2.2 屏幕空间反射（Screen Space Reflections, SSR）：光线步进、Hi-Z 加速
- 3.4.2.3 屏幕空间全局光照（SSGI）
- 3.4.2.4 反射阴影映射（Reflective Shadow Maps, RSM）：间接光源
- 3.4.2.5 虚拟点光源（Virtual Point Lights, VPL / Instant Radiosity）
- 3.4.2.6 光传播体积（Light Propagation Volumes, LPV）
- 3.4.2.7 级联光传播体积（Cascaded LPV）
- 3.4.2.8 体素锥追踪（Voxel Cone Tracing, VXGI）
- 3.4.2.9 基于面元（Surfel）的 GI：G-Buffer 生成面元、分层辐射度
- 3.4.2.10 光线追踪 GI（RTXGI）：探针重照明 + 时空滤波
- 3.4.2.11 动态漫反射全局光照（DDGI）
- 3.4.2.12 Lumen（Unreal Engine 5）：面元卡片 + 屏幕空间追踪 + Mesh SDF 追踪 + 辐射缓存
- 3.4.2.13 基于有符号距离场的 GI（SDF 追踪）

### 3.5 参与介质与透���表面
- 3.5.1 半透明与透明排序（Alpha 排序：OIT 排序无关半透明）
  - 3.5.1.1 深度剥离（Depth Peeling）
  - 3.5.1.2 加权混合透明（Weighted Blended OIT）
  - 3.5.1.3 Per-Pixel Linked Lists
  - 3.5.1.4 Moment-Based OIT
  - 3.5.1.5 随机透明（Stochastic Transparency）
- 3.5.2 体积渲染（体绘制）——光栅化管线
- 3.5.3 体积光线步进（Volume Ray Marching）

### 3.6 非真实感渲染

#### 3.6.1 卡通/动画风格
- 3.6.1.1 描边技术：背面膨胀法、图像处理法、基于边缘检测
- 3.6.1.2 色块着色（Cel Shading / Toon Shading）：阶梯化漫反射与高光
- 3.6.1.3 轮廓线类型：轮廓线、折痕线、材质边界、遮挡轮廓
- 3.6.1.4 各向异性轮廓线（基于视角的线宽变化）

#### 3.6.2 艺术风格
- 3.6.2.1 素描风格（Hatching / Cross-hatching）：色调艺术图（Tonal Art Maps）
- 3.6.2.2 水彩风格渲染
- 3.6.2.3 油画风格渲染
- 3.6.2.4 点彩/马赛克风格
- 3.6.2.5 半色调（Halftoning）
- 3.6.2.6 线条艺术渲染（Line Art、Technical Illustration）

#### 3.6.3 抽象与特效风格
- 3.6.3.1 基于噪声的风格化（抖动、颗粒感）
- 3.6.3.2 笔触渲染（Stroke-based Rendering）
- 3.6.3.3 风格迁移（基于深度学习的图像/视频风格化）
- 3.6.3.4 实时风格迁移

### 3.7 后处理与图像空间技术

#### 3.7.1 色调映射与显示
- 3.7.1.1 色调映射算子：Reinhard、Filmic（Uncharted 2 / ACES）、Hable、Gran Turismo
- 3.7.1.2 曝光控制：自动曝光（Eye Adaptation）
- 3.7.1.3 HDR 显示支持（HDR10、Dolby Vision、scRGB）
- 3.7.1.4 SDR 与 HDR 的色域映射

#### 3.7.2 颜色处理
- 3.7.2.1 白平衡
- 3.7.2.2 色彩分级（Color Grading）：LUT、CDL、曲线
- 3.7.2.3 饱和度、对比度、亮度调整
- 3.7.2.4 查找表（LUT）生成与应用
- 3.7.2.5 HDR 显示映射（Display Mapping / Output Transform）

#### 3.7.3 镜头模拟效果
- 3.7.3.1 景深（Depth of Field, DoF）：散景（Bokeh）、散景形状模拟
- 3.7.3.2 运动模糊（Motion Blur）：每像素速度向量、相机/对象模糊
- 3.7.3.3 泛光（Bloom）：下采样金字塔 + 合成
- 3.7.3.4 镜头光晕（Lens Flare）：伪影（Ghost、光晕）、衍射星芒
- 3.7.3.5 炫光（Glare）
- 3.7.3.6 色差（Chromatic Aberration）
- 3.7.3.7 暗角（Vignette）
- 3.7.3.8 胶片颗粒（Film Grain）
- 3.7.3.9 镜头畸变（Lens Distortion：径向、切向）

#### 3.7.4 超分辨率与图像重建
- 3.7.4.1 空间超分辨率（FSR 1.0）
- 3.7.4.2 时域超分辨率（TAAU、DLSS 2/3/4、FSR 2/3/4、XeSS）
- 3.7.4.3 帧生成（DLSS Frame Generation、FSR 3 Frame Generation）
- 3.7.4.4 多帧生成（DLSS 4 / Multi Frame Generation）
- 3.7.4.5 检查板渲染（Checkerboard Rendering）
- 3.7.4.6 可变速率着色（VRS）与超分辨率协同

### 3.8 可微渲染
- 3.8.1 可微光栅化：前向与反向传播
- 3.8.2 可微路径追踪：边采样、重参数化技巧
- 3.8.3 可微体积渲染（NeRF 中的体积渲染梯度）
- 3.8.4 可微 BRDF / 材质优化
- 3.8.5 可微几何优化（网格顶点梯度传播）
- 3.8.6 逆向渲染（Inverse Rendering）
  - 3.8.6.1 从图像恢复几何（光度立体、Shape-from-Shading）
  - 3.8.6.2 从图像恢复材质与光照（逆向路径追踪）
  - 3.8.6.3 联合逆渲染（几何+材质+光照参数同时估计）
- 3.8.7 可微渲染框架（Mitsuba 3、Redner、PSDR-CUDA、Nvdiffrast、Slang.D）

### 3.9 神经渲染
- 3.9.1 神经辐射场（NeRF）：位置编码、分层采样、粗到细
- 3.9.2 NeRF 加速（Instant NGP、TensoRF、Plenoxels、DIVeR、MERF、SMERF）
- 3.9.3 少视图 NeRF（PixelNeRF、MVSNeRF、RegNeRF、FreeNeRF）
- 3.9.4 动态 NeRF（D-NeRF、HyperNeRF、TiNeuVox、K-Planes）
- 3.9.5 大场景 NeRF（Block-NeRF、Mega-NeRF、BungeeNeRF）
- 3.9.6 可编辑/可重建 NeRF（NeRF-Editing、NeRF-W / Wild）
- 3.9.7 3D Gaussian Splatting（3DGS）：
  - 3.9.7.1 点基元 + 协方差矩阵 + 球谐颜色
  - 3.9.7.2 自适应密度控制（克隆 / 分裂）
  - 3.9.7.3 基于 tile 的可微光栅化
  - 3.9.7.4 变体：2DGS（Surfel）、动态 4DGS、压缩 3DGS
- 3.9.8 神经 SDF / 占用场（NeuS、VolSDF、MonoSDF）
- 3.9.9 神经材质（Neural BRDF / Neural BTF）
- 3.9.10 神经辐射缓存（Neural Radiance Cache, NRC）
- 3.9.11 基于扩散模型的 3D 生成（DreamFusion / SDS Loss、SJC、ProlificDreamer / VSD）
- 3.9.12 前馈 3D 重建（LRM、Instant3D、LGM、GRM）

---

## 第四章 · 动画

### 4.1 关键帧动画
- 4.1.1 关键帧与插值曲线
- 4.1.2 线性插值
- 4.1.3 贝塞尔/样条曲线插值
- 4.1.4 缓动函数（Easing Functions）：Ease-in、Ease-out、Ease-in-out
- 4.1.5 时间重映射（Time Remapping）
- 4.1.6 参数化关键帧（Parameterization by arc length）

### 4.2 骨骼动画

#### 4.2.1 骨架结构
- 4.2.1.1 关节层级（Joint Hierarchy）
- 4.2.1.2 局部变换与全局变换
- 4.2.1.3 绑定姿态（Bind Pose / Rest Pose）
- 4.2.1.4 关节限制（Joint Limits / Constraints）

#### 4.2.2 前向运动学
- 4.2.2.1 链式变换组合
- 4.2.2.2 变换矩阵堆栈
- 4.2.2.3 FK 在动画管线中的应用

#### 4.2.3 逆向运动学
- 4.2.3.1 解析 IK（两关节/三关节闭合解）
- 4.2.3.2 循环坐标下降（Cyclic Coordinate Descent, CCD）
- 4.2.3.3 雅可比矩阵法（Jacobian Transpose / Damped Least Squares / Pseudo-Inverse）
- 4.2.3.4 FABRIK（Forward And Backward Reaching IK）
- 4.2.3.5 全身 IK（Full-Body IK）
- 4.2.3.6 IK 约束（Look-At、极向量、目标匹配）

#### 4.2.4 蒙皮
- 4.2.4.1 刚体蒙皮 / 分区蒙皮
- 4.2.4.2 线性混合蒙皮（Linear Blend Skinning, LBS / Skeletal Subspace Deformation）
- 4.2.4.3 LBS 问题：糖纸效应（Candy-wrapper Artifact）、体积塌陷
- 4.2.4.4 对偶四元数蒙皮（Dual Quaternion Skinning, DQS）
- 4.2.4.5 优化中心蒙皮（Optimization-based Skinning）
- 4.2.4.6 线性旋转不变坐标（Rigid / Elasticity-Based Skinning）
- 4.2.4.7 蒙皮分解（Skinning Decomposition, SSDR / Smooth Skinning Decomposition）
- 4.2.4.8 Delta Mush 平滑
- 4.2.4.9 姿势空间变形（Pose Space Deformation, PSD）
- 4.2.4.10 蒙皮权重的自动计算 / 热扩散法（Bounded Biharmonic Weights, BBW）

### 4.3 变形技术

#### 4.3.1 基于网格的变形
- 4.3.1.1 自由形变（Free-Form Deformation, FFD）：格子变形
- 4.3.1.2 尽可能刚性变形（As-Rigid-As-Possible, ARAP）
- 4.3.1.3 基于拉普拉斯网格编辑（Laplacian Mesh Editing / Differential Coordinates）
- 4.3.1.4 基于骨架的变形
- 4.3.1.5 空间变形：弯曲、扭曲、锥化、拉伸
- 4.3.1.6 笼子变形（Cage-based Deformation）：均值坐标、调和坐标、格林坐标
- 4.3.1.7 双调和变形（Biharmonic Deformation）

#### 4.3.2 融合变形
- 4.3.2.1 混合形状（Blend Shapes / Morph Targets）
- 4.3.2.2 面部动画编码系统（FACS: Facial Action Coding System）
- 4.3.2.3 自动混合形状生成（从扫描到目标模型）
- 4.3.2.4 基于 PCA 的表情压缩
- 4.3.2.5 非线性融合变形（Corrective Blend Shapes）

#### 4.3.3 数据驱动变形
- 4.3.3.1 基于示例的变形（Example-Based Deformation）
- 4.3.3.2 人体参数化模型（SMPL、SMPL-X、STAR、GHUM）
- 4.3.3.3 面部参数化模型（FaceWarehouse、FLAME、3DMM）
- 4.3.3.4 手部参数化模型（MANO）

### 4.4 刚体模拟

#### 4.4.1 基础动力学
- 4.4.1.1 牛顿运动定律与欧拉运动方程
- 4.4.1.2 刚体运动学（位置、方向、线速度、角速度）
- 4.4.1.3 刚体动力学（力、力矩、惯性张量）
- 4.4.1.4 质心与世界坐标系下的运动方程

#### 4.4.2 时间积分
- 4.4.2.1 显式欧拉法
- 4.4.2.2 半隐式欧拉法（Symplectic Euler）
- 4.4.2.3 Verlet 积分
- 4.4.2.4 龙格-库塔方法（RK4）
- 4.4.2.5 隐式积分（后向欧拉）

#### 4.4.3 碰撞检测
- 4.4.3.1 碰撞检测管线：广相（Broad Phase）→ 窄相（Narrow Phase）→ 响应
- 4.4.3.2 广相算法：排序与扫描（Sweep and Prune / SAP）、空间哈希、BVH
- 4.4.3.3 窄相算法：
  - 4.4.3.3.1 Gilbert-Johnson-Keerthi（GJK）算法
  - 4.4.3.3.2 膨胀多面体算法（EPA）
  - 4.4.3.3.3 分离轴定理（SAT）
  - 4.4.3.3.4 特征对特征检测（Lin-Canny、V-Clip）
- 4.4.3.4 连续碰撞检测（CCD）：基于扫描的 CCD、推测 CCD
- 4.4.3.5 碰撞响应：冲量法、惩罚力法、约束求解法
- 4.4.3.6 摩擦模型（Coulomb 模型、静摩擦与动摩擦）
- 4.4.3.7 堆叠与静止接触处理（Contact Manifold、Contact Graph）

#### 4.4.4 约束动力学
- 4.4.4.1 关节类型：球窝关节（Ball-and-Socket）、铰链（Hinge）、滑动（Slider）、固定（Fixed）
- 4.4.4.2 约束方程与雅可比矩阵
- 4.4.4.3 基于力的约束（罚方法）
- 4.4.4.4 基于冲量的约束（Sequential Impulse / PGS 求解器）
- 4.4.4.5 基于位置的动力学（Position Based Dynamics, PBD）
- 4.4.4.6 扩展 PBD（XPBD）
- 4.4.4.7 降坐标方法（Reduced Coordinate / Featherstone 算法）
- 4.4.4.8 柔体约束（应变约束：拉伸、剪切、弯曲）

### 4.5 柔体与可变形体模拟

#### 4.5.1 质点-弹簧系统
- 4.5.1.1 质点-弹簧模型基础
- 4.5.1.2 结构弹簧、剪切弹簧、弯曲弹簧
- 4.5.1.3 阻尼与数值耗散
- 4.5.1.4 布料模拟应用（Provot 布料模型）

#### 4.5.2 有限元法
- 4.5.2.1 连续介质力学基础：变形梯度、Green 应变、Cauchy 应力
- 4.5.2.2 本构模型：线弹性（Hooke）、超弹性（Neo-Hookean、Mooney-Rivlin、StVK）
- 4.5.2.3 塑性模型（von Mises、Drucker-Prager）
- 4.5.2.4 有限元离散：四面体、六面体、形函数、刚度矩阵组装
- 4.5.2.5 隐式积分与 Newton-Raphson 求解
- 4.5.2.6 基于优化的隐式积分（Projective Dynamics）
- 4.5.2.7 快速质量弹簧 FEM（Corotational FEM）

#### 4.5.3 无网格法与粒子法
- 4.5.3.1 光滑粒子流体动力学（SPH）
- 4.5.3.2 物质点法（MPM：Material Point Method）
- 4.5.3.3 移动最小二乘法（MLS-MPM）
- 4.5.3.4 离散元法（DEM）

### 4.6 流体模拟

#### 4.6.1 基于网格的方法
- 4.6.1.1 纳维-斯托克斯方程（Navier-Stokes Equations）
- 4.6.1.2 不可压缩条件（div v = 0）
- 4.6.1.3 交错网格（Staggered Grid / MAC Grid）
- 4.6.1.4 对流项求解：半拉格朗日法、BFECC、MacCormack
- 4.6.1.5 压力投影与泊松方程求解（共轭梯度、多重网格）
- 4.6.1.6 自由表面处理（VOF 法、Level Set 法、Particle Level Set）
- 4.6.1.7 涡度约束（Vorticity Confinement）
- 4.6.1.8 耦合边界条件（固壁、流入/流出、周期边界）

#### 4.6.2 基于粒子的方法
- 4.6.2.1 SPH 流体模拟（WCSPH, IISPH, DFSPH, PCISPH）
- 4.6.2.2 流体隐式粒子法（FLIP / PIC）
- 4.6.2.3 APIC（Affine Particle-In-Cell）
- 4.6.2.4 PolyPIC / 高阶 PIC

#### 4.6.3 混合方法
- 4.6.3.1 FLIP + 网格（Hybrid FLIP）
- 4.6.3.2 粒子 + Level Set
- 4.6.3.3 MPM 用于流体（工程与视觉混合）

#### 4.6.4 专门流体效果
- 4.6.4.1 自由表面流（水、海洋波浪：Gerstner 波、FFT 海洋）
- 4.6.4.2 气泡与泡沫
- 4.6.4.3 粘弹性流体（Giesekus、Oldroyd-B）
- 4.6.4.4 多相流（液-气、液-固耦合）
- 4.6.4.5 表面张力建模
- 4.6.4.6 流体-刚体双向耦合
- 4.6.4.7 实时流体模拟（Nvidia Flex、PhysX Fluids、Unreal Niagara Fluids）

### 4.7 粒子系统与特效
- 4.7.1 粒子基础（发射器、速度、生命周期、力场）
- 4.7.2 GPU 粒子（Compute Shader 驱动、Transform Feedback）
- 4.7.3 粒子碰撞（与场景几何、粒子间碰撞）
- 4.7.4 粒子光照与渲染（Billboard、Soft Particles、条带/拖尾）
- 4.7.5 特效应用：火花、爆炸、烟尘、魔法、碎片
- 4.7.6 Niagara (UE) / VFX Graph (Unity) 高级粒子系统

### 4.8 角色动画

#### 4.8.1 运动学
- 4.8.1.1 人体运动学模型（关节自由度、ROM）
- 4.8.1.2 运动重定向（Motion Retargeting）
- 4.8.1.3 运动变形与风格化

#### 4.8.2 运动合成
- 4.8.2.1 运动图（Motion Graph）
- 4.8.2.2 运动匹配（Motion Matching）：特征向量搜索
- 4.8.2.3 Learned Motion Matching（神经网络加速）
- 4.8.2.4 运动场（Motion Fields）

#### 4.8.3 程序化动画
- 4.8.3.1 程序化步态（Locomotion）：脚步 IK、步态周期适配
- 4.8.3.2 程序化适应（地形适应、上下坡、跨越障碍）
- 4.8.3.3 基于物理的角色动画（Physics-Based Character Animation）
- 4.8.3.4 深度强化学习驱动角色控制（DeepMimic、AMP、ASE）

#### 4.8.4 面部动画
- 4.8.4.1 面部动作编码系统（FACS / Action Units）
- 4.8.4.2 语音驱动的嘴唇同步（Lip Sync / Viseme 映射）
- 4.8.4.3 面部表演捕捉与重定向
- 4.8.4.4 基于神经网络的面部动画（Audio2Face、面部视频驱动）

#### 4.8.5 运动捕捉与处理
- 4.8.5.1 光学运动捕捉（Vicon、OptiTrack）
- 4.8.5.2 惯性运动捕捉（Xsens、Rokoko）
- 4.8.5.3 视频运动捕捉（OpenPose、MediaPipe、HybrIK、WHAM）
- 4.8.5.4 运动数据格式（BVH、FBX、ASF/AMC、C3D）
- 4.8.5.5 运动数据清洗与滤波（去噪、间隙填充、平滑）
- 4.8.5.6 运动数据标注与分割

### 4.9 群集模拟
- 4.9.1 Boids 模型（分离、对齐、聚集）
- 4.9.2 连续介质人群模型（Continuum Crowds）
- 4.9.3 基于社会力模型（Social Force Model）
- 4.9.4 基于速度障碍的方法（RVO / ORCA）
- 4.9.5 多智能体强化学习导航
- 4.9.6 大规模人群渲染（实例化、LOD、冒名顶替者 Impostor）

### 4.10 毛发与纤维模拟
- 4.10.1 毛发几何表示：引导发 + 插值（Guide Hair + Interpolation）
- 4.10.2 毛发动力学：FTL（Follow The Leader）、弹簧链
- 4.10.3 毛发碰撞检测与自碰撞
- 4.10.4 毛发渲染：Kajiya-Kay 模型、Marschner 模型、双圆柱散射模型
- 4.10.5 基于发束（Clump）与 Level-of-Detail
- 4.10.6 动物皮毛（Fur Shells / Fin Geometry + 透明层叠）
- 4.10.7 GPU 毛发渲染（TressFX、HairWorks、基于 Compute Shader）
- 4.10.8 羽毛建模

---

## 第五章 · 几何处理

### 5.1 网格数据结构与基本操作
- 5.1.1 网格数据结构综述（面集、翼边、半边、有向边、角表）
- 5.1.2 邻接操作（顶点→面、顶点→边、面→面、边→面等）
- 5.1.3 局部拓扑操作（边折叠、边分裂、边翻转、顶点移除）
- 5.1.4 欧拉操作（保持拓扑一致性的编辑原语）
- 5.1.5 法线计算（均匀/面积/角度加权）
- 5.1.6 高斯曲率与平均曲率估计（离散微分几何算子）
- 5.1.7 主曲率方向与主曲率估计
- 5.1.8 形状直径函数（Shape Diameter Function）

### 5.2 网格简化与细化
- 5.2.1 顶点聚类（Vertex Clustering）
- 5.2.2 边折叠简化（Edge Collapse）：QEM 二次误差度量（Garland-Heckbert）
- 5.2.3 基于外观保持的简化（Image-Driven Simplification）
- 5.2.4 渐进网格（Progressive Meshes）
- 5.2.5 自适应简化（视点相关 LOD / View-Dependent Refinement）
- 5.2.6 网格细化（细分曲面逆过程：√3细化、Loop 细化应用）
- 5.2.7 重网格化（Remeshing）：各向同性/各向异性重网格化

### 5.3 网格平滑与去噪
- 5.3.1 拉普拉斯平滑（Laplacian Smoothing / Umbrella Operator）
- 5.3.2 双边网格滤波（Bilateral Mesh Filtering）
- 5.3.3 平均曲率流（Mean Curvature Flow）
- 5.3.4 基于优化的去噪：L₀ 最小化、L₁ 稀疏优化
- 5.3.5 非局部均值去噪（Non-local Means）
- 5.3.6 特征保持平滑（Feature-Preserving Smoothing）
- 5.3.7 引导法向滤波（Guided Normal Filtering）
- 5.3.8 基于深度学习的网格去噪

### 5.4 网格参数化
- 5.4.1 参数化基本概念（平面嵌入、扭曲度量）
- 5.4.2 凸组合方法（Floater 均值坐标、调和映射）
- 5.4.3 基于几何能量的方法（Dirichlet 能量、共形能量）
- 5.4.4 最小二乘共形映射（LSCM）
- 5.4.5 尽可能刚性参数化（ARAP Parameterization）
- 5.4.6 边界固定/自由/ABF（Angle Based Flattening）
- 5.4.7 全局无缝参数化（Seamless / Globally Smooth Parameterization）
- 5.4.8 锥奇异点（Cone Singularities）与割缝生成
- 5.4.9 交叉参数化（Cross-Parameterization / Consistent Parameterization）
- 5.4.10 体积参数化（Tetrahedral / Hexahedral Parameterization）
- 5.4.11 UV 展开的图集打包（Atlas Packing / Rectangle Packing）

### 5.5 表面重建
- 5.5.1 从点云到网格：
  - 5.5.1.1 移动立方体（Marching Cubes）
  - 5.5.1.2 移动四面体（Marching Tetrahedra）
  - 5.5.1.3 泊松表面重建（Poisson Surface Reconstruction）
  - 5.5.1.4 筛选泊松重建（Screened Poisson）
  - 5.5.1.5 径向基函数隐式曲面重建（RBF Reconstruction）
  - 5.5.1.6 浮动尺度泊松重建（Floating Scale / FPSR）
- 5.5.2 多视图立体视觉重建（MVS Patch-Based、深度图融合）
- 5.5.3 基于 TSDF（截断有符号距离函数）的融合（KinectFusion、Voxel Hashing）
- 5.5.4 占用场到网格提取（Multi-resolution Iso-surface Extraction）
- 5.5.5 基于深度学习的表面重建（Deep Marching Cubes、Occupancy Networks、Neural Surface）
- 5.5.6 从线稿/草图重建（Sketch-based Modeling）
- 5.5.7 完整性与非完整扫描配准（Scan Completion）

### 5.6 形状分析
- 5.6.1 形状描述子：
  - 5.6.1.1 全局：球形谐描述子、形状分布（D2）、Zernike 矩
  - 5.6.1.2 局部：自旋图（Spin Image）、SHOT、FPFH、RoPS
  - 5.6.1.3 谱描述子（Heat Kernel Signature HKS、Wave Kernel Signature WKS）
- 5.6.2 形状对应（Shape Correspondence）：
  - 5.6.2.1 函数映射框架（Functional Maps）
  - 5.6.2.2 基于谱匹配（Spectral Matching / Blended Intrinsic Maps）
  - 5.6.2.3 非刚性配准（Non-rigid ICP、CPD）
- 5.6.3 对称性检测：
  - 5.6.3.1 反射对称、旋转对称、平移对称
  - 5.6.3.2 内在对称性（Intrinsic Symmetry / 基于测地线的对称检测）
- 5.6.4 形状分割（Mesh Segmentation）：
  - 5.6.4.1 基于曲率 / 基于分水岭
  - 5.6.4.2 基于谱聚类
  - 5.6.4.3 基于随机割（Randomized Cuts）
  - 5.6.4.4 基于机器学习的分割（PointNet 系列变体应用于分割）
- 5.6.5 骨架提取（Skeletonization）：中轴变换（Medial Axis）、曲线骨架（Curve Skeleton）
- 5.6.6 显著性检测（Mesh Saliency / 视觉注意区域）

### 5.7 形变与编辑
- 5.7.1 基于微分坐标的编辑（Laplacian Coordinates / δ-Coordinates）
- 5.7.2 ARAP 形变（As-Rigid-As-Possible Deformation）
- 5.7.3 空间变形（FFD、Cage Deformation、Green Coordinates）
- 5.7.4 基于物理的形变（线弹性 FEM、Neo-Hookean 非线性形变）
- 5.7.5 大变形处理与旋转估计（Polar Decomposition）
- 5.7.6 形状插值与形变迁移（Shape Interpolation / Deformation Transfer）

### 5.8 模型修复与清理
- 5.8.1 非流形检测与修复
- 5.8.2 法线方向统一（Consistent Normal Orientation）
- 5.8.3 自交检测与修复
- 5.8.4 孔洞填充（Hole Filling：基于最小面积、基于曲率连续性）
- 5.8.5 退化和零面积面片处理
- 5.8.6 拓扑错误修复（非流形边/顶点、孤立顶点、重复面）
- 5.8.7 水密化处理（Watertight Conversion）
- 5.8.8 基于深度学习的自动修复

### 5.9 几何压缩
- 5.9.1 几何压缩基础（量化、预测、熵编码）
- 5.9.2 网格压缩标准：MPEG-4 3DMC、Draco (Google)、Cortocodec
- 5.9.3 渐进式网格压缩
- 5.9.4 基于神经网络的几何压缩
- 5.9.5 纹理坐标与属性的有损/无损压缩

---

## 第六章 · 色彩科学与视觉感知

### 6.1 光度学与色度学基础
- 6.1.1 可见光谱与辐射度量学回顾
- 6.1.2 光度学单位（流明 lm、坎德拉 cd、勒克斯 lx、尼特 cd/m²）
- 6.1.3 人眼视觉特性（感光细胞：视锥/视杆、光谱灵敏度）

### 6.2 色彩空间
- 6.2.1 CIE 1931 XYZ 色彩空间
- 6.2.2 CIE xy 色度图
- 6.2.3 CIE 1976 L*a*b*（CIELAB）色彩空间：感知均匀性
- 6.2.4 CIE L*u*v* 色彩空间
- 6.2.5 CIE LCh（亮度、色度、色相）色彩空间
- 6.2.6 sRGB：原色、白点、Gamma 曲线、线性值与编码值
- 6.2.7 DCI-P3、Display P3
- 6.2.8 Adobe RGB、ProPhoto RGB
- 6.2.9 Rec.709（HDTV）、Rec.2020（UHD/HDR）
- 6.2.10 ACES（Academy Color Encoding System）：ACES2065-1、ACEScg、ACEScct
- 6.2.11 ICtCp（ITU-R BT.2100）
- 6.2.12 广色域（Wide Color Gamut, WCG）
- 6.2.13 OKLab / OKLCH（感知均匀的色彩空间）

### 6.3 伽玛、传递函数与色调映射
- 6.3.1 Gamma 编码与校正（Gamma 2.2、sRGB EOTF/OETF）
- 6.3.2 传递函数（Transfer Function / OETF / EOTF）
- 6.3.3 PQ（Perceptual Quantizer, ST.2084 / SMPTE 2084）
- 6.3.4 HLG（Hybrid Log-Gamma）
- 6.3.5 场景参考（Scene-Referred）vs 显示参考（Display-Referred）管线
- 6.3.6 色调映射算子（回顾 3.7.1）
- 6.3.7 HDR 到 SDR 的动态范围适配

### 6.4 色貌模型
- 6.4.1 CIECAM02 / CIECAM16
- 6.4.2 iCAM06（HDR 图像外观模型）
- 6.4.3 色适应变换（Chromatic Adaptation：von Kries、Bradford、CAT02/16）

### 6.5 视觉感知模型
- 6.5.1 对比敏感度函数（Contrast Sensitivity Function, CSF）
- 6.5.2 可见性阈值（Just Noticeable Difference, JND）
- 6.5.3 视觉掩蔽效应（Visual Masking）：亮度掩蔽、纹理掩蔽、时域掩蔽
- 6.5.4 感知度量（SSIM、MS-SSIM、FSIM、LPIPS、DISTS、ST-LPIPS）
- 6.5.5 视觉注意力模型（Saliency Maps、Itti-Koch 模型、深度注视预测）
- 6.5.6 基于视觉感知的渲染优化（Foveated Rendering / 注视点渲染）

### 6.6 高动态范围成像
- 6.6.1 HDR 图像格式（OpenEXR、Radiance HDR、PFM、JPEG-XL HDR、AVIF HDR）
- 6.6.2 多曝光合成 HDR（Debevec & Malik 方法、Robertson 方法）
- 6.6.3 鬼影去除（Ghost Removal）
- 6.6.4 HDR 显示技术（OLED、Mini-LED、Micro-LED 背光）
- 6.6.5 HDR 环境贴图捕获与处理

---

## 第七章 · 硬件架构与系统

### 7.1 GPU 体系结构

#### 7.1.1 渲染管线硬件视角
- 7.1.1.1 顶点获取与几何引擎
- 7.1.1.2 图元装配与光栅化器（Rasterizer / ROPs）
- 7.1.1.3 纹理单元（TMU）与缓存层次
- 7.1.1.4 流式多处理器（SM / CU / Xe Core）架构
- 7.1.1.5 SIMD / SIMT 执行模型：Warp / Wavefront / Subgroup
- 7.1.1.6 分支发散（Branch Divergence）与占用率（Occupancy）
- 7.1.1.7 寄存器文件与共享内存/局部数据存储（LDS）
- 7.1.1.8 光栅化输出单元（ROP）与像素混合

#### 7.1.2 现代 GPU 特性
- 7.1.2.1 异步计算（Async Compute）与并行队列
- 7.1.2.2 Mesh Shader / Task Shader 管线（取代传统几何管线）
- 7.1.2.3 可变速率着色（VRS Tier 1/2）
- 7.1.2.4 采样器反馈（Sampler Feedback）与纹理空间着色
- 7.1.2.5 光线追踪核心（RT Core：BVH 遍历、三角形求交加速）
- 7.1.2.6 张量核心（Tensor Core：矩阵乘法加速、AI 推理/降噪/DLSS）
- 7.1.2.7 着色器执行重排序（Shader Execution Reordering, SER）
- 7.1.2.8 不透明与不透明微映射（OMM / DMM）
- 7.1.2.9 GPU 工作图（Work Graphs / GPU-Driven Rendering Pipeline）
- 7.1.2.10 直接存储访问（DirectStorage / GPU 直通 SSD）

#### 7.1.3 显存与带宽
- 7.1.3.1 显存类型：GDDR6/6X/7、HBM2/3/3e
- 7.1.3.2 缓存层次（L1、L2、Infinity Cache / Last-Level Cache）
- 7.1.3.3 带宽压缩（Delta Color Compression, DCC / 无损带宽压缩）
- 7.1.3.4 纹理压缩硬件支持（BCn、ASTC、ETC）
- 7.1.3.5 稀疏/部分驻留资源（Tiled Resources / Sparse Textures）

### 7.2 图形 API

#### 7.2.1 OpenGL / OpenGL ES / WebGL
- 7.2.1.1 OpenGL 管线模型与状态机
- 7.2.1.2 OpenGL ES 3.x / WebGL 2.0 能力集
- 7.2.1.3 扩展机制（GL_EXT / GL_ARB）
- 7.2.1.4 无绑定设计（Bindless Textures / ARB_bindless_texture）
- 7.2.1.5 AZDO（Approaching Zero Driver Overhead）技术

#### 7.2.2 Vulkan
- 7.2.2.1 实例、物理设备、逻辑设备
- 7.2.2.2 命令缓冲与命令池（多线程录制）
- 7.2.2.3 管线状态对象（PSO）：图形/计算/光追管线
- 7.2.2.4 描述符集布局与描述符池（Descriptor Indexing / Update After Bind）
- 7.2.2.5 同步原语：信号量、围栏、管线屏障、子通道依赖
- 7.2.2.6 渲染通道（Render Pass）与动态渲染（Dynamic Rendering）
- 7.2.2.7 内存管理：VMA（Vulkan Memory Allocator）、设备本地 vs 主机可见
- 7.2.2.8 推送常量（Push Constants）与特殊化常量（Specialization Constants）
- 7.2.2.9 时间线信号量（Timeline Semaphores）
- 7.2.2.10 Vulkan 光线追踪（VK_KHR_ray_tracing_pipeline）
- 7.2.2.11 Vulkan 视频编解码（VK_KHR_video_queue）

#### 7.2.3 DirectX 12
- 7.2.3.1 设备创建与工厂模式
- 7.2.3.2 命令队列、命令列表、命令分配器
- 7.2.3.3 管线状态对象（PSO）与根签名（Root Signature）
- 7.2.3.4 资源描述符堆（CBV/SRV/UAV 描述符堆）
- 7.2.3.5 资源屏障（Resource Barriers）与状态转换
- 7.2.3.6 围栏同步（Fence-Based Synchronization）
- 7.2.3.7 DirectX Raytracing（DXR）：状态对象（RTPSO）、着色器表（Shader Table）
- 7.2.3.8 DirectML（机器学习推理与训练加速）
- 7.2.3.9 DirectStorage（GPU 直通 NVMe SSD）

#### 7.2.4 Metal
- 7.2.4.1 MTLDevice、MTLCommandQueue、MTLCommandBuffer
- 7.2.4.2 渲染管线描述符（MTLRenderPipelineDescriptor）
- 7.2.4.3 参数缓冲（Argument Buffers）：GPU 可写描述符
- 7.2.4.4 堆（Heaps）与围栏同步
- 7.2.4.5 Metal 光线追踪（Metal Ray Tracing / MPSRayIntersector）
- 7.2.4.6 MetalFX（时域超分辨率 / 空间超分辨率）

#### 7.2.5 WebGPU
- 7.2.5.1 适配器与设备模型
- 7.2.5.2 管线（渲染管线 + 计算管线）
- 7.2.5.3 绑定组布局（Bind Group）
- 7.2.5.4 命令编码器（RenderPass / ComputePass）
- 7.2.5.5 WGSL 着色语言
- 7.2.5.6 与 WebGL 的比较与异构回退

#### 7.2.6 跨平台抽象
- 7.2.6.1 bgfx、The-Forge、NVRHI、Diligent Engine
- 7.2.6.2 Google ANGLE（OpenGL ES → Vulkan/Metal/D3D）
- 7.2.6.3 MoltenVK（Vulkan → Metal 转换层）
- 7.2.6.4 DXVK / vkd3d-proton（D3D → Vulkan 转换层）

### 7.3 着色器编程语言

#### 7.3.1 高级着色语言
- 7.3.1.1 GLSL（OpenGL Shading Language）
- 7.3.1.2 HLSL（High-Level Shading Language）：SM 5.0 / SM 6.x 特性
- 7.3.1.3 MSL（Metal Shading Language）：基于 C++14
- 7.3.1.4 WGSL（WebGPU Shading Language）
- 7.3.1.5 OpenCL 内核语言（用于通用 GPU 计算）

#### 7.3.2 着色器编译与中间表示
- 7.3.2.1 SPIR-V（标准可移植中间表示）
- 7.3.2.2 DXIL（DirectX Intermediate Language）
- 7.3.2.3 Metal IR（基于 LLVM 位码）
- 7.3.2.4 着色器编译工具链：glslang、DXC、SPIRV-Cross、 slang、Rust-GPU

#### 7.3.3 现代着色器特性
- 7.3.3.1 Wave / Subgroup 内建操作（ballot、shuffle、vote、reduce）
- 7.3.3.2 16 位类型支持（min16float、half）
- 7.3.3.3 8 位整型运算（DP4A / Int8 加速推理）
- 7.3.3.4 结构化缓冲与字节地址缓冲
- 7.3.3.5 着色器指针与递归（SPV_KHR_physical_storage_buffer_addresses）
- 7.3.3.6 无绑定资源（Bindless / Descriptor Indexing）

### 7.4 GPU 计算与并行编程
- 7.4.1 CUDA（统一计算设备架构）：
  - 7.4.1.1 线程层次：Grid → Block → Thread
  - 7.4.1.2 共享内存、常量内存、全局内存、纹理内存
  - 7.4.1.3 协作组（Cooperative Groups）
  - 7.4.1.4 CUDA Graph（降低启动开销）
  - 7.4.1.5 多流并发（Streams / Async Copy / Overlap Compute & Transfer）
- 7.4.2 OpenCL：平台、设备、上下文、命令队列、内核
- 7.4.3 Vulkan Compute / DirectX Compute Shader
- 7.4.4 SYCL / DPC++（基于标准 C++ 的加速编程）
- 7.4.5 HIP（AMD ROCm 异构接口）
- 7.4.6 GPU 归约、扫描、排序模式（Reduction、Prefix Sum、Radix Sort / Bitonic Sort）
- 7.4.7 GPU 并行算法设计模式（Map、Gather、Scatter、Partition）

### 7.5 渲染引擎架构

#### 7.5.1 通用引擎组件
- 7.5.1.1 资源管理器（纹理、网格、着色器、材质生命周期管理）
- 7.5.1.2 场景管理（场景图、空间划分、流式加载）
- 7.5.1.3 渲染图（Render Graph / Frame Graph）：资源依赖自动解析与屏障生成
- 7.5.1.4 渲染管线抽象（Pass、View、Technique）
- 7.5.1.5 材质系统：Shader 变体管理、参数绑定
- 7.5.1.6 绘制调用收集/排序/合批
- 7.5.1.7 多线程渲染架构（游戏线程 → 渲染线程 → GPU）
- 7.5.1.8 流式世界加载（World Streaming / Level Streaming）

#### 7.5.2 可见性与裁剪
- 7.5.2.1 视锥体裁剪（Frustum Culling）
- 7.5.2.2 遮挡剔除：
  - 7.5.2.2.1 硬件遮挡查询（Occlusion Query）
  - 7.5.2.2.2 软件遮挡剔除（Potentially Visible Set, PVS）
  - 7.5.2.2.3 Hierarchical Z-Buffer (Hi-Z) 遮挡剔除
  - 7.5.2.2.4 基于距离的剔除
  - 7.5.2.2.5 入口剔除（Portal Culling / 室内场景）
- 7.5.2.3 可见性缓冲（Visibility Buffer）：两阶段可见性+材质
- 7.5.2.4 GPU 驱动剔除（GPU-Driven Culling / Indirect Draw Count Generation）

#### 7.5.3 调试与性能分析
- 7.5.3.1 GPU 调试工具：RenderDoc、NVIDIA Nsight、PIX、Xcode GPU Capture
- 7.5.3.2 GPU 性能计数器与瓶颈诊断（ALU / Bandwidth / Fill-Rate / Latency Bound）
- 7.5.3.3 着色器性能分析（ALUs、Texture Stalls、Occupancy）
- 7.5.3.4 帧分析器（Frame Profiler / Timing Graph）
- 7.5.3.5 图形调试与像素历史（Pixel History / Mesh Viewer）
- 7.5.3.6 API 验证层（Vulkan Validation Layers、D3D12 Debug Layer）

#### 7.5.4 主流引擎
- 7.5.4.1 Unreal Engine 5 渲染架构（Nanite、Lumen、虚拟阴影图）
- 7.5.4.2 Unity 渲染管线（Built-in、URP、HDRP、自定义 SRP）
- 7.5.4.3 Godot 渲染架构（Vulkan/GLES3 后端）
- 7.5.4.4 O3DE (Open 3D Engine) 渲染器
- 7.5.4.5 自定义引擎的设计考量

---

## 第八章 · 显示与人机交互

### 8.1 显示技术
- 8.1.1 LCD、OLED、Mini-LED、Micro-LED、QLED
- 8.1.2 刷新率、响应时间、输入延迟
- 8.1.3 V-Sync、Adaptive Sync（G-Sync / FreeSync）、VRR
- 8.1.4 多显示器拼接与 CAVE 环境
- 8.1.5 颜色校准与色彩管理（ICC Profile / 显示器校准流程）

### 8.2 虚拟现实
- 8.2.1 VR 渲染管线（立体渲染：双眼视差、IPD）
- 8.2.2 透镜畸变校正（反桶形畸变 / Barrel Distortion Correction）
- 8.2.3 色差校正
- 8.2.4 异步时间扭曲（Asynchronous Time Warp, ATW）
- 8.2.5 异步空间扭曲（Asynchronous Space Warp, ASW）
- 8.2.6 注视点渲染（Foveated Rendering：固定/动态注视点、眼球追踪）
- 8.2.7 延迟敏感性与运动到光子（Motion-to-Photon）延迟优化
- 8.2.8 单通道立体渲染（Single-Pass Stereo / Instanced Stereo）
- 8.2.9 VR 输入与追踪（6DOF 控制器、手势追踪）

### 8.3 增强现实与混合现实
- 8.3.1 透视 AR（光学/视频透视）渲染
- 8.3.2 光照一致性（环境光照估计、环境探针 / IBL）
- 8.3.3 遮挡一致性（实时遮挡估计与分割）
- 8.3.4 平面检测与锚定（ARCore / ARKit / HoloLens 空间映射）
- 8.3.5 实时语义分割与深度估计

### 8.4 3D 显示
- 8.4.1 立体显示（快门式 / 偏振式 3D）
- 8.4.2 自动立体显示（裸眼 3D / Lenticular Lens、视差屏障）
- 8.4.3 光场显示
- 8.4.4 体积显示（Volumetric Display）
- 8.4.5 全息显示概念

### 8.5 用户交互与 3D UI
- 8.5.1 3D 拾取（Picking）：光线投射法、基于像素 ID 的颜色编码
- 8.5.2 3D 操纵器（Gizmo / Manipulator）：平移、旋转、缩放
- 8.5.3 3D 相机控制（Orbit、FPS、Trackball、Arcball）
- 8.5.4 手势与体感交互（Leap Motion、Kinect、Vision-based Hand Tracking）
- 8.5.5 触觉反馈（Haptic Feedback / 触觉渲染）
- 8.5.6 基于注视点的交互（Gaze-based Interaction）

---

## 第九章 · 三维视觉与计算摄影

### 9.1 相机模型与几何
- 9.1.1 针孔相机模型
- 9.1.2 内参矩阵（焦距、主点、畸变参数）
- 9.1.3 外参矩阵（旋转 R + 平移 t）
- 9.1.4 径向畸变与切向畸变模型（Brown-Conrady 模型）
- 9.1.5 鱼眼镜头模型（等距投影、等立体角投影、FOV 模型）
- 9.1.6 双相机模型与全景缝合
- 9.1.7 光场/全光函数（Plenoptic Function / Light Field）

### 9.2 多视角几何
- 9.2.1 对极几何（Epipolar Geometry）
- 9.2.2 本质矩阵（Essential Matrix E）与基础矩阵（Fundamental Matrix F）
- 9.2.3 单应性矩阵（Homography H）与平面场景
- 9.2.4 三角测量（Triangulation）
- 9.2.5 运动恢复结构（Structure from Motion, SfM）
  - 9.2.5.1 增量式 SfM（COLMAP 风格）
  - 9.2.5.2 全局式 SfM
  - 9.2.5.3 层次式 SfM
- 9.2.6 同时定位与建图（SLAM）：
  - 9.2.6.1 视觉 SLAM（ORB-SLAM3、DSO、VINS-Mono）
  - 9.2.6.2 视觉-惯性 SLAM（VIO）
  - 9.2.6.3 稠密 SLAM（KinectFusion、ElasticFusion、BundleFusion）
  - 9.2.6.4 基于 NeRF / 3DGS 的 SLAM

### 9.3 深度估计
- 9.3.1 双目立体匹配（Stereo Matching）：
  - 9.3.1.1 局部匹配：SAD、NCC、Census Transform
  - 9.3.1.2 全局匹配：图割、半全局匹配（SGM）
  - 9.3.1.3 基于深度学习的立体匹配（PSMNet、RAFT-Stereo、CREStereo）
- 9.3.2 单目深度估计：
  - 9.3.2.1 基于线索（散焦、线性透视、相对大小）
  - 9.3.2.2 基于深度学习（MiDaS、DPT、ZoeDepth、Depth Anything）
- 9.3.3 飞行时间法（ToF：调制连续波、脉冲法）
- 9.3.4 结构光法（编码结构光、随机散斑：Kinect v1）

### 9.4 三维重建
- 9.4.1 多视角立体视觉（Multi-View Stereo, MVS）：
  - 9.4.1.1 体素着色与空间雕刻（Space Carving）
  - 9.4.1.2 基于面片（PatchMatch / PMVS / ACMM）
  - 9.4.1.3 基于深度图融合（COLMAP MVS、OpenMVS）
- 9.4.2 光度立体（Photometric Stereo）
- 9.4.3 Shape-from-X（SfS / SfD / SfP / SfT）
- 9.4.4 基于深度学习的 MVS（MVSNet、CasMVSNet、PatchMatchNet）
- 9.4.5 神经隐式重建（NeuS、VolSDF、Neuralangelo、BakedSDF）

### 9.5 计算摄影
- 9.5.1 HDR 捕获与融合
- 9.5.2 全景拼接（Panorama Stitching：图像配准、接缝优化、增益补偿）
- 9.5.3 图像消抖（Image / Video Stabilization）
- 9.5.4 人像模式（深度估计 + Bokeh Rendering）
- 9.5.5 超分辨率（单图 / 多图融合）
- 9.5.6 低光增强（多帧降噪与融合）
- 9.5.7 计算照明（闪光/环境光分解与重新照明）
- 9.5.8 去除反射与障碍物（Reflection Removal / Obstruction Removal）

---

## 第十章 · 文件格式与数据交换

### 10.1 3D 文件格式
- 10.1.1 OBJ：网格、法线、纹理坐标、材质库（MTL）
- 10.1.2 PLY（Stanford Polygon Format）：支持顶点属性
- 10.1.3 STL：三角网格标准（二进制/ASCII）、3D 打印
- 10.1.4 FBX（Autodesk）：场景层级、动画、材质、嵌入式数据
- 10.1.5 glTF 2.0（GL Transmission Format / "3D JPEG"）：
  - 10.1.5.1 JSON 场景描述 + 二进制缓冲（.bin）
  - 10.1.5.2 PBR 材质标准（Metallic-Roughness / Specular-Glossiness 扩展）
  - 10.1.5.3 动画、蒙皮、变形目标支持
  - 10.1.5.4 Draco 网格压缩扩展
  - 10.1.5.5 KTX 2.0 纹理扩展（Universal 纹理压缩）
  - 10.1.5.6 EXT_meshopt_compression、EXT_texture_webp 等扩展
- 10.1.6 USD / Universal Scene Description（Pixar）：
  - 10.1.6.1 层级场景合成（Composition Arcs：Sublayer, Reference, Payload, VariantSet）
  - 10.1.6.2 Hydra 渲染框架
  - 10.1.6.3 USDZ（Apple AR 格式）
- 10.1.7 Alembic：几何缓存与动画交换
- 10.1.8 Collada（.dae）：XML 交换格式
- 10.1.9 3DS Max（.3ds）、Blender（.blend）、Maya（.ma/.mb）原生格式
- 10.1.10 CAD 格式：STEP、IGES、JT、BREP

### 10.2 图像与纹理格式
- 10.2.1 PNG、JPEG、WebP、AVIF、JPEG-XL
- 10.2.2 HDR 格式：OpenEXR、Radiance HDR（.hdr）、32-bit TIFF
- 10.2.3 GPU 纹理格式（BCn、ASTC、ETC2、PVRTC）
- 10.2.4 KTX 2.0（Khronos 纹理容器）：Basis Universal 超压缩
- 10.2.5 DDS（DirectDraw Surface）

### 10.3 着色器与材质交换
- 10.3.1 MaterialX（工业标准材质定义与交换）
- 10.3.2 MDL（NVIDIA Material Definition Language）
- 10.3.3 OpenPBR（由 Adobe、Autodesk 等共同推进）
- 10.3.4 UsdShade（USD 材质绑定）
- 10.3.5 SPIR-V（着色器交换）

### 10.4 动画与运动数据格式
- 10.4.1 BVH（Biovision Hierarchy）
- 10.4.2 FBX 动画数据
- 10.4.3 glTF 动画（关键帧、线性插值、Cubic Spline）
- 10.4.4 Alembic 动画缓存
- 10.4.5 C3D（运动捕获原始数据）

---

## 第十一章 · 应用领域

### 11.1 游戏与实时交互
- 11.1.1 AAA 游戏渲染（3A 级画面流水线）
- 11.1.2 独立游戏渲染风格（像素艺术、2D 光照、低多边形风格）
- 11.1.3 UI 渲染（矢量化字体、SDF 文本、分辨率自适应布局）
- 11.1.4 移动端图形优化（低功耗、带宽友好策略）

### 11.2 影视与动画
- 11.2.1 离线渲染器（RenderMan、Arnold、V-Ray、Cycles、Redshift、Octane、MoonRay）
- 11.2.2 视觉特效（VFX）管线：合成、抠像、跟踪、粒子特效
- 11.2.3 虚拟制片（Virtual Production）：LED 墙 + 引擎实时渲染（StageCraft）
- 11.2.4 表演捕捉（Performance Capture）：体态 + 面部同步
- 11.2.5 数字人（Digital Human / MetaHuman）

### 11.3 科学可视化
- 11.3.1 体绘制（直接/间接体渲染，传输函数设计）
- 11.3.2 流场可视化（流线、条纹线、LIC 线积分卷积）
- 11.3.3 张量场可视化（超流线、扩散张量成像 DTI 可视化）
- 11.3.4 信息可视化（网络图、层次图、平行坐标）
- 11.3.5 地理信息可视化（GIS、地形渲染、大规模点云）
- 11.3.6 医学可视化（CT/MRI 重建、手术模拟、解剖教学）

### 11.4 工业与工程设计
- 11.4.1 CAD（计算机辅助设计）：实体建模、曲面建模、参数化
- 11.4.2 CAE（计算机辅助工程）：有限元分析前/后处理可视化
- 11.4.3 CAM（计算机辅助制造）：刀具路径可视化
- 11.4.4 BIM（建筑信息建模）
- 11.4.5 3D 打印切片与支撑结构生成
- 11.4.6 数字孪生（Digital Twin）可视化

### 11.5 自动驾驶与机器人仿真
- 11.5.1 传感器仿真（RGB 相机、LiDAR、雷达、深度相机）
- 11.5.2 合成数据生成（域随机化、Autoencoder-based 真实化）
- 11.5.3 环境仿真（天气、光照条件变化、动态障碍物）
- 11.5.4 仿真平台（CARLA、AirSim、NVIDIA DRIVE Sim / Omniverse、Isaac Sim）

### 11.6 虚拟人/数字人
- 11.6.1 高精度面部重建与动画（Light Stage、多视角 3DMM 拟合）
- 11.6.2 皮肤渲染（次表面散射、毛孔细节、微几何细节）
- 11.6.3 眼球渲染（角膜反射、瞳孔折射、虹膜细节）
- 11.6.4 毛发渲染（基于曲线的毛发、Marschner 散射模型）
- 11.6.5 服装模拟与渲染
- 11.6.6 实时数字人（MetaHuman、NVIDIA ACE / Audio2Face）

---

## 第十二章 · 前沿与交叉方向

### 12.1 神经渲染与生成
- 12.1.1 神经场景表示（NeRF、3DGS、NGP、Triplane）
- 12.1.2 生成对抗网络 GAN 在图形学中的应用
- 12.1.3 扩散模型用于 3D 生成与纹理合成
- 12.1.4 自回归 3D 生成
- 12.1.5 多模态 3D 生成（文本/图像/视频 → 3D）

### 12.2 可微图形学
- 12.2.1 可微渲染在逆向问题中的应用
- 12.2.2 可微物理模拟
- 12.2.3 可微管线端到端学习
- 12.2.4 梯度驱动的内容创建工具

### 12.3 云渲染与流式传输
- 12.3.1 云游戏架构（GeForce Now、Xbox Cloud Gaming、Luna）
- 12.3.2 像素流送（Pixel Streaming）：编码、延迟优化、带宽适配
- 12.3.3 虚拟工作站（NVIDIA vGPU、AWS Thinkbox Deadline 分布式渲染）
- 12.3.4 WebRTC 与低延迟视频流
- 12.3.5 边缘计算在图形学中的角色

### 12.4 量子图形学
- 12.4.1 量子计算在光线追踪中的潜力
- 12.4.2 量子蒙特卡洛采样

### 12.5 生物启发图形学
- 12.5.1 仿生视觉（基于人眼模型的渲染）
- 12.5.2 基于神经科学的图形学评价指标
- 12.5.3 大脑启发的计算摄影

### 12.6 图形学与 AI 的融合
- 12.6.1 AI 辅助内容创作（AI-Assisted Art / Copilot for 3D）
- 12.6.2 AI 驱动的实时渲染优化（自适应采样、预测性 LOD）
- 12.6.3 神经超采样与智能画质增强
- 12.6.4 以图形学为基础生成合成训练数据
- 12.6.5 世界模型（World Model）与生成式世界模拟（Sora / Genie 方向）

### 12.7 元宇宙与空间计算
- 12.7.1 跨平台空间锚点与持久化世界
- 12.7.2 实时全局 3D 重建与共享
- 12.7.3 空间音频渲染（Spatial Audio / HRTF / Ambisonics）
- 12.7.4 3D 资产互操作性标准（OpenUSD / glTF 生态）
- 12.7.5 光场/全息通信（3D 视频通话 / 远程呈现）

---

## 附录 A · 著名会议与期刊
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

## 附录 B · 里程碑式论文与著作
- B.1 Phong (1975) — 经验光照模型
- B.2 Blinn (1977) — Blinn-Phong 反射与凹凸贴图
- B.3 Whitted (1980) — 递归光线追踪
- B.4 Cook & Torrance (1981) — 微面元 BRDF
- B.5 Kajiya (1986) — 渲染方程
- B.6 Loren Carpenter (1980s) — Reyes 渲染架构 (RenderMan)
- B.7 Debevec & Malik (1997) — HDR 图像捕获与基于图像的建模
- B.8 Veach & Guibas (1997) — Metropolis 光传输
- B.9 Kajiya & Kay (1989) — 毛发渲染
- B.10 Perlin (1985) — 噪声函数
- B.11 Catmull & Clark (1978) — 细分曲面
- B.12 Garland & Heckbert (1997) — QEM 网格简化
- B.13 Möller & Trumbore (1997) — 光线-三角形快速求交
- B.14 Loop (1987) — 三角形细分曲面
- B.15 Kajiya & Von Herzen (1984) — 体积渲染中的光线步进
- B.16 Veach (1997 PhD) — 路径积分框架与 MIS
- B.17 Jensen (1996) — 光子映射
- B.18 Müller et al. — MPM 引入图形学
- B.19 Mildenhall et al. (2020) — NeRF
- B.20 Kerbl et al. (2023) — 3D Gaussian Splatting

## 附录 C · 重要国际标准
- C.1 Khronos: OpenGL, Vulkan, OpenCL, SPIR, glTF, WebGL, WebGPU, OpenXR
- C.2 ISO/IEC JTC 1/SC 24: CGM, VRML/X3D, SEDRIS
- C.3 MPEG: 3D Mesh Coding, Video-based Point Cloud Compression (V-PCC)
- C.4 SMPTE: 色彩相关标准（ST 2084/PQ, ST 2086, ST 2094 动态元数据）
- C.5 ITU-R: 色彩空间标准（BT.709, BT.2020, BT.2100）
- C.6 IEEE: 浮点标准 (754)、显示标准
- C.7 CIE: 色度学标准（CIE 1931, CIE 1976, CIECAM02/16）
- C.8 OpenUSD Alliance: USD 生态标准

---

*本文档旨在提供一个计算机图形学知识体系的全面概览，涵盖从基础数学到前沿研究的各个层次。每个条目代表一个独立的知识点或技术方向，可作为课程设计、自学路线或技术调研的参考索引。*

---

**作者：Xx1899**
