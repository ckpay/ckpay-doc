## 统一下单

- 支付请求接口

> 请求URL:`http://www.ckpay.top/api/v1/PayApply`

> 请求方式:`POST`   

> 是否需要证书：`否`

> method：`ckapy.pay.applypay`

- 公共参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>method</td>
    <td>String</td>
    <td>是</td>
    <td>100</td>
    <td>具体业务接口名称</td>
    <td>ckapy.pay.applypay</td>
</tr>
<tr>
    <td>version</td>
    <td>String</td>
    <td>是</td>
    <td>10</td>
    <td>版本号,默认1.0</td>
    <td>1.0</td>
</tr>
<tr>
    <td>app_id</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>应用ID，商户的应用id</td>
    <td>ckp180809001000010000305E305D256</td>
</tr>
<tr>
    <td>mch_id</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>商户ID,商户的商户id</td>
    <td>100001</td>
</tr>
<tr>
    <td>charset</td>
    <td>String</td>
    <td>是</td>
    <td>10</td>
    <td>编码格式默认为utf-8</td>
    <td>utf-8,gb2312,gbk</td>
</tr>
<tr>
    <td>timestamp</td>
    <td>String</td>
    <td>是</td>
    <td>19</td>
    <td>发送请求的时间</td>
    <td>yyyyMMddHHmmss,20181030152539</td>
</tr>
<tr>
    <td>biz_content</td>
    <td>String</td>
    <td>是</td>
    <td>不限</td>
    <td>请求参数集合,Json格式,长度不限,具体参数见如下业务参数</td>
    <td>Json格式</td>
</tr>
<tr>
    <td>sign_type</td>
    <td>String</td>
    <td>是</td>
    <td>10</td>
    <td>商户生成签名字符串所使用的签名算法类型</td>
    <td>md5</td>
</tr>
<tr>
    <td>sign</td>
    <td>String</td>
    <td>是</td>
    <td>256</td>
    <td>商户请求参数的签名串</td>
    <td>详见示例</td>
</tr>
</table>

- 业务参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>out_trade_no</td>
    <td>String</td>
    <td>是</td>
    <td>64</td>
    <td>商户系统内部订单号,要求64个字符内、且在同一个商户号下唯一</td>
    <td>20181022113011517</td>
</tr>
<tr>
    <td>subject</td>
    <td>String</td>
    <td>是</td>
    <td>256</td>
    <td>订单标题</td>
    <td>购买礼品</td>
</tr>
<tr>
    <td>total_fee</td>
    <td>Int</td>
    <td>是</td>
    <td></td>
    <td>订单总金额,单位为分</td>
    <td>100</td>
</tr>
<tr>
    <td>coin_code</td>
    <td>String</td>
    <td>是</td>
    <td>16</td>
    <td>币种代码(BTC,ETH,USDT等)</td>
    <td>ETH</td>
</tr>
<tr>
    <td>client_ip</td>
    <td>String</td>
    <td>是</td>
    <td>16</td>
    <td>终端IP(用户端实际ip)</td>
    <td>127.0.0.1</td>
</tr>
<tr>
    <td>currency_type</td>
    <td>String</td>
    <td>是</td>
    <td>18</td>
    <td>金额类型(0=币种值,1=人民币,2=英镑,3=港币,4=美元)</td>
    <td>0</td>
</tr>
<tr>
    <td>over_market_rate</td>
    <td>String</td>
    <td>是</td>
    <td>18</td>
    <td>非币种金额换算币值高于市场价百分比例(5%)</td>
    <td>5</td>
</tr>
<tr>
    <td>expire_minute</td>
    <td>String</td>
    <td>否</td>
    <td>32</td>
    <td>多少分钟后失效(0不限制)</td>
    <td>0</td>
</tr>
<tr>
    <td>attach</td>
    <td>String</td>
    <td>是</td>
    <td>127</td>
    <td>附加数据,在查询和支付通知中原样返回,可作为自定义参数使用格式:{“key1”:”value1”,”key2”:”value2”,…}</td>
    <td>{}</td>
