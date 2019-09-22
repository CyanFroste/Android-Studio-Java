### THE JAVA CODE
```
package com.example.test;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.Toast;


public class MainActivity extends AppCompatActivity {    

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    public void OnCheckClick(View v){
        if(((CheckBox)v).isChecked()){
            Toast.makeText(MainActivity.this, ((CheckBox)v).getText().toString()+" Is Selected", Toast.LENGTH_LONG).show();
        }
    }

    public void onClick(View v){
        CheckBox Chk1 = (CheckBox)findViewById(R.id.CBHorse);
        CheckBox Chk2 = (CheckBox)findViewById(R.id.CBRabbit);
        CheckBox Chk3 = (CheckBox)findViewById(R.id.CBWolf);
        Button Button = (Button)findViewById(R.id.button);

        StringBuffer result = new StringBuffer();
        result.append("Horse: ").append(Chk1.isChecked());
        result.append("\nRabbit: ").append(Chk2.isChecked());
        result.append("\nWolf: ").append(Chk3.isChecked());

        Toast.makeText(MainActivity.this, result.toString(), Toast.LENGTH_LONG).show();
    }
}
```