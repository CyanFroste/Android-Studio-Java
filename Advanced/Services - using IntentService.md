### THE JAVA CODE

- ServicesManager.java
```
package com.example.myapplication;

import android.app.IntentService;
import android.content.Intent;
import android.widget.Toast;
import androidx.annotation.Nullable;

public class ServicesManager extends IntentService {


     // Creates an IntentService.  Invoked by your subclass's constructor.

    public ServicesManager() {
        super("myThread");
    }

    @Override
    public int onStartCommand(@Nullable Intent intent, int flags, int startId) {
        Toast.makeText(ServicesManager.this, "Service Started", Toast.LENGTH_SHORT).show();
        return super.onStartCommand(intent, flags, startId);
    }

    @Override
    public void onDestroy() {
        Toast.makeText(ServicesManager.this, "Service Stopped", Toast.LENGTH_SHORT).show();
        super.onDestroy();
    }

    @Override
    protected void onHandleIntent(@Nullable Intent intent) {
        // write long running tasks here
        synchronized (this){
            try {
                wait(20000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```

- MainActivity.java
```
package com.example.myapplication;

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

### XML

AndroidManifest.xml
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapplication">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        
        <service android:name=".ServicesManager"
            android:exported="false"/>
    </application>

</manifest>
```