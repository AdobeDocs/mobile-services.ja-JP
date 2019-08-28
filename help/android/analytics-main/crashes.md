---
description: この情報は、クラッシュの追跡方法と、誤ったクラッシュを処理するためのベストプラクティスを理解する場合に役立ちます。
seo-description: この情報は、クラッシュの追跡方法と、誤ったクラッシュを処理するためのベストプラクティスを理解する場合に役立ちます。
seo-title: アプリのクラッシュの追跡
solution: Marketing Cloud、Analytics
title: アプリのクラッシュの追跡
topic: 開発者と導入
uuid: 3ab98c14- ccdf-4060- ad88- ec07c1c6bf07
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# アプリのクラッシュを追跡 {#track-app-crashes}

この情報は、クラッシュの追跡方法と、誤ったクラッシュを処理するためのベストプラクティスを理解する場合に役立ちます。

>[!TIP]
>
>アプリのクラッシュは、ライフサイクル指標の一部として追跡されます。クラッシュを追跡するには、プロジェクトにライブラリを追加して、ライフサイクルを実装します。詳しくは、コア実装および *ライフサイクル* で [、"SDKおよび設定ファイルのIntelliJ IDEAまたはEclipseプロジェクトへの追加」を参照](/help/android/getting-started/dev-qs.md)してください。

ライフサイクル指標を実装すると、各アクティビティの `Config.collectLifecycleData` メソッドで `OnResume` が呼び出されます。`onPause` メソッドで、呼び出しが `Config.pauseCollectingLifeCycleData`おこなわれます。

`pauseCollectingLifeCycleData` の内部では、正常終了を示すフラグが設定されます。アプリが再起動または再開されると、`collectLifecycleData` がこのフラグをチェックします。アプリがフラグステータスのとおり正常に終了しなかった場合は、次の呼び出しで `a.CrashEvent` コンテキストデータが送信され、クラッシュイベントがレポートされます。

正確なクラッシュレポートが生成されるようにするには、各アクティビティの `pauseCollectingLifeCycleData` メソッド内で `onPause` を呼び出す必要があります。次の Android アクティビティのライフサイクル図を参照してください。この呼び出しが重要である理由がわかります。

![](assets/android-lifecycle.png)

Android アクティビティのライフサイクルについて詳しくは、[アクティビティ](https://developer.android.com/guide/components/activities.html)を参照してください。

*この Android のライフサイクルの図は、[Android Open Source Project](https://source.android.com/)によって作成および共有され、[Creative Commons 2.5 Attribution License](https://creativecommons.org/licenses/by/2.5/)の条項に従って使用されています。*

## 誤ったクラッシュがレポートされる原因

1. Android Studio などの IDE を使用してデバッグしている場合、アプリがフォアグラウンドにあるときに IDE からアプリを再度起動するとクラッシュが発生します。

   >[!TIP]
   >
   >アプリケーションをバックグラウンドでバックグラウンドに切り替えてからIDEから再度起動すると、このクラッシュを回避できます。

1. If the last foreground Activity of your app is backgrounded and does not call `Config.pauseCollectingLifecycleData();` in `onPause`, and your app is manually closed or killed by the OS, the next launch results in a crash.

## フラグメントの処理方法

フラグメントには、アクティビティと同様のアプリケーションライフサイクルイベントがあります。ただし、フラグメントは、アクティビティにアタッチしないとアクティブにできません。

>[!IMPORTANT]
>
>コードを含むアクティビティを含むライフサイクルイベントに依存する必要があります。これはフラグメントの親ビューで処理されます。

## （オプション）アクティビティライフサイクルコールバックの実装

API レベル 14 以降、Android では、アクティビティに対するグローバルライフサイクルコールバックが許可されます。For more information, see [Application](https://developer.android.com/reference/android/app/Application).

You can use these callbacks to ensure that all of your Activities correctly call `collectLifecycleData()` and `pauseCollectingLifecycleData()`. このコードは、メインのアクティビティと、アプリを起動する他のアクティビティにのみ追加する必要があります。

```js
import com.adobe.mobile.Config; 
  
public class MainActivity extends Activity { 
... 
    @Override 
    protected void onCreate(Bundle savedInstanceState) { 
        super.onCreate(savedInstanceState); 
        setContentView(R.layout.activity_main); 
  
        getApplication().registerActivityLifecycleCallbacks(new Application.ActivityLifecycleCallbacks() { 
            @Override 
            public void onActivityResumed(Activity activity) { 
                Config.setContext(activity.getApplicationContext()); 
                Config.collectLifecycleData(activity); 
            } 
  
            @Override 
            public void onActivityPaused(Activity activity) {     
                Config.pauseCollectingLifecycleData(); 
            } 
    
            // the following methods aren't needed for our lifecycle purposes, but are required to be implemented 
            // by the ActivityLifecycleCallbacks object 
            @Override 
            public void onActivityCreated(Activity activity, Bundle savedInstanceState) {} 
            @Override 
            public void onActivityStarted(Activity activity) {} 
            @Override 
            public void onActivityStopped(Activity activity) {} 
            @Override 
            public void onActivitySaveInstanceState(Activity activity, Bundle outState) {} 
            @Override 
            public void onActivityDestroyed(Activity activity) {} 
        }); 
    } 
... 
}
```

To send additional context data with your lifecycle call by using `Config.collectLifecycleData(Activity activity`, `Map<String`, `Object> contextData)`, you must override the `onResume` method for that Activity and ensure that you call `super.onResume()` after manually calling `collectLifecycleData`.

```js
@Override 
protected void onResume() { 
    HashMap<String, Object> cdata = new HashMap<>(); 
    cdata.put("someKey", "someValue"); 
    Config.collectLifecycleData(this, cdata); 
  
    super.onResume(); 
}
```

