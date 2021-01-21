# Android

### Clone URL of Demo：

[http://dnsdk.vimedia.cn:8080/summary/VigameDemo-Android-Google.git](http://dnsdk.vimedia.cn:8080/summary/VigameDemo-Android-Google.git)

## 1:Add maven repositories

```text
buildscript {
    repositories {
        jcenter()
        google()
        //WB plugin
        maven { url "http://dnsdk.vimedia.cn:8081/repository/vigame-public/" }
    }
    dependencies {
        classpath 'com.wb.check:plugin:1.0.3'
        //WB plugin
        classpath 'com.android.tools.build:gradle:3.2.1'
    }
}
```

```text
allprojects {
    repositories {
        jcenter()
        google()
        //WB maven
        maven { url "http://dnsdk.vimedia.cn:8081/repository/vigame-public/" }

        maven {
            url  "https://dl.bintray.com/ironsource-mobile/android-adapters/"
        }
        maven {
            url "https://dl.bintray.com/ironsource-mobile/android-sdk"
        }
    }
}
```

## 2：Apply Plugin

```groovy
apply plugin: 'Wb-check'
def WB = getPlugins().findPlugin('Wb-check')
```

## 3：Implementation modules

```groovy
    //vigame common modules
    implementation WB.fixVersions('Proxy:Features_new')
    implementation WB.fixVersions('Loader:VigameLoader')
    implementation WB.fixVersions('Core:CoreManager')
    implementation WB.fixVersions('Pay:PayManager')
    implementation WB.fixVersions('AD3:ADManager')
    implementation WB.fixVersions('Social:SocialManager')
    implementation WB.fixVersions('Extention:ExtManager')
    implementation WB.fixVersions('TJ:TJManager')
    implementation WB.fixVersions('Core:PushService')
    implementation WB.fixVersions('Push:PHManager')

    //third library
    implementation WB.fixVersions('Core:android-query')
    implementation 'com.android.support:support-v4:28.0.0'
    implementation 'com.android.support:appcompat-v7:28.0.0'
    
    //vigame google channel modules
    implementation WB.fixVersions('AD3:Ironsource_JuHe')
    implementation WB.fixVersions('Pay:GooglePlay')
    implementation WB.fixVersions('TJ:Facebook')
    implementation WB.fixVersions('TJ:AppsFlyer')
```

## 4：Add proguard config

```text
buildTypes {

        release {
            minifyEnabled true
            shrinkResources false
            // here added 'vigame_proguard.pro'
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro', 'vigame_proguard.pro'  
            signingConfig signingConfigs.release
            zipAlignEnabled true
        }
    }
```

> If the release version does not enable minify, you can skip

## 5：Add code in the project

#### 5.1 Modify Application.java

Add code in the corresponding life cycle in MyApplication class:

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

Or

Made your MyApplication class inherit VigameApplication:

```groovy
public class MyApplication extends VigameApplication {

}
```

#### 5.2 Modify the main Activity

> Unity games can skip this step and change the main Acitivity to UniWbActivity or its subclasses.

Modify MainActivity And add code in the corresponding life cycle：

```text
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        VigameLoader.activityOnCreate(this);
        //init sdk
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

## 6. Modify AndroidManifest.xml

Add related parameter configuration, And use VigameStartActivity as launch item.

```text
       <meta-data
            android:name="com.vigame.sdk.appid"
            android:value="${WB_AppId}" /><!--15265-->
       <meta-data
            android:name="com.vigame.sdk.appkey"
            android:value="${WB_AppKey}" />
        <meta-data
            android:name="com.vigame.sdk.prjid"
            android:value="${WB_PRJID}" /><!--10001,20350,333360-->

        <meta-data
            android:name="com.vigame.sdk.channel"
            android:value="${WB_CHANNEL}" />

        <activity android:name="com.libVigame.VigameStartActivity"
            android:theme="@android:style/Theme.NoTitleBar.Fullscreen"
            android:screenOrientation="portrait"
            >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <!--MainActivity-->
        <activity android:name="org.cocos2dx.cpp.AppActivity"
                  android:label="@string/app_name"
                  android:screenOrientation="portrait"
                  android:theme="@android:style/Theme.NoTitleBar.Fullscreen"
                  android:configChanges="orientation|keyboardHidden|screenSize"
            >
            <meta-data android:name="unityplayer.UnityActivity" android:value="true" />
        </activity>
```

## 7. Put in the configuration file and modify

Copy VigameConfig.xml and agrement.html to assets dictionary.

And You can configurate ConfigVigame.xml in assets. Property description is as follows:

| Name | description | necessary |
| :--- | :--- | :--- |
| GameOpenActivity | the path of your main Activity | yes |
| ScreenOrientation | the orientation of screen | no |
| SupportAdPositions | the adPositionName of supports | no |
| WithSplashAD | Support splash ad | no |
| IsSDK | 'true' always and don't modify | yes |
| CompanyIndex | the index of company，default 1 | yes |

## 8：Configuration items of test

#### 1.Open app/build.gradle，modify package/channel/umeng appkey.

Recommendation the package name as follows for Advertising display

```groovy
defaultConfig {
        applicationId "com.gzsj.game.hw"
        ...
        manifestPlaceholders = [
                WB_PRJID    : "333361",
                WB_CHANNEL: "google",
                WB_AppId :"37683 ",
                WB_AppKey:"wfm542g5dc40n0qmynbtxhthj2kdnhcm7gc99fs1ts8jloayyz",
                ADMOB_APP_ID: "ca-app-pub-7851203648968517~5682113463",
                AppsFlyer_DevKey:"X9NxxaMp4neHCFYreDxtd5"
        ]
}
```

#### 2. Modify the background of Splash AD.

If needs,repalace "bg\_splash\_vigame.png" file in res/drawable.

