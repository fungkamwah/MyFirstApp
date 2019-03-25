# MyFirstApp


# 1创建项目
安装好Android Studio，下载并配置好相关开发包资源后，我们开始创建并运行第一个Android应用。
## 1.1创建新项目
运行Andriod并点击『Create New Project』打开创建窗口，选择『Phone and Tablet』下面的『Add No Activity』,然后下一步。
![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-130857.png)

填写应用名称及应用包名，PackageName是APP的唯一标识，每个安卓的应用的PackageName都应该是不同的。
Minimum API level是指本次创建的应用支持安卓系统的最低版本，图中可见当前85%以上的安卓手机运行的是5.0以上的系统版本。

![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-132513.png)

点击『Finish』，等待项目创建完成。
把项目目录视图切换为『Project』，如下图。

![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-133646.png)  切换视图为![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-135625.png)

此时项目虽然已创建，但并非可运行调试的。如图所示。![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-135904.png)

## 1.2创建Activity
Activity为安卓应用中四大组件之一，也是开发中最频繁接触的内容。可先理解为APP的界面，一个Activity相当于APP的一个界面。
关于Activity的详细介绍请参考[：http://www.runoob.com/w3cnote/android-tutorial-activity.html](http://www.runoob.com/w3cnote/android-tutorial-activity.html)

下面开始创建Activity及其布局layout
在app/src/main/java中右键应用的包名，选择『New』--『Java Class』
![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-142028.png)
填写类名Name 并继承android.app.Activity

![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-142413.png)

创建完MainActivity.java

```
package net.gzchunxiang.myfirstapp;

import android.app.Activity;

public class MainActivity extends Activity {
    
}
```

## 1.3创建layout
接着创建此Activity要显示的内容布局文件，在app/src/main/res目录下创建layout文件夹
，在该文件夹下新建资源文件，右键『New』-『Layout Resource file』创建.xml格式的资源文件。

![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-143457.png)
![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-143724.png)

填写文件名'layout_main'，Root element根元素'LinearLayout'。
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

</LinearLayout>
```

得到layout_main.xml，是一个只有根元素，没有具体内容布局文件，现在我们给它添加一个'Hello World!'。如下
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">
    
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Hello World!"/>

</LinearLayout>
```

## 1.4给Activity指定layout
在MainActivity.java中重写onCreate方法如下
```
package net.gzchunxiang.myfirstapp;

import android.app.Activity;
import android.os.Bundle;

public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.layout_main);
    }
}
```
setContentView方法中，R表示应用的资源文件，这里我们给Activity指定内容视图为上面创建的layout_main.xml


# 2运行应用项目
## 2.1指定默认Activity
些时项目仍然是无法运行，![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-135904.png)。

虽然已经创建了第一个Activity，仍虽在配置清单文件AndroidManifest.xml进行一些配置。

![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-151513.png)

```
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="net.gzchunxiang.myfirstapp">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme"
        tools:ignore="GoogleAppIndexingWarning">

        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```
在文件添加了一个activity元素，并指定了Mainactivity为应用启动时的默认Activity。此时APP状态变为可运行调试了![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-153923.png)

## 2.2在手机或模拟器上运行
点击三角形运行按钮，待项目编译加成后弹出选择框，选择要运行的真机或模拟器并确认。

*基本上使用真机做开发调试了，用模拟器实在是慢，很耗内存的。*

![http://po1d0nnr5.bkt.clouddn.com/QQ20190311-154607.png](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-154607.png)

等待应用部署到设备上，最后可看到运行效果。

![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-155056.png)

项目运行成功，默认打开了MainActivity，展示了对应的layout_main的内容。

*AS ERROR: x86 emulation currently requires hardware acceleration!报错解决傻瓜教程[https://blog.csdn.net/qq_38280242/article/details/81253278](https://blog.csdn.net/qq_38280242/article/details/81253278)*

***如果电脑硬件架构不支持x86的话，尝试选择其他架构的镜像创建模拟器。不过推荐使用真机做开发调试，用模拟器实在是慢，很耗内存。***

关于Activity的详细介绍请参考[：http://www.runoob.com/w3cnote/android-tutorial-activity.html](http://www.runoob.com/w3cnote/android-tutorial-activity.html)

## 2.3调试工具Logcat
可使用Logcat工具查看输出日志。
![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-160120.png)

可以在代码使用Log类进行各级别的打印，以便在logcat中进行观察调试。
```
package net.gzchunxiang.myfirstapp;

import android.app.Activity;
import android.os.Bundle;
import android.util.Log;

public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.layout_main);
        Log.i("Tag","MainActivity 的 onCreate方法");
    }
}
```
重新运行项目，观察logcat打印的内容。
![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-160743.png)


## 2.4 Debug工具
也可以通过debug的方式运行应用，进行断点调试。
![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190311-161211.png)





---


*Android项目工程相关解析，请自行查阅：[ http://www.runoob.com/w3cnote/android-tutorial-project-src-analysis.html](http://www.runoob.com/w3cnote/android-tutorial-project-src-analysis.html)*
