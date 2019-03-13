## 阅读对象

```text
本文阅读对象商户系统（在线购物、收银系统、智能收银系统或其他）对接数字钱包支付平台API方式，所涉及的技术架构师，研发工程师，测试工程师，系统运维工程师。
```

## 协议规定

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
```

```text
根据规则应生成MD5签名串：
app_id=ckp180809001000010000305E305D256&biz_content={"out_trade_no":"20181201152622602","coin_code":"ETH","subject":"测试0.01个eth","trade_currency":"0","total_fee":"0.01","over_market_rate":"5","client_ip":"127.000.000.001","notify_url":"http://localhost/Heebit/Test/Pay/RecNotifyUrl.aspx","return_url":"http://localhost/Heebit/Test/Pay/RecReturnUrl.aspx"}&charset=utf-8&mch_id=100001&method=ckpay.pay.apply&sign_type=MD5&timestamp=20181201152622&version=1.0&key=822EC6E4A3D24D66AC27D555
```


```test
MD5签名转大写后：
"sign":"AB1FB7103ED08C64E8310674BA079ED8"
```

- 参数规定


```test
交易量：
交易金额默认为币种交易，暂不支持其他法定货币类型
```

```test
法定货币金额换算币种量：
商户可设置5%-10% 之间的比例自行换算，用户下单的交易金额需为换算后的币种量。
```

- 开发步骤：

```text
 申请注册ckapy商户账号
 开通所需要的支付币种
 查询商户ID、APPID、KEY,如果您是服务商模式
 根据API规范，开始程序对接
```