</tr>
<tr>
    <td>notify_url</td>
    <td>String</td>
    <td>是</td>
    <td>255</td>
    <td>异步通知的地址</td>
    <td>http://…</td>
</tr>
<tr>
    <td>return_url</td>
    <td>String</td>
    <td>否</td>
    <td>255</td>
    <td>同步通知地址</td>
    <td>http://…</td>
</tr>
</table>

- 公共响应参数
<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>return_code</td>
    <td>String</td>
    <td>是</td>
    <td>16</td>
    <td>返回状态码</td>
    <td>SUCCESS</td>
</tr>
<tr>
    <td>return_msg</td>
    <td>String</td>
    <td>是</td>
    <td>128</td>
    <td>返回状态码描述</td>
    <td>执行完成</td>
</tr>
</table>


```
以下字段在return_code为SUCCESS时返回
```

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>result_code</td>
    <td>String</td>
    <td>否</td>
    <td>16</td>
    <td>业务状态码</td>
    <td>SUCCESS</td>
</tr>
<tr>
    <td>result_msg</td>
    <td>String</td>
    <td>否</td>
    <td>16</td>
    <td>返回业务状态码描述</td>
    <td>下单申请成功</td>
</tr>
<tr>
    <td>sign</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>签名结果</td>
    <td>1234567890</td>
</tr>
</table>

```
以下字段在return_code为FAIL时返回
```

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>error_code</td>
    <td>String</td>
    <td>否</td>
    <td>32</td>
    <td>详见错误列表</td>
    <td>0</td>
</tr>
<tr>
    <td>error_msg</td>
    <td>String</td>
    <td>否</td>
    <td>128</td>
    <td>错误返回的信息描述</td>
    <td>ok</td>
</tr>
</table>

- 响应参数

```
以下字段在return_code为SUCCESS时，result_code为SUCCESS时返回
```

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>app_id</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>应用ID,商户的应用id</td>
    <td>Ap22512545</td>
</tr>
<tr>
    <td>out_trade_no</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>商户订单号</td>
    <td>276952</td>
</tr>
<tr>
    <td>bill_no</td>
    <td>String</td>
    <td>否</td>
    <td>32</td>
    <td>ckpay预支付单号</td>
    <td>P1810301525002636304</td>
</tr>
<tr>
    <td>hy_pay_id</td>
    <td>String</td>
    <td>否</td>
    <td>32</td>
    <td>ckpay预支付ID</td>
    <td>P1sa9dgd02kv9g</td>
</tr>
<tr>
    <td>subject</td>
    <td>String</td>
    <td>是</td>
    <td>16</td>
    <td>订单标题</td>
    <td>购买</td>
</tr>
<tr>
    <td>total_fee</td>
    <td>String</td>
    <td>是</td>
    <td></td>
    <td>总金额</td>
    <td>单位与金额类型(currency_type)保持一致</td>
</tr>
<tr>
    <td>real_vol</td>
    <td>String</td>
    <td>是</td>
    <td></td>
    <td>用户实际支付量</td>
    <td>单位与币种代码(coin_code)保持一致</td>
</tr>
<tr>
    <td>hy_url</td>
    <td>String</td>
    <td>是</td>
    <td>128</td>
    <td>收银台 url</td>
    <td>http://…</td>
</tr>
</table>

## 订单查询

- 订单查询接口

> 请求URL:`http://www.ckpay.top//api/v1/PayQuery`

> 请求方式:`POST`   

> 是否需要证书：`否`

> method：`ckpay.pay.query`

- 公共参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>method</td>
    <td>String</td>
    <td>是</td>
    <td>128</td>
    <td>具体业务接口名称</td>
    <td>ckpay.pay.query</td>
</tr>
<tr>
    <td>version</td>
    <td>String</td>
    <td>是</td>
    <td>10</td>
    <td>版本号,默认1.0</td>
    <td>1.0</td>
