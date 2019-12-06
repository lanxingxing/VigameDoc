# Unity

## Clone URL of Demo：

### Unity Project：

[http://dnsdk.vimedia.cn:8080/r/UnityDemo.git](http://dnsdk.vimedia.cn:8080/r/UnityDemo.git)

### Android Studio Project：

[http://dnsdk.vimedia.cn:8080/r/UnityDemo-Google.git](http://dnsdk.vimedia.cn:8080/r/UnityDemo-Google.git)

## Unity plugin for download:

[UniWb.Wb](http://gui.vigame.cn/UniWb/wb/UniWb.Wb.unitypackage)

## Use

import into project.StreamingAssets/st.txt saved signature info,and you can insert signature info of yourself in this file.

UniWb/wb is interface，there are ADManger , CoreManger, PayManger, ToolManger, XyxManger

and interface is in the folder named 'interface' ， eg: AD is in AD/interface/ADBase

## Use interface

AD：

```text
      Wb.ADManager.Instance.OpenAd("banner");

      bool result = Wb.ADManager.Instance.IsAdReady(adName);

      Wb.ADManager.Instance.OpenAd("home_mfzs", result =>
        {
            if (result)
            {
                ShowBottomToast("video open success", false);
            }
            else
            {
                ShowBottomToast("video open fail", true);
            }
        });
```

View base class,you can find functions witch is implemented.

## Android

implementation module in app/build.gradle

```java
implementation 'com.libVigame.bridge:UnityBridge:1.0.8'
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

Your main Activity inherits UniWbActivity , and the interface that interacts with unity is visible in the UniWbActivity class.

You can also use UniWbActivity Activity directly.

## Signature verification

```text
 Wb.CoreManager.Instance.CheckSignature();
```

At the beginning of the game, if signature verification is required, the method is called and the st.txt file saves the hash of the signature.

st.txt is in StreamingAssets

st.txt 内容

-49852205,1765204456

## Signature configuration

Download [vigame\_signature\_tool](http://gui.vigame.cn/signtool/vigame签名获取工具.apk)

Sign the above apk with the signature to be added, and then add the signature information obtained in the above tool to the st.txt file

