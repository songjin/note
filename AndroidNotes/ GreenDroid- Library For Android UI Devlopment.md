[Green Droid](http://greendroid.cyrilmottier.com/) is a great open source library for Android UI Devlopment. And it's under Apache License, you can use it in commercial product.

Use the library is samlpe:

1. Under your project directory:  `git clone git://github.com/cyrilmottier/GreenDroid.git`

2. Open Eclipese, `New -> Android Project from Existing Code``, chose the directory of GreenDroid

3. You may need to fix some error. Becouse Eclipese will treat the GreenDroid-GoogleApis as Android Project and not link the Google API Library automatically. Chose the project's properties and select Android Tab, Change Project Build Path to Google APIs.

4. Create a new Android Application Project 

5. In your AndroidManifest.xml, go to the application tag and add `android:theme="@style/Theme.GreenDroid"` as a new attribute.

6. create you activity inheritiing from GDActivity and Put this code in you activity

      
		protected void onCreate(Bundle savedInstanceState) {
			super.onCreate(savedInstanceState);
			setActionBarContentView(R.layout.main);
		}

7. Run it ! 


