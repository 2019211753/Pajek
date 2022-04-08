# Pajek和txtPajek
安装包，侵删

**最近要做复杂网络的链路预测，需要重新划分训练集和测试集，于是先检查了一下图是不是连通的等等。但是在全网都没找到对应版本的说明书。把我的使用心得记载在这里，希望能对新朋友有所帮助。**



## txt2pajek

### 下载路径
[txt2Pajek](https://github.com/2019211753/txt2Pajek "txt2Pajek")  

**因为在github上没有找到txtPajek文件，所以在这里分享到我的仓库里，如有侵权，请告知删除。**

### 用途
我们正常情况下的连线文件都是txt格式的，但是如果想用Pajek的话就要转成.net格式。

### 用法
![](https://github.com/2019211753/photos/blob/main/image.png?raw=true)  

input File 为想转换的txt文件，依照每列之间的间隔符号：""（空格对应的是blank）、"tab"....选择。然后在1st column选择第一列对应的数值、2st同理。再然后如果是简单无向图，选择1-mode network→undirected（*Edges)。最后点击Create Pajek File即可。  
如果间隔符选择正确，Preview处会显示如_________1.0000000e+00_________3.5530000e+03这种格式。  

使用手册：[http://www.pfeffer.at/txt2pajek/txt2pajek.pdf](http://www.pfeffer.at/txt2pajek/txt2pajek.pdf)

## Pajek

### 下载路径
[Pajek](http://mrvar.fdv.uni-lj.si/pajek/ "Pajek")

### 用途
我用的也不是很明白，因为官网的版本和现有的所有说明书都已经脱节了。我用的也不过是皮毛，这里只是说明如何得到最大连通子图的结点数等等。

### 用法

#### 读取网络并作图
File→Network→Read读取.net文件。第一行最右边的Draw→Network→（弹窗)Layout→Energy→Kamada-kawai→Free可以做出还凑合的图，这个图是NetWorks的图。  

其实作图功能完全可以交给matlab，游离在外的节点会很显眼...  

#### 划分网络点集
Network→Create Patition→Component→Weak/Strong。关于强连通图和弱连通图在此就不做解释了。如果是连通图，partition只会有一个编号。有几个分离的部分就有几个编号。（comp=?）  

#### 根据网络点集提取连通图
关键：提取最大连通图  
首先和上面一样，分别提取出有几部分点集。然后根据patition提取Cluster。  
Partition→Make Cluster→Vertices from selected Cluster  
接着Operations→Partition+Cluster 提取对应的连通点集  

或者：提取完  partition 直接 Operations→Network+Partition→Extract→SubNetwork Induced By Union Of selected Clusters  
输入为你想提取的点集对应编号。然后保存Partition处的新文件就行了。


使用手册：
[https://wenku.baidu.com/view/e368760e52ea551810a68773.html](https://wenku.baidu.com/view/e368760e52ea551810a68773.html "https://wenku.baidu.com/view/e368760e52ea551810a68773.html")
