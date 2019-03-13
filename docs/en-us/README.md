
- 本文阅读对象商户系统（在线购物、收银系统、智能收银系统或其他）对接数字钱包支付平台API方式，所涉及的技术架构师，研发工程师，测试工程师，系统运维工程师。

- 协议规定

<table data-hy-role="doctbl">
    <th>规则</th>
    <th>描述</th>
  </tr>
<tr>
    <td>传输方式</td>
    <td>为保证交易安全性，采用HTTPS传输</td>
</tr>
<tr>
    <td>字符编码</td>
    <td>统一采用UTF-8字符编码</td>
</tr>
<tr>
    <td>签名算法</td>
    <td>MD5，后续会兼容SHA1、SHA256、HMAC等。</td>
</tr>
<tr>
    <td>签名要求</td>
    <td>请求和接收数据均需要校验签名，详细方法请参考：MD5签名规则。</td>
</tr>
<tr>
    <td>证书要求</td>
    <td>调用申请退款、撤销订单接口需要商户证书</td>
</tr>
<tr>
    <td>判断逻辑</td>
    <td>先判断协议字段返回，再判断业务返回，最后判断交易状态</td>
</tr>
</table>

- MD5签名规则
```
第一步：把字典按Key的字母顺序排序；
第二步：把所有参数名和参数值串在一起；
第三步：在第二步生成的参数串后加入KEY;
第四步：讲第三步得到的参数串进行MD5加密；
第五步：将MD5串转大写。
```

- 示例

```text

APP_KEY：822EC6E4A3D24D66AC27D555
请求参数（除sign外）：
{"method":"ckpay.pay.apply","version":"1.0","mch_id":"100001","app_id":"ckp180809001000010000305E305D256","charset":"utf-8","sign_type":"MD5","timestamp":"20181201152622","biz_content":"{\"out_trade_no\":\"20181201152622602\",\"coin_code\":\"ETH\",\"subject\":\"测试0.01个eth\",\"trade_currency\":\"0\",\"total_fee\":\"0.01\",\"over_market_rate\":\"5\",\"client_ip\":\"127.000.000.001\",\"notify_url\":\"http://localhost/Heebit/Test/Pay/RecNotifyUrl.aspx\",\"return_url\":\"http://localhost/Heebit/Test/Pay/RecReturnUrl.aspx\"}"}
根据规则应生成MD5签名串：
app_id=ckp180809001000010000305E305D256&biz_content={"out_trade_no":"20181201152622602","coin_code":"ETH","subject":"测试0.01个eth","trade_currency":"0","total_fee":"0.01","over_market_rate":"5","client_ip":"127.000.000.001","notify_url":"http://localhost/Heebit/Test/Pay/RecNotifyUrl.aspx","return_url":"http://localhost/Heebit/Test/Pay/RecReturnUrl.aspx"}&charset=utf-8&mch_id=100001&method=ckpay.pay.apply&sign_type=MD5&timestamp=20181201152622&version=1.0&key=822EC6E4A3D24D66AC27D555
MD5签名转大写后：
"sign":"AB1FB7103ED08C64E8310674BA079ED8"

```

- 参数规定

```
1.交易量：
交易金额默认为币种交易，暂不支持其他法定货币类型

2.法定货币金额换算币种量：
商户可设置5%-10% 之间的比例自行换算，用户下单的交易金额需为换算后的币种量。
```

- 开发步骤

```
1.申请注册ckapy商户账号
2.开通所需要的支付币种
3.查询商户ID、APPID、KEY,如果您是服务商模式
4.根据API规范，开始程序对接
```

- 场景介绍

```text

CKPAY支付系统使用场景介绍

CKPAY可以提供商家与顾客之间的点对点支付服务，增加用户支付渠道，增加数字货币流通领域，提高数字货币使用频次，推动数字货币在新应用场景的发展。未来，CKPAY将致力于便捷支付、安全支付，通过区块链技术使得应用在钱包的支付更安全、更快速、更普及和更有价值。对接CKPAY支付功能商户平台开发人员无需了解区块链的相关知识，CKPAY系统沿用了传统支付接口模式，使商户平台能快速对接投产使用。

CKPAY支付系统的两大使用场景
1. 订单二维码主扫（付款人使用CKPAY APP主动扫描商家网站实时生成的带支付金额的二维码）。
   说明：用户在商户平台发起支付行为，使用CKPAY APP”扫一扫”扫描商户网站生成的二维码进行主动付款（二维码为实时生成且带商品及支付金额信息）。CKPAY将代收金额结算给商家后，商家可以通过CKPAY 系统内OTC 功能进行兑换货币，也可以转移到交易所兑换。
   应用场景：适用于商户PC端网站。
   应用案例：适用于线上PC网站电商、旅游、订票、游戏、直播等平台提供支付服务。

2. APP支付（商户APP集成CKPAY支付系统SDK）
   说明：适用于商户在移动端APP中集成CKPay支付功能。商户APP调用CKPAY支付系统SDK，唤起CKPAY支付模块，商户平台用户确认金额、收款方等信息之后，输入支付密码进行支付，支付完后跳回到商户APP内，最后展示支付结果。此种方式是基于支付SDK形式，为商户平台提供一键数字支付功能。
   应用场景：适用于线上商户移动端APP支付。
   应用案例：适用于移动端电商、旅游、订票、游戏、直播等平台提供支付服务。

```





