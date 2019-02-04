### 程序自动化	
AS-i BSAP CC-Link CIP CAN CANopen DeviceNet ControlNet DF-1 DirectNET EtherCAT Ethernet Global Data (EGD) Ethernet Powerlink EtherNet/IP Factory Instrumentation Protocol FINS FOUNDATION fieldbus H1 HSE GE SRTP HART Protocol Honeywell SDS HostLink INTERBUS MECHATROLINK MelsecNet Modbus Optomux PieP Profibus PROFINET IO RAPIEnet SERCOS interface SERCOS III Sinec H1 SynqNet TTEthernet
### 工业控制系统	
MTConnect OPC DA OPC HDA OPC UA
### 智能建筑	
1-Wire BACnet C-Bus DALI DSI DyNet Factory Instrumentation Protocol KNX LonTalk Modbus oBIX VSCP X10 xAP xPL ZigBee
### 电力系统	
IEC 60870-5-103 IEC 60870-5 IEC 60870-6 DNP3 Factory Instrumentation Protocol IEC 61850 IEC 62351 Modbus Profibus
### 自动抄表	
ANSI C12.18 IEC 61107 DLMS/IEC 62056 M-Bus Modbus ZigBee
### 车辆总线	
AFDX ARINC 429 CAN ARINC 825 SAE J1939 NMEA 2000 FMS Factory Instrumentation Protocol FlexRay IEBus J1587 J1708 Keyword Protocol 2000 UDS LIN MOST VAN




**SCADA：数据采集与监视控制系统

ICS：工业控制系统

DCS：分布式控制系统/集散控制系统

PCS：过程控制系统

ESD：应急停车系统

PLC：可编程序控制器(Programmable Logic Controller)

RTU：远程终端控制系统

IED：智能监测单元

HMI：人机界面(Human Machine Interface)

MIS：管理信息系统(Management Information System)

SIS： 生产过程自动化监控和管理系统（Supervisory Information System）

MES：制造执行管理系统**



## 协议端口及测试脚本
Modbus
MODBUS协议定义了一个与基础通信层无关的简单协议数据单元（PDU）。特定总线或网络上的MODBUS协议映射能够在应用数据单元（ADU）上引入一些附加域。

 

### 安全问题

缺乏认证：仅需要使用一个合法的Modbus地址和合法的功能码即可以建立一个Modbus会话
缺乏授权：没有基于角色的访问控制机制， 任意用户可以执行任意的功能。
缺乏加密：地址和命令明文传输， 可以很容易地捕获和解析
 

### PROFIBUS
一种用于工厂自动化车间级监控和现场设备层数据通信与控制的现场总线技术，可实现现场设备层到车间级监控的分散式数字控制和现场通信网络

### DNP3
DNP(Distributed Network Protocol,分布式网络协议)是一种应用于自动化组件之间的通讯协议，常见于电力、水处理等行业。

简化OSI模型，只包含了物理层，数据层与应用层的体系结构（EPA）。

SCADA可以使用DNP协议与主站、RTU、及IED进行通讯。

### ICCP
电力控制中心通讯协议。

### OPC     
过程控制的OLE （OLE for Process Control）。
OPC包括一整套接口、属性和方法的标准集，用于过程控制和制造业自动化系统。

### BACnet
         
楼宇自动控制网络数据通讯协议（A Data Communication Protocol for Building Automation and Control Networks）。

         
BACnet 协议是为计算机控制采暖、制冷、空调HVAC系统和其他建筑物设备系统定义服务和协议

### CIP
通用工业协议，被deviceNet、ControINet、EtherNet/IP三种网络所采用。

Siemens S7
属于第7层的协议，用于西门子设备之间进行交换数据，通过TSAP，可加载MPI,DP,以太网等不同物理结构总线或网络上，PLC一般可以通过封装好的通讯功能块实现。

其他工控协议
         IEC 60870-5-104、EtherNet/IP、Tridium Niagara Fox、Crimson V3、OMRON FINS、PCWorx、ProConOs、MELSEC-Q。按需求自行查阅资料。

 

信息探测
协议测试脚本
序号



测试脚本



CIP

#### 端口号：44818

#### enip-enumerate.nse



Modbus

#### 端口号：502

#### modicon-info.nse



IEC 61870-5-101/104

#### 端口号：2404

#### iec-identify.nse



Siemens S7

#### 端口号：102

#### s7-enumerate.nse
#### mms-identify.nse



Tridium Niagara Fox

#### 端口号：1911

#### fox-info.nse

PS：简要测试，大量脚本自行测试。

相关搜索引擎
Shodan搜索

 

