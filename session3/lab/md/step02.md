#Menu

In Donation, introduce the following menu event handler:

~~~java
  @Override
  public boolean onOptionsItemSelected(MenuItem item)
  {
    switch (item.getItemId())
    {
      case R.id.action_settings: Toast toast = Toast.makeText(this, "Settings Selected", Toast.LENGTH_SHORT);
                                 toast.show();
                                 break;
    }
    return true;
  }
~~~

We already have a menu called 'donate.xml' in the res folder. Add a new menu item like the one shown below:

~~~xml
<menu xmlns:android="http://schemas.android.com/apk/res/android" >

    <item
        android:id="@+id/action_settings"
        android:orderInCategory="100"
        android:showAsAction="never"
        android:title="@string/menuSettings"/>

    <item
        android:id="@+id/menuReport"
        android:orderInCategory="100"
        android:showAsAction="never"
        android:title="@string/menuReport"/>    
    
</menu>
~~~

This will require a new String in the strings.xml file:

~~~xml
    <string name="menuReport">Report</string>
~~~

Run the app and when you press the menu hardware button and select 'settings', you should see the toast message appear.
