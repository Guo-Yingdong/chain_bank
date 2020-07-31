# github学习笔记

1.在本地电脑中安装git

2.在github上创建个人仓库

3.复制仓库地址

4.	在本地随便创建一个文件夹（注意路径不要中文）

5.	进入文件中，鼠标右键如果安装成功git,菜单中会多出Git bash Here和Git GUI Here两个菜单，选择Git bash Here

6.	输入命令：

（1）	从github中克隆：git clone https://github.com/Guo-Yingdong/im2latex.git

（2）	进入该文件夹 cd im2latex

（3）	将要上传的代码copy到文件中，继续输入命令：git status

（4）	将要要上传代码添加到本地仓库：git  add ./

（5）	重复  :     git status   发现刚才都是绿色，说明文件已经添加了

（6）	加上传代码注释（一定要这一步）：git commit -m "注释"

（7）	最后将代码发往github:    git push -u origin master   

查看仓库说明成功


# 单点登录

单点登录全称Single Sign On（简称SSO），是指在多系统应用群中登录一个系统，便可在其他所有系统中得到授权而无需再次登录，包括单点登录与单点注销两部分。

# 前后端分离
通常情况下，我们说的前端，都是指浏览器这一端，浏览器这一端，又在通常情况下，都是用JS来实现的，所以又会引申为，用JS写的大部分程序都是前端，包括App，小程序，H5等。而NodeJS出现之后，用NodeJS写的后端部分，也会被人归类为前端，为了区分之前的前端，就给他们起了一个名字，叫做“大前端”。
前后端分离的"前"特指浏览器端(或客户端)。

# 微服务
以一个网上超市应用为例来说明这一过程。
 
![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/1.png)

所有应用都在一个数据库上操作，数据库出现性能瓶颈。特别是数据分析跑起来的时候，数据库性能急剧下降。

微服务改造的过程实际上也是个抽象的过程。

1.用户服务

2.商品服务

3.促销服务

4.订单服务

5.数据分析服务

![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/2.png)

这个阶段只是将服务分开了，数据库依然是共用的，所以一些烟囱式系统的缺点仍然存在：

1.	数据库成为性能瓶颈，并且有单点故障的风险。

2.	数据管理趋向混乱。即使一开始有良好的模块化设计，随着时间推移，总会有一个服务直接从数据库取另一个服务的数据的现象。

3.	数据库表结构可能被多个服务依赖，牵一发而动全身，很难调整。

完全拆分后各个服务可以采用异构的技术。比如数据分析服务可以使用数据仓库作为持久化层，以便于高效地做一些统计计算；商品服务和促销服务访问频率比较大，因此加入了缓存机制等。
使用微服务架构同时也需要组织结构做相应的调整。所以说做微服务改造需要管理者的支持。

### 困难：

1.	微服务架构整个应用分散成多个服务，定位故障点非常困难。

2.	稳定性下降。服务数量变多导致其中一个服务出现故障的概率增大，并且一个服务故障可能导致整个系统挂掉。事实上，在大访问量的生产场景下，故障总是会出现的。

3.	服务数量非常多，部署、管理的工作量很大。

4.	开发方面：如何保证各个服务在持续开发的情况下仍然保持协同合作。

5.	测试方面：服务拆分后，几乎所有功能都会涉及多个服务。原本单个程序的测试变为服务间调用的测试。测试变得更加复杂。

微服务的调用需要一个把关的东西，也就是网关。在调用者和被调用者中间加一层网关，每次调用时进行权限校验。另外，网关也可以作为一个提供服务接口文档的平台。

![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/3.png)

# Camunda流程引擎笔记
## 一、下载安装
### 下载
点击https://camunda.com/download/modeler/下载camunda-modeler流程绘制工具
![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/4.png)

### 安装
安装camunda-modeler流程绘制工具后打开可以看到以下界面：
![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/5.png)

## 二、绘制简单的流程
### 新建一个BPMN文档
双击圆圈添加注释双击圆圈添加注释。
![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/6.png)

### 创建一个 SERVICE TASK
点击图中圆圈选择圆角方框。添加注释审核，然后点击小扳手选择
![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/7.png)

### 配置 SERVICE TASK
![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/8.png)

Implementation有多个类型，这里只演示Java Class，其他类型可以自行试试。

### 绘制流程结束节点
点击审核圆角方框，选择黑色圆圈，添加注释审核流程结束。
![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/9.png)

### 保存
将上面绘制的流程保存为audit.bpmn。

## 三、配置应用
### 配置
<ul> 
 <li> 在src/main/resources目录下创建META-INF文件夹，创建一个空的processes.xml文件。</li>
 <li> 将上面绘制audit.bpmn拷贝到下。 </li>
 <p> ![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/10.png) </p>
 <li> 在应用引导类上添加@EnableProcessApplication注解，开启camunda自动配置。 </li>
