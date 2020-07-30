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
