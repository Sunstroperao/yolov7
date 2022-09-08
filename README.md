# yolov7——使用yolov7训练自己的数据集并进行推理

## 1.配置环境（遇到问题可查阅网上攻略）

```python
//创建虚拟环境并激活
# conda create -n your_env_name
# conda activate your_env_name
// 安装依赖的包
# cd 到requirements.txt文件夹所在的目录下
# pip install -r requirements.txt
```

**配置好环境好可直接运行detect.py，若可以跑通可以进行下一步**

![](/home/jh/图片/截图/1.png)



## 2.数据集转转换：voc格式数据集转换成yolo格式

**1.将自己的数据集保存到VOCdevkit/VOC2007文件夹下面，voc数据集格式如下(其中ImageSets非必需)**

![](/home/jh/图片/截图/2.png)

**2.数据集保存好之后运行代码voc_to_yolo.py,运行之前需要修改一下classes的值（根据自己的数据集进行修改），我这里用于检测人头，所以只设置了一个类别**

![](/home/jh/图片/截图/3.png)

​		**运行之后得VOCdevkit文件夹变成如下形式：**

![](/home/jh/图片/截图/4.png)

​	**此时数据集转换完毕，可以用来训练模型。**

## 3.修改配置文件

**1.首先修改cfg/training/yolov7.yaml,类别的数目设置成自己数据集的类别数目**

![](/home/jh/图片/截图/5.png)

**2.然后在data文件下面设置自己的yaml文件，修改训练数据集和测试数据集的路径（修改成VOCdevkit文件下训练和测试数据集的路径），以及类别和类别数目**

![](/home/jh/图片/截图/6.png)

## 4.开始训练网络

**训练之前可以修改一下参数，data改成上一步创建的yaml文件，我这里是head.yaml;训练周期epoch可以根据自己的需求进行设置，batch-size也可以根据自己的电脑配置进行修改，原模型是16,我这里改成了2，设置完成之后右键run运行即可**

![image-20220908175012742](/home/jh/.config/Typora/typora-user-images/image-20220908175012742.png)

**训练完成之后，runs文件下会多处一个train文件夹保存训练好的权重，best.qt代表效果最好的权重**

![image-20220908175412112](/home/jh/.config/Typora/typora-user-images/image-20220908175412112.png)

## 5.推理

### 加载训练好的权重进行推理

**修改detect.py里面的参数，加载自己训练好的权重，同时把需要检测的图片或者视频文件放在inference/images文件下，右键run运行**

![image-20220908180015247](/home/jh/.config/Typora/typora-user-images/image-20220908180015247.png)

![image-20220908180037713](/home/jh/.config/Typora/typora-user-images/image-20220908180037713.png)

**运行结束之后runs/detect文件夹下查看检测效果**