</tr>
<tr>
    <td>app_id</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>应用ID，商户的应用id</td>
    <td>ckp180809001000010000305E305D256</td>
</tr>
<tr>
    <td>mch_id</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>商户ID,商户的商户id</td>
    <td>100001</td>
</tr>
<tr>
    <td>charset</td>
    <td>String</td>
    <td>是</td>
    <td>10</td>
    <td>编码格式默认为utf-8</td>
    <td>utf-8,gb2312,gbk</td>
</tr>
<tr>
    <td>timestamp</td>
    <td>String</td>
    <td>是</td>
    <td>19</td>
    <td>发送请求的时间</td>
    <td>yyyyMMddHHmmss,20181030152539</td>
</tr>
<tr>
    <td>biz_content</td>
    <td>String</td>
    <td>是</td>
    <td>不限</td>
    <td>请求参数集合,Json格式,长度不限,具体参数见如下业务参数</td>
    <td>Json格式</td>
</tr>
<tr>
    <td>sign_type</td>
    <td>String</td>
    <td>是</td>
    <td>10</td>
    <td>商户生成签名字符串所使用的签名算法类型</td>
    <td>md5</td>
</tr>
<tr>
    <td>sign</td>
    <td>String</td>
    <td>是</td>
    <td>256</td>
    <td>商户请求参数的签名串</td>
    <td>详见示例</td>
</tr>
</table>

- 业务参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>bill_no</td>
    <td>String</td>
    <td>否</td>
    <td>28</td>
    <td>平台单号(平台单号和商户单号不可同时为空,同时都有以此参数为准)</td>
    <td>P1810301525002636304</td>
</tr>
<tr>
    <td>out_trade_no</td>
    <td>String</td>
    <td>否</td>
    <td>64</td>
    <td>商户系统内部单号,要求同一个商户号下唯一</td>
    <td>Hylsjdklj245</td>
</tr>
</table>

- 公共响应参数
<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>return_code</td>
    <td>String</td>
    <td>是</td>
    <td>16</td>
    <td>返回状态码</td>
    <td>SUCCESS</td>
</tr>
<tr>
    <td>return_msg</td>
    <td>String</td>
    <td>是</td>
    <td>128</td>
    <td>返回状态码描述</td>
    <td>执行完成</td>
</tr>
</table>


```
以下字段在return_code为SUCCESS时返回
```

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>result_code</td>
    <td>String</td>
    <td>否</td>
    <td>16</td>
    <td>业务状态码</td>
    <td>SUCCESS</td>
</tr>
<tr>
    <td>result_msg</td>
    <td>String</td>
    <td>否</td>
    <td>16</td>
    <td>返回业务状态码描述</td>
    <td>下单申请成功</td>
</tr>
<tr>
    <td>sign</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>签名结果</td>
    <td>1234567890</td>
</tr>
</table>

```
以下字段在return_code为FAIL时返回
```

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>error_code</td>
    <td>String</td>
    <td>否</td>
    <td>32</td>
    <td>详见错误列表</td>
    <td>0</td>
</tr>
<tr>
    <td>error_msg</td>
    <td>String</td>
    <td>否</td>
    <td>128</td>
    <td>错误返回的信息描述</td>
    <td>ok</td>
</tr>
</table>

- 响应参数

```
以下字段在return_code为SUCCESS时，result_code为SUCCESS时返回
```

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>app_id</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>应用ID,商户的应用id</td>
    <td>Ap22512545</td>
</tr>
<tr>
    <td>out_trade_no</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>商户订单号</td>
    <td>276952</td>
</tr>
<tr>
    <td>bill_no</td>
    <td>String</td>
    <td>否</td>
    <td>32</td>
    <td>ckpay预支付单号</td>
    <td>P1810301525002636304</td>
</tr>
<tr>
    <td>hy_pay_id</td>
    <td>String</td>
    <td>否</td>
    <td>32</td>
    <td>ckpay预支付ID</td>
    <td>P1sa9dgd02kv9g</td>
