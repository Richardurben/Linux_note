## Linux

> UnixLinux 基础讲义.pdf

## ubuntu18桌面卡死解决方法
1. 直接 alt+f2 会弹出个输入框 里边输入 小写 r 回车 这样会重启你的gnome-shell 桌面环境 
2. ctrl+f3 进入终端 黑白屏环境：top 一下 你会发现 gnome-shell 这个cpu 100% 就是这个桌面环境依赖的gnome-shell 和它的pid 确认下眼神，你可以 接着 kill -9 pid，系统还是会自动重启桌面也就是 gnome-shell 你等会 再按 ctrl+f1 切换会桌面环境登录即可。
3. 这个方法 比较通用 就是按住你的 alt+Prc Sc SysRq 然后按顺序按 r e i s u b 这样便会重启你的系统。 这种方式对系统损伤最小。

## ubuntu18.04系统备份(systemback)
- 安装
~~~
sudo gedit /etc/apt/sources.list
deb http://ppa.launchpad.net/nemh/systemback/ubuntu xenial main
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 382003C2C8B7B4AB813E915B14E4942973C62A1B
sudo apt update
sudo apt install systemback
wait...
~~~
- 备份

> [参考链接1](https://blog.csdn.net/rechardchen123/article/details/90649208?depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1&utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1)
> [参考链接2](https://www.cnblogs.com/linuxAndMcu/p/10774020.html#_label0)

创建Live系统 ->(包含用户数据文件)->创建新的(wait)->转化为iso文件(小于4G)->插入u盘(写入设备直接制作系统)
if sblive大于4G->使用cdrtools生成iso(具体参考上述链接2)

## ubuntu开机检查到错误报告
sudo gedit /etc/default/apport

enable=1 -> 0

## Linux分屏操作
徽标键+左右箭头键 

## Linux下寻找文件的方法
1. whereis+文件名
2. find / -name +文件名
3. locate+文件名
4. which+可执行文件名

## Linux中软件安装位置索引
Example:

**/etc**  包含了系统文件配置

**/lib, /usr/lib, /usr/loacl/lib**  中，最后者包含了python2.7和python3.6通过pip安装的dist-packages和site-packages文件

**/mnt,/media** 为光盘默认的挂载点

**/opt** 用户额外安装的软件目录

**/proc** 存储在内存中的数据，目录，如系统核心，网络状态，外部设备，如/proc/cpuinfo、/proc/interrupts、/proc/dma、/proc/ioport、/proc/net/\*等

**/root** 系统管理员目录，和/home相对

**/sbin** 优先级权限高于bin，为系统管理员提供使用，如fdisk，shutdown、mount等命令

**/srv** 服务器启动后需要访问的数据目录

**/var** 用于存储经常变化的文件，如随时更改的日志文件

## Linux的命令选项
[option] :

[-a] :指定目录下的所有文件，包含隐藏文件

[-l] :以列表方式显示文件的详细信息

[-h] :以人性化的方式显示文件大小

Example：ls -lh

[文件类型：d/-/s等][文件所有者][用户组][其他用户组]（格式：rwx（可读可写可执行）若无则-)

## Linux常见命令
### 管道命令：
|：ls -alh | more 

可理解为左边列表出但前文件的信息，右边分页显示（左边写，右边读）

### 目录创建：
mkdir -p 以递归方式创建目录，可包含多个子目录

### 删除文件
经典：rm -rf /*   删库跑路

-i  以交互方式进行（最保险）

-f  强制删除无提示

-r 递归删除，删除文件夹必须使用

### 创建链接文件（快捷方式）
格式： In -s 源文件 链接文件

使用 -s 可以使两文件相互关联，源文件删除，链接文件同时删除

### 查看合并文件
cat 文件1 文件2 > 文件3

### 文本中搜索
grep [option] '搜索字符串' 待搜索文本

-v 显示不匹配所有行，去反

-n 显示匹配行号

-i 忽略大小写

### 统计文件字数或行数
wc [option]

-l 行数

-w 字数

-c/m 字符数

### 查找文件
find 目录 文件名

### 拷贝和移动
cp 要拷贝的文件 拷贝到的地方 [option]
mv 要拷贝的文件 拷贝到的地方 [option]
-r 同rm 要拷贝的是一个目录，采用递归的方式，目的地址要求是一个目录

### 压缩和归档
tar [option] 打包文件名 文件

[-f] 指定档案文件名称，如果多个option，需要把f放到最后

[-v]列出归档解档的详细过程，显示进度

[-t] 列出档案中包含的文件

[-x] 解开档案文件

**especial: tar cvzf 压缩包包名 文件1，文件2...(多文件归档后压缩) ** 
**解压 tar zxvf 压缩包包名（xxx.tar.gz）**

### 文件压缩解压
gzip [option] 压缩文件/解压后的文件名+压缩文件

[-d] 解压 gzip -d xxx.tar.gz

[-r] 压缩 gzip -r xxx.tar xxx.tar.gz

## 同理文件解压缩命令bzip2，zip，unzip

## 常用命令
whoami:看当前账户

who:看用户信心

w [选项] [用户名]

exit: 退出登录用户

sudo -:切换用户

groupadd/groupdel:添加删除组账号

usermod -g 用户组 用户名 修改用户所在组（/home里的个用户组）

useradd [参数] 新建用户账号（useradd -d /home/abc abc -m:创建abc，若不存在，则自动创建目录，同时用户属于abc组）

userdel abc:删除abc用户

passwd:设置用户组密码

last:查询用户从哪里登录

chmod:改文件权限(chmod u/g/o/a +/-/=(设定权限）rwx 文件

chown:修改文件所有者 （chown 用户名 文件或目录)

chgrp:修改文件所属组

chgrp 用户组名 文件或目录名

## 系统管理命令
cal 查看当前日历

date 显示或设置时间

ps 查看进程

-a 显示终端所有进程

-u 显示进程详细状态

-x 显示没有控制的终端进程

-w 显示加宽

-r 只显示正在运行的进程

top 动态显示进程

kill 终止制定进程，配合ps(提供pid)

kill  -9 pid (强制结束)

&、jobs、fg

& 将前台执行程序调入后台执行（ctrl+z）

jobs 查看后台执行程序(提供编号)

fg 编号(由jobs提供),将程序调处前台

reboot  重启

shhutdown -h 时间/+数字

定时关机和延时关机

init 0 关机

init 6 重启

df 磁盘检测

-a 显示所有文件系统的磁盘使用情况

-m 以1024字节为单位显示

-T 显示文件系统

du 检测目录所占磁盘空间

du [选项] 目录或文件

-a 递归显示制定目录各文件所占的数据块

-s 显示指定文件所占数据块

-b 以字节为单位显示磁盘占用的情况

-l 计算所有文件大小

mkfs 格式化

mkfs [选项] 设备文件名 [blocks]

-V 详细显示模式

 -t 制定文件系统类型，默认类型为ext32
 
 -c 创建文件系统同时，进行磁盘坏块检查
 
 ## 安装软件
 sudo apt-get update
 sudo apt-get install xxx
 sudo apt -get autoremove xxx
 
 ## 查看配置网卡信息
 ifconfig
 
 ifconfig eth0 inet 192.168.10.254 netmask 255.255.255.0.up（修改保存在内存中，重启后失效）
eth0 网络接口名称

-a 显示所有网络接口信息
 
 inet [IP地址] 设置IP地址
 
 netmask [子网掩码]
 
 up 启用网络接口
 
 down 关闭网络接口
 
 ## 测试远程主机连通性
 ping  主机ip地址
 
## 网络路由设置
route add default gw 192.68.1.1 dev eth0
添加默认网关地址，指定网络接口

## 网络状态监控
netstat [选项]

-a 列出所有端口

-i 显示网络接口列表

-at 所有tcp端口

-au 所有udp 端口

 -l 所有坚监听端口
 
 -lt tcp监听端口
 
 -lu 指定网络接口
 
 -s 显示所有协议统计信息
 
 -r 当前路由状态
 
 -p 输出显示PID 和进程名称，可以与其他开关一起使用
 
 ## 编辑器
 gedit 
vi 文件 打开文件
i进入输入模式，esc退出

保存文件先esc后shift+zz(ZZ)
 
 ## 远程连接
 ssh -l usrname hostip
 
 被远程登录的用户名 被远程登录的ip地址(双Linux系统操作)
 windows和Linux之间需要在window安装软件如xmanager
 
 ##远程传输文件
 
 Linux之间互相传输
 

## Linux下的源代码编译

* 从release下编译
~~~
$ tar xf /xxx.tar.xz
$ cd xxx
$ mkdir build
$ cd build
$ cmake ..
$ make
$ sudo make install
~~~
*  从 git下编译
~~~
$ git clone https://github.com/transmission/transmission Transmission
$ cd Transmission
$ git submodule update --init
$ mkdir build
$ cd build
$ cmake ..
$ make
$ sudo make install
~~~
* 更新git编译
~~~
$ cd Transmission/build
$ make clean
$ git pull --rebase --prune
$ git submodule update
$ cmake ..
$ make
$ sudo make install
~~~

## Linux下的C语言编译
1. 创建c语言文件（gedit等）
2. 编译文件，生成可执行文件
~~~
gcc -o 生成可执行文件的名字 源文件名字(可同时编译多个)
~~~
3. 执行文件
~~~
./xxx
~~~

## Linux下的网络分析(from github失效2020.3.20)
curl https://richardurben.github.io  （80端口，443端口）

ping richardurben.github.io   ->ttl

my traceroute

sudo mtr richardurben.github.io --tcp -P 80

sudo mtr richardurben.github.io --tcp -P 443

[端口分析](http://port.ping.pe/)










