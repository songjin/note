创建一个服务（当然要在Manifest中注册）


	public class update extends Service {
	
		@Override
		public IBinder onBind(Intent intent) {
			// TODO Auto-generated method stub
			return null;
		}
	
	}
	
	
	
启动或者暂停服务

	startService(new Intent(this, update.class));
	stopService(new Intent(this, update.class));


用一个内部类继承Thread来定时在后台开启服务

	private class DoSomething extends Thread {
	
	
		public void run(){
			While (runFlag) {
				doSomething();
				Thread.sleep(DELAY);
			}
		}
	
	}
	
	
	
将组件放入独立的进程中,可以通过配置文件的 process 参数来实现,代码如下:
			// 在service配置信息中,增加process 
		<service android:name="SimpleService"
		android:process=":a_unique_process_name"/>
		但这样的方式会增加进程开销。因此,另一种可行的策略是在服务组件中另起一个 独立的线程,将那些耗时又费力的操作交给它来打理。