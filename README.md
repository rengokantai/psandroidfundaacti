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
