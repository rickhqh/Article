## matplotlib

- Matplotlib是一个Python 2D绘图库，它可以在各种平台上以各种硬拷贝格式和交互式环境生成出具有
出版品质的图形。 Matplotlib可用于Python脚本，Python和IPython shell，Jupyter笔记本，Web应用
程序服务器和四个图形用户界面工具包。
Matplotlib试图让简单的事情变得更简单，让无法实现的事情变得可能实现。 只需几行代码即可生成绘
图，直方图，功率谱，条形图，错误图，散点图等。
为了简单绘图，pyplot模块提供了类似于MATLAB的界面，特别是与IPython结合使用时。 对于高级用
户，您可以通过面向对象的界面或MATLAB用户熟悉的一组函数完全控制线条样式，字体属性，轴属性
等。

![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182318708.png)


```python
import matplotlib.pyplot as plt
# 在jupyter中执行的时候显示图片 
#%matplotlib inline 
# 传入x和y, 通过plot画图 
plt.plot([1, 0, 9], [4, 5, 6]) 
# 在执行程序的时候展示图形 
plt.show()
```


​    
![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182318881.png)
​    


![3.png](attachment:3.png)

## 折线图


```python
from matplotlib import pyplot as plt 
x = range(1,8) 
# for i in x :
#   print(i)
# x轴的位置 
y = [17, 17, 18, 15, 11, 11, 13] 
# 传入x和y, 通过plot画折线图 
plt.plot(x,y,color='red',alpha=0.5,linestyle='--',linewidth=3) 
plt.show()
# show已经销毁
plt.plot(x,y,marker='o') 
plt.show()
```


![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182318355.png)
    




![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182318593.png)
    


### 基础属性设置 
    color='red' : 折线的颜色 
    alpha=0.5 : 折线的透明度(0-1)
    linestyle='--' : 折线的样式 
    linewidth=3 : 折线的宽度 
### 线的样式 
  - 实线(solid) 
  - 短线(dashed) 
  - 短点相间线(dashdot) 
  - 虚点线(dotted)

### 设置图片的大小 
  - figsize:指定figure的宽和高，单位为英寸； 
  - dpi参数指定绘图对象的分辨率，即每英寸多少个像素，缺省值为80 1英寸等于2.5cm,A4纸是 21*30cm的纸张
  - plt.savefig('./t1.png')


```python
import matplotlib.pyplot as plt
import random
x=range(2,26,2)
y=[random.randint(15,30) for i in x]

#图片大小 与分辨率设置
plt.figure(figsize=(20,8),dpi=100)

#画
plt.plot(x,y,marker='o')
# 保存
# plt.savefig('./t1.png')
plt.show()
```


![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182318428.png)
    


## 绘制刻度
  - 设置x轴的刻度 # plt.xticks(x) # plt.xticks(range(1,25)) 
  - 设置y轴的刻度 # plt.yticks(y) # plt.yticks(range(min(y),max(y)+1)) 
  - 构造x轴刻度标签 
  - x_ticks_label = ["{}:00".format(i) for i in x] 
  - rotation = 45 让字旋转45度 
  - plt.xticks(x,x_ticks_label,rotation = 45) 
  - 设置y轴的刻度标签 
  - y_ticks_label = ["{}℃".format(i) for i in range(min(y),max(y)+1)]    
  
  - plt.yticks(range(min(y),max(y)+1),y_ticks_label)


```python
x=range(2,26,2)
y=[random.randint(15,30) for i in x]

#图片大小 与分辨率设置
plt.figure(figsize=(20,8),dpi=100)

x_ticks_label = ["{}:00".format(i) for i in x] 
y_ticks_label = ["{}℃".format(i) for i in y] 
plt.xticks(x,x_ticks_label)# 第一个是刻度数量 第二个是 刻度的值
plt.yticks(y,y_ticks_label)
#画
plt.plot(x,y,marker='o')
# 保存
# plt.savefig('./t1.png')
plt.show()
```


​    
![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182318358.png)
​    


## 设置中文
  - 查看Windows下的字体：“C:\Windows\Fonts” 可以自己下载字体文件（xxx.ttf），然后双击安装即可 
  -  my_font = font_manager.FontProperties(fname='C:\WINDOWS\Fonts\STXINWEI.TTF',size=18) 
  - plt.ylabel("天气",fontproperties=my_font)


```python

```


```python
from matplotlib import pyplot as plt 
import matplotlib 
import random 
from matplotlib import font_manager 
my_font = font_manager.FontProperties(fname='C:\WINDOWS\Fonts\STXINWEI.TTF',size=18) 
x = range(0,20) 
y = [random.randint(10,30) for i in x]
plt.figure(figsize=(20,8),dpi=80) 
x_ticks_label = ["{}点".format(i) for i in x] 
y_ticks_label = ["{}度".format(i) for i in y] 
plt.xticks(x,x_ticks_label,fontproperties=my_font)# 第一个是刻度数量 第二个是 刻度的值 第三个 字体
plt.yticks(y,y_ticks_label,fontproperties=my_font)
plt.plot(x,y)

# 设置标题
plt.xlabel('时间',rotation=45,fontproperties=my_font) #旋转
plt.ylabel("次数",fontproperties=my_font)

#设置标题 
plt.title('每分钟跳动次数',fontproperties=my_font,color='red') 
plt.show()
```