</tr>
<tr>
    <td>subject</td>
    <td>String</td>
    <td>是</td>
    <td>16</td>
    <td>订单标题</td>
    <td>购买</td>
</tr>
<tr>
    <td>total_fee</td>
    <td>String</td>
    <td>是</td>
    <td></td>
    <td>总金额</td>
    <td>单位与金额类型(currency_type)保持一致</td>
</tr>
<tr>
    <td>real_vol</td>
    <td>String</td>
    <td>是</td>
    <td></td>
    <td>用户实际支付量</td>
    <td>单位与币种代码(coin_code)保持一致</td>
</tr>
<tr>
    <td>hy_url</td>
    <td>String</td>
    <td>是</td>
    <td>128</td>
    <td>收银台 url</td>
    <td>http://…</td>
</tr>
</table>


## 订单关闭

- 订单关闭接口

> 请求URL:`http://www.ckpay.top/api/v1/PayClose`

> 请求方式:`POST`   

> 是否需要证书：`否`

> method：`ckpay.pay.close`

- 公共参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>method</td>
    <td>String</td>
    <td>是</td>
    <td>128</td>
    <td>具体业务接口名称</td>
    <td>ckpay.pay.close</td>
</tr>
<tr>
    <td>version</td>
    <td>String</td>
    <td>是</td>
    <td>10</td>
    <td>版本号,默认1.0</td>
    <td>1.0</td>
</tr>
<tr>
    <td>app_id</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>应用ID，商户的应用id</td>
    <td>ckp180809001000010000305E305D256</td>
</tr>
<tr>
    <td>mch_id</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>商户ID,商户的商户id</td>
    <td>100001</td>
</tr>
<tr>
    <td>charset</td>
    <td>String</td>
    <td>是</td>
    <td>10</td>
    <td>编码格式默认为utf-8</td>
    <td>utf-8,gb2312,gbk</td>
</tr>
<tr>
    <td>timestamp</td>
    <td>String</td>
    <td>是</td>
    <td>19</td>
    <td>发送请求的时间</td>
    <td>yyyyMMddHHmmss,20181030152539</td>
</tr>
<tr>
    <td>biz_content</td>
    <td>String</td>
    <td>是</td>
    <td>不限</td>
    <td>请求参数集合,Json格式,长度不限,具体参数见如下业务参数</td>
    <td>Json格式</td>
</tr>
<tr>
    <td>sign_type</td>
    <td>String</td>
    <td>是</td>
    <td>10</td>
    <td>商户生成签名字符串所使用的签名算法类型</td>
    <td>md5</td>
</tr>
<tr>
    <td>sign</td>
    <td>String</td>
    <td>是</td>
    <td>256</td>
    <td>商户请求参数的签名串</td>
    <td>详见示例</td>
</tr>
</table>

- 业务参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>bill_no</td>
    <td>String</td>
    <td>否</td>
    <td>28</td>
    <td>平台单号(平台单号和商户单号不可同时为空,同时都有以此参数为准)</td>
    <td>P1810301525002636304</td>
</tr>
<tr>
    <td>out_trade_no</td>
    <td>String</td>
    <td>否</td>
    <td>64</td>
    <td>商户系统内部单号,要求同一个商户号下唯一</td>
    <td>Hylsjdklj245</td>
</tr>
</table>

- 公共响应参数
<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>return_code</td>
    <td>String</td>
    <td>是</td>
    <td>16</td>
    <td>返回状态码</td>
    <td>SUCCESS</td>
</tr>
<tr>
    <td>return_msg</td>
    <td>String</td>
    <td>是</td>
    <td>128</td>
    <td>返回状态码描述</td>
    <td>执行完成</td>
</tr>
</table>


```
以下字段在return_code为SUCCESS时返回
```

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>result_code</td>
    <td>String</td>
    <td>否</td>
    <td>16</td>
    <td>业务状态码</td>
    <td>SUCCESS</td>
