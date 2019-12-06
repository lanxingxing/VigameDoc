# 微信支付

## 第一步：引入模块

修改build.gralde文件，加入微信支付所需模块:

```groovy
implementation WB.fixVersions('Social:WeChat')
implementation WB.fixVersions('Pay:WeChatPay')
```

{% hint style="info" %}
以上两个模块有依赖关系，必须同时引入
{% endhint %}

## 第二步：添加入口文件

在{$包名}/wxapi目录下，添加WXPayEntryActivity.java文件，内容如下

```java
package com.dn.tgxm.gg.wxapi;


import android.app.Activity;
import android.content.Intent;
import android.os.Bundle;

import com.libSocial.WeChat.WeChatPayActivityHandler;

public class WXPayEntryActivity extends Activity {
    private WeChatPayActivityHandler weChatPayActivityHandler = null;

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        weChatPayActivityHandler = new WeChatPayActivityHandler();
        weChatPayActivityHandler.onCreate(this);
        this.finish();
    }

    @Override
    protected void onNewIntent(Intent intent) {
        super.onNewIntent(intent);
        if (weChatPayActivityHandler != null) {
            weChatPayActivityHandler.onNewIntent(intent);
        }
    }
}
```

## 第三步：配置计费信息

1.在assets目录添加ConfigPay.xml,用于配置手机在不同运营商模式下默认所使用的计费类型

```java
<Config>
    <DefalultPay>
        <DefalultOperator
            CMCC="wx"
            UNICOM="wx"
            TELECOM="wx"
            Other="wx"
        />
    </DefalultPay>
</Config>属性
```

DefalultOperator用来配置手机在不同运营商模式下所使用的计费类型，各属性含义如下

| 属性 | 含义 |
| :--- | :--- |
| CMCC | 移动运营商 |
| UNICOM | 联通 |
| TELECOM | 电信 |
| Other | 无卡 |

2.在assets目录添加feedata\_wx.xml，用于配置游戏中的计费点信息

```java
<?xml version="1.0" encoding="utf-8"?>
<data>
  <feeinfo>
    <ID>1</ID>
    <price>1</price>
    <desc>20钻石</desc>
  </feeinfo>

  <feeinfo>
    <ID>2</ID>
    <price>1200</price>
    <desc>50钻石</desc>
  </feeinfo>

</data>

```

feeinfo标签表示一条计费点信息，属性说明如下：

| 名称 | 类型 | 解释 |
| :--- | :--- | :--- |
| ID | int | 计费点ID |
| price | int | 价格 |
| desc | string | 计费点描述 |

## 注意事项

* 包名需使用申请微信支付能力时的包名
* 签名需使用申请支付时的签名，一般情况下为我方签名。如测试需要可联系我方技术人员协助签名
* 需要在真实包名文件路径下放置wxapi/WXPayEntryActivity.java文件



