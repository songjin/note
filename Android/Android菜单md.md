侧滑菜单

<http://stackoverflow.com/questions/8657894/android-facebook-style-slide>



Activity中按Menu显示的菜单：

	　 @Override
	    public boolean onCreateOptionsMenu(Menu menu) {
	        getMenuInflater().inflate(R.menu.activity_main, menu);
	        return true;
	    }
	
		@Override
		public boolean onOptionsItemSelected(MenuItem item) {
			switch (item.getItemId()) {
			case R.id.menu_settings:
				startActivity(new Intent(this,PrefsActivity.class));
				//启动菜单Activity
			}
		
			return super.onOptionsItemSelected(item);
		}
		
其中`activity_main`内容：

		<menu xmlns:android="http://schemas.android.com/apk/res/android">
		    <item android:id="@+id/menu_settings"
		        android:title="@string/menu_settings"
		        android:orderInCategory="100"
		        android:showAsAction="never" />
		</menu>
		

PrefsActivity

	public class PrefsActivity extends PreferenceActivity {

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        addPreferencesFromResource(R.menu.prefs);
        
    }
    
res/menu/prefs.xml

	<?xml version="1.0" encoding="utf-8"?>
	<PreferenceScreen xmlns:android="http://schemas.android.com/apk/res/android" >
	
	    <EditTextPreference
	        android:key="username"
	        android:summary="Enter you user name"
	        android:title="UserName" >
	    </EditTextPreference>
	    <EditTextPreference
	        android:key="password"
	        android:summary="Enter you user password"
	        android:title="Password" >
	    </EditTextPreference>
	
	</PreferenceScreen>
	
在程序中调用

	SharedPreferences prefs;
	prefs = PreferenceManager.getDefaultSharedPreferences(this);
	String username = prefs.getString("username", "hello, I'm defualt");      
	      
首选项可能改变，所以要实现监听的接口

	public class MainActivity extends Activity  implements OnSharedPreferenceChangeListener　｛
	
	prefs.registerOnSharedPreferenceChangeListener((OnSharedPreferenceChangeListener) this);
	

	
	
	@Override
	public void onSharedPreferenceChanged(SharedPreferences sharedPreferences,
			String key) {
		
	}
	
	｝
	
当然在Manifest中要注册PrefsActivity
	
