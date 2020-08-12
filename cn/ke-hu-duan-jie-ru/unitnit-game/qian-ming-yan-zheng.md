# 签名验证

## 签名验证

在游戏开始的时候，如果需要签名验证，调用该方法

```text
 Wb.CoreManager.Instance.CheckSignature();
```

StreamingAssets/st.txt 文件保存默认签名 加密后的哈希值，内容为：kDiJOe7UjhVAbaGa7qTIIuFZo1fVMThwKsLeFVlk0AY=

如需添加自己的签名，可下载地址 [vigame签名获取工](http://gui.vigame.cn/signtool/vigame签名获取工具.apk)[具](http://gui.vigame.cn/signtool/vigame签名获取工具.apk)。

[加密工具下载](http://gui.vigame.cn/WbAESGUI/WbAESGUI.exe)

然后用待添加的签名，签名上述apk，用加密工具加密签名的哈希值， 然后在 st.txt 文件里添加上述工具中获取到的签名信息 （注意明文签名用英文逗号分割）。

![UniWb01](../../../.gitbook/assets/WbAESGUI%20.png)

## 

