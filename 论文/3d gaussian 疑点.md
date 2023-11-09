1. cuda_rasterizer/forward.cu中的in_frustum函数只判断了点与像素的深度关系，并没有进行视锥判定
2. forward.cu中的216行，直接将世界坐标与相机内参做变换到屏幕坐标
3. 