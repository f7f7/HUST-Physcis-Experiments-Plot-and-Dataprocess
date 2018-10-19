# HUST-Physcis-Experiments-Plot-and-Dataprocess
华中科技大学物理实验（二）画图及数据处理（使用`python`）。  
## 这是什么？
这是一个用`python`处理物理实验数据的仓库，既可以画图，也可以计算，一站式解决。  
## 看下效果  
### 1.偏振与双折射实验：画极坐标图  
![偏振光画极坐标图](https://github.com/LoveThinkinghard/HUST-Physcis-Experiments-Plot-and-Dataprocess/blob/master/%E5%81%8F%E6%8C%AF%E4%B8%8E%E5%8F%8C%E6%8A%98%E5%B0%84/I-%CE%B8%20on%20polor%20axis.png)  
### 2.音叉实验：画图，自动寻找半功率点并计算锐度  
![音叉实验](https://github.com/LoveThinkinghard/HUST-Physcis-Experiments-Plot-and-Dataprocess/blob/master/%E9%9F%B3%E5%8F%89%E5%AE%9E%E9%AA%8C/damped.png)  
### 3.导热系数实验：计算不确定度  
```python
# 计算间接测量量热导系数x的不确定度 Ux，讲义上提到，该实验仪器的温度分辨率为：0.1℃，计时分辨率为：0.1s
def ua(x):
    # 计算A类不确定度
    x_array = np.array(x)
    return np.sqrt(x_array.var()/(x_array.size-1))

def U(ua, delta):
    # 计算直接测量量，需传入A类不确定度，和仪器误差
    # 这里，置信概率p取0.95，查表得
    tp = 2.26
    kp = 1.96
    return np.sqrt((tp*ua)**2+(kp*delta/np.sqrt(3))**2)

# 最后计算间接测量量热导系数x的不确定度 Ux
Ux = k * np.sqrt((U(ua(T_10), 0.1)/T_10.mean())**2+(U(ua(time_2_s), 0.1)/time_2_s.mean())**2)
print('导热系数的不确定度为：{:.5f} W/(m·K)'.format(Ux))
print('置信概率为：0.95')
```
## 谁会需要这个？
此仓库主要是为了帮助那些想要学习使用`python`处理数据与画图的同学，希望我的代码能够帮到你；  
即使你以前没有接触过`python`，也不用担心，因为`python`上手很容易，至少要读懂并不难。  
## 你需要什么？
`Anaconda`是最为推荐的选择（各种数据处理与画图的库都打包好了）；  
或者你使用普通的`python`，不过需要安装几个常用的库`numpy`，`matplotlib`，`scipy`。  
## 如何使用？
使用`jupyter notebook`打开`ipynb`文件；  
或者用其他编辑器（比如spyter）打开`py`文件；
在需要的地方把实验数据改成你自己的（代码注释中有提示），然后一步步运行即可（当然可以用原本的数据先运行看看结果）。  
## 进展与简单介绍
（如果我用了代码处理数据我会把代码上传）  
### 1.电路的暂态过程
柯老师只让手工作图（虽然他要求严格，我还是挺喜欢这位老师的）。  
### 2.音叉实验（2018.9.22）  
1.绘制有无阻尼的图像，寻找半功率点，计算锐度；  
2.绘制T^2-m关系图，计算`k`和`m0`。  
### 3.偏振与双折射（2018.9.28）  
1.绘制I-cos^2(θ)图像；  
2.绘制极坐标图。  
### 4.转动惯量的测量
1.这真是一个简单的实验，也不用作图，会有较多剩余时间；  
2.老师建议上课就把数据处理了，听他的吧。  
### 5.液体的表面张力（2018.10.10）
1.这也是一个要求手工作图的，所以没有代码，也不需要；  
2.里面有个思考题是：为什么拉脱法里U会先增大后减小？我觉得这是一个有趣的问题，网上有一种解释是最大值时是包含了被拉起来的液体的重量的，而减小则是去掉这部分质量的过程。
### 6.导热系数（2018.10.19）
1.绘制升温曲线，冷却曲线；  
2.计算冷却速率，导热系数以及不确定度。  
## 总结
到今天为止，我已经完成了所有物理实验，在我做的实验中只有三个实验需要并可以使用计算机绘图，因此最终这里只有三个实验。  
最后，欢迎大家`fork`，把更多实验添加到这里，包括我没做但需要计算机绘图的实验，当然也包括物理实验（一）。  
## 友情链接
1.物理实验预约以及讲义下载网址：（说起来很蠢，但我还是忍不住提醒你：使用校园网）  
http://210.42.109.72/HustElective/  
2.awesome-hust: （集中了一些适用于华科的资料，小工具等）  
https://github.com/recolic/awesome-hust  
3.recolic的物理实验数据处理套装：（很全，有专门的网页，可以傻瓜式的处理实验数据，但不能画图）  
https://github.com/recolic/phy-exp  
