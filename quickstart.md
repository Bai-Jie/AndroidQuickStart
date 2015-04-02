#工具

* jdk >= 1.7
* Android SDK(通过SDK Manager安装)
* Android Studio(IDE，可选，推荐)
* Gradle(构建工具，必用，会自动下载，可以不安装)
* 版本管理工具(如：Git、SVN)
* 用于测试的Android手机和手机驱动程序（可选，推荐）

#教程

* 官网：http://developer.android.com/training/index.html
* 第三方翻译：http://hukai.me/android-training-course-in-chinese/



#[四大组件][App Components]

##Activities
和用户交互的接口。多个Activity合力构成一个应用，各个Activity负责一块特定的工作。以电子邮件应用为例，可以有负责查看邮件列表、撰写邮件、读邮件的三个Activity。

##Services
后台（无界面）执行长期操作或为远程进程工作。例如播放音乐、从网上下载数据。其它组件可以启动或绑定（和之交互）服务。

##Content Providers
提供可共享数据。它的数据可以来自本地文件、数据库、Web或其他应用可访问的持久存储位置。其它应用可以通过Content Provider查询甚至修改数据（Content Provider允许的话）。例如Android系统有管理联系人信息的Content Provider，拥有权限的应用可以读写特定联系人的信息。
即使不用向外共享数据，Content Provider对读写私有数据也很有用。

##Broadcast Receivers
Broadcast Receiver负责响应系统级广播公告。许多广播来自系统，如屏幕关闭、电量低、捕获了图片的广播。应用也可以发布广播，例如通告下载了些其他应用可以用的数据。
虽然Broadcast Receiver没有界面，但可以创建状态栏通知，通知用户发生了某事件。而更一般的情况是，Broadcast Receiver只作为其它组件的关口，它只做非常少的工作。例如启动服务来执行些与事件相关的工作。

##综合
Android的一个特点是应用可以使用其他应用的组件，例如如果应用想照张照片，可以用照相机应用的相应组件，应用不用包含照相机应用的代码，或有对其的链接。而是告诉系统你的意图，系统让照相机应用完成工作，再把照到的照片结果给应用使用。
所以应用不止一个入口（无main方法），也是Android的特色。

应用的组件和可实现的意图，都在Manifest文件中定义。
此外Manifest文件中还有
* 支持的API（Android版本）
* 需要的特性（如照相、蓝牙、多点触控等）
* 使用的权限
* 应用需要链接的API库（非Android框架的API），如Google地图库。
* …

res目录等资源

#[Activity生命周期][Activity Lifecycle]

* active or running
* paused
* stopped（内存中保持状态和成员信息）
* frozen state（系统资源不足时）

[Demo程序][Activity Lifecycle Demo]

##[Saving activity state][Saving activity state]
Activity的默认onSaveInstanceState()实现，自动调用布局中每个View的onSaveInstanceState()。但要保存状态信息的View要有ID（android:id熟悉）。如果没有ID，系统无法保存它的状态。

[App Components]:http://developer.android.com/guide/components/fundamentals.html#Components
[Activity Lifecycle]:http://developer.android.com/reference/android/app/Activity.html#ActivityLifecycle
[Activity Lifecycle Demo]:http://developer.android.com/training/basics/activity-lifecycle/index.html
[Saving activity state]:http://developer.android.com/guide/components/activities.html#SavingActivityState
