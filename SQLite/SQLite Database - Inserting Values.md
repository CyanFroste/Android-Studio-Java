### THE JAVA CODE

- DatabaseHelper.java
```
package com.example.myapplication;

import android.content.ContentValues;
import android.content.Context;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;
import androidx.annotation.Nullable;

public class DatabaseHelper extends SQLiteOpenHelper {

    public static final String DATABASE_NAME = "Student.db";
    public static final String TABLE_NAME = "Students";


    public DatabaseHelper(@Nullable Context context) {
        super(context, DATABASE_NAME, null, 1);
    }

    @Override
    public void onCreate(SQLiteDatabase db) {
        String sql = "CREATE TABLE " + TABLE_NAME + "( ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT, MARKS INTEGER)";
        db.execSQL(sql);
    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
        String sql = "DROP TABLE IF EXISTS " + TABLE_NAME;
        db.execSQL(sql);
        onCreate(db);
    }

    public boolean insertData(String Name, String Marks){
        SQLiteDatabase db = this.getWritableDatabase();
        ContentValues contentValues = new ContentValues();
        contentValues.put("NAME", Name);
        contentValues.put("MARKS", Marks);
        long result = db.insert(TABLE_NAME, null, contentValues);
        if(result == -1)
            return false;
        else
            return true;
    }
}
```

- MainActivity.java
```
package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;


public class MainActivity extends AppCompatActivity {

    DatabaseHelper myDB;
    EditText Name, Marks;
    Button Add;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        myDB = new DatabaseHelper(this);

        Name = (EditText)findViewById(R.id.txtName);
        Marks = (EditText)findViewById(R.id.txtMarks);
        Add = (Button)findViewById(R.id.button);
    }

    public void addData(View v){
       boolean status = myDB.insertData(Name.getText().toString(), Marks.getText().toString());
       if(status)
           Toast.makeText(MainActivity.this, "Data Inserted", Toast.LENGTH_SHORT).show();
       else
           Toast.makeText(MainActivity.this, "Data Not Inserted", Toast.LENGTH_SHORT).show();
    }
}
```