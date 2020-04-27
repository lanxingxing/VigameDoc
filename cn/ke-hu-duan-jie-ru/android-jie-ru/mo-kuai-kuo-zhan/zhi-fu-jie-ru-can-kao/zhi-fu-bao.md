# 支付宝

## 第一步：引入模块

修改build.gralde文件，加入支付宝所需模块:

```java
    implementation WB.fixVersions('Pay:AliPayLoader')
    implementation WB.fixVersions('Pay:AliPayApp')
```

> 以上两个模块有依赖关系，必须同时引入

## 第二步：配置计费信息

1.在assets目录添加ConfigPay.xml,用于配置手机在不同运营商模式下默认所使用的计费类型

```java
<Config>
    <DefalultPay>
        <DefalultOperator
            CMCC="alipay"
            UNICOM="alipay"
            TELECOM="alipay"
            Other="alipay"
        />
    </DefalultPay>
</Config>属性
```

DefalultOperator各属性含义如下

| 属性 | 含义 |
| :--- | :--- |
| CMCC | 移动运营商 |
| UNICOM | 联通 |
| TELECOM | 电信 |
| Other | 无卡 |

2.在assets目录添加feedata\_ali.xml，用于配置游戏中的计费点信息

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

