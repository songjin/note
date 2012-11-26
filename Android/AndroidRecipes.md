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


### DP,SP
-  字体一般用SP，可以根据首选项放大缩小
-  其他用DP


### Menu



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
	
### 弹出式菜单

public class MainActivity extends Activity {

	
AlertDialog actions;

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        setTitle("Hello World");
        Button  button= new Button(this);
        button.setText("Click for Option");
        button.setOnClickListener(buttOnClickListener);
        
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Hello, I'm a DialogAlert");
        String []optionStrings = {
        		"Delete Item",
        		"Copy Item",
        		"Edit Item"
        };
        builder.setItems(optionStrings, actionListener);
        builder.setNegativeButton("Cancel", null);
        actions = builder.create();
        
        setContentView(button);
    }
    
    DialogInterface.OnClickListener actionListener = 
    		new DialogInterface.OnClickListener( ) {
				
				@Override
				public void onClick(DialogInterface dialog, int which) {
					// TODO Auto-generated method stub
					switch (which) {
					case 0:
						break;
					case 1:
						break;
					case 2:
						break;
					default:
						break;
					}
				}
			};
			
	View.OnClickListener buttOnClickListener = new View.OnClickListener(	) {
		
		@Override
		public void onClick(View v) {
			// TODO Auto-generated method stub
			actions.show();
			
		}
	};
        

 
### 监听按键

重载onKeyDown，　onKeyup方法

	@Override
	public boolean onKeyDown(int keyCode, KeyEvent event) {
		// TODO Auto-generated method stub
		if (keyCode == KeyEvent.KEYCODE_BACK) {
			
			return true;
		}
		return super.onKeyUp(keyCode, event);
	}
	
API Level5以上提供专门的方法

	@Override
    public void onBackPressed() {
    		setTitle("OOXX");
    }
    
### 通过监听按键启动活动

	@Override
	public boolean onKeyDown(int keyCode, KeyEvent event) {
		// TODO Auto-generated method stub
		if (keyCode == KeyEvent.KEYCODE_BACK) {
			Intent intent = new Intent(Intent.ACTION_MAIN);
	        intent.addCategory(Intent.CATEGORY_APP_MAPS);
	        startActivity(intent);
	        return true;
		}
		return super.onKeyDown(keyCode, event);
	}
	
### 监听TextView


通过`implements TextWather`

 	@Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        text = new EditText(this);
        text.addTextChangedListener(this);
        setContentView(text);
    }
    
    
	@Override
	public void onTextChanged(CharSequence s, int start, int before, int count) {
		// TODO Auto-generated method stub
		textCount = text.getText().length();
		setTitle(String.valueOf(textCount));
	}
	
### synchronized
　java中的synchronized是线程锁定
　
### 自定义TextView

	
	public class Currency implements TextWatcher {
		boolean mEditing;

		public Currency() {
			mEditing = false;
		}
		
		
		@Override
		public void afterTextChanged(Editable s) {
			// TODO Auto-generated method stub
			if (!mEditing) {
				mEditing = true;
				String dight = s.toString().replaceAll("\\D", "");
				NumberFormat nf = NumberFormat.getCurrencyInstance();
				try {
					String formatted = nf.format(Double.parseDouble(dight)/100);
					s.replace(0, s.length(), formatted);
				}catch (NumberFormatException nfe) {
					s.clear();
				}
				mEditing = false;
			}
			
		}

		@Override
		public void beforeTextChanged(CharSequence s, int start, int count,
				int after) {
			// TODO Auto-generated method stub
			
		}

		@Override
		public void onTextChanged(CharSequence s, int start, int before,
				int count) {
			// TODO Auto-generated method stub
			
		}
		
	}
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        text  = new EditText(this);
        text.addTextChangedListener(new Currency());
        setContentView(text);
    }
    
 
## 文字滚动
 	@Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        TextView tickerTextView = (TextView)findViewById(R.id.ticker);
        tickerTextView.setSelected(true);
    }
    
    
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:singleLine="true"
        android:id="@+id/ticker"
        android:scrollHorizontally="true"
        android:ellipsize="marquee"
        android:marqueeRepeatLimit="marquee_forever"
        android:text="fdasfasfdsafklasfmdksalmflasfmdlasfmlasf
        fdasfsadaaaaaaaaaa"
      />
      
TextView的android:ellipsize可以定义超出边界的时候的行为。

- none 直接裁掉
- start 开头裁，有一个省略号
- middle　中间裁，有一个省略号
- end　末尾裁，一个省略号
- marquee　滚动

###　自定义背景布局


在drawable定义一个xml文件　`background.xml`

	<?xml version="1.0" encoding="utf-8"?>
	<shape xmlns:android="http://schemas.android.com/apk/res/android" 
	    android:shape="rectangle">
	    
	    <gradient
	        android:startColor="#111111"
	        android:endColor="#989898"
	        android:type="linear"
	        android:angle="270"
	     />
	    
	</shape>
 	   

 就可以在布局中用`android:background="@drawable/background"`定义背景了。这里实现的是一个渐变颜色的效果。
 
 
### 把Activity弄成对话框一样


修改Activity主题

 		<activity
            android:name=".MainActivity"
            android:label="@string/title_activity_main" 
            android:theme="@android:style/Theme.Dialog">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    
    
 代码里面给TextView弄一点留白
    
    	TextView tView = new TextView(this);
        tView.setText("fdasfsafas");
        tView.setPadding(12, 21, 12, 21);
        setContentView(tView);
        
        
### 创建不同布局的资源文件

对于不同的方向，资源文件名后面添加-land 或者　-port

不同尺寸，资源文件名后面添加-small, -medium或者-large，-xlarge（注意是屏幕物理尺寸）

