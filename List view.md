### THE JAVA CODE
```
package com.example.test;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private static ListView ListView;
    private static String[] Names = new String[] { "Cyan", "Black", "Wulf", "Blue"};

    public void listView(){
        ListView = (ListView)findViewById(R.id.list);
        ArrayAdapter<String> adapter = new ArrayAdapter<String>(this, R.layout.namelist, Names);
        ListView.setAdapter(adapter);
        ListView.setOnItemClickListener(
                new AdapterView.OnItemClickListener() {
                    @Override
                    public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                        String value = String.valueOf(ListView.getItemAtPosition(position));
                        // String value = (String)ListView.getItemAtPosition(position);
                        Toast.makeText(MainActivity.this, "Position :" + position + " Value :" + value, Toast.LENGTH_SHORT).show();
                    }
                }
        );
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        listView();
    }
}
```


### ADDITIONAL XML 
- Create a new Layout XML file under layouts

    - namelist.xml  [ use to design the list layout ]
```
<TextView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:textSize="30sp">
</TextView>
```