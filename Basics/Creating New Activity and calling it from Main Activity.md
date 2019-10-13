![How-To](https://github.com/CyanFroste/Android-Studio-Java/blob/master/img/new-activity.png)

### THE JAVA CODE
```
package com.example.test;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

    }

    public void onClick(View v){
        Intent Branch = new Intent(MainActivity.this, Branch.class);
        startActivity(Branch);
    }
}
```
