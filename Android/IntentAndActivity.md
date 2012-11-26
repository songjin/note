	
	###　启动活动
	
	Intent intent = new Intent(Intent.ACTION_VIEW,Uri.parse(data));
	// data可以是http://也可以是tel://.如果定义的是tel://110就是给110打电话
	startActivity(intent)
	
	

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
    