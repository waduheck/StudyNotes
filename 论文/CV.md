## SLAM
## GAN
## NeRF
### 1. 前期工作：DeepSDF
SDF是Signed Distance Function的缩写。DeepSDF通过回归（regress）一个分布来表达三维表面的。如下图所示，SDF>0的地方，表示该点在三维表面外面；SDF<0的地方，表示该点在三维表面里面。

### 2. NeRF
采用体积渲染方法，用神经网络来拟合Radiance Fields，是一种隐式的三维场景表示