</tr>
<tr>
    <td>result_msg</td>
    <td>String</td>
    <td>否</td>
    <td>16</td>
    <td>返回业务状态码描述</td>
    <td>下单申请成功</td>
</tr>
<tr>
    <td>sign</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>签名结果</td>
    <td>1234567890</td>
</tr>
</table>

```
以下字段在return_code为FAIL时返回
```

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>error_code</td>
    <td>String</td>
    <td>否</td>
    <td>32</td>
    <td>详见错误列表</td>
    <td>0</td>
</tr>
<tr>
    <td>error_msg</td>
    <td>String</td>
    <td>否</td>
    <td>128</td>
    <td>错误返回的信息描述</td>
    <td>ok</td>
</tr>
</table>

- 响应参数

```
以下字段在return_code为SUCCESS时，result_code为SUCCESS时返回
```

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>app_id</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>应用ID,商户的应用id</td>
    <td>Ap22512545</td>
</tr>
<tr>
    <td>out_trade_no</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>商户订单号</td>
    <td>276952</td>
</tr>
</table>


## 支付结果通知

- 支付状态异步通知API（主动发请求给商户）

> 请求URL:`请求接口提供的notify_url`

> 请求方式:`POST/GET`   


- 公共参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
    <th>是否必填</th>
    <th>最大长度</th>
    <th>描述</th>
    <th>示例值</th>
</tr>
<tr>
    <td>version</td>
    <td>String</td>
    <td>是</td>
    <td>10</td>
    <td>版本号,默认1.0</td>
    <td>1.0</td>
</tr>
<tr>
    <td>mch_id</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>商户ID,商户的商户id</td>
    <td>100001</td>
</tr>
<tr>
    <td>app_id</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>应用ID，商户的应用id</td>
    <td>ckp180809001000010000305E305D256</td>
</tr>
<tr>
    <td>isv_mch_uid</td>
    <td>String</td>
    <td>否</td>
    <td>32</td>
    <td>服务商商户号</td>
    <td></td>
</tr>
<tr>
    <td>isv_app_id</td>
    <td>String</td>
    <td>否</td>
    <td>32</td>
    <td>服务商应用ID</td>
    <td></td>
</tr>
<tr>
    <td>coin_code</td>
    <td>String</td>
    <td>是</td>
    <td>64</td>
    <td>币种代码</td>
    <td>BTC</td>
</tr>
<tr>
    <td>subject</td>
    <td>String</td>
    <td>是</td>
    <td>64</td>
    <td>标题</td>
    <td>购买</td>
</tr>
<tr>
    <td>out_trade_no</td>
    <td>String</td>
    <td>是</td>
    <td>64</td>
    <td>商户订单号</td>
    <td>123456</td>
</tr>
<tr>
    <td>hy_bill_no</td>
    <td>String</td>
    <td>是</td>
    <td>64</td>
    <td>订单号</td>
    <td>hy123456</td>
</tr>
<tr>
    <td>pay_type</td>
    <td>int</td>
    <td>是</td>
    <td></td>
    <td>支付类型</td>
    <td>0=未知,1=账户余额支付,2=链上支付</td>
</tr>
<tr>
    <td>total_fee</td>
    <td>int</td>
    <td>是</td>
    <td></td>
    <td>总交易量</td>
    <td>100</td>
</tr>
<tr>
    <td>real_vol</td>
    <td>Int</td>
    <td>是</td>
    <td></td>
    <td>实际支付量</td>
    <td>100，支付成功时返回</td>
</tr>
<tr>
    <td>pay_account</td>
    <td>String</td>
    <td>是</td>
    <td>50</td>
    <td>支付账号</td>
    <td>13811059841</td>
</tr>
<tr>
    <td>bill_status</td>
    <td>String</td>
    <td>否</td>
    <td>32</td>
    <td>单据状态:Undeal=未支付,Success=支付成功,Failure=支付失败</td>
    <td>Undeal</td>
