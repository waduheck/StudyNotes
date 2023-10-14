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
***外参矩阵***即旋转矩阵与平移矩阵

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
### 光线追踪
### 渲染

#### 体渲染
##### camera pose and camera matrix

#### 直接点表示

#### SDF


### ray warping function

### Level sets method

### SFM
