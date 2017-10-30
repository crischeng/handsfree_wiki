## 机器人入门

#### 概述

- 机器人是一个复杂系统，对理论和工程知识的要求综合度是非常高的，如果你没有足够的激情，不断学习的心态，独立解决困难的决心，建议你还是不要入这个神坑。
- 即使你有上述的基本素质，机器人也不是想玩就能玩的，至少不是你有钱买个平台你就有能力玩起来的， 虽然我自己也很菜， 但是我还是得给新手指指方向。我觉得如果你能满足以下条件再开始你的HandsFree开发之旅会比较好一点。
  - 编程功底要够好
 编程就和学英语一样，需要你在平时的科研进程中不断学习和练习，没有最强只有更强，不懂计算机语言永远别想踏进IT世界，而然编程语言多如牛毛，不同领域的软件工程师有不同的选择，也很难划定界限。如果你以后要搞机器人系统，机器学习，计算机视觉 ，我建议要掌握好C++ 和 python ， 特别是如果你是走工程路线的话，那么C++一定要非常好，这也是学ROS HandsFree 必过的一关。具体可以参考**C++学习规划**。
  - 对机器人的整体系统有一定的了解
虽然你可能只是一个 SLAM，计算机视觉，机器学习等局部问题的研究者，但是如果你要玩整机那就得对整体系统，从机械结构到机器人学，电路，嵌入式等有一些最基本的了解。这本书可以帮你入门，请确保你可以看懂：
自主移动机器人导论 （美）西格沃特（Siegwart,R.），（美）诺巴克什（Nourbakhsh,I.R.）		
  - 学习ROS
ROS 可能是大部分人入门的工具，请你在有一定基本了解的前提下再买我们的平台，否则你可能会失望，除非你懂机器人且不用 ROS 来构建你的机器人系统。ROS学习请参考 **ROS 学习规划**

#### C++学习规划
1. 最基本的是要能看懂 stephen prata 的《C++ Primer Plus》 ，另外《C++ 标准程序库》可供参考，相关资料可以参考HandsFree 百度云提供的[编程学习资料](https://pan.baidu.com/s/1nuSvs7Z#list/path=%2FHANDSFREE%2FHands_Free_Release%2F5_Learning_Data%2Fprograming&parentPath=%2FHANDSFREE)

2. 对C++语法和编程有一定基础之后，你也许已经写过很多小程序了，接下来你需要培养你看大工程代码的感觉，就和学英语一样，掌握语法和句子之后，看看英语文章或者小说会增加你的阅读能力，以下是个人建议
  - 掌握几个知名的库，比如qt，opencv ， boost等 ， 可以参考 [qt 学习教程](https://pan.baidu.com/s/1nuSvs7Z#list/path=%2FHANDSFREE%2FHands_Free_Release%2F5_Learning_Data%2Fprograming%2FQT_Learning&parentPath=%2FHANDSFREE)
  - 通过工程实战来提升运用能力，比如看一些常用的ROS的包或者仔细研读HandsFree的代码，也可以根据自己的研究方向去学习相关的开源工程，通过改开源的代码实现一些自定义的应用，久而久之，你就有能力独立的搭建大工程了。
  - 在这个过程中，你对编程会有一些自己的体会，并慢慢的需要看一些编程思想，编程风格之类的书，并需要对C++有更深的理解，推荐学习google 和 ros 的编程风格 ，阅读《(More)Effective C++》、《(More)Exceptional C++》、《Effective STL》及《C++编程规范》提升对C++的理解，可以参考HandsFree百度云 [编程学习资料](https://pan.baidu.com/s/1nuSvs7Z#list/path=%2FHANDSFREE%2FHands_Free_Release%2F5_Learning_Data%2Fprograming&parentPath=%2FHANDSFREE) 提供的相关资料。 

3.  在以上过程中，会发现那些优秀的工程比如ROS Qt 等就像精美的艺术品，娴熟的语法运用，优美统一的风格，严谨紧凑的逻辑，这除了说明他们对自己领域的知识看的非常透彻外，也说明他们驾驭编程已经上升到编程哲学境界了，虽然这辈子我们都难成为这种高手，但是有必要关注一下高手的世界。我们可以通过学习设计模式 和 泛型编程，来帮助我们理解如何构建大的软件工程。

#### ROS 学习规划
 
* 关于ROS的学习，现在网上已经有很多中文教程了 , 可以参考 [易科机器人](http://blog.exbot.net/)，[RosClub](http://www.rosclub.cn/)，最重要的是要学会如何使用[ros wiki](http://wiki.ros.org/)。
* HandsFree不是ROS基础教程，只适合有一定ROS基础的同学深入学习研究ROS，或者基于HandsFree研究机器人相关话题比如SLAM ， 机械臂控制，多机器人协同。如果你要开始使用或者购买HandsFree平台，请确保你已经满足以下条件。
  - 请确保你看懂[beginner level](http://wiki.ros.org/ROS/Tutorials) 的教程，如果你的经验还不够多，请多看几遍。
  - 请确保你看过比较正式的书籍，随便一本你看懂了就行：比如你已经大概看懂 ros by example 1 indigo 前 8 章
  - 另外我再推荐一个国外的 ROS 入门 ppt： http://u.cs.biu.ac.il/~yehoshr1/89-685/

相关学习资料可以看[HandsFree百度云](https://pan.baidu.com/s/1nuSvs7Z#list/path=%2FHANDSFREE%2FHands_Free_Release%2F5_Learning_Data%2Fros&parentPath=%2FHANDSFREE) ，如果你以上条件你都 ok， 那么入手实物机器人就比较科学了，当然你要知道的远不止这些，很多细节的问题和工程经验是列不完的。

* 相关学习资源
 - https://hands-free.github.io/
 - http://blog.exbot.net/archives/2790
 - https://zhuanlan.zhihu.com/p/22763273
 - http://blog.exbot.net/archives/1129
 - http://www.guyuehome.com/

#### 需要的工程素质
* 学会使用google，翻墙，查资料
* 对机器人系统有一定认识，机械结构，电路，嵌入式，传感器等
* 学会用[markdown](https://guides.github.com/features/mastering-markdown/)来编辑文档，这是我们团队的通用文档格式之一
* [会用git，github  来管理代码，与人合作开发](https://guides.github.com/)
* 软件开发人员最好熟悉使用linux，学会makefile cmake linux_shell xml 等常用的脚本或标签语言

### 参考学习方向
> #### 移动机器人基础
* 了解机器人的定义，各种不同形态的机器人：无人机，地面机器人，水下航行器 以及其子分类。	
* 着重了解地面机器人中的轮式移动机器人，了解不同结构的移动机器人：差速，全向，平衡车，汽车形态的等等
* 了解移动机器人的历史 ， 组成和功能：云台，地盘，机械臂，升降杆等
*  移动机器人的各种伺服结构和驱动方法
*  移动机器人的各种传感器的作用，以及整个移动机器人系统是如何工作的，如何实现自主。

> #### 各个组别的学习可以参考[HandsFree NWPU Club的分组学习计划](https://github.com/HandsFree-Nwpu/HandsFree-Nwpu.github.io/wiki/2.3-Club-Group)

