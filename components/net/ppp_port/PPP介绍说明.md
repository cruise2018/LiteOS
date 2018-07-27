#### ppp介绍

关于PPP的介绍，网上资料蛮多，可以参考相关的RFC文档

[RFC1661](https://tools.ietf.org/html/rfc1661)

[RFC1334](https://tools.ietf.org/html/rfc1334)

[RFC1172](https://tools.ietf.org/html/rfc1172)

另外有一个关于PPP的博客写的挺好的，可以[参阅](https://www.cnblogs.com/gtarcoder/p/6259105.html)。

关于LWIP中PPP的移植部分，可以参考[LWIP文档](http://www.nongnu.org/lwip/2_0_x/group__ppp.html)。

需要说明的一个问题是：无线模组默认的状态是AT命令状态，即任何的输入都会默认作为AT命令来处理，因此在运行PPP拨号前务必先用AT命令让模组从AT状态切换到数据状态，拨号参数跟使用的运营商和无线制式有关系；

| 运营商（ISP）             | APN   | 拨号号码  | 账号            | 密码       |
| ------------------------- | ----- | --------- | --------------- | ---------- |
| 中国联通（WCDMA）         | 3GNET | *99#      | 空              | 空         |
| 中国电信（CDMA2000/EVDO） | 空    | #777      | ctnet@mycdma.cn | vnet.mobi  |
| 1X网络                    | 空    | #777      | card(CARD)      | card(CARD) |
| 中国移动（TD-SCDMA）      | CMNET | *98*1#    | 空              | 空         |
| 中国移动（GPRS/EGDE）     | CMNET | *99****1# | 空              | 空         |

比方使用中国移动的GPRS，则拨号命令为"ATD*99****1#",如果拨号成功，一般返回的是CONNECT...；如果使用的是物联网卡或者专网卡，务必和提供商联系获取相应的USER PASSWORD APN。

#### 使用说明

* LiteOS的PPP部分，已经CloudStm32F429工程和NXP51U68的KEIL工程已经做了适配，可以直接导入工程使用。（需要打开宏开关USE_PPPOS=1）。
* PPPOS是不做校验和计算的，如果你在LWIP的配置文件中开启了该功能，请务必关闭





































