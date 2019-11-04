### THE JAVA CODE
```
package com.example.test;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;
import java.io.BufferedReader;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStreamReader;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editText = findViewById(R.id.editText);
        textView = findViewById(R.id.textView);
    }

    private static TextView textView;
    private static EditText editText;
    private static Button READ, WRITE;

    public void read(View v){
        try {
            FileInputStream fileInputStream = openFileInput("myText.txt");
            InputStreamReader inputStreamReader = new InputStreamReader(fileInputStream);
            BufferedReader bufferedReader = new BufferedReader(inputStreamReader);
            StringBuffer stringBuffer = new StringBuffer();
            String lines;
            while((lines = bufferedReader.readLine()) != null ){
                stringBuffer.append(lines + "\n");
            }
            textView.setText(stringBuffer.toString());
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    public void write(View v){
        String text = editText.getText().toString();
        try {
            FileOutputStream fileOutputStream = openFileOutput("myText.txt", MODE_PRIVATE);
            fileOutputStream.write(text.getBytes());
            fileOutputStream.close();
            Toast.makeText(getApplicationContext(), "File Saved as txt", Toast.LENGTH_SHORT).show();
            editText.setText("");
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```