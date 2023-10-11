## 基础知识

### 体渲染(Volume rendering)

### camera pose and camera matrix

## 模型
### SLAM
### GAN
### NeRF家族
#### 1. 前期工作：DeepSDF
SDF是Signed Distance Function的缩写。DeepSDF通过回归（regress）一个分布来表达三维表面的。如下图所示，SDF>0的地方，表示该点在三维表面外面；SDF<0的地方，表示该点在三维表面里面。

#### 2. NeRF
采用体积渲染方法，用神经网络来拟合Radiance Fields，是一种隐式的三维场景表示
##### 训练技巧
1. 分层采样
2. 位置编码

##### 缺点
Voxel Reresentation显示生成3D Object和3D Feature的方法，由于学习的是投影函数，分别会导致离散化物体或者降低生成图像的视图一致性。***另外NeRF的隐式方法需要很多不同角度的视图，需要对每个场景重新训练，并且不能生成新的场景***
#### 多目标
##### GRAF
受到NeRF的启发，GRAF设计了一种NeRF表示的条件变体，展示了如何从一组未设定pose的2D图像中学习出丰富的生成模型。 除了改变视角之外，GRAF 还允许修改生成对象的形状和外观。

与之前的方法相比，GRAF 的优势是以神经辐射场来描述场景。神经辐射场自带视角一致性，而这是之前的3D生成模型存在的最大问题。
##### GIRAFFE
GIRAFFE提出将场景表示为合成的neural feature fields，它可以控制相机的姿势，物体在场景中摆放的位置与角度，以及物体的形状与外观。更强大的是，GIRAFFE 还可以在场景中自由地增加多个物体，将生成的场景从 single-object 扩展到 multi-object，即使训练数据中没有这样的素材。
#### 动态场景：
##### D- NeRF
将时间加入变量
