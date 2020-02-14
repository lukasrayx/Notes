# 前言

使用linux的初衷只是觉得i3的桌面看起来很帅，但是时间难免会花在各种配置上面，而现在对自己有用的不过是git的使用，terminal的使用，vim的使用，所以有空我可以学学这些，当然这些也不是那么的紧迫，我应该要有一个priority。



# !mac	terminal 代理！

```
export https_proxy=http://127.0.0.1:7890;export http_proxy=http://127.0.0.1:7890;export all_proxy=socks5://127.0.0.1:7891;echo \"Set proxy successfully\"
```





# Terminal使用

pwd

Ls -a

ls -l

Man ls

cd / 到根目录

cd.. 和 .. 回到上一级目录

Cd ~ or cd  到home目录

Mkdir 新建文件夹

Touch 新建文件

**sudo rm -r -f \**文件夹名\****

Cat  new_file 把文件内容映射到终端

Less new_file	像打开man一样显示文件，q退出



mv 移动文件

mv new_file ~/Desktop 

mv new_file new_folder/old_file.txt

Mv old_file.txt file.txt



cp file.txt file_duplicate.txt

mv -加上tab   显示-后面可以出现的指令

Killall





# Manjaro使用

1. 输出系统基本信息:`sudo screenfetch`
2. 强制关机:`sudo shutdown now`
3. 升级系统:`sudo pacman -Syyu`
4. 清理系统中无用的包:`sudo pacman -R $(pacman -Qdtq)`
5. 清除已下载的安装包:`sudo pacman -Scc`
6. 显示文件系统的磁盘使用情况:`sudo df -h`或`sudo df -hT`
7. 显示文件系统的磁盘使用情况:`sudo fdisk -u -l`

## pacman命令

1. 安装应用 `sudo pacman -S '应用名'`
2. 删除应用 `sudo pacman -Rns '应用名'`
3. 升级应用 `sudo pacman -Syu '应用名'`
4. 清除缓存 `sudo pacman -Sc`
5. 显示软件 `sudopacman -Qq` 自己装的`sudo pacman -Qe` 
6. 查询不需要的软件 `sudo pacman -Qdtq` 删除 `sudo pacman -R $(pacman -Qdtq)` 
7.  



super + f 进入全屏

super +v  or super + h 垂直加窗口或者水平

super➕方向键 切换当前focus的窗口

super➕m 切换全屏或退出

super➕n 在顶端显示路径（但是不知道怎么撤销）



Super shift r 刷新

Super + r 更改窗口大小



terminal: 终端，显示你输入和电脑输出的字符串

Shell: 终端命令解析器 bash zsh fish

终端模拟器：arch的alaritty, ubuntu: gnome, deepin 



xorg 修改键盘位置软件（更改硬件设置：亮度，键位）

Xmodmap -pke

Xmodmap -pke > ~/.xmodmap

xev 显示keycode

clear control 

clear mod1

... 修改要替换的键位

Add control 

add mod1

或者用另一个办法

xkb，setxkbmap -option ctrl:swapcaps



## 软件：

Feh， variety更改terminal界面

chromium

kdenlivej 剪视频

gimp修图软件

Libreoffice（自带）

vlc视屏播放

virtualbox虚拟机

transmission，qbittorrent, thunder 下载软件

ranger文件管理器

polybar 状态栏

deepin terminal

compton 半透明工具

Alacrity terminal

Window compositor:  compton

图形界面linux桌面环境：kde，sfc

dwm

yay

tlp   <!--管理电量使用-->

Netease-cloud-music   <!--网易云音乐-->

gimp       <!--修图软件-->

lazygit <!--termial git管理软件-->

vlc









??????????????????

config改了但是default的terminal还是原来的

sol.: 配置文件在~/.i3 里面, 而不是/etc/i3



??????????????????



!!!!!!!!!!!!!!!!!!!!!!!!!!!!

manjaro左下角键盘strg换成了alt, alt换成了ctl

右下角键盘alt换成了super， 目录换成了ctl

!!!!!!!!!!!!!!!!!!!!!!!!!!!!



## Terminal代理问题

Terminal 输入setProxy / unsetProxy 启用/关闭代理













