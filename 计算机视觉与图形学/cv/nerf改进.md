## 动态

### 添加位移场

## 抗锯齿

### 锥体渲染

## mip-nerf

## zip-nerf
https://zhuanlan.zhihu.com/p/622325164

## 2. NeRF
采用体积渲染方法，用神经网络来拟合Radiance Fields，是一种隐式的三维场景表示
### 训练技巧
1. 分层采样
2. 位置编码

### 缺点
1. Voxel Reresentation显示生成3D Object和3D Feature的方法，由于学习的是投影函数，分别会导致离散化物体或者降低生成图像的视图一致性。***另外NeRF的隐式方法需要很多不同角度的视图，需要对每个场景重新训练，并且不能生成新的场景***
2. 速度过慢，可以运用体素渲染加速
3. 具有歧义性
## 多目标
### GRAF
受到NeRF的启发，GRAF设计了一种NeRF表示的条件变体，展示了如何从一组未设定pose的2D图像中学习出丰富的生成模型。 除了改变视角之外，GRAF 还允许修改生成对象的形状和外观。

与之前的方法相比，GRAF 的优势是以神经辐射场来描述场景。神经辐射场自带视角一致性，而这是之前的3D生成模型存在的最大问题。
### GIRAFFE
GIRAFFE提出将场景表示为合成的neural feature fields，它可以控制相机的姿势，物体在场景中摆放的位置与角度，以及物体的形状与外观。更强大的是，GIRAFFE 还可以在场景中自由地增加多个物体，将生成的场景从 single-object 扩展到 multi-object，即使训练数据中没有这样的素材。
### 动态场景：
### D- NeRF
将时间加入变量，引入形变场
### Nerfies
https://blog.csdn.net/weixin_50973728/article/details/126542258
https://zhuanlan.zhihu.com/p/532319893
引入变形场：SO(3)与SE(3)
正则化：
1. 弹性正则
2. 背景正则
3. C2F, 退火ntk
### Hyper NeRF
https://blog.csdn.net/weixin_50973728/article/details/126628235
参考DeepSDF与nerf
切水果撕开纸张这种操作会改变拓扑，人脸中张合嘴巴也会改变皮肤表面连通性的变化，也就是拓扑变化，往往在三维重建中导致运动不连续或奇异点。

本文把level set和deformable field结合了一下，用MLP来建立level set框架。
升到高维加可变形切片

- 经典level set只有一个环境维度，但是本文可以加任意多环境维度增加自由度。
- 并不把level sets限定在超平面，而是允许一般的弯曲的切片流形（用MLP表示），就是把每一帧建模成nerf切出来的非平面切片
### NSFF
https://blog.csdn.net/weixin_50973728/article/details/126539716


### DynlBaR
### 语义分割
### Semantic-NeRF
场景中的实体如果属于同一类别，那么他们的外观以及形状应当具有较高的相似性，语意这种 high level 的信息应当与几何以及辐射信息高度相关。

### Semantic-Ray
两次多头注意力


### 高质量重建