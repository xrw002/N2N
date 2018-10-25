这是n2n p2p vpn软件的开发分支。

https://github.com/ntop/n2n

它包含对n2n的v2版本的一些修改，这是最新的稳定版本
并应用于生产环境。
所有当前的开发都发生在new_protocol分支的这个存储库中，即 
打算来到n2n的v3版本，然后合并回原来的svn存储库
在ntop.org上。

使用sglib http://sglib.sourceforge.net。

新协议和密码规范
新协议版本的文档将在此处完成：https：//github.com/meyerd/n2n/tree/p2p_crypto/doc

改进思路
重新分配数据包格式
改进的加密（使用加密密钥或由pbkdf2生成）
MAC（带第二个密钥，超级节点应该检查以防止泄漏私有边缘信息）
会话密钥
向前保密
评估DTLS的用法
评估gnutls和gnupg的支持
清除pending_peers
看看lzo压缩（似乎主要是实现但不起作用）

git clone https://github.com/meyerd/n2n.git

apt-get install cmake libssl-dev

cd n2n/n2n_v2

mkdir build

cd build

cmake -build . ..

make

3.windows下编译，需要VS2015环境【试过VS2010编译很难】

cd n2n/n2n_v2

mkdir build

cmake -G "Visual Studio 14" --build .\ ..\

然后打开n2n.sln编译

4.supernode运行，一般在linux服务器上

supernode -l 822

5.edge运行

ubuntu-linux

安装虚拟网卡

apt-get install uml-utilities

tunctl -t tun0

运行edge

./edge -c tttc -k egova -a 172.16.0.200 -s 255.255.0.0 -l 121.42.174.178:822

windows

【安装虚拟网卡，借助http://www.vpnhosting.cz/n2nguien.exe来安装。一般可先不安装试试】

edge.exe -c tttc -k egova -a 172.16.0.200 -s 255.255.0.0 -l 121.42.174.178:822

或替换n2ngui目录下的edge2.exe为自己编译的edge.exe【否则不能用】，并修改目录下的n2ngui.ini配置文件，使用n2ngui.exe来启动。

 

之后客户端之间的网络即可联通。例子使用的是172.16段的B类私有地址。【10段A类与阿里云内网冲突，192.168段C类可能和内网冲突，B类IP地址数据也基本够用】

-c 网络组，相同的网络组内可互通
-k 加密密码，两节点需要相同才可通信
-l supernode的IP和端口

------------------------------

windows系统下n2n配置

注意：请将附件压缩包（n2n_windows.zip）中的内容放到D盘直属目录下，即确保路径为D:\n2n（如图1所示）

1）  安装驱动n2nguien.exe ；

注：N2N Gui settings窗口直接关了就行，不用配置；

2）安装n2n：管理员权限执行install_n2n.bat；

3）安装vc_redist.x86_2015.exe；

4）修改注册表中的ip地址（此IP地址可以找李健生分配），并双击导入n2n.reg；
