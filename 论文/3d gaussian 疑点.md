1. cuda_rasterizer/forward.cu中的in_frustum函数只判断了点与像素的深度关系，并没有进行视锥判定
3. forward.cu中的computeCov2D似乎并没有把超出相机的点去除，而是留在边缘
4. 背景光是常数，所有地点统一
5.   return std::make_tuple(rendered, out_color, radii, geomBuffer, binningBuffer, imgBuffer);这里的render返回数据顺序与接收顺序不一样  ，gaussian_render中的

    rendered_image, radii = rasterizer(
        means3D = means3D,
        means2D = means2D,
        shs = shs,
        colors_precomp = colors_precomp,
        opacities = opacity,
        scales = scales,
        rotations = rotations,
        cov3D_precomp = cov3D_precomp)
6. 高斯spilt是按固定模式计算分裂后的模型
7. 颜色是怎么来的