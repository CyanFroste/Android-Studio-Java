### THE JAVA CODE
```
package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.SeekBar;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private static SeekBar Seekbar;
    private static TextView Value;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        seekBar();
    }

    public void seekBar(){
        Seekbar = (SeekBar)findViewById(R.id.seekBar);
        Value = (TextView)findViewById(R.id.textView);

        Value.setText(String.valueOf(Seekbar.getProgress()));

        Seekbar.setOnSeekBarChangeListener(
                new SeekBar.OnSeekBarChangeListener() {

                    @Override
                    public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
                        // Value.setText(String.valueOf(progress));
                        Value.setText(String.valueOf(Seekbar.getProgress()));
                    }

                    @Override
                    public void onStartTrackingTouch(SeekBar seekBar) {
                        Toast.makeText(MainActivity.this, "Seeking Started", Toast.LENGTH_SHORT).show();
                    }

                    @Override
                    public void onStopTrackingTouch(SeekBar seekBar) {
                        Toast.makeText(MainActivity.this, "Seeking Stopped", Toast.LENGTH_SHORT).show();
                    }
                }
        );
    }
}
```