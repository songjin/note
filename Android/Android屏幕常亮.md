taaw.com归纳下在Android手机开发程序中控制屏幕长亮的方法。


首先Android长亮是有PowerManager下的类WakeLock对象管理的。以下是具体方法。 
A、屏幕控制需要对应的权限permission声明

<uses-permission android:name="android.permission.WAKE_LOCK" />

B、启用屏幕长亮

PowerManager manager = ((PowerManager)getSystemService(POWER_SERVICE)); 
WakeLock wakeLock = manager.newWakeLock(PowerManager.SCREEN_BRIGHT_WAKE_LOCK| PowerManager.ON_AFTER_RELEASE, "ATAAW"); 
wakeLock.acquire();

C、关闭屏幕长亮只需要将对象释放掉

wakeLock.release();"")""
