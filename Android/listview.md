http://www.vogella.com/articles/AndroidListView/article.html


- ArrayAdapter can handle data based on Arrays or java.util.List.

- SimpleCursorAdapter can handle database related data. This description focuses on the non database case.

The Android platform provides default layouts for rows in ListViews. For example android.R.layout.simple_list_item1. By default ArrayAdapter uses the android.R.id.text1 ID, but you can define another one in the ArrayAdapter constructor.

Layout

    <?xml version="1.0" encoding="utf-8"?>
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical" >

        <ListView
            android:id="@+id/mylist"
            android:layout_width="match_parent"
            android:layout_height="wrap_content" >
        </ListView>

    </LinearLayout> 


Activity

    ListView listView = (ListView) findViewById(R.id.mylist);
    String[] values = new String[] { "Android", "iPhone", "WindowsMobile",
      "Blackberry", "WebOS", "Ubuntu", "Windows7", "Max OS X",
      "Linux", "OS/2" };

    // First paramenter - Context
    // Second parameter - Layout for the row
    // Third parameter - ID of the TextView to which the data is written
    // Forth - the Array of data
    ArrayAdapter<String> adapter = new ArrayAdapter<String>(this,
      android.R.layout.simple_list_item_1, android.R.id.text1, values);

    // Assign adapter to ListView
    listView.setAdapter(adapter); 


listener

     listView.setOnItemClickListener(new OnItemClickListener() {
      @Override
      public void onItemClick(AdapterView<?> parent, View view,
        int position, long id) {
        Toast.makeText(getApplicationContext(),
          "Click ListItem Number " + position, Toast.LENGTH_LONG)
          .show();
      }
    }); 



自动义行


	package de.vogella.android.listactivity;

	import android.content.Context;
	import android.view.LayoutInflater;
	import android.view.View;
	import android.view.ViewGroup;
	import android.widget.ArrayAdapter;
	import android.widget.ImageView;
	import android.widget.TextView;

	public class MySimpleArrayAdapter extends ArrayAdapter<String> {
	  private final Context context;
	  private final String[] values;

	  public MySimpleArrayAdapter(Context context, String[] values) {
	    super(context, R.layout.rowlayout, values);
	    this.context = context;
	    this.values = values;
	  }

	  @Override
	  public View getView(int position, View convertView, ViewGroup parent) {
	    LayoutInflater inflater = (LayoutInflater) context
	        .getSystemService(Context.LAYOUT_INFLATER_SERVICE);
	    View rowView = inflater.inflate(R.layout.rowlayout, parent, false);
	    TextView textView = (TextView) rowView.findViewById(R.id.label);
	    ImageView imageView = (ImageView) rowView.findViewById(R.id.icon);
	    textView.setText(values[position]);
	    // Change the icon for Windows and iPhone
	    String s = values[position];
	    if (s.startsWith("iPhone")) {
	      imageView.setImageResource(R.drawable.no);
	    } else {
	      imageView.setImageResource(R.drawable.ok);
	    }

	    return rowView;
	  }
	} 

listactivity

package de.vogella.android.listactivity;

import android.app.ListActivity;
import android.os.Bundle;
import android.widget.ArrayAdapter;

public class MyListActivity extends ListActivity {
  public void onCreate(Bundle icicle) {
    super.onCreate(icicle);
    String[] values = new String[] { "Android", "iPhone", "WindowsMobile",
        "Blackberry", "WebOS", "Ubuntu", "Windows7", "Max OS X",
        "Linux", "OS/2" };
    ArrayAdapter<String> adapter = new ArrayAdapter<String>(this,
        android.R.layout.simple_list_item_1, values);
    setListAdapter(adapter);
  }
} 


