# GooglePlay

## 模块引入

```text
    implementation WB.fixVersions('Pay:GooglePlay')
```

## 配置文件说明

```text
无需特殊配置，带上计费文件即可
```

## 混淆过滤

```text
-keep class com.android.vending.billing.**
```

## 集成测试

如何判断sdk是否初始化成功？
```text
通过GooglePayAgent查看日志，当日志输出“Init success,The BillingClient is ready”则证明初始化成功。
```

## 问题说明

```text
1.初始化失败：
  日志报：Init failed,The BillingClient is not ready,code=3
  1）可能是google play service版本太旧，2）SDK版本太旧，3）vpn地域不支持，4）国内手机不支持。
  解决方法：a.先验证环境。在商店下载一个有内购的应用，看能否进行内购。b.如果别人的能进行内购之后，再次测试你的应用，看是否正常，来确认应用的支付环境   是否正常。
  
2. 能够查询价格，但无法购买，提示"商品无法购买"之类。
  这是基础配置问题，有以下可能：版本号与线上版本不对应，测试版本却不是测试账号(大概率)，签名不对应。

3. 能调起弹窗，但是弹窗内容是内部错误，日志为“getDebugMessage==An internal error occurred”的，建议更换VPN。

4. 能够查询价格，但无法调起支付都没有弹窗，错误码:3，报错：Error:In-app billing error: Null data in IAB activity resul。
   原因是没有给Google play商店弹窗权限，国内很多手机都有弹窗权限管理，特别是小米，如果没允许，是不会有任何提示，并且拦截了的。(这个问题在新版的gp商    店已经不存在）

5. 支付提示成功，但却走onQueryFail回调，并且返回的商品列表为null。
   这是因为你调错了方法，记得purchaseInApp是内购的，purchaseSubs是订阅的。查询的时候同理。另外查询的时候报错，很有可能是你setSKUS的时候传了一个空    字符串，而不是空数组。

6. 查询的时候返回的商品列表长度为0。
   setSkus的时候将内购sku和订阅sku的参数顺序弄错了，应该是第一个是内购的，第二个参数是订阅的。
   或者是商品还没有发布成功，需要等待一段时间(很有可能，新发布的商品是无论怎么查询还是购买，谷歌那边都是没有响应的)
7.错误码总结：

        响应代码	                           值	       说明
BILLING_RESPONSE_RESULT_OK	                 0	成功
BILLING_RESPONSE_RESULT_USER_CANCELED	         1	用户按上一步或取消对话框
BILLING_RESPONSE_RESULT_SERVICE_UNAVAILABLE	 2	网络连接断开
BILLING_RESPONSE_RESULT_BILLING_UNAVAILABLE	 3	所请求的类型不支持 Billing API 版本(支付环境问题)
BILLING_RESPONSE_RESULT_ITEM_UNAVAILABLE	 4	请求的商品已不再出售。
BILLING_RESPONSE_RESULT_DEVELOPER_ERROR	         5	提供给 API 的参数无效。此错误也可能说明未在 Google Play 中针对应用内购买结算正确签署或设置                                                     应用，或者应用在其清单中不具备所需的权限。
BILLING_RESPONSE_RESULT_ERROR	                 6	API 操作期间出现严重错误
BILLING_RESPONSE_RESULT_ITEM_ALREADY_OWNED	 7	未能购买，因为已经拥有此商品
BILLING_RESPONSE_RESULT_ITEM_NOT_OWNED	         8	未能消费，因为尚未拥有此商品
```

