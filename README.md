# knowledge
## 音视频录制播放概览

音视频录制原理：
<img width="1347" alt="image" src="https://user-images.githubusercontent.com/17528531/184130226-b81747af-0171-4ea2-a2c7-a5b521965b15.png">


音视频播放原理：
<img width="1356" alt="image" src="https://user-images.githubusercontent.com/17528531/184130602-2c6bbded-027d-4b2a-acad-5dda485a1476.png">

## 视频基础
### 图像基础概念

- 像素:像素是一个图片的基本单位，pix是英语单词picture的简写，加上英 语单词“元素element”，就得到了“pixel”，简称px，所以“像素”有“图像元素” 之意。
- 分辨率:是指图像的大小或尺寸。比如1920x1080。图片的分辨率和大小是什么关系？？
  360P(640x360)、720P(1280x720)、1080P(1920x1080)、4K(3840x2160)、8K(7680x4320)

  字母p表示逐行扫描 （progressive scan）；

  360P是600×360分辨率（15:9视频画面）逐行扫描视频，480×360分辨率相当于电视信号480i的清晰度。字母p表示逐行扫描 （progressive scan），数字 360 表示其垂直分辨率，也就是垂直方向有360条水平线的扫描线


  字母k表示图像水平方向上分辨率；

  4K(3840x2160) 水平方向上有3840个像素点 接近4k

- 位深:是指在记录数字图像的颜色时，计算机实际上是用每个像素需要的位深来表示的。比如红色分量用8bit。
  通常每个通道用8bit表示，8bit能表示256种颜色，每个通道的位深越大，能够表示的颜色值就越大，比如现在高端电视说的10bit色 彩，即是每个通道用10bit表示，每个通道有1024种颜色。1024*1024*1024约为 10,7374万色=10亿色， 是8bit的64倍。常见的颜色还是8bit居多。
- 帧率:在1秒钟时间里传输的图片的帧数，也可以理解为图形处理器每秒钟 能够刷新几次。比如25fps表示一秒有25张图片。
- 码率:视频文件在单位时间内使用的数据流量。比如1Mbps。
- Stride:指在内存中每行像素所占的空间。为了实现内存对齐每行像素在 内存中所占的空间并不一定是图像的宽度。


### rgb & yuv
rgb:
<img width="1320" alt="image" src="https://user-images.githubusercontent.com/17528531/184137118-9a2e1971-1810-4a50-8cfa-23c644357ad9.png">

yuv:
<img width="1256" alt="image" src="https://user-images.githubusercontent.com/17528531/184137053-fe6f5f7b-1abf-4118-8cbd-f62c80912958.png">


注：yuv排列方式不一样:
- packed(打包)格式：每个像素点的yuv数据交叉排列
- planar(平面)格式：使用三个数组分开存放yuv

<img width="1413" alt="image" src="https://user-images.githubusercontent.com/17528531/184138977-c8d01d94-5d00-45d5-a88e-784d5e6df4d0.png">

yuv采样表示法 444 422 420
<img width="867" alt="image" src="https://user-images.githubusercontent.com/17528531/184139932-b5adaa95-0399-4734-a28a-658c7843cfc1.png">

I帧: 一个完整的不依赖其他的图片
P帧：前向预测的帧间编码
B帧：双向时间预测

## 音频基础
