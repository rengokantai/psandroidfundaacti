# psandroidfundaacti
## 1.
### 4
Activitiy,Service,Broadcast, Receiver, Content Provider

### 12
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
### 14
3rd way,
```
android:onClick="changeMethod"
```
(no parentheses)


## 5. Sharing Data Between Activities Using Explicit Intent
### 1 Introduction to Explicit and Implicit Intent
explicit Intent: target activity is known  
implicit Intent: target activity is not known....
### 19
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





## 6. Exploring Activity Lifecycle
### 1 Why AppCompatActivity?
When use AppCompatActivity?
- If Material Design implementation needed. target below v21

When use FragmentActivity?
- If nested Fragments needed

Activity
- None of the above needed

### 2 Exploring Activity Lifecycle
onCreate->onStart(visible,but user cannot use)->onResume->（Activity Visible）->onPause(when calling second activity)
(second) onCreate->onStart->onResume->(main activity)onStop.
When user quit second, (second)onPause,but still visible to user,(main)onRestart,(second)onStop,onDestroy

### 3 Demo: Activity Lifecycle
```
Intent intent = new Intent(MainActivity.this,SecondActivity.class);
startActivity(intent);
```
### 4 Activity and Stack
### 5 Summary and Significance of Lifecycle Methods
onCreate()
- called when activity is first create,
- create views
- attach layouts(setContentView)
- init field variables and widgets
- Make use of Bundle parameter to retrive previous frozen state.

onStart()
- Called when Activity is becoming visible to user
- User interaction not allowed

onResume()
- User interaction enabled
- Activity appears at top of Activity Stack
- Always followed by onPause()
- Activity is completed in Foreground

onPause()
- Activity starts to go into Background
- Manually, save the Persistent data

onStop()
- User Interaction stops
- Activity completely in Background

onDestroy()
- Activity is Destroyed





## 7. Understanding Activity Lifecycle in Context of Screen Rotation
### 1 Behavior of Activity Lifecycle
potrait to landscape:  
onCreate-onStart-onResume-onPause-onStop-onDestroy

### 3 Impact of Screen Rotation on Views
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





