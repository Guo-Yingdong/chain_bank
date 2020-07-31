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
 <li> 在应用引导类上添加@EnableProcessApplication注解，开启camunda自动配置。 </li>
</ul>

![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/11.png)

### 编写回调函数
要实现流程回调Java代码，Java类必须实现org.camunda.bpm.engine.delegate.JavaDelegate接口

### 测试
<ul>
 <li> 启用应用 </li>
 <li>开启一个流程实例
  <p>访问http://localhost:8080/app/tasklist/default/#/开启流程实例。</p>
  <p>回到应用控制台可以看到Java回调类打印的字符串：</p>
  <p>流程结束</p>
 </li>
</ul>

![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/11.png)

![image](https://github.com/Guo-Yingdong/chain_bank/blob/master/img/12.png)


# docker

## 什么是docker
docker是一个开源的应用容器引擎，开发者可以打包自己的应用到容器里面，然后迁移到其他机器的docker应用中，可以实现快速部署。如果出现的故障，可以通过镜像，快速恢复服务。

## 原理
docker是利用Linux内核虚拟机化技术（LXC），提供轻量级的虚拟化，以便隔离进程和资源。LXC不是硬件的虚拟化，而是Linux内核的级别的虚拟机化，相对于传统的虚拟机，节省了很多硬件资源。

NameSpace

LXC是利用内核namespace技术，进行进程隔离。其中pid, net, ipc, mnt, uts 等namespace将container的进程, 网络, 消息, 文件系统和hostname 隔离开。

Control Group

LXC利用的宿主机共享的资源，虽然用namespace进行隔离，但是资源使用没有收到限制，这里就需要用到Control Group技术，对资源使用进行限制，设定优先级，资源控制等。

## 内核支持

在CentOS6.8是可以支持docker，但是有些特性无法使用，因此至少使用3.8的内核版本，建议是使用3.10版本以上。国内生产环境很多都是使用CentOS，所以一般使用CentOS7即可。

当然如果是Ubuntu/Debian/Deepin系列的发行版本也是支持的。

## 环境准备

操作系统：CentOS 7.6.1810

软件源：阿里云镜像（在阿里云镜像站上面可以找到docker-ce的软件源，使用国内的源速度比较快）

安装docker-ce

如果没有物理机，可以先使用虚拟机进行学习。操作系统安装，跳过（网上教程很多）。

1、安装依赖

docker依赖于系统的一些必要的工具，可以提前安装。

yum install -y yum-utils device-mapper-persistent-data lvm2

2、添加软件源

yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

3、安装docker-ce

yum clean all yum makecache fastyum -y install docker-ce

4、启动服务

通过systemctl启动服务

systemctl start docker

5、查看安装版本

这样子就安装成功了，启动服务以后可以使用docker version查看一下当前的版本。

docker version

Client:Version: 18.09.2 API version: 1.39 Go version: go1.10.6 Git commit: 6247962 Built: Sun Feb 10 04:13:27 2019 OS/Arch: linux/amd64 Experimental: falseServer: Docker Engine - Community Engine: Version: 18.09.2 API version: 1.39 (minimum version 1.12) Go version: go1.10.6 Git commit: 6247962 Built: Sun Feb 10 03:47:25 2019 OS/Arch: linux/amd64 Experimental: false