</tr>
<tr>
    <td>attach</td>
    <td>String</td>
    <td>是</td>
    <td>100</td>
    <td>商户附加信息</td>
    <td></td>
</tr>
<tr>
    <td>sign</td>
    <td>String</td>
    <td>是</td>
    <td>32</td>
    <td>数据签名</td>
    <td></td>
</tr>
</table>

```
验签成功商户响应参数：ok 或者 success
通知参数示例：
通知参数格式为json格式
{
“version”:”1.0”,
“mch_id”:”100001”,
“app_id”:”ckp180809001000010000305E305D256”,
“subject”:”测试0.01个eth”,
“out_trade_no”:”20181124144753400”,
“hy_bill_no”:”P1811241448002167308”,
“pay_type”:”0”,
“total_fee”:”0.01000000”,
“real_vol”:”0.01000000”,
“pay_account”:”18614087902”,
“bill_status”:”Success”,
“sign”:”60C1317D0585F088A6DB6F1779E76D38”
}
```


## 获取币种价格 

- 获取币种价格请求接口

> 请求URL:`http://www.ckpay.top/api/v1/GetCoinPriceInfo`

> 请求方式:`POST`   

> 是否需要证书：`否`

> method：`ckpay.get.coin.price`

- 公共参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>method</td>
    <td>String</td>
	<td>是</td>
	<td>128</td>
	<td>具体业务接口名称</td>
	<td>ckapy.get.coin.price</td>
</tr>
<tr>
    <td>version</td>
    <td>String</td>
	<td>是</td>
	<td>10</td>
	<td>版本号,默认1.0</td>
	<td>1.0</td>
</tr>
<tr>
    <td>app_id</td>
    <td>String</td>
	<td>是</td>
	<td>32</td>
	<td>应用ID,商户的应用id</td>
	<td>ckp180809001000010000305E305D256</td>
</tr>
<tr>
    <td>mch_id</td>
    <td>String</td>
	<td>是</td>
	<td>32</td>
	<td>商户ID</td>
	<td>100001</td>
</tr>
<tr>
    <td>charset</td>
    <td>String</td>
	<td>是</td>
	<td>10</td>
	<td>编码格式默认为UTF-8</td>
	<td>UTF-8</td>
</tr>
<tr>
    <td>timestamp</td>
    <td>String</td>
	<td>是</td>
	<td>19</td>
	<td>发送请求的时间</td>
	<td>yyyyMMddHHmmss,20181031150802</td>
</tr>
<tr>
    <td>biz_content</td>
    <td>String</td>
	<td>是</td>
	<td>不限</td>
	<td>请求参数集合,Json格式,长度不限,具体参数见如下业务参数</td>
	<td>Json格式</td>
</tr>
<tr>
    <td>sign_type</td>
    <td>String</td>
	<td>是</td>
	<td>10</td>
	<td>商户生成签名字符串所使用的签名算法类型</td>
	<td>md5</td>
</tr>
<tr>
    <td>sign</td>
    <td>String</td>
	<td>是</td>
	<td>256</td>
	<td>商户请求参数的签名串</td>
	<td>详见示例</td>
</tr>
</table>

- 业务参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>coin_id</td>
    <td>int</td>
	<td>否</td>
	<td></td>
	<td>币种ID（默认0，如果指定币种，则获取该币种的价格，不指定则获取所有可用币种价格）</td>
	<td>1000</td>
</tr>
</table>

- 公共响应参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>return_code</td>
    <td>String</td>
	<td>是</td>
	<td>16</td>
	<td>返回状态码</td>
	<td>SUCCESS</td>
</tr>
<tr>
    <td>return_msg</td>
    <td>String</td>
	<td>是</td>
	<td>128</td>
	<td>返回状态码描述</td>
	<td>执行完成</td>
</tr>
</table>

```
*以下字段在return_code为SUCCESS时返回
```

