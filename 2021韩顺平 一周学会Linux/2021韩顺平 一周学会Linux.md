[040_韩顺平Linux_linux组的介绍_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Sv411r7vd?p=40&vd_source=339a4744bd362ae7b381fd9629bfd3a9)

[(26条消息) [学习笔记]2021韩顺平一周学会Linux_N刻后告诉你的博客-CSDN博客](https://blog.csdn.net/zhangyifeng_1995/article/details/128485382)

# 04 Linux的目录结构 
>Linux的文件系统是采用级层式的树状目录结构，在此结构中的最上层是根目录“/”，然后在此目录下在创建其他的目录
>注：linux会将硬件映射成文件来进行管理

-   /bin [常用] (/usr/bin、/usr/local/bin)：  
    是Binary的缩写，这个目录存放着最经常使用的指令，如cd指令。
-   /sbin (/usr/sbin、/usr/local/sbin)：  
	s是Super User的意思，这里存放的是系统管理员使用的系统管理程序
-   /home [常用]：  
    存放普通用户的根目录，在Linux中每个用户都有一个自己的目录，一般该目录名是以用户的账号 命名。可以在终端用下面命令创建和删除linux用户：
```
useradd jack # 创建名为jack的用户，同时在/home目录下会创建jack目录
userdel -r jack # 移除jack用户，同时在/home目录下会移除jack目录
```
-   /root [常用]：  
    该目录为系统管理员，也称作超级权限者的用户主目录
-   /lib：系统开机所需要最基本的动态连接共享  库，其作用类似于Windows里的DLL文件。几乎所 有的应用程序都需要用到这些共享库
-   /lost+found这个目录一般情况下是空的，当系统非法关机后，这里就存放了一些文件(lost+found目录一般是隐藏的，通过在终端，在根目录输入ls可以查看到)
-   /etc [常用]：所有的系统管理所需要的配置文件和子目录，比如安装mysql数据库，则数据库的配置文件会默认放在etc下面。当然etc也有系统的一些配置文件
- /usr [常用]: 这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下，类似于windows下的program files目录(windows下安装的程序默认的目录)
-  /boot [常用]：存放的是启动Linux时的一些核心文件，包括一些连接文件以及镜像文件
-  /proc [不能动]：这个目录是一个虚拟的目录，它是系统内存的映射，访问这个目录来获取系统信息
-  /srv [不能动]: service缩写，该目录存放一些服务启动之后需要提取的数据
-  /sys [不能动]: 这是linux2.6内核的一个很大的变化。该目录下安装了2.6内核中新出现的一个文件系统sysfs
-  /tmp: 这个目录是用来存放一些临时文件的
-  /dev：类似于windows的设备管理器，把所有的硬件用文件的形式存储，如cpu，硬盘等
-  /media [常用]：linux系统会自动识别一些设备，如U盘、光驱等等，当识别后，linux会把识别的设备挂载到这个目录下
-  /mnt [常用]：系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将外部的存储挂载在/mnt/上，然后进入该目录就可以查看里面的内容了
-  /opt：这是给主机额外安装软件所存放的目录。如安装ORACLE数据库就可以放到该目录下。默认为空
-  /usr/local [常用]：这是另一个给主机额外安装软件安装的目录。(软件安装好存放的目录)一般是通过编译源码方式安装的程序
- /var [常用]：这个目录中存放着不断扩充着的东西，习惯将经常被修改的目录放在该目录下。包括各种日志文件
- /selinux [security-enhanced linux]: SELinux是一种安全子系统，它能控制程序只访问呢特定文件，有三种工作模式，可自行设置

# 06 Vi和Vim编辑器
## vi和vim常用的三种模式
>正常模式
> 以vim打开一个档案就直接进入一般模式(默认模式)。在这个模式中，你可以使用[上下左右]按键来移动光标，你可以使用[删除字符]或[删除整行]来处理档案内容，也可以使用[复制、粘贴]来处理你的文件数据

>插入模式
>按下i，I，o，O，a，A，r，R等任何一个字母之后才会进入编辑模式，一般来说按i即可

>命令行模式
>先输入esc，再输入冒号：或/，就能切换到命令行模式。在这个模式中，可以提供你相关指令，完成读取、写入(w)、替换、离开vim(q)、显示行号、写入并退出(wq)等动作

## 各种模式的相互切换
![](attachments/Pasted%20image%2020230211222940.png)

## vi和vim快捷键
1. 拷贝当前行：在一般模式下输入yy ；拷贝当前行向下的5行：在一般模式下输入5yy ；并粘贴(输入p)
2. 删除当前行：在一般模式下输入dd ；删除当前行向下的5行：在一般模式下输入5dd
3. 在文件中查找某个单词：在命令行模式下输入“/单词”，回车就会对单词进行查找，输入n就是查找下一个
4. 设置文件的行号，取消文件的行号：在命令行模式下，输入“:set nu”和“:set nonu”
5. 编辑/etc/profile文件，在一般模式下，使用快捷键到该文档的最末行[G]和最首行[gg]
6. 在一个文件中输入“hello”，然后又撤销这个动作：在一般模式下，输入“u”
7. 编辑/etc/profile文件，并将光标移动到20行：在一般模式下，输入“20“再输入”shift+g”
![](attachments/Pasted%20image%2020230211224522.png)


# 09 指令 25-39
## 9.1 指定运行级别
>基本级别说明：
	0：关机
	1：单用户【找回丢失密码】
	2：多用户状态没有网络服务（用的很少）
	3：多用户状态有网络服务（用的最多的，不带图形界面，节省资源；支持多用户且有网络服务-在实际生产环境中使用最多）
	4：系统未使用保留给用户（用的比较少）
	5：图形界面（启动后默认进入的级别，是多用户的）
	6：系统重启
	常用运行级别是3和5，也可以指定默认运行级别

```linux
# 通过init来切换不同的运行级别，比如修改级别为3：则命令为init 3
init [0123456]
```

在centos7以前，我们是在/etc/inittab文件中进行修改，它里面有个数字。
到了centos7，进行了简化，在/etc/inittab文件中有如下：
multi-user.target：analogous to runlevel 3 (多用户，等价于级别3)
graphical.target：analogous to runlevel 5 (图形化，等价于级别5)

```linux
# To view current default target, run:（以下指令可以查看当前运行级别）  
systemctl get-default

# To set a default target, run:（以下指令可以设置默认运行级别）  
systemctl set-default TARGET.target
```

## 9.2 找回root密码

## 9.3 帮助指令
>man获取帮助信息
	基本语法：man 命令或配置文件 （功能描述：获取帮助信息）
	案例：查看ls命令的帮助信息：man ls
	注意：
	1.如果帮助信息太长，没有显示完全，那么按空格键，会继续往下显示。
	2.ls中常用的选项
	-a：列出所有文件，包括以”.“开头的隐含文件（在linux中，隐含文件是以”.“开头的，a代表all）。
	-l：单行输出。
	3.按h寻求man指令的帮助，按q退出man指令。
	4.选项可以组合使用，如-la（顺序无所谓，也可以是-al），则表示单行输出，且包含所有隐藏文件
	5.ls -al默认是查看当前目录的，如果要查看root目录下的文件，则可以用ls -al /root

>help命令（功能描述：获得shell内置命令的帮助信息）
	注意：help命令只能显示shell内置命令的帮助信息，而linux系统中绝大多数命令是外部命令。而通过man命令查看其它命令的详细文档。没有内建与外部命令的区分，因为 man 工具是显示系统手册页中的内容，man 得到的内容比 help 更多更详细。

## 9.4 文件目录类
### pwd指令
基本语法：pwd （功能描述：显示当前工作目录的绝对路径）

### ls指令
基本语法：ls [选项]  
常用选项  
-a：显示当前目录所有的文件和目录，包括隐藏的  
-l：以列表的方式显示信息

### cd指令
基本语法：cd [参数]  (功能描述：切换到指定目录)
cd ~或cd：回到自己的家目录，比如你是root，cd ~，则到/root，如果是tom，cd ~，则到/home/tom  
cd .. 回到当前目录的上一级目录
注：前面带/表示绝对路径，如cd /home/Linux，前面不带斜杠表示相对路径，如cd home/Linux。cd abc为进入当前目录下面的abc子目录；cd /abc为进入系统根目录/下的abc子目录

### mkdir指令(make directory)
mkdier指令用于创建目录
基本语法：mkdir [选项] 要创建的目录
常用选项
-p：创建多级目录
案例1：创建一个目录/home/dog：mkdir /home/dog
案例2：创建多级目录/home/animal/tiger：mkdir -p /home/animal/tiger

### rmdir指令
rmdir指令删除空目录
基本语法
rmdir [选项] 要删除的空目录

案例：删除一个空目录 /home/dog：rmdir /home/dog
使用细节
rmdir 删除的是空目录，如果目录下有内容时无法删除的。
提示：如果需要删除非空目录，需要使用 ’rm -rf 要删除的目录‘（-rf表示强制递归）
比如：rm -rf /home/animal
注意：
1.使用rm -rf进行删除时，要非常谨慎。
2.rm指令单独只能删除文件，加上参数-r可以删除包含文件的文件夹。但是在删除前shell会询问

### touch指令
touch指令创建空文件  
基本语法  
touch文件名称  
案例：在/home目录下，创建一个空文件 hello.txt：touch hello.txt

### cp指令
cp指令拷贝文件到指定目录
基本语法
cp [选项] source dest
常用选项
-r：递归复制整个文件夹

案例1：将/home/hello.txt拷贝到/home/bbb目录下：在/home目录下，cp hello.txt bbb
案例2：递归复制整个文件夹，比如将/home/bbb整个目录，拷贝到/opt：cp -r /home/bbb /opt（这样拷贝是将整个目录，包括目录bbb本身，都拷贝到/opt下的）
使用细节
强制覆盖不提示的方法：\cp：如上面的指令如果要强制覆盖，则为\cp -r /home/bbb /opt

### rm指令
说明：rm指令移除文件或目录
基本语法
rm [选项] 要删除的文件或目录
常用选项
-r：递归删除整个文件夹
-f：强制删除不提示

案例1：将/home/hello.txt删除：rm /home/hello.txt ，在提示中选择y
案例2：递归删除整个目录 /home/bbb：rm -r /home/bbb（删除整个目录，但每删其中的一个文件都会提示）
使用细节：
强制删除不提示的方法：带上-f参数即可


### mv指令
mv移动文件与目录或重命名
基本语法
mv oldNameFile newNameFile （功能描述：重命名）
mv /temp/movefile /targetFolder（功能描述：移动文件）
注意：
1.重命名是在同一个目录下
2.移动是在不同的目录下

案例1：将/home/cat.txt文件重新命名为pig.txt：在/home目录下，mv cat.txt pig.txt
案例2：将/home/pig.txt文件移动到/root目录下：在home目录下，mv cat.txt /root
案例3：移动整个目录，比如将/opt/bbb移动到/home下，并重命名为uuu：mv /opt/bbb /home/uuu（/home目录下本来没有/uuu目录）
注意：
对案例3，如果/home目录下本来有/uuu目录，则mv /opt/bbb /home/uuu命令会把/bbb目录移到/home/uuu目录下


### cat指令
cat查看文件内容（与vim的区别是，cat只能查看，不能修改，更安全）
基本语法
cat [选项] 要查看的文件
常用选项
-n：显示行号

案例1：/etc/profile 文件内容，并显示行号：cat -n /etc/profile
使用细节
cat只能浏览文件，而不能修改文件，为了浏览方便，一般会带上 管道命令：| more
补充：管道命令有点类似于，将前面的结果，再交给下一个指令进行处理，管道命令就是一个竖杠，再带一个其他命令

### more指令
more指令是一个基于VI编辑器的文本过滤器，它以全屏幕的方式按页显示文本文件的内容。more指令中内置了若干快捷键（交互的指令），详见操作说明  
基本语法  more 要查看的文件  
操作说明，如图
![](attachments/Pasted%20image%2020230210194035.png)

### less指令
less指令用来分屏查看文件内容，它的功能与more指令类似，但是比more指令更加强大，支持各种显示终端。less指令在显示文件内容时，并不是一次将整个文件加载之后才显示，而是根据显示需要加载内容，对于显示大型文件具有较高的效率。  
基本语法   less要查看的文件  
操作说明
![](attachments/Pasted%20image%2020230210194713.png)

### echo指令
echo输出内容到控制台
基本语法 echo [选项] [输出内容]

案例1：使用echo指令输出环境变量，比如输出环境变量$PATH：echo $PATH ；输出主机名$HOSTNAME: echo $HOSTNAME
案例2：使用echo指令输出hello,world！：echo ‘hello，world~“（引号可加可不加）

### head指令
head用于显示文件的开头部分内容，默认情况下head指令显示文件的前10行内容
基本语法
head 文件（功能描述：查看文件头10行内容）
head -n 5文件 （功能描述：查看文件头5行内容，5可以是任意行数）

案例：查看/etc/profile的前面5行代码：head -n 5 /etc/profile（去掉-n 5，默认看前10行）
注意：空行也算一行


### tail指令
tail用于输出文件中尾部的内容，默认情况下tail指令显示文件的前10行内容。
基本语法
1.tail 文件 (功能描述：查看文件尾10行内容）
2.tail -n 5 文件 （功能描述：查看文件尾5行内容，5可以是任意行数)
3.tail -f 文件 （功能描述：实时追踪该文档的所有更新）

### >指令和>>指令
\>输出重定向（覆盖写入）和>>追加
基本语法
1.ls -l >文件 （功能描述：列表的内容写入文件a.txt中（覆盖写））
2.ls -al >>文件 （功能描述：列表的内容追加到文件aa.txt的末尾）
3.cat 文件1>文件2 （功能描述：将文件1的内容覆盖到文件2的内容）
4.echo ’内容‘ >> 文件 （功能描述：将内容追加到文件中）

案例1：将/home目录下的文件列表写入/home/info.txt中，覆盖写入：ls -l /home > /home/info.txt（如果没有info.txt，则会创建）
案例2：将当前日历信息追加到/home/mycal文件中：cal >> /home/mycal

### ln指令
软链接也称为符号链接，类似于windows里的快捷方式，主要存放了链接其他文件的路径
基本语法 ln -s [原文件或目录] [软链接名] （功能描述：给原文件创建一个软链接）

案例1：在/home目录下创建一个软链接myroot，连接到/root目录：ln -s /root /home/myroot
案例2：删除软连接myroot：rm /home/myroot（会提示是否删除符号链接）
注意：
如果rm /home/myroot/，会提示无法删除/home/myroot/，是一个目录
细节说明
当我们使用pwd指令查看目录时，仍然看到的是软链接所在目录

### history指令
查看已经执行过的历史指令，也可以执行历史指令
基本语法
history（功能描述：查看已经执行过的历史命令）

案例1：显示所有的历史命令：history
案例2：显示最近使用过的10个指令：history 10
案例3：执行历史编号为5的指令：!5 （可以输入负数，表示倒数的指令）

## 9.5 时间日期类
### date指令-显示当前日期
基本语法
1.date （功能描述：显示当前时间）
2.date +%Y （功能描述：显示当前年份）
3.date +%m （功能描述：显示当前月份）
4.date +%d （功能描述：显示当前是哪一天）
5.date ’+%Y-%m-%d %H:%M:%S‘ （功能描述：显示年月日时分秒）

案例1：显示当前时间信息：date （2023年 01月 06日 星期五 09:58:54 CST）
案例2：显示当前时间年月日：date ’+%Y-%m-%d‘
案例3：显示当前时间年月日时分秒：date ‘+%Y-%m-%d %H:%M:%S’

### date指令-设置日期
基本语法   date -s 字符串时间  
案例：设置系统当前时间，比如设置成2021-11-11 11:22:22：date -s ‘2021-11-11 11:22:22’

### cal指令
查看日历指令  
基本语法  cal [选项] （功能描述：不加选项，显示本月日历）  

案例1：显示当前日历：cal  
案例2：显示2020年日历：cal 2020

## 9.6 搜索查找类
### find指令
find指令将从指定目录向下递归地遍历其各个子目录，将满足条件的文件或者目录显示在终端。  
基本语法   find [搜索范围] [选项]  
选项说明
![](attachments/Pasted%20image%2020230210203716.png)

案例1：按文件名：根据名称查找/home目录下的hello.txt文件：find /home -name hello.txt(没找到就没有信息)
案例2：按拥有者：查找/opt目录下，用户名称为nobody的文件：find /opt -user nobody
案例3：查找整个linux系统下大于200M的文件（+n大于 -n小于 n等于，单位有k,M,G）：find / -size +200M
补充：
ls -lh，h表示人可以看清楚的形式展示，此时显示的文件大小会自动转化为人可以看明白的xx M

### locate指令
locate指令可以快速定位文件路径。locate指令利用事先建立的系统中所有文件名称及路径的locate数据库实现快速定位给定的文件。locate指令无需遍历整个文件系统，查询速度较快。为了保证查询结果的准确度，管理员必须定期更新locate时刻。
基本语法 locate 搜索文件
特别说明，由于locate指令基于数据库进行查询，所以第一次运行前，必须使用updatedb指令创建locate数据库

案例：请使用locate指令快速定位hello.txt文件所在目录
```
updatedb 
locate hello.txt
```

### grep指令和管道符号|
grep过滤查找，管道符，“|”，表示将前一个命令的处理结果传递给后面的命令处理  
基本语法 ：grep [选项] 查找内容 源文件  
常用选项
![](attachments/Pasted%20image%2020230210204603.png)

案例：请在hello.txt文件中，查找’yes‘所在行，并显示行号  
方法1：cat /home/hello.txt | grep -n ’yes‘  
方法2：grep -n ’yes‘ /home/hello.txt

## 9.7 压缩和解压类
### gzip/gunzip指令
gzip用于压缩文件，gunzip用于解压的
基本语法
gzip文件 （功能描述：压缩文件，只能将文件压缩为*.gz文件）
gunzip文件.gz （功能描述：解压缩文件命令）

案例1：gzip压缩，将/home下的hello.txt文件进行压缩：gzip /home/hello.txt
案例2：gunzip压缩，将/home下的hello.txt.gz文件进行解压缩：gunzip /home/hello.txt.gz


### zip/unzip指令
zip用于压缩文件（或目录），unzip用于解压的
基本语法
zip [选项] xxx.zip 将要压缩的内容（功能描述：压缩文件和目录的命令）
unzip [选项] xxx.zip （功能描述：解压缩文件）
zip常用选项
-r：递归压缩，即压缩目录
unzip的常用选项
-d<目录>：指定解压后文件的存放目录

案例1：将/home下的所有文件进行压缩成myhome.zip：zip -r myhome.zip /home(将home目录及其包含的文件和子文件夹都压缩）
案例2：将myhome.zip解压到/opt/tmp目录下：unzip -d /opt/tmp /home/myhome.zip

### tar指令
tar指令是打包指令，最后打包后的文件是.tar.gz的文件  
基本语法  
tar [选项] xxx.tar.gz 打包的内容 （功能描述：打包目录，压缩后的文件格式.tar.gz）  
选项说明
![](attachments/Pasted%20image%2020230210211628.png)
-z表示指定gzip格式压缩或解压

案例1：压缩多个文件，将/home/pig.txt和/home/cat.txt压缩成pc.tar.gz：
tar -zcvf pc.tar.gz /home/pig.txt /home/cat.txt
(压缩时候在绝对路径下压缩，会把/home目录也压缩进去，在相对路径下压缩则不会这样）
案例2：将/home的文件夹压缩成myhome.tar.gz:
tar -zcvf myhome.tar.gz /home
案例3：将pc.tar.gz解压到当前目录
tar -zxvf pc.tar.gz
案例4：将myhome.tar.gz解压到/opt/tmp2目录下 
tar -zxvf /home/myhome.tar.gz -C /opt/tmp2

注意：
1.-C 目标目录表示指定目标目录
2.任何压缩方法，被压缩文件路径最好使用相对路径，否则会自动压缩绝对路径多创文件夹
补充：打包解包是针对.tar文件而言的，.tar文件就是将多个文件合并成一个单文件，解压和压缩是针对.gz文件而言，-c是打包成.tar文件，-x是把.tar包解开，-z会根据带的x还是c来决定解压还是压缩

# 10 组管理和权限管理 40-
# 大数据shell篇 91-107


# python定制篇 108-115


# Linux高级篇 117-141


# 面试题 142-153