# Vim

shift+i 行前插入 shift+a 行尾插入

hjkl 左下上右 ， 改键位为jkli

更改键位 noremap 新键 旧键



## Vim-config

syntax on 打开高亮

set number 打开行号

set relativenumber

set cursorline

Set wrap	

Set showcmd

Set wildmenu





# GIt

git init <!--初始化当前路径为git仓库-->

Git status

Git add .  <!--添加所有修改-->

git diff <!--显示还没被add的内容-->

git reset <!--取消add的文件-->

git config --global user.name “提交人”

git commit -m “对于提交的描述” <!--提交文件-->

vim  .gitignore  <!--其中记录不想让git追踪管理的文件-->

git rm --cached xxfile <!--取消追踪管理xxfile-->



git branch pictures <!--创建分支-->

git checkout master <!--切换到主分支-->

git merge pictures <!--把pictures分支合并到主分支-->

git branch -d pictures <!--删除pictures分支-->

git branch -D <!--强制删除分支-->



git remote add origin https://github仓库地址

git push --set -upstream origin master <!--把已经提交的更改push到github-->

git config credential.helper store <!--保存github账号密码-->

git clone xx <!--复制xx仓库-->

git pull <!--下载最新的状态到本地-->



# ranger使用

ctr + f  <!--模糊文件查找-->

F7 <!--创建文件夹-->

cw <!--renaame-->

y <!--yank复制-->

p <!--paste-->

pp

dd <!--剪切-->

dD <!--删除-->

空格 <!--选中-->

# Install manjaro i3

### 制作启动盘(macos)

Step1 ：在disk utility中erase u盘

Step2 ：diskutil list,  diskutil unmountdisk /dev/disk2

Step3 ：sudo dd if=/Users/lucas/Downloads/manjaro-gnome-18.1.5-191229-linux54.iso of=/dev/disk2 bs=1m



### 配置manjaro

更改镜像源：sudo pacman-mirrors -i -c China

Sudo pacman -Syyu 更新完后reboot

Sudo pacman -S vim

Sudo -E vim /etc/pacman.conf      #color --> color

sudo pacman -S fish <!--install fish-->

Which fish

Chsh -s /usr/bin/fish

curl -L https://get.oh_my.fish | fish <!--install oh-my-fish-->

Fish_config <!--更改fish样式-->

alias c clear <!--把clear换成c-->

Funcsave <!--保存配置-->

 sudo pacman -S i3 <!--install i3,reboot after finish--> 

Sudo pacman -S alacritty

sudo pacman -S dmenu <!--super + s/d 启动 -->

vim ~/.Xresources 中修改 Xft.dpi: 120 <!--调整字体大小-->

Super + shift + c   <!--刷新i3.config配置-->



sudo pacman -S xorg <!--更改键位-->

xmodmap <!--输出当前几个键位-->

xmodmap -pke   <!--输出所有键位-->

Xmodmap -pke  >  ~/.xmodmap

xev <!--启动软件，告诉你现在按的键的keycode-->

vim .xmodmap <!--更改键位-->

最上面Clear xxx     最下面add xxx    <!--xxx为删除和增加的键名-->

Xmodmap ~/.xmodmap <!--刷新配置-->



new_window 1pixel <!--去掉边框-->

sudo pacman -S feh <!--桌面-->

sudo pacman -S variety <!--桌面图片-->

vim ~/.config/alacritty/alacritty/alacritty.yml

Sudo pacman -S compton 

sudo pacman -S ranger <!--文件管理软件-->

github安装fzf <!--文件查询软件-->

gaps inner 15  <!--调整窗口边框-->

Sudo pacman -S fcitx fcitx-im fcitx-configtool

sudo pacman -S fcitx-(double click tab for more info.)

调整桌面字体大小: vim ~/.Xresources 中修改 Xft.dpi: xxx



#更改添加config配置

Exec_always sleep; xmodmap ~/.xmodmap #开启i3后1s启动xmodmap 

new_window 1pixel 取消terminal四周边框

exec --no-startup-id compton -b 开机运行

 

exec --no-startup-id compton -b  <!--开机启动-->



# ProblemSolving

**make报错error127** ： 安装base-devel后解决







