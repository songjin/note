		 <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />

---




		LocationManager locMan = (LocationManager) getSystemService(Context.LOCATION_SERVICE);
		Location loc = locMan.getLastKnownLocation(LocationManager.GPS_PROVIDER);
		if (loc != null) {
			double lat = loc.getLatitude();
			long x = loc.getTime();
			Log.d("LXY", "latitude: " +x);
		}

		locMan.requestLocationUpdates(LocationManager.GPS_PROVIDER, 60000, 10, 
				new LocationListener() {
				//分别是更新的时间(毫秒)，距离

			@Override
			public void onStatusChanged(String provider, int status, Bundle extras) {
				// TODO Auto-generated method stub


			}

			@Override
			public void onProviderEnabled(String provider) {
				// TODO Auto-generated method stub

			}

			@Override
			public void onProviderDisabled(String provider) {
				// TODO Auto-generated method stub

			}

			@Override
			public void onLocationChanged(Location location) {
				// TODO Auto-generated method stub
				if (location != null) {
					double lat = location.getLatitude();
					Log.d("LXY", "latitude: " + lat);

				}

			}
		});
	}

