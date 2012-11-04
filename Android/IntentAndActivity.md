	
	
	
	Intent intent = new Intent(Intent.ACTION_VIEW,Uri.parse(data));
	// data可以是http://也可以是tel://.如果定义的是tel://110就是给110打电话
	startActivity(intent)
	
	