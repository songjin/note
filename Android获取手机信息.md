在android系统中获取imei号和其他手机信息
如果需要通过android SDK获取手机相关信息。需要通过如下方式获取：
	
	 TelephonyManager telephonyManager=(TelephonyManager) this.getSystemService(Context.TELEPHONY_SERVICE);
	String imei=telephonyManager.getDeviceId();
不过，光这么写，会有类似如何查看android产生的异常的报错，主要是因为android的权限需要打开，在AndroidManifest.xml文件中增加：

	 <uses-permission android:name="android.permission.READ_PHONE_STATE" />
就可以拿到手机的imei号了。


TelephonyManager还有其他方法可以调用，获取手机的其他信息。

比如获取手机号码，可以这样：

	telephonyManager.getLine1Number();

不过在g1手机上测试，使用移动全球通的sim卡，无法得到手机号码，是个空字符串。

获取手机的sim卡号：

	telephonyManager.getSimSerialNumber();

这个可以在上述环境下得到。

获取客户id，在gsm中是imsi号：

	telephonyManager.getSubscriberId();

这个也能在商户环境得到。