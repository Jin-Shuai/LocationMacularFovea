# 飞桨常规赛：PALM眼底彩照中黄斑中央凹定位 - 11月第5名方案


## 项目描述
> 题目要求为在一组图片上找到黄斑中心，但是图片的大小不一，每张图片对应的黄斑中心的取值范围也随着图片大小的变化而变化，从而缺乏一个统一的标准。

## 项目结构
>   指定缩放尺寸，将所有的图片均缩放到指定尺寸。对于中心点坐标，将所有的中心点坐标转化为中心点在xy轴的百分比位置，如目标点在最中间则认为横纵分别为0.5。最后再将预测后的小数还原为整数即可得到真实图片上的像素点坐标。
```
（本程序没有实现异步读取，直接做了最基础的读数据，运行。最后会在./work/Fovea_Localization_Results.csv中保存测试结果。）
  1. 依次读取训练图片，将图片转为灰度模式，将图片缩放到指定尺寸，将黄斑中心转化到[0,1]。直接使用dataframe记录图片信息和黄斑中心分别作为输入和输出。
  2. 构造神经网络，这部分直接参考0基础入门的示例中的识别手写数字。[https://www.paddlepaddle.org.cn/tutorials/projectdetail/2182025]
  3. 训练数据，将之前保存过的dataframe转化为tensor直接训练即可，本程序将xy坐标分开进行训练。
  4. 依次读取测试图片，将图片转为灰度模式，将图片缩放到指定尺寸。直接使用dataframe记录图片信息和原始图片尺寸，原始图片尺寸用于将预测结果转化为真实坐标。
  5. 预测，并将预测后的值转化到真实坐标上
```
## 使用方式
> 如何快速上手这个项目：
在AI Studio上[运行本项目](https://aistudio.baidu.com/aistudio/projectdetail/3144970?contributionType=1)  

