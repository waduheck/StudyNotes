## SLAM
## GAN
## NeRF
### 1. 前期工作：DeepSDF
SDF是Signed Distance Function的缩写。DeepSDF通过回归（regress）一个分布来表达三维表面的。如下图所示，SDF>0的地方，表示该点在三维表面外面；SDF<0的地方，表示该点在三维表面里面。

### 2. NeRF
采用体积渲染方法，用神经网络来拟合Radiance Fields，是一种隐式的三维场景表示
#### 训练技巧
1. 分层采样
2. 位置编码

### 缺点
Voxel Reresentation显示生成3D Object和3D Feature的方法，由于学习的是投影函数，分别会导致离散化物体或者降低生成图像的视图一致性。***另外NeRF的隐式方法需要很多不同角度的视图，需要对每个场景重新训练，并且不能生成新的场景***
## GIRAFFE