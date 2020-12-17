<h1>Linux的学习</h1>

<h4>基础指令的操作</h4>date 日期与时间 </br>cal  日历 </br> bc 计算器

快捷键：Tab ：“ 命令补全与文件补全”

​				CTRL+c：将正在运行的程序中断

​				ctrl+d ：命令行结束

<h4>指令集</h4>

`--help:`

-  data --help(找到相关选项与参数)

`man page:`

- man date , 按 q 来离开man page页面，可以使用man man 来获取更多的信息

`nano文本编辑器：`

- nano + 文件名（文件名存在，则打开旧文件，没有打开新文件）
- crtl-x：离开nano 文件

`common:`

- who  看谁在线

- netstat -a  网络的连接状态

- ps -aux  背景执行的程序

  

`关机：`

- shutdown -h  关机

- shut 【-krhc】【时间】【警告讯息】

- shutdown -h now 立刻关机，此外还有poweroff，halt，reboot

  

`文件权限与目录配置：`

- 使用 su 指令来切换身份，如 su seaflower,使用exit来返回身份

- -rwxr--r--

  解释：

  d  ： 表示目录

  -：表示文件

  l：表示链接文件

  c:表示键盘鼠标等

  r--4  w--2  x--1

  `文件的rwx权限代表着什么：`

  r:可以查看文件   如做 cat/more/head/less等操作

  w：可以修改   vim

  x：可以执行  比如脚本script，command命令等
  
  `目录的rwx权限代表着什么：`
  
  r：可以列出目录中的内容，可以ls
  
  w：可以在目录下创建，删除文件，做touch操作
  
  x：可以cd
  
  **所以你要删除一个文件，就得对文件所在的目录有写的权限**
  
  charp: 改变文件所属群组
  
  chown：改变文件的拥有者
  
  chmod：改变文件的权限
  
  

`mkdir创建新目录：`

- mkdir 【-mp】 目录名
- -p ：递回的创建起来
- -m：权限    如：mkdir -m  711 目录名

`cp复制：`

- 语法：cp 格式  来源文件 目标文件

- -r ：复刻目录

- -p : 保留属性

  

`mv剪切：`

- 语法：mv 原文件或目录  目标目录
- mv 也可以实现改名的功能

`rm删除文件：`

- -r：删除目录

- -f:  强制执行（不会有询问）

- rmdir ： 删除一个空目录

  

`touch创建空文件：`

- 语法：touch + 文件名

- touch  ‘’program files‘’     创建了一个文件，有双引号，不建议这样做

- touch   program files       创建了两个文件

  

`cat显示文件内容:`

- 语法：cat 文件名

- -n ：显示行号

  

`tac:`

- 显示文件内容，反向列示

`more:`

- 分页显示文件内容，适用于文件内容较多

- 语法 ： more 【文件名】

- 空格或  f 翻页

- Enter ：换行

- q 或 Q  退出

  

`less:`

- 分页显示文件内容（可以向上翻页，more不可以向上翻页）
- 语法： less 【文件名】
- pageup  可以向上翻页

`head显示前几行:`

- 语法：head 【文件名】
- -n ： 指定行数，默认查看前10 行

`tail显示后几行:`

- 语法： tail【文件名】
- -n：显示文件后面几行
- -f：动态显示文件末尾内容

#### 链接命令：

`ln生成链接文件:`

- ln -s 【原文件】 【目标文件】

- -s ：创建软链接

- 链接分为 软链接 和 硬链接，软链接类似于Windows 的快捷方式

- 硬链接：相当于 cp -p +同步更新，对原文件修改，硬链接也会修改

  

`ln创建硬链接：`

- ln 【原文件】【目标文件】

  

#### 权限管理命令

`chmod:`

- 语法：chmod 【{ugoa}{+-=}{rwx}】【文件或目录】
- 方式二：chmod 【mode=421】【文件或目录】
- -r ：递归修改
- 举例 ：
  - chmod u+x 文件名
  
  - chmod g+w，o-r 【文件名】 可以同时对多个文件修改
  
  - chmod g=rwx  【文件名】
  
    

`chown改变文件或目录的所有者：`

- 语法：chown 【用户】【文件或目录】
- 如：chown seaflower www.txt  将文件www.txt的用户改为seaflower
- 在Linux中，改变一个文件的所有者，只有root可以做

`charp改变文件或目录的所属组：`

- charp 【用户组】【文件或目录】

`umask显示，设置文件的缺省权限：`

- 语法：umask 【-S】

- -S  以rwx形式显示文件的缺省权限（可以显示 新建文件的缺省权限）

- 在Linux里面任何创建的文件，都会把可执行权限 x 去掉，这就是使用umask 查看目录 和文 

  件权限不同的原因，基于安全的考虑，默认新建的文件是不具有可执行权限的

#### 文件搜索命令

`Find文件搜索:`

- 语法：find 【搜索范围】【匹配条件】
- 根据文件名来搜索  eg：find / -name 文件名，【文件名严格区分大小写】
- 根据文件名关键子搜索，find / - name * 文件名中含有的字母 *
  
- *可以匹配任意字符，？可以匹配单个字符
  
