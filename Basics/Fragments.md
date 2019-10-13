![Create New Fragments under layouts](https://github.com/CyanFroste/Android-Studio-Java/blob/master/Images/new-fragment.png)

### THE JAVA CODE
```
package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;
import androidx.fragment.app.FragmentManager;
import androidx.fragment.app.FragmentTransaction;
import android.os.Bundle;
import android.view.View;

public class MainActivity extends AppCompatActivity {


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    public void changeFragment(View v){

        if(v == findViewById(R.id.button1)){
            FragOne fragment = new FragOne();
            FragmentManager FM = getSupportFragmentManager();
            FragmentTransaction FT = FM.beginTransaction();
            FT.replace(R.id.fragmentPlaceholder, fragment);
            FT.commit();
        }
        if(v == findViewById(R.id.button2)){
            FragTwo fragment = new FragTwo();
            FragmentManager FM = getSupportFragmentManager();
            FragmentTransaction FT = FM.beginTransaction();
            FT.replace(R.id.fragmentPlaceholder, fragment);
            FT.commit();
        }
    }
}
```

XML

Add the xml code to the main_activity.xml file
```
<fragment
        
    android:name="com.example.myapplication.FragOne"    // name of the initial fragment in the placeholder

    android:id="@+id/fragmentPlaceholder"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
</fragment>
```
