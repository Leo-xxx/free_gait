## Github项目推荐 | 腿式机器人通用控制架构 Free Gait

AI研习社 [AI研习社](javascript:void(0);) *昨天*

![img](https://mmbiz.qpic.cn/mmbiz_jpg/bicdMLzImlibRiboYcgtAAFwZvvLPUlRkFmiaQ8aCfWBsYib2ic7uVBLAHBtL8m8gYWxDLRdVWaAoASYXjjYclph6NlQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**Free Gait - An Architecture for the Versatile Control of Legged Robots**

by **leggedrobotics**

![1559027740526274.gif](https://mmbiz.qpic.cn/mmbiz_gif/bicdMLzImlibTIgsibcjva9LYiaCXoXk4eOPibY7dLhW2WPV3MVo5TSDTPSibBsB80N23MTpWEZzJ8sFBB9JcZloXqTQ/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

*Free Gait* 是一个软件框架，它可以用来对腿式机器人进行多功能、强大且面向任务的控制。Free Gait 的界面定义了一个全身抽象层，以适应各种任务 - 空间控制命令，如末端执行器，关节和基础运动。使用全身反馈控制器跟踪定义的运动任务，以确保即使在滑动和外部干扰下也能实现准确且稳健的运动执行。Free Gait 框架的应用包括机器人的直观远程操作、行为的高效脚本化以及运动和步态规划功能的完全自主操作。

注：源代码根据 BSD 3-Clause license 发布。

作者：PéterFankhauser

维护者：PéterFankhauser，pfankhauser @anybotics.com

贡献者：Samuel Bachmann，Dario Bellicoso，Thomas Bi，Remo Diethelm，Christian Gehring

隶属：ANYbotics

本项目最初是在苏黎世联邦理工学院RSL开发的。

## Github项目地址：

**https://github.com/leggedrobotics/free_gait**



## **文章引用**

如果你在学术范畴内使用本项目，请引用以下文章：

- Fankhauser, D. Bellicoso, C. Gehring, R. Dubé, A. Gawel, M. Hutter, "Free Gait – An Architecture for the Versatile Control of Legged Robots", in IEEE-RAS International Conference on Humanoid Robots, 2016. (PDF)

- 
- 
- 
- 
- 
- 

```
  @inproceedings{Fankhauser2016FreeGait,      author = {Fankhauser, P{\'{e}}ter and Bellicoso, C. Dario and Gehring, Christian and Dub{\'{e}}, Renaud and Gawel, Abel and Hutter, Marco},      booktitle = {IEEE-RAS International Conference on Humanoid Robots},      title = {{Free Gait – An Architecture for the Versatile Control of Legged Robots}},      year = {2016},  }
```



## **单元测试**

- 

```
catkin build free_gait_core --no-deps --verbose --catkin-make-args run_tests
```



## **简介**

视频展示了Free Gait的一些应用，点击查看（YouTube）。

| ![1559028065377232.png](https://mmbiz.qpic.cn/mmbiz_png/bicdMLzImlibTIgsibcjva9LYiaCXoXk4eOP4wo4vjRprl4oktYzWsb84sBMiaUOT2nUTicLeR5ES8txia0eIEte3zUdw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1) | ![1559028082343120.jpg](https://mmbiz.qpic.cn/mmbiz_jpg/bicdMLzImlibTIgsibcjva9LYiaCXoXk4eOPWNWOLJoI137JHFzcNxZMXzXghNddIQIhsgiaDDicicnwANBtLlcF1Sictw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1) | ![1559028097724117.png](https://mmbiz.qpic.cn/mmbiz_png/bicdMLzImlibTIgsibcjva9LYiaCXoXk4eOPhia9HT9GTmI9UA5rJuVIao7BJNE3Axxx1dibwS77K7ibToqm1kMJNzYGg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1) |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 运动基于（可能是多个）腿部运动和每个命令的基本运动（步骤）的组合。 | 命令结构允许以各种方式控制有腿机器人。                       | 通过Free Gait API命令运动目标到全身运动控制器。              |



## **使用**

视频概述了Free Gait 中提供的工具，点击查看（Youtube）。

### **Free Gait 的动作**

Free Gait的动作是使用Free Gait API（针对ROS）定义动作的库和脚本。对于ROS，可以使用 free_gait_msgs 中的消息和操作定义，使用ROS客户端库以任何语言编写这些操作。对于C ++，Free Gait提供了 free_gait_core库来处理动作的定义，而 free_gait_ros 则用于连接ROS。如果使用Python，请使用 free_gait_python 库。对于简单的动作定义，Free Gait支持以YAML格式定义的动作。有关使用YAML操作的更多信息，可查看YAML脚本接口。

Free Gait 命令表示为腿（在关节或末端执行器的笛卡尔空间中）和基础运动的组合，其具有位置，速度和/或力/扭矩目标或轨迹的定义。

![img](https://mmbiz.qpic.cn/mmbiz_png/bicdMLzImlibTIgsibcjva9LYiaCXoXk4eOPLZ7Ox5zUebhb5DBW55HNw76oiaanUPpQ8QWZb89FEP3JAaBT19tlPQw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

Free Gait 的操作可以手动启动，也可以在 free_gait_action_loader 的帮助下启动。

### **Free Gait 动作加载器**

free_gait_action_loader允许通过ROS服务或ROS操作启动操作。 目前，动作加载器支持YAML动作定义，Python脚本，以及为C ++和其他库启动ROS启动文件。

运行free_gait_action_loader

- 

```
rosrun free_gait_action_loader action_loader.py
```

free_gait_action_loader 管理操作并确保此时只有一个操作正在运行。如果要使用free_gait_action_loader注册一个动作，必须将动作加载为ROS插件。

### **RQT Free Gait 动作**

rqt_free_gait_action包为free_gait_action_loader提供了一个rqt用户界面。界面显示在集合中组织的操作，并允许预览和发送操作。 此外，集合可以作为一系列操作运行，通过右键单击，可以选择一个集合作为收藏。 收藏夹显示为顶部的按钮，以便快速访问。

![1559028878921698.gif](https://mmbiz.qpic.cn/mmbiz_gif/bicdMLzImlibTIgsibcjva9LYiaCXoXk4eOPXqcAMkoiaJic5CkCPg4cHR1IueobfYT63ojPgoic78YfiaMLGHXGeZA4Ag/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

### **RQT Free Gait 监视器**

一旦Free Gait动作服务器执行了动作，rqt_free_gait_monitor就会显示动作的执行进度，并允许暂停和停止活动中的动作。

![1559028923455769.gif](https://mmbiz.qpic.cn/mmbiz_gif/bicdMLzImlibTIgsibcjva9LYiaCXoXk4eOP3SW2LH6NJpgBKKXNKSjCJyqfFsn145cKzVwUFPH0yXy1fhfxF5gbtw/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

### **Free Gait RViz 插件**

可以使用 free_gait_rviz_plugin预览动作。 它将获取机器人的当前状态，并根据定义的动作对运动可视化。 RViz 插件允许擦洗时间并且可视化立足点、轨迹、支持多边形等。

![1559029029282290.gif](https://mmbiz.qpic.cn/mmbiz_gif/bicdMLzImlibTIgsibcjva9LYiaCXoXk4eOPF3CRJ7JsWzfR1pGQFs2lVLeSKvQs9OEVuTwJHRUpHGNAFBYnEJOe5Q/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

### **YAML脚本界面**

对于简单的运动序列，可以将Free Gait动作定义为YAML定义序列。

例如，这个动作将抬起机器人的右前腿：

![1559029063541017.gif](https://mmbiz.qpic.cn/mmbiz_gif/bicdMLzImlibTIgsibcjva9LYiaCXoXk4eOP8zHfLk22kQwVMkIqdcCkFZStuuicdEKbNxichk7KrGbWIkL8I5hQFuCA/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

- 
- 
- 
- 
- 
- 
- 
- 
- 
- 
- 
- 
- 
- 
- 
- 

```
adapt_coordinates: - transform:    source_frame: footprint    target_frame: odom
steps: - step:   - base_auto: - step:   - base_auto:   - end_effector_target:      name: RF_LEG      ignore_contact: true      target_position:       frame: footprint       position: [0.39, -0.22, 0.20]
```

adapt_coordinates命令将source_frame中所定义的运动转换为target_frame。



## **FAQ**

### **找不到动作怎么办？**

如果未能找到/加载Free Gait动作，那么以下服务的调用将返回空值：

- 

```
rosservice call /free_gait_action_loader/list_actions "collection_id: ''"
```

在这种情况下，可以尝试使用以下命令初始化rosdep：

- 
- 

```
sudo rosdep initrosdep update
```

**2019 全球人工智能与机器人峰会**



由中国计算机学会主办、雷锋网和香港中文大学（深圳）联合承办的 2019 全球人工智能与机器人峰会（ CCF-GAIR 2019），将于 **2019 年 7 月 12 日至 14 日**在深圳举行。

**届时，诺贝尔奖得主JamesJ. Heckman、中外院士、世界顶会主席、知名Fellow，多位重磅嘉宾将亲自坐阵**，一起探讨人工智能和机器人领域学、产、投等复杂的生存态势。

![gair海报.jpg](https://mmbiz.qpic.cn/mmbiz_jpg/bicdMLzImlibTIgsibcjva9LYiaCXoXk4eOPmLDgH4Dr4pR43opfVP5ABqC42sV76DxPooibC4oBkNj96fs27TRFQDA/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![img](https://mmbiz.qpic.cn/mmbiz_gif/bicdMLzImlibRAS3Tao2nfeJk00qqxX3axIgPV3yia4NPESGdUJEM9vsfw1O4Dg1iat7lVNAmbCMY65ia2pzfBXm5kg/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1) 点击 **阅读原文** ，进技术交流小组查看更多Github项目推荐

[阅读原文](https://mp.weixin.qq.com/s?__biz=MjM5ODU3OTIyOA==&mid=2650676888&idx=4&sn=4b1efcffa4d3569dc31fc9aebd6cf16c&chksm=bec223eb89b5aafdebdb334df38baebdec4ff6de2fd6c0e3a0be58b27a15744ffcffc92e145a&mpshare=1&scene=1&srcid=0606LITEVnC7aJfNQU1TNFZ8&key=90581f21d61583cc9e88afef43fc0734f76593531f61336f48ba08829ba266e64b53c55f96e693f50784908e480ec0734706ec1b54c2667ba803e32fee3e78588119698e433394f54a955b15232d108d&ascene=1&uin=MjMzNDA2ODYyNQ%3D%3D&devicetype=Windows+10&version=62060833&lang=zh_CN&pass_ticket=j1uTOp9D07FsfGFhPHh28YNCJ%2FyHSoU6yZwOcgzUfvz0aEZLkGZyC5AWXxX7pG28##)







微信扫一扫
关注该公众号