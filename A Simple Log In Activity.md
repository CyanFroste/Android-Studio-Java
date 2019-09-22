### THE JAVA CODE
```
package com.example.loginscratch;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

public class Login extends AppCompatActivity {

    private static EditText username;
    private static EditText password;
    private static TextView counter;
    private static Button button;
    int count = 5;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_login);
    }

    public void loginButton(View v){
        username = (EditText)findViewById(R.id.txtUsr);
        password = (EditText)findViewById(R.id.txtPass);
        button = (Button)findViewById(R.id.button);
        counter = (TextView)findViewById(R.id.txtCount);

        counter.setText(Integer.toString(count));

        if(username.getText().toString().equals("cyan") && password.getText().toString().equals("froste")){
            Toast.makeText(Login.this, "Valid Credentials", Toast.LENGTH_SHORT).show();
            Intent intent = new Intent(Login.this, user.class);
            startActivity(intent);
        }
        else{
            Toast.makeText(Login.this, "Invalid Credentials", Toast.LENGTH_SHORT).show();
            count--;
            counter.setText(Integer.toString(count));
            if(count == 0){
                button.setEnabled(false);
            }
        }
    }
}
```