- find / -iname 文件名【文件名不区分大小写】

  

#### 帮助命令

`man：`

- 语法：man 【命令或配置文件】  eg：man ls

- man 查看配置文件的时候， 不能用 man 配置文件的绝对路径，只要man  配置文件的名称即可

- 1  命令的帮助

- 5 配置文件的帮助  如 man 5 passwd 

  

`whatis：`

简单查看命令是干什么用的  如：whatis ls

`apropos：`

简单查看配置文件的信息

`--help:`

简单查看命令有哪些选项

`help:`

查看shell内置命令的帮助，比如 cd 就是一种shell内置命令，找不到命令所在的路径的命令

man shell内置命令  不会显示shell内置的命令

#### 用户管理命令

`useradd:添加新用户`

- 语法：useradd 用户名  如 useradd  seaflower

  

`passwd:为用户添加密码`

- 语法：passwd  用户名

`who:`

- 查看登录用户的信息

- 语法：who      显示出来的是  登录用户名  登录终端 （ tty本地终端  pts远程终端）登录时间  登录主机的ip地址

  

`w:`

- 查看登录用户的详细信息
- 语法：w

#### 压缩解压命令

`常见的压缩格式：`

- .gz  .zip等

`gzip压缩文件：`

- 语法：gzip 【文件】

- 压缩文件格式：.gz

  

`gunzip解压缩：`

- 语法：gunzip 【压缩文件】   也可以使用 gzip -d 来解压缩文件
- 能解压 .gz 的文件
- gzip 只能压缩文件，不能压缩目录，这和Windows是不一样的
- gzip 压缩后不保留原文件

`tar打包命令：`

- 语法：tar 选项【-zcf】【压缩后文件名】【目录】  (以zcvf的顺序)
  - -c 打包
  - -v 显示详细信息
  - -f 指定文件名
  - -z 打包同时压缩

- 功能：打包目录

- 压缩后的格式：.tar.gz

  

`tar解压缩命令：`

- -x 解包
- -v 显示详细信息
- -f 指定解压文件
- -z 解压缩

`zip:`

- 语法：zip 选项【-r】【压缩后文件名】【文件或目录】
- -r 压缩目录
- 功能：压缩文件或目录
- 压缩后格式：.zip

`unzip压缩解压缩命令：`

- 语法：unzip 压缩文件
- 功能：解压.zip的压缩文件

`bzip2:`

- 语法：bzip2 选项【-k】【文件】
  - -k  产生压缩文件后保留原文件
- 功能：压缩文件，压缩后文件格式为 .bz2
- 压缩能力惊人

`bunzip2:`

- 语法：bunzip2 选项【-k】【压缩文件】
  - -k  解压缩后保留原文件

#### 网络命令

`write:`

- 功能: 给在线用户发信息，以ctrl+d保存结束

- 语法：write 【用户名】

  

`wall:`

- 功能：发广播信息（所有在线用户）

- 语法：wall 【message】

  

`ping:`

- 功能：测试网络连通性
- 语法：ping 选项  IP地址
  - -c 指定发送次数   如: ping -c 3 baidu.com

- 和windows不同的是，会一直ping下去，除非按ctrl+c 终止

`ifconfig:`

- 功能：查看和设置网卡信息

- 语法：ifconfig  网卡名称  ip地址

  

`mail:`

- 功能：查看发送电子邮件,可以给离线的用户发
- 语法: mail 【用户名】  ，ctrl+d键保存发送
- 删除  右键 d+序列号
- 查看邮件目录 h

`last:`

- 功能：列出目前与过去登入系统的用户信息
- 语法:last

`lastlog  最后一次登录信息`

- last -u  502(uid) 只查看某用户的登录信息

  

`traceroute:`

功能：显示数据包到主机间的路径

语法：traceroute  如：traceroute www.baidu.com

`netstat:`

- 显示网络相关信息

- 语法：netstat 【选项】

  - -t TCP 协议

  - -u UDP协议

  - -l 监听

  - -r 路由

  - -n 显示ip地址和端口号

  - 如 ：netstat -an   查看本机所有的网络连接  

  - netstat -tlun  查看本机监听的端口

  - netstat -rn 查看本机路由表

    

`setup配置网络：`（Redhat专有的工具）

配完以后重启网络服务：service network restart，配置才会生效

`mount挂载命令：`

- 语法：mount 【-t 文件系统】设备文件名 挂载点
- u盘等只能手动来挂载

#### 关机重启命令

`shutdown:`

- 语法：shutdown 选项  时间
  - -c 取消前一个关机命令
  - -h 关机 （now立刻关机，或20：30）
  - -r 重启

`其他关机命令：`

- halt
- poweroff
- init 0

`其他重启命令：`

- reboot
- init 6

### vim文本编辑器

vim没有菜单，只有命令

`vim命令`

- 插入

  - i  在光标所在字符前插入

  - I 在光标所在的行首插入

  - a 在光标所在字符后插入

  - A 在光标所在行尾插入

  - o 在光标下插入新行

  - O 在光标上插入新行

    

    

- 在命令模式下按 ：，输入你的命令  如：set nu  加行号