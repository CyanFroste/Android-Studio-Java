### THE JAVA CODE
```
package com.example.test;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.RatingBar;
import android.widget.TextView;
import android.widget.Toast;

import org.w3c.dom.Text;


public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        listenerForRatingBar();
    }
    private static RatingBar RatingBar;
    private static TextView Text;
    private static Button Button;

    public void listenerForRatingBar() {
        RatingBar = (RatingBar)findViewById(R.id.ratingBar);
        Text = (TextView)findViewById(R.id.textView);
        Button = (Button)findViewById(R.id.button);

        RatingBar.setOnRatingBarChangeListener(
                new RatingBar.OnRatingBarChangeListener() {
                    @Override
                    public void onRatingChanged(android.widget.RatingBar ratingBar, float rating, boolean fromUser) {
                        Text.setText(String.valueOf(rating));
                    }
                }
        );
    }

    public void onClick(View v){
        RatingBar = (RatingBar)findViewById(R.id.ratingBar);
        Button = (Button)findViewById(R.id.button);
        Toast.makeText(MainActivity.this, String.valueOf(RatingBar.getRating()), Toast.LENGTH_SHORT).show();
    }
}
```