PS：Shodan搜索引擎介绍 http://drops.wooyun.org/tips/2469

 

Zoomeye搜索

 

PS：敏感信息，你懂得。




#### Ethernet/IP  44818



nmap -p 44818 --script enip-enumerate.nse  85.132.179.*

 

#### Modbus  502
nmap --script modicon-info.nse -Pn -p 502 -sV 91.83.43.*

 

 

#### IEC 61870-5-101/104  2404
nmap -Pn -n -d --script iec-identify.nse  --script-args=iec-identify -p 2404 80.34.253.*

 

#### Siemens S7  102
nmap -p 102 --script s7-enumerate -sV 140.207.152.*

 

nmap -d --script mms-identify.nse  --script-args='mms-identify.timeout=500' -p 102  IP

 

#### Tridium Niagara Fox  1911
nmap -p 1911 --script fox-info 99.55.238.*

 

意义何在
上述NSE脚本意义：

定位工控系统及协议模块。
收集目标工控的信息，如版本、内网IP、模块、硬件信息等。
结合对应的NSE脚本进一步拓展，例如自定义空间搜素引擎。
 

脚本资源
Github测试脚本
https://github.com/atimorin/scada-tools

https://github.com/atimorin/PoC2013

https://github.com/drainware/scada-tools

https://github.com/drainware/nmap-scada

Exploit-db测试脚本
https://www.exploit-db.com/exploits/19833/

https://www.exploit-db.com/exploits/19832/

https://www.exploit-db.com/exploits/19831/

https://www.exploit-db.com/search/?action=search&description=scada&e_author=

0x03乌云工控漏洞的分析
工控相关漏洞分析
         针对乌云主站的漏洞进行关键字搜索：工控(31)、SCADA(15)、Modbus(9)、PLC并进一步整合得到如下列表。

缺陷编号

漏洞起因

漏洞标题

wooyun-2015-132010

弱口令

工控安全之华润燃气敏感环境竟然未走专线可导致内网渗透（监控/配置/阀门可控未测）

wooyun-2015-129388

注入

华润化工控股有限公司信息门户设置缺陷/sql注入

wooyun-2015-125651

弱口令

某地有线电视内网沦陷可能修改推送广告内容等

wooyun-2015-125399

注入

中华工控网SQL注入导致全网数据沦陷90W会员数据#打包

wooyun-2015-122677

弱口令

某工控系统配置不当危及船只安全

wooyun-2015-117227

弱口令

某水库工控系统存在弱口令(成功渗透)

wooyun-2015-116558

配置不当

某电厂监管系统缺陷可导致整个工控网络沦陷（DCS/PLC可被操控执行任何命令）

wooyun-2015-107326

注入

某油田开发公司工控系统sql注入

wooyun-2015-96729

配置错误

VA弱密码致华北工控内网远程桌面服务器/内网穿透/涉及敏感信息

wooyun-2014-87708

弱口令

温州市管道燃气公司SCADA系统弱口令

wooyun-2014-86726

逻辑漏洞

中国工控网任意用户密码重置漏洞

wooyun-2014-83839

弱口令

大量外网web监控系统后台存在弱口令(涉及两款监控产品，涵盖宾馆、车间、仓库、企业内部等)

wooyun-2014-71890

弱口令

某财政信息网系统管理系统密码泄露

wooyun-2014-58681

配置不当

对电厂生产控制网络的一次漫游（针对工控网络的小型APT攻击）

wooyun-2013-42212

目录遍历

北京市一工控系统多处漏洞可内网渗透（已经发现webshell）

wooyun-2013-22961

网络未授权访问

301基础设施系列-国外基础设施1（鲍里斯波尔国际机场地面照明控制和监测系统）暴漏

wooyun-2013-21848

弱口令

从对某电厂DCS控制系统的实体控制续谈工控安全（可控制电厂实体设备）

wooyun-2013-21314

弱口令

从某知名厂商MIS软件逻辑缺陷谈对某工控网络的渗透 第二份案例

wooyun-2013-21250

弱口令

从某知名厂商MIS软件逻辑缺陷谈对某工控网络的渗透

wooyun-2012-16328

未授权访问

美国一工业操作系统越权访问,可控制能源基础设施

wooyun-2012-10818

弱口令

武汉市某工控系统弱口令导致信息泄漏，企业各种记录在内

wooyun-2012-09565

命令执行

放统计代码，站长一秒钟变APT攻击专家（wooyun-2012-09025续）

wooyun-2012-09025

设计缺陷

UC云端加速引擎存在非正常泄露referer问题

wooyun-2012-07340

账户体系控制不严

某省级能源集团旗下XX存在安全隐患

