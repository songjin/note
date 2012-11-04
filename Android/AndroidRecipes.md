### 自定义窗口　

AndroidMainfest.xml 里面的android:theme

* 使用系统主题
* 使用自定义主题　res/values/styles.xml定义
* 代码里定义

		使用Activity.requestWindowFeature(),
		在setContentView()之前定义
		
		super.onCreate(savedInstanceState);
		requestWindowFeature(Window.FEATURE_NO_TITLE);
		//设置一个没有标题的窗口
		setContentView(R.layout.activity_main);
		
			
		//设置一个进度条
		super.onCreate(savedInstanceState);
	    requestWindowFeature(Window.FEATURE_PROGRESS);
	    setContentView(R.layout.activity_main);
	    
	    setProgressBarVisibility(true);
	    setProgress(0);
	    setProgress(10000);//进度条到100%的时候消失
	    
	   //设置另一种进度条
		super.onCreate(savedInstanceState);
		requestWindowFeature(Window.FEATURE_INDETERMINATE_PROGRESS);
		setContentView(R.layout.activity_main);
		setProgressBarIndeterminateVisibility(true);
		
		另外还有FEATURE_LEFT_ICON,FEATURE_RIGHT_ICON可以定义标题左侧，右侧的小图标等
		
### 代码中添加视图

		LinearLayout layout = (LinearLayout) getLayoutInflater().inflate(
        R.layout.activity_main, null);
        Button reset = new Button(this);
        reset.setText("Reset Form");
        layout.addView(reset, new LinearLayout.LayoutParams(LayoutParams.MATCH_PARENT,
        LayoutParams.WRAP_CONTENT));
        setContentView(layout);
           		
           		
### 监听点击

在XML布局中加入

	android:onClick="lis"    		
		
在源代码中就可以用lis方法监听

	public void lis(View v) {
		reset.setText("Hello, I am after click");
   	}
   	
### 图片分辨率适配

- ldpi:120dpi  75% of mdpi
- mdpi:160dpi
- hdpi:240dpi   150%
- xhdpi:320dpi   200%

### 锁定活动方向

在AndroidManifest.xml中的<activity>标签中设置
	`android:screenOrientation=" "`可以改变活动方向。
	
- portrait　纵向
- landscape 横向
- behind 和前一个活动栈的activity一样

### 动态改变方向

	setRequestedOrientation(ActivityInfo.SCREEN_ORIENTATION_LANDSCAPE);

可以读取当前方向信息


	int current =  getResources().getConfiguration().orientation;


	


### 按钮监听

- http://blog.csdn.net/rhljiayou/article/details/7061201

		button.setOnClickLisener(this)
		
		public void on Click(View v){ 
		}


### 菜单选项

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button button = new Button(this);
        button.setText("Click For Opition");
        button.setOnClickListener( new OnClickListener() {
			@Override
			public void onClick(View v) {
				openContextMenu(v);
			}
        }
		);
        registerForContextMenu(button);
        setContentView(button);
    }

   
    
    
    @Override
	public boolean onContextItemSelected(MenuItem item) {
		// TODO Auto-generated method stub
		switch (item.getItemId()) {
		case R.id.menu_delete:
			return true;　// Do Some Delete
		case R.id.menu_copy:
			return true;
		case R.id.menu_edit:
			return true;
		default:
			break;
		}
		return super.onContextItemSelected(item);
	}
### DP,SP
-  字体一般用SP，可以根据首选项放大缩小
-  其他用DP


### Menu

	@Override
	public void onCreateContextMenu(ContextMenu menu, View v,
			ContextMenuInfo menuInfo) {
		// TODO Auto-generated method stub
		super.onCreateContextMenu(menu, v, menuInfo);
		getMenuInflater().inflate(R.menu.activity_main, menu);
		menu.setHeaderTitle("Chose an Opition");
	}

XML文件是这样的

	<menu xmlns:android="http://schemas.android.com/apk/res/android">
    
    <item android:id="@+id/menu_delete"
        android:title="Delete Item"/>
    
    <item 
        android:id="@+id/menu_copy"
        android:title="Copy Item"
        
        />
    
    <item 
        android:id="@+id/menu_edit"
        android:title="Edit Item"
        />
	</menu>

		
### Log
- .d() debug
- .e() error
- .i() info
- .w() warnning
- .wtf() what the fuck…

### 多线程

	class getImage extends AsyncTask<String, String, String> {

		@Override
		protected String doInBackground(String... params) {
		}
    }
    
 - doInBackgroud  后台
 - onProgressUpdate 更新状态
 - onPostExecute 执行完毕触发
 
 调用new getImage.execute(args)触发
 
### Toast
	Toask.makeText(…).show;
### 监听输入框变化

	editText.addTextChangedListener(this)
	
	public void afterTextChanged(Editavle statusText) {
		doSomething
	}
此外还有

- beforeTextChanged
- onTextChanged

### 色彩
可以用ARGB的格式：
	
	android:background = "cfff"
	
			