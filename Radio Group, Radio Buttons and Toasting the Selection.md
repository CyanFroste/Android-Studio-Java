### THE JAVA CODE
```
package com.example.test;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.Toast;


public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    private static RadioGroup RadioGroup;
    private static RadioButton RB;
    private static Button Button;

    public void onClick(View v){
        RadioGroup = (RadioGroup)findViewById(R.id.RGFruits);
        Button = (Button)findViewById(R.id.button);

        int RBID = RadioGroup.getCheckedRadioButtonId();
        RB = (RadioButton)findViewById(RBID);
        Toast.makeText(MainActivity.this, RB.getText().toString()+" Is Submitted", Toast.LENGTH_SHORT).show();

    }
}
```