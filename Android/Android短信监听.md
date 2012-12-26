  	 
  	 
  	 Intent intent = new Intent("android.provider.Telephony.SMS_RECEIVED");
     List<ResolveInfo> infos = getPackageManager().queryBroadcastReceivers(intent, 0);
     for (ResolveInfo info : infos) {
         Log.d("HELLO","Receiver name:" + info.activityInfo.name + "; priority=" + info.priority);
     }


输出日志：


	12-18 20:45:58.077: D/HELLO(4714): Receiver name:cn.com.fetion.android.receivers.FetionReceiver; priority=2147483647
	12-18 20:45:58.077: D/HELLO(4714): Receiver name:com.qq.AppService.MainReceiver; priority=2147483647
	12-18 20:45:58.077: D/HELLO(4714): Receiver name:com.tencent.qqphonebook.component.remote.SmsReceiver; priority=2147483647
	12-18 20:45:58.077: D/HELLO(4714): Receiver name:com.wandoujia.phoenix2.receivers.SmsReceivedReceiver; priority=2147483647
	12-18 20:45:58.077: D/HELLO(4714): Receiver name:com.OnTheWay2.MyReceiver; priority=2147483647
	12-18 20:45:58.077: D/HELLO(4714): Receiver name:info.linxiangyu.autosms.SMSReceiver; priority=2147483647
	12-18 20:45:58.077: D/HELLO(4714): Receiver name:com.ti.bluetooth.map.SmsEventReceiver; priority=0
	12-18 20:45:58.077: D/HELLO(4714): Receiver name:com.android.mms.transaction.PrivilegedSmsReceiver; priority=0			
	12-18 20:45:58.077: D/HELLO(4714): Receiver name:com.htc.usage.receiver.MessageReceiver; priority=0
	12-18 20:45:58.077: D/HELLO(4714): Receiver name:net.hidroid.hinet.receiver.SmsReceiver; priority=0



reciver里面写一个
abortBroadcast();// 中止发送
就能终止发送


拦截<http://www.eoeandroid.com/thread-148381-1-1.html>