<table data-hy-role="doctbl"> 
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>result_code</td>
    <td>String</td>
	<td>否</td>
	<td>16</td>
	<td>业务状态码</td>
	<td>SUCCESS</td>
</tr>
<tr>
    <td>return_msg</td>
    <td>String</td>
	<td>否</td>
	<td>16</td>
	<td>返回业务状态码描述</td>
	<td>查询成功</td>
</tr>
<tr>
    <td>sign</td>
    <td>String</td>
	<td>是</td>
	<td></td>
	<td>签名结果</td>
	<td>1234567890</td>
</tr>
</table>

```
*以下字段在return_code为FAIL时返回
```

<table data-hy-role="doctbl"> 
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>error_code</td>
    <td>String</td>
	<td>否</td>
	<td>32</td>
	<td>详见错误列表</td>
	<td>0</td>
</tr>
<tr>
    <td>error_msg</td>
    <td>String</td>
	<td>否</td>
	<td>128</td>
	<td>错误返回的信息描述</td>
	<td>ok</td>
</tr>
</table>

- 响应参数：
```
*以下字段在return_code为SUCCESS时，result_code为SUCCESS时返回
```
<table data-hy-role="doctbl"> 
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>coin_price_list</td>
    <td>json</td>
	<td>是</td>
	<td></td>
	<td>币种价格列表</td>
	<td></td>
</tr>
<tr>
    <td>coin_id</td>
    <td>int</td>
	<td>是</td>
	<td></td>
	<td>币种ID</td>
	<td>1000</td>
</tr>
<tr>
    <td>coin_code</td>
    <td>String</td>
	<td>是</td>
	<td>50</td>
	<td>币种代码</td>
	<td>BTC</td>
</tr>
<tr>
    <td>coin_name</td>
    <td>String</td>
	<td>是</td>
	<td>50</td>
	<td>币种名称</td>
	<td>Bitcoin</td>
</tr>
<tr>
    <td>subject</td>
    <td>String</td>
	<td>是</td>
	<td>16</td>
	<td>订单标题</td>
	<td>购买</td>
</tr>
<tr>
    <td>coin_name</td>
    <td>String</td>
	<td>是</td>
	<td>50</td>
	<td>币种名称</td>
	<td>Bitcoin</td>
</tr>
<tr>
    <td>total_fee</td>
    <td>String</td>
	<td>是</td>
	<td></td>
	<td>总金额</td>
	<td>单位与金额类型（currency_type）保持一致</td>
</tr>
<tr>
    <td>real_vol</td>
    <td>String</td>
	<td>是</td>
	<td></td>
	<td>用户实际支付量</td>
	<td>单位与币种代码（coin_code）保持一致</td>
</tr>
<tr>
    <td>hy_url</td>
    <td>String</td>
	<td>是</td>
	<td>128</td>
	<td>收银台url</td>
	<td>http://…</td>
</tr>
</table>


## 币种列表接口 

- 币种列表请求接口

> 请求URL:`http://www.ckpay.top/api/v1/coinlist`

> 请求方式:`POST`   

> 是否需要证书：`否`

> method：`ckpay.coin.list`

- 公共参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>method</td>
    <td>String</td>
	<td>是</td>
	<td>128</td>
	<td>具体业务接口名称</td>
	<td>ckpay.coin.list</td>
</tr>
<tr>
    <td>version</td>
    <td>String</td>
	<td>是</td>
	<td>10</td>
	<td>版本号,默认1.0</td>
	<td>1.0</td>
</tr>
<tr>
    <td>app_id</td>
    <td>String</td>
	<td>是</td>
	<td>32</td>
	<td>应用ID,商户的应用id</td>
	<td>ckp180809001000010000305E305D256</td>
</tr>
<tr>
    <td>mch_id</td>
    <td>String</td>
	<td>是</td>
	<td>32</td>
	<td>商户ID</td>
	<td>100001</td>
