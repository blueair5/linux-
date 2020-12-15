<h1>Linux的学习</h1>

<h4>基础指令的操作</h4>date 日期与时间 </br>cal  日历 </br> bc 计算器

快捷键：Tab ：“ 命令补全与文件补全”

​				CTRL+c：将正在运行的程序中断

​				ctrl+d ：命令行结束

<h2>指令集</h2>

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
  -  chmod g+w，o-r 【文件名】 可以同时对多个文件修改
  - chmod g=rwx  【文件名】