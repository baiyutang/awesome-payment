# awesome-payment
awesome payment

## 常识

### 支付方式
* [扫码支付](https://opendocs.alipay.com/open/194#%E6%89%AB%E7%A0%81%E6%94%AF%E4%BB%98%E5%BA%94%E7%94%A8%E5%9C%BA%E6%99%AF) 或 主扫：即C端用户`主动`扫商家收款码，这个收款码是收款机构预生成订单，由商家输入收款金额，请求至收款机构，然后返回一条链接（此链接能在支付APP中调起支付）给商户测，商户在移动POS机或别的屏幕设备上展示次链接生成的二维码，用户扫描，输入支付密码即可完成支付。

* 付款码支付、二维码支付 或 [条码支付](https://opendocs.alipay.com/open/194#%E6%9D%A1%E7%A0%81%E6%94%AF%E4%BB%98%E5%BA%94%E7%94%A8%E5%9C%BA%E6%99%AF) 或 被扫：即C端用户出示自己的付款二维码，`被动`的由商户经过扫码枪等设备获取条码编号，商户将条码编号和扣款金额设置请求至收款机构，然后由收款机构扣款，发起向C端用户的支付确认窗（小额可能免密），完成支付。

* JSAPI支付：JSAPI支付是用户在支付APP中（微信、支付宝、云闪付）打开商户定义的H5页面，请求后端接口根据商户信息、付款金额等，将付款请求至收款机构，收款机构返回相关PayInfo字符串参数(里面包含订单号、商户在微信/支付宝/云闪付等平台的商户信息、校验签名等等)，H5页面已提前引入微信/支付包/云闪付的JS SDK，根据PayInfo中的参数调起支付，输入密码，即可完成支付。市面上常见的小微商户的多码合一的`台卡`就是利用这个接口来做到聚合支付的。

* APP支付：APP支付又称移动端支付，是商户通过在移动端应用APP中集成开放SDK调起微信支付模块完成支付的模式。

### 角色
* 个人用户：付款方，消费者
* 商家：终端商户，最终收款人
* 服务商：第三方，具有支付牌照的能够进行收款业务的聚合支付服务商
* 收款机构
* 清算中心
* 网联：非银行支付机构网络支付清算平台，简称网联，网联取代之前第三方支付公司与银行直接对接的模式。网联作为清算平台，一端连接第三方支付公司，另一端对接银行系统。
* 银联

实际上也有可能出现第四方、第五方、第六方，因为在法律允许下，技术上是可以做中转或支持多个支付渠道的聚合支付技术公司。只要不参与违规清算，这也是市面上很多的聚合支付生存之道。

### 行为
* 清算：清分+结算
* 清分：记账+发送指令+算账
* 结算：扣费+转账

### MCC行业编码
MCC，全称Merchant Category Code。即商户行业代码，代表商户所在行业。由中国银联统一设置并由各家支付机构及银行共同使用的分类编码，和其他特定信息一起组成了商家POS机的商户编号
* [MCC查询-中国银联开放平台](https://open.unionpay.com/tjweb/api/detail?apiSvcId=514)
### 结算类型
* 对公：公司名义与第三方支付公司签约，提供公司的对公银行账户
* 对私：个人与第三方支付公司签约，提供商户法人或指定人的个人银行账户

### 备付金
第三方支付公司在各个银行开立的账户，通常用作预存或留存在银行机构的货币资金，以及由支付机构为客户代收或代付的货币资金

### 二清
* [支付行业里二清是指什么？第三方机构不能接二清吗？](https://www.zhihu.com/question/38240219)
### 手续费
* 保底费率：交易额比较小时，必须收取的手续费率
* 封顶费率：大额交易（每个渠道可能收取不同）时，收取的最高手续费率

### 银行缩写简称

### 到账
```
t+1为第二个工作日到账;
t+0为当天工作日到账;
d+1为第二天到账(包含休息日，节假日);
d+0为全年当天到账(包含休日，节假日);
```
### 代付
商户系统资金代付
### 用户信息
* [openid](https://pay.weixin.qq.com/wiki/doc/api/jsapi.php?chapter=4_4)是微信用户在公众号appid下的唯一用户标识（appid不同，则获取到的openid就不同），可用于永久标记一个用户，同时也是微信JSAPI支付的必传参数
* [buyer_id](https://docs.open.alipay.com/53/104114)
* userId

### 补单


### 对账
* 单边账和双边账
* [如何做一个对账系统](https://www.cnblogs.com/ityouknow/p/7015879.html)


## 渠道
* [蚂蚁金服开放平台](https://open.alipay.com/platform/home.htm)
* [微信支付开发文档](https://pay.weixin.qq.com/wiki/doc/api/index.html)
* [微信开放社区-微信支付](https://developers.weixin.qq.com/community/pay)
* [中国银联开放平台](https://open.unionpay.com/tjweb/index)
* [汇付天下](https://docs.adapay.tech/api/introduce.html)

## 跨境支付
一点介绍[严查重罚跨境支付“无照驾驶”](https://mp.weixin.qq.com/s/Atk6Wmh7m1cOMd4KCDpCcg)
[2018年第三方跨境支付行业研究报告](/src/2018年第三方跨境支付行业研究报告.pdf)
## 原则
* 支付结果判断：明确成功才成功，明确失败就失败，状态未知为支付中
* 代码设计上注意胶水层对外部接口的转换，并在日志或数据层面对原始数据的保存，不过度消化数据，适当抽象（因为可能会遇到一个字段回来转换拼凑的情景）

## 可能遇到的坑
* 上游渠道域名或ip变更带来的接口不可用，假如在没有完善的监控或切至备用渠道或域名，只能两眼一抹黑，被动的处理bug
* 由于第一条，多留意支付渠道相关公告，留意自己服务器或域名备案相关充值或账号到期等问题

## 安全
### 加解密
* [主流数字证书都有哪些格式？](https://help.aliyun.com/knowledge_detail/42214.html?spm=a2c4g.11186623.2.15.2a0d3469KScK0V)
## 工具
* [ssl工具及各类加解密在线算法--开始收费，不推荐](http://www.ssleye.com/)
* [RSA公钥和私钥的生成以及PKCS#1与PKCE#8格式的转换](https://www.jianshu.com/p/e51fa37b3a36)
* [各类加解密工具](http://tool.chacuo.net/cryptrsapkcs1pkcs8)
* RSA私钥及公钥生成工具： [使用支付宝提供的一键生成工具](https://docs.open.alipay.com/291/105971)
* 银联号查询 http://www.5cm.cn/bank/ 
* 身份证号码验证查询 https://shenfen.supfree.net/
* [根据银行卡号码获取银行卡归属行以及logo图标](https://blog.csdn.net/qq_28268507/article/details/68941754) 
* 银行卡真实性验证 https://ccdcapi.alipay.com/validateAndCacheCardInfo.json?_input_charset=utf-8&cardNo=6217002430035835629&cardBinCheck=true
* 根据银行缩写单词获取该行logo https://apimg.alipay.com/combo.png?d=cashier&t=ABC
* [中国银联开放平台提供的辅助工具集](https://open.unionpay.com/tjweb/support/doc/online/5)
* [微信支付API v3 Postman脚本使用指南](https://github.com/wechatpay-apiv3/wechatpay-postman-script)

## 系统架构
* [微信支付商户系统跨城冗灾升级指引](https://pay.weixin.qq.com/wiki/doc/api/jsapi.php?chapter=23_6&index=4#)

## 国外的支付平台工具
* [stripe]( https://stripe.com/hk)
* Paypal
* Pefectmoney
* Advcash
* Webmoney
* Okey
* Fasapay
* Tether
* Bitcoin
* Payeer
* 全球支付工具列表参考>> https://www.shopify.com/payment-gateways

## 聚合支付包（库）
* [Javen205/IJPay](https://github.com/Javen205/IJPay) 🔥 IJPay 让支付触手可及，封装了微信支付、支付宝支付、银联支付常用的支付方式以及各种常用的接口
* [Payum/Payum](https://github.com/Payum/Payum)PHP 7+ Payment processing library. It offers everything you need to work with payments: Credit card & offsite purchasing, subscriptions, payouts etc. - provided by Forma-Pro
* [Exrick/xpay](https://github.com/Exrick/xpay)XPay个人免签收款支付系统 完全免费 资金直接到达本人账号 
* [phoenixg/omnipay-pingpp](https://github.com/phoenixg/omnipay-pingpp)一个聚合了支付宝（APP、Wap、PC、即时到账、扫码、企业付款），微信（APP、公众号、红包）， 银联网关、银联企业网银、Apple Pay、QQ 钱包、易宝支付、百度钱包、京东支付、京东白条、招行一网通、分期支付等国内主流支付渠道的聚合支付网关
* [helei112g/payment](https://github.com/helei112g/payment)Payment是php版本的支付聚合第三方sdk，集成了微信支付、支付宝支付、招商一网通支付。提供统一的调用接口，方便快速接入各种支付、查询、退款、转账能力。服务端接入支付功能，方便、快捷
* [laravel-pay](https://github.com/yansongda/laravel-pay) 可能是我用过的最优雅的 Alipay 和 WeChat 的 laravel 支付扩展包了
* [FastPay](https://github.com/limuyang2/FastPay)一个使用LiveData集成的微信、支付宝、银联支付的小巧库

## 主页或博客
* [梁川博客：出家如初成佛有余--曾经的第三方支付从业者，现在区块链从业者](https://www.yeeach.com/)
* [梁川知乎](https://www.zhihu.com/people/chuanliang/answers)
* [接蒜君的微信公众号：jiesuanjun, 点击此链接打开二维码图片](https://mp.weixin.qq.com/mp/qrcode?scene=10000005&__biz=MzIxMTYyNjI0NA==&mid=2247483856&idx=1&sn=a68a1d66c9bd3015be82468b94418fa9)
* [乐刷聚合支付文档](https://www.yuque.com/leshuazf/doc)
## 支付平台架构
* [我对支付平台架构设计的一些思考](https://juejin.im/post/5cf69f1c6fb9a07f08708372)
* [《58到家支付系统架构与实践》蔡敏.pdf](/src/《58到家支付系统架构与实践》蔡敏.pdf)
* [刘恒-盒子科技聚合支付系统演进.pdf](/src/刘恒-盒子科技聚合支付系统演进.pdf)
* [李胜军-美的支付架构演进.pdf](/src/李胜军-美的支付架构演进.pdf)
* [支付平台架构设计评审核心要点与最佳实践.pdf](/src/支付平台架构设计评审核心要点与最佳实践.pdf)
* [马蜂窝支付中心架构演进](https://juejin.im/post/5d1eea43f265da1bc23f96ec)

## 书籍
* [支付大讲堂 中国支付清协会培训课程精选系列](https://book.douban.com/subject/27080419/)
* [移动支付用户体验设计](https://book.douban.com/subject/26835739/)
* [移动支付理论与实务](https://book.douban.com/subject/26942242/)
* [深度支付](https://book.douban.com/subject/30411023/)
* [移动金融:支付革命](https://book.douban.com/subject/26948021/)
* [互联网金融弄潮儿 : 第三方支付](https://book.douban.com/subject/27024322/)
* [蚂蚁金服 : 从支付宝到新金融生态圈](https://book.douban.com/subject/27085867/)
* [支付宝体验设计精髓](https://book.douban.com/subject/26910220/)

## 课题
* 风控
