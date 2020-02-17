# Android

### Clone URL of Demo：

[http://dnsdk.vimedia.cn:8080/r/VigameDemo-Android-Google.git](http://dnsdk.vimedia.cn:8080/r/VigameDemo-Android-Google.git)

## 1:Add maven repositories

```text
buildscript {
    repositories {
        google()
        jcenter()
    //vigame plugin
    maven { url 'http://gui.vigame.cn/plugin/' }
        //umeng
        maven { url 'https://dl.bintray.com/umsdk/release' }
    }    
}
```

```text
allprojects {
    repositories {
        google()
        jcenter()

        //vigame
        maven { url "http://dnsdk.vimedia.cn:8081/repository/vigame-public/" }

        //umeng
        maven { url 'https://dl.bintray.com/umsdk/release' }
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
    //vigame modules
    implementation WB.fixVersions('Proxy:Features')
    implementation WB.fixVersions('Loader:VigameLoader')
    implementation WB.fixVersions('Core:CoreManager')
    implementation WB.fixVersions('Pay:PayManager')
    implementation WB.fixVersions('AD2:ADManager')
    implementation WB.fixVersions('TJ:TJManager')
    implementation WB.fixVersions('Social:SocialManager')
    implementation WB.fixVersions('Extention:ExtManager')

    //third library
    implementation WB.fixVersions('Core:android-query')
    implementation 'com.android.support:support-v4:28.0.0'
    implementation 'com.android.support:appcompat-v7:28.0.0'
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
                WB_PRJID:"333361",
                AppsFlyer_DevKey:"X9NxxaMp4neHCFYreDxtd5",
                WB_CHANNEL:"gg"
        ]
}
```

#### 2. Modify the background of Splash AD.

If needs,repalace "bg\_splash\_vigame.png" file in res/drawable.

