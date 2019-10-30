# Android

### Demo工程克隆地址：

[http://gitblit.vigame.cn:6300/r/VigameDemo-Android.git](http://gitblit.vigame.cn:6300/r/VigameDemo-Android.git)

## 第一步：添加maven仓库地址

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

        //动能maven仓库
        maven { url "http://dnsdk.vimedia.cn:8081/repository/vigame-public/" }

        //添加友盟仓库
        maven { url 'https://dl.bintray.com/umsdk/release' }
    }
}
```

## 第二步：引入仓库中的模块

```text
    //vigame相关模块
    implementation 'com.libVigame.Proxy:Features:2.6.2'
    implementation 'com.libVigame.Loader:VigameLoader:2.6.0'
    implementation 'com.libVigame.Core:CoreManager:2.4.6'
    implementation 'com.libVigame.Pay:PayManager:2.2.8'
    implementation 'com.libVigame.AD2:ADManager:2.3.8'
    implementation 'com.libVigame.TJ:TJManager:2.0.8'
    implementation 'com.libVigame.Social:SocialManager:2.1.8'
    implementation 'com.libVigame.Extention:ExtManager:2.0.1'
    //用到的第三方库
    implementation 'com.libVigame.Core:android-query:2.1.1'
    implementation 'com.android.support:support-v4:28.0.0'
    implementation 'com.android.support:appcompat-v7:28.0.0'
```

## 第三步：添加框架代码调用

修改MyApplication.java在对应生命周期中加入模块的调用代码：

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

修改MainActivity，在对应生命周期中加入VigameLoader模块的调用代码：

```text
    @Override
    protected void onResume() {
        super.onResume();
        VigameLoader.activityOnResume(this);
    }

    @Override
    protected void onPause() {
        super.onPause();
        VigameLoader.activityOnPause(this);
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        VigameLoader.activityOnDestroy(this);
    }
    @Override
    public void onWindowFocusChanged(boolean hasFocus) {
        super.onWindowFocusChanged(hasFocus);
        VigameLoader.activityOnWindowFocusChanged(this,hasFocus);
    }
    @Override
    protected void onActivityResult(int requestCode, int resultCode, @Nullable Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        VigameLoader.activityOnActivityResult(this,requestCode,resultCode,data);
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        VigameLoader.activityOnRestart(this);
    }
```

## 第四步：修改Manifest文件

添加相关的参数配置，并将VigameStartActivity设置为启动的Activity

```text
<meta-data
    android:name="com.vigame.sdk.appid"
    android:value="10001" />
<meta-data
    android:name="com.vigame.sdk.appkey"
    android:value="abcdefg" />
<meta-data
    android:name="com.vigame.sdk.prjid"
    android:value="333360" />
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
| WithSplashAD | 是否出现闪屏广告（默认出现） | 否 |
| IsSDK | 填true，请勿修改该标签 | 是 |
| CompanyIndex | 公司名称ID，默认填1 | 是 |

## 第六步：配置测试相关项

#### 1.修改app/build.gradle文件，修改包名、渠道名、umeng参数

建议使用如下示例的包名，以方便广告展示

```text
defaultConfig {
        applicationId "com.dn.tgxm.gg"
        ...
        manifestPlaceholders = [
                UMENG_APPKEY     : "",
                WB_CHANNEL       : "gg"
        ]
}
```

#### 2.修改开屏广告的背景

开屏广告默认内置一张白色背景，如需修改改背景文件，请将要替换的背景图放在res/drawable/目录并重命名为bg\_splash\_vigame.png。