​    
![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182318211.png)
​    


## 一图多线
### 绘制网格gird(网格)（网格也是可以设置线的样式)
  - alpha=0.4 设置透明度
  - plt.grid(alpha=0.4)

###  添加图例legnd(刻印文字) :
  - (注意：只有在这里需要添加prop参数是显示中文，其他的都用fontproperties) 
  - upper left、 lower left、 center left、 upper center
  - plt.legend(prop=my_font,loc='upper right')


```python
# 假设大家在30岁的时候，根据自己的实际情况，统计出来你和你同事各自从11岁到30岁每年交的男/女朋友 的数量如列表y1和y2，请在一个图中绘制出该数据的折线图，从而分析每年交朋友的数量走势。 
y1 = [1,0,1,1,2,4,3,4,4,5,6,5,4,3,3,1,1,1,1,1] 
y2 = [1,0,3,1,2,2,3,4,3,2,1,2,1,1,1,1,1,1,1,1] 
x = range(11,31) 
# 设置图形 
plt.figure(figsize=(20,8),dpi=80) 

plt.plot(x,y1,color='red',label='自己') 
plt.plot(x,y2,color='blue',label='同事') 
# 设置x轴刻度 
xtick_labels = ['{}岁'.format(i) for i in x] 
my_font = font_manager.FontProperties(fname='C:\WINDOWS\Fonts\STXINWEI.TTF',size=18) 
plt.xticks(x,xtick_labels,fontproperties=my_font,rotation=45) 
# 绘制网格（网格也是可以设置线的样式) alpha=0.4 设置透明度 
plt.grid(alpha=0.4) 
# 添加图例(注意：只有在这里需要添加prop参数是显示中文，其他的都用fontproperties) 

#设置位置loc : upper left、 lower left、 center left、 upper center 
plt.legend(prop=my_font,loc='upper right') 
#展示 
plt.show()
```


​    
![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182318248.png)
​    


## 使用scatter(散射)绘制散点图
  - plt.scatter(x,y,label= '3月份')


```python
'''题干
3月份每天最高气温a =
[11,17,16,11,12,11,12,6,6,7,8,9,12,15,14,17,18,21,16,17,20,14,15,15,15,19,21,22,
22,22,23]
'''
from matplotlib import pyplot as plt 
from matplotlib import font_manager 
y =[11,17,16,11,12,11,12,6,6,7,8,9,12,15,14,17,18,21,16,17,20,14,15,15,15,19,21,22,
22,22,23]
x = range(1,32)

# 设置图形大小
plt.figure(figsize=(20,8),dpi=80) 
# 使用scatter绘制散点图
plt.scatter(x,y,label= '3月份')
# plt.plot(x,y,label= '3月份')

# 调整x轴的刻度
my_font = font_manager.FontProperties(fname='C:\WINDOWS\Fonts\STXINWEI.TTF',size=10)

_xticks_labels = ['3月{}日'.format(i) for i in x]

plt.xticks(x[::3],_xticks_labels[::3],fontproperties=my_font,rotation=45) 
plt.xlabel('日期',fontproperties=my_font)
plt.ylabel('温度',fontproperties=my_font)

# 图例
plt.legend(prop=my_font) 
plt.show()
```


![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182319174.png)
    


##  条形图


```python
a = ['流浪地球','疯狂的外星人','飞驰人生','大黄蜂','熊出没·原始时代','新喜剧之王']
b = ['38.13','19.85','14.89','11.36','6.47','5.93']
print(b)
my_font = font_manager.FontProperties(fname='C:\WINDOWS\Fonts\STXINWEI.TTF',size=10)

plt.figure(figsize=(20,8),dpi=80)
rects=plt.bar(range(len(a)),b,width=0.3,color='red')
print(rects)
plt.xticks(range(len(a)),a,fontproperties=my_font)
# plt.yticks(range(len(b)),b,fontproperties=my_font)
plt.yticks(range(len(b)),b) 
for rect in rects:
    height = rect.get_height()
    plt.text(rect.get_x() + rect.get_width() / 2, height+0.3, str(height),ha="center")
plt.show()
```

    ['38.13', '19.85', '14.89', '11.36', '6.47', '5.93']
    <BarContainer object of 6 artists>




![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182319969.png)
    



