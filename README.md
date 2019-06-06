# awesome-payment
awesome payment

## 常识
### 商户类型
* 企业
* 个人
* 代理商
* 服务商

### 结算类型
* 对公：公司名义与第三方支付公司签约，提供公司的对公银行账户
* 对私：个人与第三方支付公司签约，提供商户法人或指定人的个人银行账户
### 手续费
* 保底费率：交易额比较小时，必须收取的手续费率
* 封顶费率：大额交易（每个渠道可能收取不同）时，收取的最高手续费率
### 到账
```
t+1为第二个工作日到账;
t+0为当天工作日到账;
d+1为第二天到账(包含休息日，节假日);
d+0为全年当天到账(包含休日，节假日);
```
### 代付
商户系统资金代付

## 渠道
* [蚂蚁金服开放平台](https://open.alipay.com/platform/home.htm)
* [微信支付开发文档](https://pay.weixin.qq.com/wiki/doc/api/index.html)
## 工具
* [ssl工具及各类加解密在线算法](http://www.ssleye.com/)
* RSA私钥及公钥生成工具： [使用支付宝提供的一键生成工具](https://docs.open.alipay.com/291/105971)
* 银联号查询 http://www.5cm.cn/bank/ 
* 身份证号码验证查询 https://shenfen.supfree.net/
* [根据银行卡号码获取银行卡归属行以及logo图标](https://blog.csdn.net/qq_28268507/article/details/68941754) 
* 银行卡真实性验证 https://ccdcapi.alipay.com/validateAndCacheCardInfo.json?_input_charset=utf-8&cardNo=6217002430035835629&cardBinCheck=true
* 根据银行缩写单词获取该行logo https://apimg.alipay.com/combo.png?d=cashier&t=ABC

## 国外的支付工具
* [stripe]( https://stripe.com/hk)

## 聚合支付包（库）
* [Javen205/IJPay](https://github.com/Javen205/IJPay) 🔥 IJPay 让支付触手可及，封装了微信支付、支付宝支付、银联支付常用的支付方式以及各种常用的接口
* [Payum/Payum](https://github.com/Payum/Payum)PHP 7+ Payment processing library. It offers everything you need to work with payments: Credit card & offsite purchasing, subscriptions, payouts etc. - provided by Forma-Pro
* [Exrick/xpay](https://github.com/Exrick/xpay)XPay个人免签收款支付系统 完全免费 资金直接到达本人账号 
* [phoenixg/omnipay-pingpp](https://github.com/phoenixg/omnipay-pingpp)一个聚合了支付宝（APP、Wap、PC、即时到账、扫码、企业付款），微信（APP、公众号、红包）， 银联网关、银联企业网银、Apple Pay、QQ 钱包、易宝支付、百度钱包、京东支付、京东白条、招行一网通、分期支付等国内主流支付渠道的聚合支付网关
* [helei112g/payment](https://github.com/helei112g/payment)Payment是php版本的支付聚合第三方sdk，集成了微信支付、支付宝支付、招商一网通支付。提供统一的调用接口，方便快速接入各种支付、查询、退款、转账能力。服务端接入支付功能，方便、快捷

## 支付平台架构
* [我对支付平台架构设计的一些思考](https://juejin.im/post/5cf69f1c6fb9a07f08708372)
