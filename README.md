# github学习笔记
## git配置
###1.基本配置

git config --global user.name 'xxx'
git config --global user.email 'xxx'
###2.不同权限配置
git config --local # 针对某仓库配置
git config --add --local user.name 'xxx' # 增加一个新的用户名
git config --global # 针对当前用户所有仓库，最常用
git config --system # 对系统中所有用户都有效，基本不用
###3.当前存在用户信息
分别查看不同水平上的配置情况
git config --list --local # 需要在具体仓库中使用
git config --list --global
git config --list --system
