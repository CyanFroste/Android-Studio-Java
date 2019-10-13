### THE JAVA CODE
```
package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.ArrayAdapter;
import android.widget.AutoCompleteTextView;

public class MainActivity extends AppCompatActivity {

    AutoCompleteTextView autoText;
    String[] Countries = {"America", "Australia", "Albania" , "Algeria", "Argentina", "Austria" };

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        autoText = (AutoCompleteTextView)findViewById(R.id.autoComplete);
        ArrayAdapter adapter = new ArrayAdapter(this, android.R.layout.select_dialog_item, Countries);
        // The value defines how many characters need to be entered for it to suggest
        autoText.setThreshold(1);
        autoText.setAdapter(adapter);
    }
}
```