### THE JAVA CODE
```
package com.example.test;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;


public class MainActivity extends AppCompatActivity {

    // Declaration
    private EditText PassWord;  
    private Button Button;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        addListenerOnButton();      // This Listens to the Click On Create

    }

    private void addListenerOnButton(){

        // Casting the values
        PassWord = (EditText)findViewById(R.id.editText);
        Button = (Button)findViewById(R.id.button);

        Button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                
                // Generating the Toast Message
                Toast.makeText(MainActivity.this, PassWord.getText(), Toast.LENGTH_SHORT).show();
            }
        });
    }

}
```