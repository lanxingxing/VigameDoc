# UnityWb 运营接口 

​	

## 下载地址

[UniWb.Wb](http://gui.vigame.cn/UniWb/wb/UniWb.Wb.unitypackage)



## 使用

​	导入到工程后，有两个文件夹，**StreamingAssets/st.txt**  保存的是签名的信息，若需要新的签名则可以添加在这个文件中。

​	UniWb/wb 是业务接口，主要有 ADManger , CoreManger, PayManger, ToolManger, XyxManger 

接口在对应的 interface 文件夹下， 例如 AD 在 AD/interface/ADBase



## 接口使用

​	AD：

```c#
      Wb.ADManager.Instance.OpenAd("banner");
     
      bool result = Wb.ADManager.Instance.IsAdReady(adName);

      Wb.ADManager.Instance.OpenAd("home_mfzs", result =>
        {
            if (result)
            {
                ShowBottomToast("视频广告打开成功", false);
            }
            else
            {
                ShowBottomToast("视频广告打开失败", true);
            }
        });
```


其它 Manger 如此，查看 Base 基类，可比较方便的查看已实现的方法。



## Android 接入

在  build.gradle 中引入 

```java
implementation 'com.libVigame.bridge:UnityBridge:1.0.2'
```



```java
package org.cocos2dx.cpp;
import android.os.Bundle;
import com.vigame.unitybridge.UniWbActivity;

public class AppActivity extends UniWbActivity 
{    
@Override  
   protected void onCreate(Bundle savedInstanceState) 
   {       
   		super.onCreate(savedInstanceState);  
   }
}
```



Activity 继承 UniWbActivity 即可， 与 unity 交互的 接口在 UniWbActivity 类中，可查看。

也可直接 使用 UniWbActivity   Activity 



## 签名验证

```c#
 Wb.CoreManager.Instance.CheckSignature();
```

在游戏开始的时候，如果需要签名验证，调用该方法， st.txt 文件保存签名信息。

## 签名配置

下载地址 [vigame签名获取工具](http://gui.vigame.cn/signtool/vigame签名获取工具.apk)

​	 用待添加的签名，签名上述apk，然后再 st.txt 文件里添加上述工具中获取到的签名信息

