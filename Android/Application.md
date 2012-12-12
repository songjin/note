Android的App里面，Application保存各对象的共享的状态。App里面任何一个组建在运行，Application对象都会被系统创建并维护。


创建一个Application：

		public class HelloApplication extends Application {
			public String hello = "Hello World. I'm From Hello Application";
			@Override
			public void onCreate() {
				// TODO Auto-generated method stub
				super.onCreate();
			}
		
			@Override
			public void onTerminate() {
				// TODO Auto-generated method stub
				super.onTerminate();
			}
	
		}
		
在Manifest里面把Application的Android:name属性改成自己的Application的名字。

然后就可以调用Application里面的对象了

	 HelloApplication app = (HelloApplication)getApplication();
	 app.hello　// => "Hello World. I'm From Hello Application"
        