wooyun-2012-07172

配置错误

某环境集成平台存在严重问题！获得客户端控制实权！

wooyun-2012-07084

弱口令

中国电信某GPS监控平台存在严重问题

wooyun-2012-06997

SQL注入

天津鑫然智能DCS监控平台

wooyun-2012-06196

配置不当

国内某大型风电工控系统应用配置失误

wooyun-2012-04702

信息泄露

南京国电自动化股份有限公司厂站监控系统源代码及配置文件泄露漏洞

wooyun-2014-84258

未授权访问

姜堰市自来水公司SCADA管网综合监测系统漏洞

wooyun-2014-80994

注入

哈药集团分公司sql注入(影响大量同服网站数据库)

wooyun-2014-58654

命令执行

CenturyStar9.0 SCADA组态软件存在远程命令执行漏洞

wooyun-2014-58130

上传漏洞

某电厂SCADA测试文件未清理存在任意上传漏洞(可导致服务器沦陷)

wooyun-2013-34711

弱口令

天能集团某SCADA系统弱口令登陆

wooyun-2013-21086

SQL注入

某煤矿SCADA系统存在严重缺陷可导致服务器沦陷

wooyun-2012-07334

未授权访问

某市燃气管道SCADA系统登录绕过

wooyun-2012-06952

设计缺陷

某SCADA电力监控系统漏洞

 

         在以上的漏洞列表中，可以得出如下结论：

乌云工控漏洞的案例中，绝大多起因是弱口令(弱口令最多的是123456，其次是admin)、注入类漏洞。
能够挖出工控的精华漏洞的人也是特定的那几位，且在Kcon2015也有过演讲。
挖掘此类漏洞主要解决两个问题
a)         如何找到工控相关的系统和地址

b)        Getshell后，基于工控知识如何操控系统

根据漏洞中的细节可以进一步的复测和拓展，进而为工控系统的漏洞挖掘提供非线性思路。
a)         结合GHDB关键字的搜素：例如inurl:SCADA……

b)        链接地址含SCADA、Modbus等协议的关键字……

c)         其他KEY：MIS、SIS、DCS、PLC、ICS、监控系统……

d)        相关公司：南京科远、金风科技、天能集团、国电南瑞、华润燃气、积成电子、重庆三峰、东方电子……

e)         至于利用以上四点去做什么，呵呵…

 

工控精华漏洞分析
乌云工控相关的精华漏洞如下7个，在思路亮点中分析了漏洞的核心，同样也可能是获得打雷精华的理由。几乎共同点均是操控了对应的工控系统。

缺陷编号

漏洞标题

思路亮点

作者

wooyun-2015-132010

工控安全之华润燃气敏感环境竟然未走专线可导致内网渗透（监控/配置/阀门可控未测）

燃气系统Getshell+内网渗透+敏感信息

 jianFen

wooyun-2015-125651

某地有线电视内网沦陷可能修改推送广告内容等

Getshell+集群指令下达+敏感信息

 scanf

wooyun-2015-116558

某电厂监管系统缺陷可导致整个工控网络沦陷（DCS/PLC可被操控执行任何命令）

发电厂getshell+内网DB+操控DCS+拓扑分析

zph

wooyun-2014-58681

对电厂生产控制网络的一次漫游（针对工控网络的小型APT攻击）

MIS&SIS分析+Getshell+内网

 Z-0ne

wooyun-2013-21314

从某知名厂商MIS软件逻辑缺陷谈对某工控网络的渗透 第二份案例

在线DCS采集系统操控

 Z-0ne

wooyun-2013-21250

从某知名厂商MIS软件逻辑缺陷谈对某工控网络的渗透

软件厂商+未授权敏感信息+Getshell+操控Syncmb

 Z-0ne

wooyun-2015-127849

某大型SCADA系统缺陷导致多地多个工控基础设施被沦陷（影响电力、自来水、运营商等）

-

zph

 

0x04参考资源
工控专题
ZoomEye工控专题： http://ics.zoomeye.org/

Shodan工控专题：https://www.shodan.io/report/l7VjfVKc

牛人分享
Z-0ne专注于工控安全攻防技术研究                         http://plcscan.org/blog/

网络空间工控设备的发现与入侵                                 https://github.com/evilcos/papers

工控安全攻防演练场景实现分享（轨道交通）     http://zone.wooyun.org/content/14428

工业网络渗透，直击工控安全的罩门(zph，暂无资料)

工控系统安全威胁与应对探索(Kimon)   

Exploit PLC on the internet（Z-0ne）

https://github.com/knownsec/KCon/tree/master/KCon%202015
