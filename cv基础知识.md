## 基础知识
### 齐次坐标系
为了解决透视与针孔成像问题，将n纬坐标用n+1维表示$(x,y) \leftrightarrow (\frac{x}{w},\frac{y}{w},1)$，并且$(x,y,0)$可以很好地表示无穷远处的点。

### 相机内外参矩阵与坐标变换
https://blog.csdn.net/jiaoyangwm/article/details/97752238
https://blog.csdn.net/fb_941219/article/details/129838372
世界坐标系（world coordinate）：表示物理上的三维世界  
相机坐标系（camera coordinate）：表示虚拟的三维相机坐标  
图像坐标系（pixel coordinate）：表示二维的图片坐标
从世界坐标系变换到相机坐标系是***刚体变换***，只需进行旋转与平移
![[旋转矩阵.png]]
![[平移矩阵.png]]
也就是说$$P_c = R P_w + T \Rightarrow 
\begin{bmatrix}
X_c\\
Y_c\\
Z_c\\
1
\end{bmatrix}= 
\begin{bmatrix}
R & T\\
0 & 1
\end{bmatrix}
\begin{bmatrix}
X_w\\
Y_w\\
Z_w\\
1
\end{bmatrix},R:3*3,T:3*1
$$
***外参矩阵***即旋转矩阵与平移矩阵，也就是上公式中的仿射变换矩阵

![[透视投影.png]]
再考虑主点不在图像坐标系原点与坐标轴倾斜的情况
$$Z_c 
\begin{bmatrix}
X\\
Y\\
1
\end{bmatrix}= 
\begin{bmatrix}
f_x & s & x_0 & 0\\
0 & f_y & y_0 & 0\\
0 & 0 & 1 & 0
\end{bmatrix}
\begin{bmatrix}
X_c\\
Y_c\\
Z_c\\
1
\end{bmatrix}$$
$$内参矩阵K = 
\begin{bmatrix}
f_x & s & x_0 \\
0 & f_y & y_0 \\
0 & 0 & 1
\end{bmatrix}$$
### 光线追踪
![[ray casting.png]]
一条射线可以用公式$r(t)=o+td$ 表示，其中$o$是原点坐标，$d$是方向向量
### 可微分渲染器
#### 立体渲染（volume rendering）
https://zhuanlan.zhihu.com/p/595117334
![[体渲染.webp]]
##### 吸收absorbing
![[体渲染吸收.webp]]
$$\frac{dI}{ds}=-\rho(s)AI(s)=-\tau_aI(s)$$
解微分方程得$$I(s)=I_0exp(-\int_0^s\tau_a(t)dt)$$
##### 放射emission
假设单个粒子发射的一束光辐射强度为$I_e$
$$\frac{dI}{ds}=I_e(s)\rho(s)A=I_e(s)\tau_a(s)$$
##### 外散射out-scattering
我们用$\tau_s$来表示外散射对光线的削弱比例
$$\frac{dI}{ds}=-\tau_s(s)I(s)$$

##### 内散射in-scattering
我们认为其他光路的辐射强度是$I_s$
$$\frac{dI}{ds}=-\tau_s(s)I_s(s)$$
##### 体渲染方程
###### 连续
将上述四个过程综合起来可以得到
$$\frac{dI}{ds} = -\tau_a(s)I(s)-\tau_s(s)I(s)+\tau_a(s)I_e(s)+\tau_s(s)I_s(s)$$
其中，**吸收**和**外散射**都会削弱光线的辐射强度，并且由于它们都和入射光有关，因此它们共同构成了体渲染中的**衰减项 (attenuation item)，而粒子发光**和**内散射**都来自独立的光源，因此被称为**源项 (source item)**。
为了求解方便，定义$\tau_t = \tau_a + \tau_s$,于是
$$I(s)=\int_0^sexp(-\int_0^t\tau_t(u)du)[\tau_a(t)I_e(t)+\tau_s(t)I_s(t)dt]+I_0exp(-\int_0^s\tau_t(t)dt)$$
我们进一步大胆假设:**$\tau_t,\tau_a,\tau_s$这些都相等，统一用$\sigma$表示,同时令$C=I_e +I_s$**
$$I(s)=\int_0^sT(t)\sigma(t)C(t)dt+T(s)I_0$$
其中$T(s)=exp(-\int_0^s\sigma(t)dt)$
我们再做简化，忽略背景光一项，即可获得nerf公式
$$C(r)=\int_{t_n}^{t_f}T(t)\sigma(r(t))c(r(t),d)dt, \quad where T(t) = exp(-\int_{t_n}^t\sigma(r(s))ds)$$
###### 离散
计算机中无法直接计算积分，我们需要将其离散化，将光路$[0,s]$,划分为N个等间距的区间:$[t_n,t_{n+1}]$,为了简化计算，我们假设每个区间nei


#### 直接点表示

#### SDF


### ray warping function

### Level sets method

### SFM
