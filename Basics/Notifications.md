### THE JAVA CODE
```
package com.example.myapplication;

import androidx.annotation.RequiresApi;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.NotificationCompat;
import android.app.NotificationChannel;
import android.app.NotificationManager;
import android.app.PendingIntent;
import android.app.TaskStackBuilder;
import android.content.Intent;
import android.graphics.Color;
import android.os.Build;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity {

    Button Button;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

    }

    @RequiresApi(api = Build.VERSION_CODES.JELLY_BEAN)
    public void onClick(View v) {

        Button = findViewById(R.id.button);
        Intent intent = new Intent(MainActivity.this, MainActivity.class);

        // Creating Task Stack to be used in a single notification
        TaskStackBuilder stackBuilder;
        stackBuilder = TaskStackBuilder.create(MainActivity.this);
        stackBuilder.addParentStack(MainActivity.class);
        stackBuilder.addNextIntent(intent);
        PendingIntent pIntent = stackBuilder.getPendingIntent(0, PendingIntent.FLAG_UPDATE_CURRENT);

        NotificationManager notificationManager = (NotificationManager) getSystemService(NOTIFICATION_SERVICE);


        // Creating a channel
        String CHANNEL_ID = "";

        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {

            CHANNEL_ID = "Channel 1";
            CharSequence name = "My Channel";
            String Description = "This is my channel";
            int importance = NotificationManager.IMPORTANCE_HIGH;
            NotificationChannel myChannel = new NotificationChannel(CHANNEL_ID, name, importance);
            myChannel.setDescription(Description);
            myChannel.enableLights(true);
            myChannel.setLightColor(Color.RED);
            myChannel.enableVibration(true);
            myChannel.setVibrationPattern(new long[]{100, 200, 300, 400, 500, 400, 300, 200, 400});
            myChannel.setShowBadge(false);
            notificationManager.createNotificationChannel(myChannel);
        }

        NotificationCompat.Builder builder = new NotificationCompat.Builder(MainActivity.this, CHANNEL_ID)
                .setTicker("Ticker Title")
                .setSmallIcon(R.mipmap.ic_launcher)
                .setContentTitle("Notification Title")
                .setContentText("Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur molestie, tortor eu consequat iaculis...")
                .addAction(R.drawable.ic_launcher_foreground, "Action 1", pIntent)
                .setContentIntent(pIntent);

        notificationManager.notify(0, builder.build());

    }
}
```
