# Langkah-langkah:
#### 1. Open android studio lalu pilih start new project lalu masukkan nama aplikasi beserta tempat penyimpanan nya seperti dibawah ini, lalu klik next

<img src="https://cdn-images-1.medium.com/max/800/1*O5Xq1BCofMaJW8y4q0YFZw.png">

#### 2. lalu kita pilih minimum SDK, kemudian klik next
 
<img src="https://cdn-images-1.medium.com/max/800/1*sBZ6A7wg4TSratKxLy6H3A.png">

#### 3. lalu kita pilih empty activity

<img src="https://cdn-images-1.medium.com/max/800/1*VqoWFpFq9bbJ2DVFCPYu7Q.png">

#### 4. Lalu biarkan saja pengaturannya default seperti dibawah ini, lalu klik finish

<img src="https://cdn-images-1.medium.com/max/800/1*yJRJ8KwBeSJlrfZ3qCwGJQ.png">

#### 5. lalu kita buka activity_main.xml dan masukkan kode dibawah ini

```<?xml version="1.0" encoding="utf-8"?>
<ListView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/listView"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="16dp"
    android:paddingLeft="16dp"
    android:paddingRight="16dp"
    android:paddingTop="16dp"
    tools:context="app.com.example.android.examplelistview.MainActivity">
</ListView>
``` 

#### 6. lalu setelah itu kita masuk ke string.xml, letaknya di folder res/values/string.xml lalu kita masukkan kode dibawah ini, disini saya contohkan menampilkan beberapa nama negara di dunia

```<resources>
    <string name="app_name">ExampleListView</string>
    <string-array name="countries_arry">
        <item>Afghanistan</item>
        <item>Albania</item>
        <item>Algeria</item>
        <item>American Samoa</item>
        <item>Andorra</item>
        <item>Angola</item>
        <item>Anguilla</item>
        <item>Antarctica</item>
        <item>Antigua and Barbuda</item>
        <item>Argentina</item>
        <item>Armenia</item>
        <item>Aruba</item>
        <item>Australia</item>
        <item>Austria</item>
        <item>Azerbaijan</item>
        <item>Bahrain</item>
        <item>Bangladesh</item>
        <item>Barbados</item>
        <item>Belarus</item>
        <item>Belgium</item>
    </string-array>
</resources>
``` 
#### 7. buat folder baru di res dengan nama folder menu kemudian buat sebuah resource file baru dengan nama list.xml

#### 6. setelah string.xml sekarang kita beralih ke MainActivity.java

```package app.com.example.android.examplelistview;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.Menu;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity implements AdapterView.OnItemClickListener{
    ListView listView;
    ArrayAdapter<CharSequence> adapter;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        listView = (ListView)findViewById(R.id.listView);
        adapter = ArrayAdapter.createFromResource(this,R.array.countries_arry,android.R.layout.simple_list_item_1);
        //adapter= new ArrayAdapter<String>(this, android.R.layout.simple_list_item_1);
        listView.setAdapter(adapter);
        listView.setOnItemClickListener(this);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.list, menu);
        return true;
    }


    @Override
    public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
        Toast.makeText(this, adapter.getItem(position), Toast.LENGTH_SHORT).show();

    }
}
``` 
Penjelasan program pada skrip program adapter = ArrayAdapter.createFromResource(this,R.array.countries_arry,android.R.layout.simple_list_item_1); itu berarti kita mengambil nilai array pada string.xml dengan nama countries_arry, lalu mnampilkannya dengan model tampilan simple_list_item-1, kemudian pada method onItemClick berarti ketika data pada listview ditekan akan menampilkan data berupa Toast message, lalu kita memanggil method onItemClick ini pada method onCreate dengan cara listView.setOnItemClickListener(this); lalu kita extended kan class MainActivity seperti ini public class MainActivity extends AppCompatActivity implements AdapterView.OnItemClickListener
