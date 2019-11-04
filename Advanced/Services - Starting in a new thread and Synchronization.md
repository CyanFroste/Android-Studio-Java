### THE JAVA CODE

- Services Manager.java
```
package com.example.myapplication;

import android.app.Service;
import android.content.Intent;
import android.os.IBinder;
import android.widget.Toast;
import androidx.annotation.Nullable;

public class ServicesManager extends Service {

    final class AThread extends Thread implements Runnable{
        int serviceID;
        AThread(int serviceID){
            this.serviceID = serviceID;
        }
        // Starting the Service in a new thread
        @Override
        public void run() {
            synchronized (this){
                try {
                    wait(5000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                stopSelf(this.serviceID);
            }
        }
    }

    @Nullable
    @Override
    public IBinder onBind(Intent intent) {
        return null;
    }

    @Override
    public void onCreate() {
        super.onCreate();
    }

    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        Toast.makeText(ServicesManager.this, "Service Started", Toast.LENGTH_SHORT).show();
        AThread thread = new AThread(startId);
        thread.start();
        return START_STICKY;
    }

    @Override
    public void onDestroy() {
        Toast.makeText(ServicesManager.this, "Service Stopped", Toast.LENGTH_SHORT).show();
    }
}
```

- MainActivity.java
```package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    public void startService(View v){
        startService(new Intent(this, ServicesManager.class));

    }

    public void stopService(View v){
        stopService(new Intent(this, ServicesManager.class));
    }

}
```