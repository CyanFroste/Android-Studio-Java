### SETTING ACTION BAR ICON

```
ActionBar ab = getActionBar();
ab.setLogo(_icon-here_);
ab.setDisplayUseLogoEnabled(true);
ab.setDisplayShowHomeEnabled(true);
```

### OVERFLOW MENU ITEM

menu_main.xml
```
<item android:id="@+id/action_settings"
    android:orderInCategory="100"
    android:title="@string/action_settings"    
    app:showAsAction="never" />
```
Java code to enable the items in the Overflow menu
```
public boolean onCreateOptionsMenu(Menu menu){
    MenuInflater menuInflater = getMenuInflater();
    menuInflater.inflate(R.menu.menu_main, menu);
    return super.onCreateOptionsMenu(menu);
}
```

### ITEMS IN THE ACTION BAR ITSELF

menu_main.xml
```
<item android:id="@+id/action_settings"
    android:orderInCategory="100"
    android:title="@string/action_settings"
    android:icon="_icon-here_"
    app:showAsAction="always" />
```
Java code to enable the above items on the Action bar itself
```
public boolean onCreateOptionsMenu(Menu menu){
    MenuInflater menuInflater = getMenuInflater();
    menuInflater.inflate(R.menu.menu_main, menu);
    return super.onCreateOptionsMenu(menu);
}
```

### INTERACT WITH MENU ITEMS
```
public boolean onOptionsItemSelected(MenuItem item){
    switch (item.getItemId()){
        case R.id.item_one:
            - Do action -
        case R.id.item_two:
            - Do action -  
    }
    return super.onOptionsItemSelected(item);
}
```

### UP ARROW IN THE ACTION BAR

Specifying the Parent Activity in the AndroidManifest.xml file
```
<activity android:name=".ActivityTwo"
            android:parentActivityName=".MainActivity"  />
<activity android:name=".ActivityOne"
            android:parentActivityName=".MainActivity"  />
```
Enabling the Up arrow 
```
getActionBar().setDisplayShowHomeEnabled(true);
```





