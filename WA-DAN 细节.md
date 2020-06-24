 <center> WS-DAN 论文细节 
 </center>



![image-20200624184459533](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20200624184459533.png)

输入图片

使用注意力进行数据增强 包括attention crop 和attentiondrop ，原图和增强数据都会传入

生成特征图

通过卷积生成特征图

使用bap提取特征

![img](https://davidocea.github.io/images/posts/WS-DAN/fingure3.png)

BAP(Bilinear Attention Pooling)的过程：首先通过网络的主干（如resnet18）部分分别得到特征图（a）和注意力图（b）。每一个注意力图都代表了目标的特定部分。通过对注意力图和特征图的元素点乘得到各个分部特征图，让后利用卷积或者池化处理分部特征图，最后将各个分部特征图结合得到特征矩阵。

![img](https://davidocea.github.io/images/posts/WS-DAN/f4.png)

![img](https://davidocea.github.io/images/posts/WS-DAN/f4-b.png)

![image-20200624184521020](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20200624184521020.png)

数据集细节

CUB-200-2011  



```
类别数： 200

图片数量： 11,788

每个图像的批注： 15个零件位置，312个二进制属性，1个边界框
图像包含在目录images /中，具有200个子目录（每个鸟类一个）

-------图像文件列表（images.txt）------ 
图像列表文件名包含在文件images.txt中，每一行对应一个图像：

<image_id> <image_name> 

-------训练/测试拆分（train_test_split.txt）------ 
建训练/测试拆分包含在文件中train_test_split.txt，每行对应一个图像：

<image_id> <is_training_image> 

其中<image_id>对应于images.txt中的ID，并且<is_training_image>的值1或0分别表示文件位于训练或测试集中。

----------类名列表（classes.txt）------ 
类名列表（鸟类）包含在文件classes.txt中，每一行对应一个类别：

<class_id> <class_name> 
------------------------------------------ - 


------- Image类标签（image_class_labels.txt）------ 
真实类别标签（鸟类标记）针对每个图像都包含在文件image_class_labels.txt，以相应于每行一幅图片：

<image_id> <class_id> 

其中<image_id>和<class_id>分别对应于images.txt和classes.txt中的ID。
```

FGVC-Aircraft

```
数据集包含10,200架飞机的图像，其中102种不同飞机模型变体中的每一种都具有100张图像，其中大多数是飞机。
训练图片data/images_train.txt
交叉验证及测试 data/images_val.txt data/images_test.txt
data/images_variant_train.txt，data/images_family_train.txt data/images_manufacturer_train.txt包含带有型号型号，系列和制造商名称的训练图像列表
data/images_box.txt包含飞机边界框
```

Stanford Cars

```
该汽车数据集包含196类汽车的16185个图像。数据被分为8,144个训练图像和8,041个测试图像，其中每个类别已大致分为50-50个分割。
```

standford dogs dataset

```
类别数：120图像数：20,580注释：类标签，边框
```

