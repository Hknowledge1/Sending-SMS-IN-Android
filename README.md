# Sending-SMS-IN-Android
package com.example.tutorialspoint;
import android.net.Uri;
import android.os.Bundle;
import android.app.Activity;
import android.content.Intent;
import android.util.Log;
import android.view.Menu;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;
public class MainActivity extends Activity {
 @Override
 protected void onCreate(Bundle savedInstanceState) {
 super.onCreate(savedInstanceState);
 setContentView(R.layout.activity_main);
 Button startBtn = (Button) findViewById(R.id.button);
startBtn.setOnClickListener(new View.OnClickListener() {
 public void onClick(View view) {
 sendSMS();
 }
 });
 }
 
 protected void sendSMS() {
 Log.i("Send SMS", "");
 Intent smsIntent = new Intent(Intent.ACTION_VIEW);
 
 smsIntent.setData(Uri.parse("smsto:"));
 smsIntent.setType("vnd.android-dir/mms-sms");
 smsIntent.putExtra("address" , new String ("01234"));
 smsIntent.putExtra("sms_body" , "Test ");
 
 try {
 startActivity(smsIntent);
 finish();
 Log.i("Finished sending SMS...", "");
 } catch (android.content.ActivityNotFoundException ex) {
 Toast.makeText(MainActivity.this, 
 "SMS faild, please try again later.", Toast.LENGTH_SHORT).show();
 }
 }
 
 @Override
 public boolean onCreateOptionsMenu(Menu menu) {
 // Inflate the menu; this adds items to the action bar if it is present.
getMenuInflater().inflate(R.menu.main, menu);
 return true;
 }
}






XML File
<?xml version="1.0" encoding="utf-8"?>

<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
 xmlns:tools="http://schemas.android.com/tools"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 android:paddingLeft="@dimen/activity_horizontal_margin"
 android:paddingRight="@dimen/activity_horizontal_margin"
 android:paddingTop="@dimen/activity_vertical_margin"
 android:paddingBottom="@dimen/activity_vertical_margin"
 tools:context=".MainActivity">
 
 <TextView
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:text="Drag and Drop Example"
 android:id="@+id/textView"
 android:layout_alignParentTop="true"
 android:layout_centerHorizontal="true"
 android:textSize="30dp" />
 
 <TextView
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:text="Tutorials Point "
 android:id="@+id/textView2"
 android:layout_below="@+id/textView"
 android:layout_centerHorizontal="true"
 android:textSize="30dp"
 android:textColor="#ff14be3c" />
 
 <ImageView
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:id="@+id/imageView"
 android:layout_marginTop="48dp"
 android:layout_below="@+id/textView2"
android:layout_centerHorizontal="true" />
 
 <Button
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:text="Compose SMS"
 android:id="@+id/button"
 android:layout_below="@+id/imageView"
 android:layout_alignRight="@+id/textView2"
 android:layout_alignEnd="@+id/textView2"
 android:layout_marginTop="54dp"
 android:layout_alignLeft="@+id/imageView"
 android:layout_alignStart="@+id/imageView" />
 
</RelativeLayout>



Manifest file
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
 package="com.example.tutorialspoint" >
 
 <application
 android:allowBackup="true"
 android:icon="@drawable/ic_launcher"
 android:label="@string/app_name"
 android:theme="@style/AppTheme" >
 
 <activity
 android:name="com.example.tutorialspoint.MainActivity"
 android:label="@string/app_name" >
 
 <intent-filter>
 <action android:name="android.intent.action.MAIN" />
 <category android:name="android.intent.category.LAUNCHER" />
 </intent-filter>
 
 </activity>
 
 </application>
</manifest>
