### THE JAVA CODE
```
package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;
import androidx.core.view.GestureDetectorCompat;

import android.os.Bundle;
// import the following 3
import android.gesture.Gesture;
import android.view.GestureDetector;
import android.view.MotionEvent;
import android.widget.TextView;

import org.w3c.dom.Text;

import static android.view.GestureDetector.*;

/* add "implements OnGestureListener,OnDoubleTapListener"
to auto generate the essential event trigger
*/

public class MainActivity extends AppCompatActivity implements OnGestureListener,OnDoubleTapListener{

    private static TextView TextView;
    private static GestureDetectorCompat GestureDetect;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        TextView =(TextView)findViewById(R.id.txt);
        GestureDetect = new GestureDetectorCompat(this, this);
        GestureDetect.setOnDoubleTapListener(this);
    }



    @Override
    public boolean onTouchEvent(MotionEvent event) {
        GestureDetect.onTouchEvent(event);
        return super.onTouchEvent(event);
    }

    // the following are auto generated while implementing Listeners
    @Override
    public boolean onSingleTapConfirmed(MotionEvent e) {
        TextView.setText("Single Tap Confirmed\n" + e.toString());
        return false;
    }

    @Override
    public boolean onDoubleTap(MotionEvent e) {
        TextView.setText("Double Tap\n" + e.toString());
        return false;
    }

    @Override
    public boolean onDoubleTapEvent(MotionEvent e) {
        TextView.setText("Double Tap Event\n" + e.toString());
        return false;
    }

    @Override
    public boolean onDown(MotionEvent e) {
        TextView.setText("Down\n" + e.toString());
        return false;
    }

    @Override
    public void onShowPress(MotionEvent e) {
        TextView.setText("Show Press\n" + e.toString());

    }

    @Override
    public boolean onSingleTapUp(MotionEvent e) {
        TextView.setText("Single Tap Up\n" + e.toString());
        return false;
    }

    @Override
    public boolean onScroll(MotionEvent e1, MotionEvent e2, float distanceX, float distanceY) {
        TextView.setText("Scroll\n" + e1.toString() + e2.toString());
        return false;
    }

    @Override
    public void onLongPress(MotionEvent e) {
        TextView.setText("LongPress\n" + e.toString());

    }

    @Override
    public boolean onFling(MotionEvent e1, MotionEvent e2, float velocityX, float velocityY) {
        TextView.setText("Fling\n" + e1.toString() + e2.toString());
        return false;
    }
}
```