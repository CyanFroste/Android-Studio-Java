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

    private EditText PassWord;
    private Button Button;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

        // View is the Superclass of Every UI Component        
    public void onButtonClick(View v) {

        // Assigning Values to Variables from IDs of elements in the interface
        // Each Element in the interface possess an ID

        EditText Num1 = (EditText)findViewById(R.id.txtNum1);
        EditText Num2 = (EditText)findViewById(R.id.txtNum2);
        TextView Sum = (TextView)findViewById(R.id.txtSum);    
        EditText SumBox = (EditText)findViewById(R.id.txtsumBox);

        int No1 = Integer.parseInt(N1.getText().toString());

        int No2 = Integer.parseInt(N2.getText().toString());

        // Setting text to TextView
        Sum.setText(Integer.toString(No1+No2));

        // Setting Text to TextField
        SumBox.setText(String.valueOf(No1+No2));
    }
}
```    