# 桌面图标

## 1.创建桌面图标

> 在QQ、OPPO、Vivo、华为小游戏上生效

方法接口：

```text
dnsdk.installShortcut(object);
```

参数说明：

### Object object

| 参数 | 参数类型 | 是否必传 | 描述 |
| :--- | :--- | :--- | :--- |
| success | function | 否 | 接口调用成功的回调函数 |
| fail | function | 否 | 接口调用失败的回调函数 |
| complete | function | 否 | 接口调用结束的回调函数 |

示例代码：

```text
dnsdk.installShortcut({
    success : function () {
        console.log("添加到桌面success");
    },
    fail:function (err) {
        console.log("添加到桌面fail:"+ JSON.stringify(err));
    },
    complete:function () {
        console.log("添加到桌面complete");
    }
});
```

