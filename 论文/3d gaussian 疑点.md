1. cuda_rasterizer/forward.cu中的in_frustum函数只判断了点与像素的深度关系，并没有进行视锥判定
3. forward.cu中的computeCov2D似乎并没有把超出相机的点去除，而是留在边缘
4. 背景光只有三维
5.   return std::make_tuple(rendered, out_color, radii, geomBuffer, binningBuffer, imgBuffer);
