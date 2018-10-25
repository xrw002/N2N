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