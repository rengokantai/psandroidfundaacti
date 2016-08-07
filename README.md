#### psandroidfundaacti
#####1
######4
Activitiy,Service,Broadcast, Receiver, Content Provider

######12
1:33
```
ptivate static final String TAG = MainActivity.class.getSimpleName();
Log.i(TAG,"string")
```
set currentMainActivity clicklistener:
```
button1.setOnClickListener(this); //same
button1.setOnClickListener(MainActivity.this);
```
using switch to handle multiple buttons
```
public void onClickk(View v){
  Log.i(TAG,"button");
  switch(v.getId()){
    case R.id.button1:
    relativeLayout.setBackgroundColor(Color.GREEN);
      break;
  }
}
```

so:two ways to memorize.
```
buttonname.setOnClickListener(new View.OnClickListener() {

   @Override
   public void onClick(View view) {

   }
});
```
Or
```
public class MainActivity extends Activity implements OnClickListener{
  protected void onCreate(){
    button.setOnClickListener(MainActivity.this);
  }
  public void onClick(View v){}
}
```
######14
3rd way,
```
android:onCick="changeMethod"
```
(no parentheses)


######16
explicit Intent: target activity is known  
implicit Intent: target activity is not known....
######19
```
Intent intent = new Intent(MainActivity.this,Second.class);
Bundle b = new Bundle();
b.putString(k,v);
b.putInt(k,v);
intent.putExtras(b);
startActivity(intent);
}
});
}
}
```
SecondActivity
```
private static final String TAG = SecondActivity.class.getSimpleName();
Intent intent = getIntent();
Bundle b = intent.getExtras();
String name = b.getString("name");
Log.i(TAG,name);
```
intent- second way
```
Intent intent = new Intent(MainActivity.this,Second.class);
intent.putExtra(k,v);
startActivity(intent);
```
######23 Exploring Activities
onCreate->onStart(visible,but user cannot use)->onResume->Activity Visible->onPause(when calling second)
(second) onCreate->onStart->onResume->(main)onStop.
When user quit second, (second)onPause,but still visible to user,(main)onRestart,(second)onStop,onDestroy

#####26 Summary
onCreate:called when activity is first create,create views,attach layouts(setContentView),init var
#####
######27 Behavior of activity lifecycle when the screen is rotated
when rotating, onPause->onStop->onDestroy->onCreate->onStart->onResume

######29 Impact of screen rotation
views do not retain state:TextView,Button  
Retain:EditText,Checkbox,Switch,RadioButton
######30 Methods
i:  
onStart->onRestoreInstanceState->onResume,onPause-> onSaveInstanceState->onStop
ii:  
onConfigurationChanged
######Use
```
protected void onRestoreInstanceState(Bundle saveInstanceState){
  super.onRestoreInstanceState(saveInstanceState);
  if(savedInstanceState!=null){
    btn.setText(savedInstanceState.getString(k));
  }
}

protected void onSaveInstanceState(Bundle outState){
  super.onSaveInstanceState(outState);
  outState.putString("k",btn.getText().toString());
}
```
######32
layout,layout-land

######33Handling configuration
not recommended
```
<activity android:name=".MainActivity" android:configChanges="orientation|screenSize">
</activity>
```
then
```
private ImageView imageView;
imageView
@Override
public void onConfigurationChanged(Configuration newConfig{
  super.onConfigurationChanged(newConfig);
  Log.i(TAG,"chnaged");
  //change bg image
  if(newConfig.orientation==Congiguration.ORIENTATION_PORTRAIT){
  Toast.makeText(getApplicationContext(),"portrait",Toast.LENTH.SHORT).show();
  imageView.setImagesource(R.drawable.pictureportrait);
  }
}
```
