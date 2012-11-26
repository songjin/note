
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


