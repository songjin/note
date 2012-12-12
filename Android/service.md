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