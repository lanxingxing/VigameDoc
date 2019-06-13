# Android接入

## 第一步：添加本地maven仓库

```text
buildscript {
    repositories {
        google()
        jcenter()
        //添加友盟仓库
        maven { url 'https://dl.bintray.com/umsdk/release' }
    }    
}
```

```text
allprojects {
    repositories {
        google()
        jcenter()

        //公司maven仓库
        maven {
            url "http://192.168.1.252:8081/repository/Vigame/"
        }
        maven {
            url "http://192.168.1.252:8081/repository/VigameSnapshot/"
        }
        //添加友盟仓库
        maven { url 'https://dl.bintray.com/umsdk/release' }
    }
}
```


## 第二步：引入仓库中的模块

```text
    //vigame相关模块
    implementation 'com.libVigame.Proxy:Features:2.4.8'
    implementation 'com.libVigame.Loader:VigameLoader:2.4.1'
    implementation 'com.libVigame.Core:CoreManager:2.3.8'
    implementation 'com.libVigame.Pay:PayManager:2.2.0'
    implementation 'com.libVigame.AD2:ADManager:2.3.1'
    implementation 'com.libVigame.Social:SocialManager:2.1.6'
    implementation 'com.libVigame.Extention:ExtManager:2.0.1'
    implementation 'com.libVigame.TJ:TJManager:2.0.5'
    implementation 'com.android.support:support-v4:28.0.0'
    implementation 'com.android.support:appcompat-v7:28.0.0'
    implementation 'com.libVigame.Core:android-query:2.1.1'
```

## 第三步：添加框架代码调用

修改MyApplication.java和MainActivity，在各生命周期中加入模块的调用代码。

```text
public class MyApplication extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        VigameLoader.applicationOnCreate(this);
    }

    @Override
    protected void attachBaseContext(Context base) {
        super.attachBaseContext(base);
        VigameLoader.applicationAttachBaseContext(this, base);
    }
}
```

```text
    VigameLoader.activityOnCreate(this);
    VigameLoader.activityOnDestroy(this);
    VigameLoader.activityOnResume(this);
    VigameLoader.activityOnPause(this);
    VigameLoader.activityOnWindowFocusChanged(this,hasFocus);
    VigameLoader.activityOnActivityResult(this, requestCode, resultCode, data);
    VigameLoader.activityOnRestart(this);
```

## 第四步：修改Manifest文件

```text
<meta-data
    android:name="com.vigame.sdk.appid"
    android:value="10001" />
<meta-data
    android:name="com.vigame.sdk.appkey"
    android:value="abcdefg" />
<meta-data
    android:name="com.vigame.sdk.prjid"
    android:value="10001" />
<meta-data
    android:name="com.vigame.purchase.channel"
    android:value="${WB_CHANNEL}" />

<activity android:name="com.libVigame.VigameStartActivity"
    android:theme="@android:style/Theme.NoTitleBar.Fullscreen">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```

## 第五步：放入配置文件并修改

拷贝VigameConfig.xml和agrement.html到assets目录

通过assets文件夹中的ConfigVigame.xml进行配置，属性说明如下：

| 名称 | 解释 | 是否必须 |
| :--- | :--- | :--- |
| GameOpenActivity | 闪屏后进入的Activity路径名称 | 是 |
| ScreenOrientation | 屏幕方向 | 是 |
| SupportAdPositions | 支持的广告位名称 | 否 |
| SplashFile | 默认的闪屏文件（assets中） | 否 |
| WithSplashAD | 是否出现闪屏广告（默认出现） | 否 |
| Permissions | 申请的权限 | 是 |

![](https://github.com/jieban0604/VigameDoc/tree/8cf06273fbae0bd555693ae2a1ebc6cfade8f391/kuai-su-ji-cheng-zhi-nan/C:/Users/宇/AppData/Local/YNote/data/qq0736283A0554F655E0818672E0467D30/022399cbb449476daaa9614d980f7b7e/clipboard.png)

