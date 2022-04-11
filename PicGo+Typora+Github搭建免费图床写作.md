# PicGo+Typora+Github搭建免费图床写作

## 配置Github

1. 新建一个GitHub仓库，名字自定义

2. 生成token：

   

   直接看图

   ![image-20220411200757623](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204112111587.png)

   ![202204112017710](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204112113704.png)

![image-20220411211218796](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204112112896.png)

最后点击`Generate token`即可看到显示的token页面，它只会显示一次，**关闭页面**后再打开这个页面就**不会显示**了。复制token值粘贴到文本文档中，先保存下来，后面配置PicGo要用到。



## 配置PicGo

1. 首先下载安装PicGo，图片上传工具PicGo下载地址：https://github.com/Molunerfinn/PicGo/releases

2. 下载完成后进行安装，安装完毕后开始配置

   ![image-20220411211157745](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204112111798.png)

- 设定仓库名：这个是刚刚第一步所新建仓库的名称，我的为Yafine-imgs，此处填写格式username/repo。
- 设定分支名：master，采用默认分支即可
- 设定Token：此处填写上一步得到的Token，添加到输入框即可。
- 指定存储路径：自定义，例：images/，相当于在刚刚新建的仓库下新建了一个文件夹。
- 设定自定义域名：格式：`https://cdn.jsdelivr.net/gh/username/repo`，`username`为GitHub用户名，`repo`为新建的仓库，用于存储图片

## 配置Typora

1. 点击偏好设置,选择图像
2. 按照下图所配置
3. 点击验证图片上传,测试是否成功

![image-20220411210221653](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204112102768.png)

![image-20220411211146769](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204112111884.png)