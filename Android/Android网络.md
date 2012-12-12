检测网络情况	
	
	
	public void myClickHandler(View view) {
	  
	    ConnectivityManager connMgr = (ConnectivityManager) 
	        getSystemService(Context.CONNECTIVITY_SERVICE);
	    NetworkInfo networkInfo = connMgr.getActiveNetworkInfo();
	    if (networkInfo != null && networkInfo.isConnected()) {
	        // fetch data
	    } else {
	        // display error
	    }
	    
	}
	
	
			
	import android.content.Context;
	import android.net.ConnectivityManager;
	import android.net.NetworkInfo;
	import android.util.Log;
	
	public class CheckNet {
	    public static boolean checkNetwork(Context context) {
		try {
		    ConnectivityManager connectivity = (ConnectivityManager) context
			    .getSystemService(Context.CONNECTIVITY_SERVICE);
	
		    if (connectivity != null) {
	
			NetworkInfo info = connectivity.getActiveNetworkInfo();
	
			if (info == null || !info.isAvailable())
			    return false;
			else
			    return true;
		    }
		} catch (Exception e) {
		    e.printStackTrace();
		}
		return false;
	    }
	}



	private static final String DEBUG_TAG = "NetworkStatusExample";
	...      
	ConnectivityManager connMgr = (ConnectivityManager) 
	        getSystemService(Context.CONNECTIVITY_SERVICE);
	NetworkInfo networkInfo = connMgr.getNetworkInfo(ConnectivityManager.TYPE_WIFI); 
	boolean isWifiConn = networkInfo.isConnected();
	networkInfo = connMgr.getNetworkInfo(ConnectivityManager.TYPE_MOBILE);
	boolean isMobileConn = networkInfo.isConnected();
	Log.d(DEBUG_TAG, "Wifi connected: " + isWifiConn);
	Log.d(DEBUG_TAG, "Mobile connected: " + isMobileConn);
	
	
	
	
	public boolean isOnline() {
	    ConnectivityManager connMgr = (ConnectivityManager) 
	            getSystemService(Context.CONNECTIVITY_SERVICE);
	    NetworkInfo networkInfo = connMgr.getActiveNetworkInfo();
	    return (networkInfo != null && networkInfo.isConnected());
	}  