## Basical functions of OpenCV  Summary

- cv2.imread(filepath,flags) 读取图片，默认是三通道(BGR)的彩色图，flags=0读入灰度图
- cv2.imwrite(filename,img) 保存图像  
- cv2.VideoCapture 读取视频
- cv2.imshow(name,img) 显示图片,需与cv2.waitkey(0)一起使用waitkey(1000):等待1000ms后关闭，cv2.waitkey(timeout) 显示图片时间，单位为ms，0代表一直显示

- b,g,r=cv2.split(img) 颜色通道提取,opencv提取格式为BGR(注意不是RBG)
- cv2.merge(b,g,r) 重新组合颜色通道
- cv2.copyMakeBorder(img,top, bottom, left, right,borderType) 填充边界
- cv2.resize(img, (width, height)) 变换图像大小（注意img.shape的出来的是(height,width))

- cv2.addWeighted(img1,α,img2,β,b) 为图片添加权重, 混合图像 αX1+βX2+b

- **滤波**

  - cv2.blur(img,ksize) 均值滤波( 矩形中间的值=矩形内的值相加取平均值)
  - cv2.boxFilter(img, ddepth,ksize, normalize=True) 方框滤波: (normalize=True等同于均值滤波， normalize=false代表直接求和不取均值，越界后显示为255)
  - cv2.GaussianBlur(img, ksize, sigmaX) 高斯滤波:(离得近的权重高，离得远的权重低）
  - cv2.medianBlur(img,ksize) 中值滤波:（矩形内的值排序后取中间值)

- **腐蚀&膨胀有关操作**

  - cv2.erode(img, kernel, iterations) 腐蚀操作

  - cv2.dilate(img1, kernel, iterations) 膨胀操作

  - cv2.morphologyEx(img, cv2.MORPH_OPEN, kernel) 开运算(先腐蚀再膨胀)

  - cv2.morphologyEx(img, cv2.MORPH_CLOSE, kernel) 闭运算(先膨胀再腐蚀)

  - cv2.morphologyEx(img, cv2.MORPH_GRADIENT, kernel) 梯度运算(膨胀-腐蚀)

  - cv2.morphologyEx(img,cv2.MORPH_TOPHAT,kernel) 顶帽运算(原始值-开运算)
  - cv2.morphologyEx(img,cv2.MORPH_BLACKHAT,kernel) 底帽运算(闭运算-原始值)

- **算子总结**

  - cv2.Sobel(img, ddepth, dx, dy,ksize) Sobel算子

  - cv2.Scharr(img, ddepth, dx, dy) Scharr算子(能捕捉到更多的细节)
  - cv2.Laplacian(img, ddepth) Laplacian算子(噪点影响很大)

- **图像采样（金字塔）**

  - cv2.pyrUp(img) 高斯金字塔:向上采样(放大图像)
  - cv2.pyrDown(img) 高斯金字塔:向下采样（缩小图像)

  - img-cv2.pyrUp(cv2.pyrDown(img)) 拉普拉斯金字塔(原图-(先缩小后放大))

- cv2.Canny(img, threshold1, threshold2) 边缘检测(threshold<value<threshold2,范围越大，边缘检测细节越多

- 轮廓相关

  - cv2.findContours(img, mode, method) 找出轮廓
  - drawContours(img, contours, contourIdx, color) 画出轮廓
  - cv2.contourArea(contour) 轮廓面积
  - cv2.arcLength(cnt, True) 轮廓周长 True表示闭合的
  - cv2.approxPolyDP(cnt, epsilon, True) 轮廓近似(普朗克算法)

- cv2.matchTemplate(img, templ, method) 模板匹配

- cv2.rectangle(img, pt1, pt2, color) 画矩形

- cv2.calcHist(img, channels, mask, histSize, ranges) 像素直方图统计

- cv2.equalizeHist(img) 直方图均衡化

  ## 原文链接：https://blog.csdn.net/qq_45453266/article/details/106698699

这个写的真不错，致谢原文，自己总结一遍