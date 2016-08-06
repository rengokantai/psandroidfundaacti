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
