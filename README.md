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
<img width="903" alt="image" src="https://user-images.githubusercontent.com/17528531/184146087-7ce19f63-a557-4006-9f04-01da131901fa.png">


### 常见视频压缩算法
MPEG2 - MPEG
H264 - MPEG
H265 - MPEG
AVS - 中国阵营
VP8 - google阵营
VP9 - google阵营

## 音频基础
>声音是由物体振动产生的，这种振动引起了周围空气压强的振动。声音可以看作是有很多震荡的函数复合在一起。振幅越大，声音越大。

### 频率
周期的倒数，每秒钟振动多少次。

人耳能听见的声音：20HZ ~ 20KHZ

**计算机需要将这种振动的模拟信号转为数字信号，---> 采样**

### 采样频率
> 每秒钟采样的个数,根据采样定律，要从采样中完全恢复原始波形，至少是信号中最高频率的两倍。所以一般采样频率是人耳能听到的最高频率的两倍44.1Khz

### 比特率
每秒传输的bit数，单位: bps, 没有压缩的音频数据比特率 = 采样频率 * 采样精度 * 通道数

### 码率
压缩后的音频数据比特率
码率 = 文件大小 / 时长；

### 帧
每次编码的采样单元，比如mp3 一般是1152个采样点作为一个采样单元，aac一般1024个采样点作为一个采样单元

### 帧长
不是一个标准的概念一般有下面两种解释：
- 一帧播放的时长
- 压缩后每帧的数据长度

### 交错模式 & 非交错模式
#### 交错模式
数字音频信号存储的方式。数据以连续帧的方式存储，即先存储1帧的左声道样本和右声道样本，然后再存储2帧。。。

#### 非交错模式
首先记录一个周期内所有帧左声道样本，然后再记录一个周期内所有右声道样本

### 音频压缩原理

1. 人耳听见以外的hz除去
2. 频谱掩蔽
<img width="616" alt="image" src="https://user-images.githubusercontent.com/17528531/184283759-f8fcc49f-84a9-42c1-ac54-5a421ad9b58f.png">
3. 时域掩蔽
4. 强音和弱音一起的时候可以给弱音去掉

### 音频压缩过程

音频采样信号 ------> 时域/频域映射 -----> 比特分配，量化，编码 ----> 比特流格式
                        ｜                 ｜
                        ｜                 ｜
                        ｜                 ｜
                         --->心理学模型-->  ｜

### 音频编解码器选型

OPUS： 语音通话用的比较多
MP3：音乐
AAC：直播的时候用的比较多
AC3和EAC3：杜比公司方案

## 封装格式
> 也称容器，将已经压缩的视频或者音频流按照一定的方案放到一个文件中，便于播放软件播放。

一般来说 文件的后缀就是它的封装格式。

比如mp4,flv, flv在网络传输的时候就比较流行，但是在本地存储的时候就比较流行用mp4


常见的视频封装格式：
AVI,MKV,MPE,MPG,MPEG,MP4,FLV,WAV,TS。。。。

**H264 + AAC 封装为FLV或者MP4是最为流行的模式**

## 音视频同步
### DTS
> 解码时间戳，这个时间戳的意义在于告诉播放器该在什么时候解码这一帧的数据
### PTS
> 显示时间戳，这个时间戳用来告诉播放器该在什么时候显示这一帧的数据。

### 同步方式

- Audio Master 同步视频到音频
- Video Master 同步音频到视频
- External Clock Master 同步音频和视频到外部时钟

一般 Audio Master > External Clock Master > Video Master