```python
from matplotlib import pyplot as plt 
from matplotlib import font_manager
a = ['流浪地球','疯狂的外星人','飞驰人生','大黄蜂','熊出没·原始时代','新喜剧之王']
b = ['38.13','19.85','14.89','11.36','6.47','5.93']
# b =[38.13,19.85,14.89,11.36,6.47,5.93]


my_font = font_manager.FontProperties(fname='C:\WINDOWS\Fonts\STXINWEI.TTF',size=10)

plt.figure(figsize=(20,8),dpi=80)

# 绘制条形图
rects = plt.bar(range(len(a)),[float(i) for i in b],width=0.3,color='red')
plt.xticks(range(len(a)),a,fontproperties=my_font)
plt.yticks(range(0,41,5),range(0,41,5)) # 在条形图上加标注(水平居中)
for rect in rects:
    height = rect.get_height()
    plt.text(rect.get_x() + rect.get_width() / 2, height+0.3, str(height),ha="center")
plt.show()
```


![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182319476.png)
    


## 直方图



```python
time = [131,	98, 125, 131, 124, 139, 131, 117, 128, 108, 135, 138, 131, 102,
107, 114,
119, 128, 121, 142, 127, 130, 124, 101, 110, 116, 117, 110, 128, 128,
115,99,136, 126, 134,95, 138, 117, 111,78, 132, 124, 113, 150, 110, 117,86,
95, 144,
105, 126, 130,126, 130, 126, 116, 123, 106, 112, 138, 123,86, 101,
99, 136,123,
117, 119, 105, 137, 123, 128, 125, 104, 109, 134, 125, 127,105, 120,
107, 129, 116,
108, 132, 103, 136, 118, 102, 120, 114,105, 115, 132, 145, 119, 121,
112, 139, 125,
138, 109, 132, 134,156, 106, 117, 127, 144, 139, 139, 119, 140,83,
110, 102,123,
107, 143, 115, 136, 118, 139, 123, 112, 118, 125, 109, 119, 133,112,
114, 122, 109,
106, 123, 116, 131, 127, 115, 118, 112, 135,115, 146, 137, 116, 103,
144,83, 123,
111, 110, 111, 100, 154,136, 100, 118, 119, 133, 134, 106, 129, 126,
110, 111, 109,
141,120, 117, 106, 149, 122, 122, 110, 118, 127, 121, 114, 125, 126,114,
140, 103,
130, 141, 117, 106, 114, 121, 114, 133, 137,92,121, 112, 146,97,
137, 105,98,
117, 112,81,97, 139, 113,134, 106, 144, 110, 137, 137, 111, 104,
117, 100, 111,
101, 110,105, 129, 137, 112, 120, 113, 133, 112,83,94, 146, 133,
101,131, 116,
111,84, 137, 115, 122, 106, 144, 109, 123, 116, 111,111, 133, 150]
my_font = font_manager.FontProperties(fname='C:\WINDOWS\Fonts\STXINWEI.TTF',size=10)   
# 2）创建画布
plt.figure(figsize=(20, 8), dpi=100)

# 3）绘制直方图
# 设置组距
distance = 2 
# 计算组数
group_num = int((max(time) - min(time)) / distance) 
# 绘制直方图
plt.hist(time, bins=group_num)

# 修改x轴刻度显示
plt.xticks(range(min(time), max(time))[::2])

# 添加网格显示
plt.grid(linestyle="-", alpha=0.5)

# 添加x, y轴描述信息
plt.xlabel("电影时长大小",fontproperties=my_font) 
plt.ylabel("电影的数据量",fontproperties=my_font)

# 4）显示图像
plt.show()
```


​    
![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182319714.png)
​    


## 饼状图


```python
import matplotlib.pyplot as plt 
import matplotlib
from matplotlib import font_manager 
my_font =font_manager.FontProperties(fname='C:\WINDOWS\Fonts\STXINWEI.TTF',size=10)

label_list = ["第一部分", "第二部分", "第三部分"]	# 各部分标签
size = [55, 35, 10]	# 各部分大小
color = ["red", "green", "blue"]	# 各部分颜色
explode = [0, 0.05, 0]	# 各部分突出值
"""
绘制饼图
explode：设置各部分突出label:设置各部分标签
labeldistance:设置标签文本距圆心位置，1.1表示1.1倍半径
autopct：设置圆里面文本
shadow：设置是否有阴影
startangle：起始角度，默认从0开始逆时针转pctdistance：设置圆内文本距圆心距离
返回值:
patches : matplotlib.patches.Wedge列表(扇形实例) 
l_text：label matplotlib.text.Text列表(标签实例) 
p_text：label matplotlib.text.Text列表(百分比标签实例) """
plt.figure(figsize=(20, 8), dpi=100) 
patches, l_text, p_text = plt.pie(size,
                                  explode=explode,
                                  colors=color,
                                  labels=label_list, 
                                  labeldistance=1.1, 
                                  autopct="%1.1f%%", 
                                  shadow=False, 
                                  startangle=90, 
                                  pctdistance=0.6)

for t in l_text: 
#     print(dir(t))
    t.set_fontproperties(my_font)
for t in p_text:
    t.set_size(18)

for i in patches: 
    i.set_color('pink') 
    break

plt.legend(prop=my_font)

plt.show()
```


​    
![png](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204182319963.png)
​    

