### THE JAVA CODE

- ServicesManager.java
```
package com.example.myapplication;

import android.app.Service;
import android.content.Intent;
import android.os.Binder;
import android.os.IBinder;
import java.util.Random;

public class ServicesManager extends Service {

    private final IBinder iBinder = new LocalBinder();
    // Class that generated Random Numbers
    private final Random RNG = new Random();

    public class LocalBinder extends Binder {
        ServicesManager getService(){
            return ServicesManager.this;
        }
    }
    public ServicesManager() {
    }

    @Override
    public IBinder onBind(Intent intent) {
        return iBinder;
    }

    public int getRandomNumber(){
        return RNG.nextInt(200);
    }
}
```

- MainActivity.java
```
package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;
import android.content.ComponentName;
import android.content.Context;
import android.content.Intent;
import android.content.ServiceConnection;
import android.os.Bundle;
import android.os.IBinder;
import android.view.View;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    ServicesManager servicesManager;
    boolean isBound = false;

    public void onClick(View v){
        TextView textView = findViewById(R.id.textView);
        textView.setText(Integer.toString(servicesManager.getRandomNumber()));
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Intent intent = new Intent(this, ServicesManager.class);
        bindService(intent, serviceConnection, Context.BIND_AUTO_CREATE);
    }

    private ServiceConnection serviceConnection = new ServiceConnection() {
        @Override
        public void onServiceConnected(ComponentName name, IBinder service) {
            ServicesManager.LocalBinder binder = (ServicesManager.LocalBinder) service;
            servicesManager = binder.getService();
            isBound = true;
        }

        @Override
        public void onServiceDisconnected(ComponentName name) {
            isBound = false;
        }
    };
}
```