### THE JAVA CODE
```
package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.webkit.WebView;
import android.webkit.WebViewClient;
import android.widget.Button;
import android.widget.EditText;


public class MainActivity extends AppCompatActivity {

    private static Button Button;
    private static EditText URL;
    private static WebView Browser;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    public void openURL(View v) {
        URL = (EditText)findViewById(R.id.editText);
        Browser = (WebView)findViewById(R.id.webView);
        Browser.getSettings().setLoadsImagesAutomatically(true);
        Browser.getSettings().setJavaScriptEnabled(true);
        Browser.setScrollBarStyle(View.SCROLLBARS_INSIDE_OVERLAY);
        Browser.setWebViewClient(new WebViewClient());
        Browser.loadUrl(URL.getText().toString());
    }
}
```


- To give permission to use internet, add this to the AndroidManifest.xml file 

```
<uses-permission android:name="android.permission.INTERNET"/>
 ```