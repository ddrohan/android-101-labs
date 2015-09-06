#Application Object

Before we complete this step, here's the code you need for the previous step.

~~~java
 @Override
  public void reset(MenuItem item)
  {
    totalDonated = 0;
    amountTotal.setText("$" + totalDonated);
  }
~~~

In order to keep out application design coherent, we now bring in an 'Application' object.

Create a new package called 'app.main' and incorporate this class here:

~~~java
package app.main;

import android.app.Application;
import android.util.Log;

public class DonationApp extends Application
{
  @Override
  public void onCreate()
  {
    super.onCreate();
    Log.v("Donation", "Donation App Started");
  }
}
~~~

Application objects need to be references in the AndroidManifest.xml - at the very top as 'andorid:name'

~~~xml
    <application
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme" 
        android:name="app.main.DonationApp">
~~~

Make sure the 'Donation App Started' appears in the logs to verify that it has actually been engaged correctly, when you launch the app.


