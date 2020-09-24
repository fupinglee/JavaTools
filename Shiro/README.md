# Shiro相关工具
ShiroScan和ShiroExploit。ShiroScan是从ShiroExploit剥离出来的一个Shiro反序列化扫描工具，用于检测存在Shiro反序列化漏洞的key值。ShiroExploit是反序列化回显利用工具，包含ShiroScan的全部功能。



## ShiroScan

用于检测存在Shiro反序列化漏洞的key值。有三种方式进行检测，第一种是利用URLDNS进行检测，第二种利用命令执行进行检测，第三种使用`SimplePrincipalCollection`序列化后进行检测（XCheck，即Xray Check）。

运行效果

![](../images/Shiro/ShiroScan.png)

## ShiroExploit

当前版本2.0，新增内存shell，完成tomcat6/7/8/9下的通用回显，无需选择tomcat版本[**参考**：https://github.com/zema1/ysoserial/]。

#### v2.0

支持内存cmd shell的写入与卸载

![](../images/Shiro/ShiroExploit-04.png)

![](../images/Shiro/ShiroExploit-05.png)





#### v1.5

新增使用`SimplePrincipalCollection`序列化后进行检测（XCheck，即Xray Check）。参考https://mp.weixin.qq.com/s/do88_4Td1CSeKLmFqhGCuQ

![](../images/Shiro/9.png)

#### v1.4

增加使用payloads来检测key，增加CommonsCollections10，支持commons-collections3.x的回显

![](../images/Shiro/7.png)

PAYLOAD可以选择，不用手动输入

![](../images/Shiro/8.png)

#### v1.3

去除输入端口，自动匹配。去掉模式选择，根据`ByteChunk`或`ByteBuffer`来输出。

Tomcat7及低版本Tomcat8输出时需要使用`ByteChunk`，Tomcat9及高版本Tomcat8使用`ByteBuffer`

![](../images/Shiro/6.png)

#### v1.2

新增使用URLDNS检测key值。

![](../images/Shiro/5.png)



选择默认DNSLOG时会自动生成一个DNSURL，然后根据Key列表进行检测。当找到key值时，任务结束，可以看到DNSLOG的请求记录。

选择自定义DNSLOG时，需要自己输入一个DNSLOG平台的地址，然后自行去平台查看。

#### v1.1

新增代理模式，支持Tomcat9。

Tomcat7下效果

![](../images/Shiro/1.png)