### 发送短信

 
	private void sendSMS(String message, String phoneNumber) {
		SmsManager sms = SmsManager.getDefault();
		List<String> texts = sms.divideMessage(message);

		for (String text : texts) {
			sms.sendTextMessage(phoneNumber, null, message, null, null);
			Log.i("sms", "send a message");
		}
	}
	
### 显示网页

要打开Internet权限


	　　　WebView webview = new WebView(this);
        webview.getSettings().setJavaScriptEnabled(true);
        webview.loadUrl("http://linxiangyu.info");
        setContentView(webview);
        
        
        
 loadView 乱码
 
 
 	http://www.eoeandroid.com/thread-990-1-1.html
        
    如果单纯显示文字的话可以写webView.loadDataWithBaseURL(null, string, "text/html", "utf-8", null);

	
	如果要显示图片可以写webView.loadDataWithBaseURL(baseUrl, string, "text/html", "utf-8", null);
	其中baseUrl为你存储照片的路径，比如：
	String baseUrl="file:///sdcard/images/photo/";
	
http://blog.sina.com.cn/s/blog_4c0706560100r8qy.html
	
	2.      许多实用loadData方法的朋友都遇到显示乱码的问题，那是因为编码器设置错误导致的。我们知道String类型的数据主要是unicode编码，而WebView一般为了节省资源使用的是UTF-8编码，所以我们在loadData的时候要告诉方法怎样转码。即要告诉它要将unicode编码的内容转成UTF-8编码的内容。有些朋友虽然在loadData的时候设置了编码方式，但是还是显示乱码，这是因为还需要为WebView的text编码指定编码方式。举例如下：
               WebView wv = (WebView)findViewById(R.id.webview) ;
                      String content = getUnicodeContent() ;
               wv.getSettings().setDefaultTextEncodingName(“UTF -8”) ;
               wv.loadData(content, “text/html”, “UTF-8”) ;
        
### WebView 显示本地图片或资源

	loadURL("file:///android_asset/android.jpg");
	
	loadData(htmlString, "text/html", "utf-8");//htmlString是一个html格式的字符串
	
### 下载图片

注：这个程序运行的时候意外退出


建立WebImageView类


	package com.example.teset;
	
	import java.io.BufferedInputStream;
	import java.io.InputStream;
	import java.net.URL;
	import java.net.URLConnection;
	
	import org.apache.http.util.ByteArrayBuffer;
	
	import android.content.Context;
	import android.graphics.Bitmap;
	import android.graphics.BitmapFactory;
	import android.graphics.drawable.BitmapDrawable;
	import android.graphics.drawable.Drawable;
	import android.os.AsyncTask;
	import android.util.AttributeSet;
	import android.widget.ImageView;
	
	public class WebImageView extends ImageView {
		private Drawable mPlaceholder, mImage;
		
	
	public WebImageView (Context context) {
		this(context, null);
		
	}
	
	public WebImageView (Context context, AttributeSet attrs) {
		this(context, null, 0);
		
	}
	
	public WebImageView (Context context, AttributeSet attrs,int defualtStyle) {
		super(context, null, defualtStyle);
		
	}
	
	
	public void setPlaceholderImage(Drawable drawable) {
		mPlaceholder = drawable;
		if (mImage == null) 
			setImageDrawable(mPlaceholder);
	}
	

	public void setPlaceholderImage(int resid) {
		mPlaceholder = getResources().getDrawable(resid);
		if (mImage == null) {
			setImageDrawable(mPlaceholder);
		}
	}
	
	public void  setImageUrl(String url) {
		DownlandTask task = new DownlandTask();
		task.execute(url);
	}
		
		
	private class DownlandTask extends AsyncTask<String, Void, Bitmap> {

		@Override
		protected Bitmap doInBackground(String... params) {
			// TODO Auto-generated method stub
			String url = params[0];
			try {
				URLConnection connection = (new URL(url)).openConnection();
				InputStream is = connection.getInputStream();
				BufferedInputStream bis = new BufferedInputStream(is);
				ByteArrayBuffer baf = new ByteArrayBuffer(50);
				int current = 0;
				while ((current = bis.read()) != -1) {
						baf.append((byte)current);
				}
				byte [] imageData = baf.toByteArray();
				return BitmapFactory.decodeByteArray(imageData, 0, imageData.length);
			} catch (Exception e) {
				return null;
				// TODO: handle exception
			}
		}
			
			
			@SuppressWarnings("deprecation")
			@Override
			protected void onPostExecute(Bitmap result) {
				mImage = new BitmapDrawable(result);
				if (mImage != null) {
					setImageDrawable(mImage);
				}
			}
			

	}
}


主程序调用

			WebImageView imageView = (WebImageView)findViewById(R.id.webImage);
	        //imageView.setPlaceholderImage(R.drawable.icon);
	        //imageView.setImageUrl("http://www.ruby-lang.org/images/logo.gif");
	        
	       
	       
layout声明

因为不属于Android包，所以必须有完整声明


    <com.examples.WebImageView
        android:id = "@+ id/webImage"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
      />

注意：Android的UI类都是非线程安全的。一样要在主程序中用回调方法来更新UI，不要在doInBackground中更新。




	@Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.activity_main, menu);
        return true;
    }
	}



##  解析JSON

JSON太多引号转义，Java又没有原始字符串，就不写了。

另外还有.getJSONOBject方法

		try {
        	JSONObject personJsonObject = (new JSONObject(JSON_STRING).getJSONObject("person"));
        	String name line1 = personJsonObject.getString("name");
        	line1.setText("The person's name is" + name );
        	line2.setText(name + "has" + personJsonObject.getJSONArray("chrildred").length + "chirldren");
        	
        }catch (JSONException e) {
        	e.printStackTrace();
        }
