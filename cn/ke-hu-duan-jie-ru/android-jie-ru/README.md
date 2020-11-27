# Android

### Demo工程git克隆地址：

```groovy
git clone http://dnsdk.vimedia.cn:8080/r/VigameDemo-Android.git
```

## 第一步：添加maven仓库地址

```groovy
buildscript {
    repositories {
        google()
        jcenter()
        //添加 动能maven仓库 版本检测插件
        maven { url "http://dnsdk.vimedia.cn:8081/repository/vigame-public/" }
        //添加友盟仓库
        maven { url 'https://dl.bintray.com/umsdk/release' }
    }   
    dependencies {
        //添加 动能 版本检测插件
        classpath 'com.wb.check:plugin:1.0.3'
    }
}
```

```groovy
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

根目录下gradle.properties文件中添加：

```text
#魅族注释掉下面这句，其他的需要打开
android.enableJetifier=true

android.useAndroidX=true
android.injected.testOnly=false
```

## 第二步：引用插件

```groovy
//添加插件引用
apply plugin: 'Wb-check'
def WB = getPlugins().findPlugin('Wb-check')
```

## 第三步：引入仓库中的模块

```groovy
    //vigame相关模块
    implementation WB.fixVersions('Proxy:Features_new')
    implementation WB.fixVersions('Loader:VigameLoader')
    implementation WB.fixVersions('Core:CoreManager')
    implementation WB.fixVersions('Pay:PayManager')
    implementation WB.fixVersions('AD3:ADManager')
    implementation WB.fixVersions('TJ:TJManager')
    implementation WB.fixVersions('Social:SocialManager')
    implementation WB.fixVersions('Extention:ExtManager')
    //用到的第三方库
    implementation WB.fixVersions('Core:android-query')

    implementation 'androidx.multidex:multidex:2.0.1'
    implementation 'androidx.legacy:legacy-support-v4:1.0.0'
    implementation 'androidx.appcompat:appcompat:1.1.0'
    implementation 'pl.droidsonroids.gif:android-gif-drawable:1.2.6'
```

## 第四步：添加动能的混淆过滤文件

```text
buildTypes {

        release {
            minifyEnabled true
            shrinkResources false
            // 此处添加 'vigame_proguard.pro' 过滤sdk的混淆
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro', 'vigame_proguard.pro'  
            signingConfig signingConfigs.release
            zipAlignEnabled true
        }
    }
```

> 如果release版本不开启混淆，可跳过

## 第五步：添加框架代码调用

#### 1.修改应用的Application类。

在MyApplication类对应生命周期中加入模块的调用代码：

```java
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

或者

直接将MyApplication类继承VigameApplication：

```groovy
public class MyApplication extends VigameApplication {

}
```

#### 2.修改主Activity

> Unity游戏可跳过该步骤，将主Acitivity改为UniWbActivity或其子类即可。

在对应生命周期中加入VigameLoader模块的调用代码：

```java
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        VigameLoader.activityOnCreate(this);
        //模块初始化
        CoreNative.init();
    }
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

## 第六步：修改Manifest文件

添加相关的参数配置，并将VigameStartActivity设置为启动的Activit，application标签的android:name 设置为com.libVigame.VigameApplication 或 xxx.xx.x.MyApplication

```markup
 <application
        android:name="org.vigame.demo.MyApplication"
        >
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
    android:name="com.vigame.sdk.channel"
    android:value="${WB_CHANNEL}" />

<activity android:name="com.libVigame.VigameStartActivity"
    android:theme="@android:style/Theme.NoTitleBar.Fullscreen">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
 </application>
```

## 第七步：放入配置文件并修改

拷贝VigameConfig.xml和agrement.html到assets目录

通过assets文件夹中的ConfigVigame.xml进行配置，注意必须属性一定要设置，属性说明如下：

| 名称 | 解释 | 是否必须 |
| :--- | :--- | :--- |
| GameOpenActivity | 闪屏后进入的Activity路径名称 | 是 |
| ScreenOrientation | 屏幕方向 | 是 |
| IsSDK | 填true，请勿修改该标签 | 是 |
| CompanyIndex | 公司名称ID，默认填1 | 是 |
| SupportAdPositions | 支持的广告位名称 | 否 |
| WithSplashAD | 是否出现闪屏广告（默认出现） | 否 |
| Debug | true或false\(Vigamelog 是否输出的标志\) | 否 |
| NoSplash | 不显示开屏时设置为true,默认不设置 | 否 |
| AutoFullScreen | 是否把当前activity设置为全屏，默认为true | 否 |
| FixSpecialScreen | 是否适配刘海屏，默认为true | 否 |
| SplashTime | 闪屏持续时长，整数（单位毫秒） | 否 |
| DelaySplashAD | 闪屏持续多长时间后打开开屏广告,默认为0 | 否 |

## 第八步：配置测试相关项

#### 1.修改app/build.gradle文件，修改包名、渠道名、umeng参数

建议使用如下示例的包名，以方便广告展示

```groovy
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

