### THE JAVA CODE

- DatabaseHelper.java
```
package com.example.myapplication;

import android.content.ContentValues;
import android.content.Context;
import android.database.Cursor;
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
        if(result == 0)
            return false;
        else
            return true;
    }

    public Cursor getData(){
        SQLiteDatabase db = this.getWritableDatabase();
        String sql = "SELECT * FROM " + TABLE_NAME;
        Cursor result = db.rawQuery(sql, null);
        return result;
    }

    public boolean updateData(String ID, String Name, String Marks){
        SQLiteDatabase db = this.getWritableDatabase();
        ContentValues contentValues = new ContentValues();
        contentValues.put("ID", ID);
        contentValues.put("NAME", Name);
        contentValues.put("MARKS", Marks);
        long result = db.update(TABLE_NAME, contentValues, "ID = ?", new String[]{ID} );
        if(result == 0)
            return false;
        else
            return true;
    }
}
```

- MainActivity.java
```
package com.example.myapplication;

import androidx.appcompat.app.AlertDialog;
import androidx.appcompat.app.AppCompatActivity;
import android.database.Cursor;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;


public class MainActivity extends AppCompatActivity {

    DatabaseHelper myDB;
    EditText Name, Marks, ID;
    Button Add;
    Button View;
    Button Update;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        myDB = new DatabaseHelper(this);

        Name = (EditText)findViewById(R.id.txtName);
        Marks = (EditText)findViewById(R.id.txtMarks);
        ID = (EditText)findViewById(R.id.txtID);
        Add = (Button)findViewById(R.id.button);
        View = (Button)findViewById(R.id.button2);
        Update = (Button)findViewById(R.id.button3);
    }

    public void addData(View v){
       boolean status = myDB.insertData(Name.getText().toString(), Marks.getText().toString());
       if(status)
           Toast.makeText(MainActivity.this, "Data Inserted", Toast.LENGTH_SHORT).show();
       else
           Toast.makeText(MainActivity.this, "Data Not Inserted", Toast.LENGTH_SHORT).show();
    }

    public void viewAll(View v){
        Cursor result = myDB.getData();
        if(result.getCount() == 0){
            showMessage("Error", "Nothing Found");
            return;
        }
        StringBuffer buffer = new StringBuffer();
        while(result.moveToNext()){
            buffer.append("ID : " + result.getString(0) + "\n")
                .append("Name : " + result.getString(1) + "\n")
                .append("Marks : " + result.getString(2) + "\n\n");
        }
        showMessage("Data", buffer.toString());
    }

    public void showMessage(String title, String message){
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setCancelable(true)
                .setTitle(title)
                .setMessage(message)
                .show();
    }

    public void updateData(View v){
        boolean status = myDB.updateData(ID.getText().toString(), Name.getText().toString(), Marks.getText().toString());
        if(status)
            Toast.makeText(MainActivity.this, "Data Updated", Toast.LENGTH_SHORT).show();
        else
            Toast.makeText(MainActivity.this, "Data Not Updated", Toast.LENGTH_SHORT).show();
    }
}
```