</tr>
<tr>
    <td>charset</td>
    <td>String</td>
	<td>是</td>
	<td>10</td>
	<td>编码格式默认为UTF-8</td>
	<td>UTF-8</td>
</tr>
<tr>
    <td>timestamp</td>
    <td>String</td>
	<td>是</td>
	<td>19</td>
	<td>发送请求的时间</td>
	<td>yyyyMMddHHmmss,20181031150802</td>
</tr>
<tr>
    <td>biz_content</td>
    <td>String</td>
	<td>是</td>
	<td>不限</td>
	<td>请求参数集合,Json格式,长度不限,具体参数见如下业务参数</td>
	<td>Json格式</td>
</tr>
<tr>
    <td>sign_type</td>
    <td>String</td>
	<td>是</td>
	<td>10</td>
	<td>商户生成签名字符串所使用的签名算法类型</td>
	<td>md5</td>
</tr>
<tr>
    <td>sign</td>
    <td>String</td>
	<td>是</td>
	<td>256</td>
	<td>商户请求参数的签名串</td>
	<td>详见示例</td>
<tr>
</table>

- 业务参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>is_open_coin_list</td>
    <td>int</td>
	<td>是</td>
	<td></td>
	<td>是否获取账号下已开启的支付币种列表,0=否(会返回所有可用币种列表),1=是</td>
	<td>1</td>
</tr>
</table>

- 公共响应参数

<table data-hy-role="doctbl">
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>return_code</td>
    <td>String</td>
	<td>是</td>
	<td>16</td>
	<td>返回状态码</td>
	<td>SUCCESS</td>
</tr>
<tr>
    <td>return_msg</td>
    <td>String</td>
	<td>是</td>
	<td>128</td>
	<td>返回状态码描述</td>
	<td>执行完成</td>
</tr>
</table>

```
*以下字段在return_code为SUCCESS时返回
```
<table data-hy-role="doctbl"> 
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>result_code</td>
    <td>String</td>
	<td>否</td>
	<td>16</td>
	<td>业务状态码</td>
	<td>SUCCESS</td>
</tr>
<tr>
    <td>return_msg</td>
    <td>String</td>
	<td>否</td>
	<td>16</td>
	<td>返回业务状态码描述</td>
	<td>查询成功</td>
</tr>
<tr>
    <td>sign</td>
    <td>String</td>
	<td>是</td>
	<td></td>
	<td>签名结果</td>
	<td>1234567890</td>
</tr>
</table>

```
*以下字段在return_code为FAIL时返回
```

<table data-hy-role="doctbl"> 
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>error_code</td>
    <td>String</td>
	<td>否</td>
	<td>32</td>
	<td>详见错误列表</td>
	<td>0</td>
</tr>
<tr>
    <td>error_msg</td>
    <td>String</td>
	<td>否</td>
	<td>128</td>
	<td>错误返回的信息描述</td>
	<td>ok</td>
</tr>
</table>

- 响应参数
```
*以下字段在return_code为SUCCESS时，result_code为SUCCESS时返回
```

<table data-hy-role="doctbl"> 
    <th>参数</th>
    <th>类型</th>
	<th>是否必填</th>
	<th>最大长度</th>
	<th>描述</th>
	<th>示例值</th>
</tr>
<tr>
    <td>coin_list</td>
    <td>json</td>
	<td>是</td>
	<td></td>
	<td>币种价格列表</td>
	<td></td>
</tr>
<tr>
    <td>coin_id</td>
    <td>int</td>
	<td>是</td>
	<td></td>
	<td>币种ID</td>
	<td>1000</td>
</tr>
<tr>
    <td>coin_code</td>
    <td>String</td>
	<td>是</td>
	<td>50</td>
	<td>币种代码</td>
	<td>BTC</td>
</tr>
<tr>
    <td>coin_name</td>
    <td>String</td>
	<td>是</td>
	<td>50</td>
	<td>币种名称</td>
	<td>Bitcoin</td>
</tr>
</table>




