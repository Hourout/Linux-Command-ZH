# Linux Command ZH

Linux 最常用命令！

Linux是目前应用最广泛的服务器操作系统，基于Unix，开源免费，由于系统的稳定性和安全性，市场占有率很高，几乎成为程序代码运行的最佳系统环境。

linux不仅可以长时间的运行我们编写的程序代码，还可以安装在各种计算机硬件设备中，如手机、路由器等，Android程序最底层就是运行在linux系统上的。

## linux的目录结构
- bin  (binaries)存放二进制可执行文件
- sbin  (super user binaries)存放二进制可执行文件，只有root才能访问
- etc (etcetera)存放系统配置文件
- usr  (unix shared resources)用于存放共享的系统资源
- home 存放用户文件的根目录
- root  超级用户目录
- dev (devices)用于存放设备文件
- lib  (library)存放跟文件系统中的程序运行所需要的共享库及内核模块
- mnt  (mount)系统管理员安装临时文件系统的安装点
- boot 存放用于系统引导时使用的各种文件
- tmp  (temporary)用于存放各种临时文件
- var  (variable)用于存放运行时需要改变数据的文件

## linux常用命令

命令格式：命令  -选项  参数 （选项和参数可以为空）

如：ls  -la  /usr

- ### 操作文件及目录

| 命令 | 参数 | 示例 | 说明 |
|--- |--- |--- |--- |
| cd |   | cd /home | 切换目录 |
| pwd |   | pwd | 显示当前工作目录目录 |
| touch |   | touch 1.txt | 创建空文件 |
| mkdir |   | mkdir testdir | 创建一个新目录 |
|   | -p | mkidr -p dir1/dir2/dir3/ | 创建多级目录，父目录不存在情况下先生成父目录 |
| cp |   | cp 1.txt | 复制文件或目录 |
|   | -r | cp -r dir1/ | 递归处理，将指定目录下的文件与子目录一并拷贝 |
| mv |   | mv dir1 dir2 | 移动文件或目录、文件或目录改名 |
| rm |   | rm 1.txt | 删除文件 |
|   | -r | rm -rf dir1 | r同时删除该目录下的所有文件 |
|   | -f | rm -rf dir1 | f强制删除文件或目录 |
| rmdir |   | rmdir dir1 | 删除空目录 |
| cat |   | cat 1.txt | 显示文本文件内容 |
| more |   | more 1.txt | 分页显示文本文件内容，可前后翻页，空格向后，b向前 |
| less |   | less 1.txt	| 分页显示文本文件内容，可前后翻页，空格向后，b向前，支持底行模式（后面介绍） |
| head |   | head 1.txt | 查看文本开头部分，默认十行 |
|   | -[num] | head -20 1.txt | 查看文本开头部分指定行数 |
| tail |   | tail 1.txt | 查看文本结尾部分，默认十行 |
|   | -[num] | tail -20 1.txt | 查看文本结尾部分指定行数 |
|   | -f | tail -f 1.txt | 循环滚动读取文件并动态显示在屏幕上，根据文件属性追踪 |
|   | -F | tail -F 1.txt | 循环滚动读取文件并动态显示在屏幕上，文件文件名追踪 |
| wc |   | wc 1.txt | 统计文本的行数、字数、字符数 |
|   | -m | wc -m 1.txt | 字符数 |
|   | -w | wc -w 1.txt | 文本字数 |
|   | -l | wc -l 1.txt | 文本行数 |
| find | -name | find / -name 1.txt | 在文件系统中的指定目录下查找指定的文件 |
| grep |   | grep aaa 1.txt | 在指定文件中查找包含指定内容的行，例：在1.txt中查找包含aaa的所有行 |
| ln |   | ln 1.txt 1_bak.txt | 建立链接文件 |
|   | -s | ln -s 1.txt 1_bak.txt | 对源文件建立符号连接，而非硬连接 |

- ### 系统常用命令

| 命令 | 参数 | 示例 | 说明 |
|--- |--- |--- |--- |
| top |   | top | 显示当前系统中耗费资源最多的进程 |
| date |   | date | 显示系统当前时间 |
| ps |   |   | 较少单独使用，配参数根据需求，ps -ef 或者ps-aux |
|   | -e /-A | ps -e | 显示所有进程，环境变量 |
|   | -f | ps -ef | 全格式显示 |
|   | -a | ps -a | 显示所有用户的所有进程（包括其它用户） |
|   | -u | ps -au | 按用户名和启动时间的顺序来显示进程 |
|   | -x | ps -aux | 显示无控制终端的进程 |
| kill | -9 | kill -9 pid | 强制杀死一个进程 |
| df |   | df | 显示文件系统磁盘空间的使用情况 |
|   | -h | df -h | 以人类可读的方式显示，Kb，Mb，GB等 |
| du |   |   | 显示指定的目录及其子目录已使用的磁盘空间的总和 |
|   | -s | du -s * | 进显示指定目录的总和，星号当前目录下表示所有 |
|   | -h | du -sh * | 以人类可读的方式显示，Kb，Mb，GB等 |
| free |   | free | 显示当前内存和交换空间的使用情况 |
| ifconfig |   | ifconfig | 网卡网络配置，常用于查看当前IP地址 |
|   |   | ifconfig eth0 192.168.12.22 | 临时修改系统IP（重启后失效） |
| ping |   | ping baidu.com | 测试网络的连通性 |
| hostname |   | hostname | 查看主机名 |
| shutdown | -r | shutdown -r | 先关机，再重启 |
|   | -h | shutdown -h | 关机后不重启 |
| halt |   | halt | 关机后关闭电源，相当于shutdown -h |
| reboot |   | reboot | 重新启动 相当于shutdown -r |

