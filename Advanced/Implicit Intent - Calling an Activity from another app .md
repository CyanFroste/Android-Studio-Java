### MAKING THE APPLICATION ACTIVITY RECOGNIZABLE TO ALL APPLICATIONS
In Application 1's AndroidManifest.xml file 

```
<activity android:name=".AppOneActivityOne">
    <intent-filter>
        <action android:name=".AppOneActivityOne" />
        <category android:name="android.intent.category.DEFAULT" />
    </intent-filter>
</activity>
```

In Application 2
### THE JAVA CODE
```
startActivity(new Intent(".AppOneActivityOne"));
```