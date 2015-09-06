#Donation Model
 
We now need to refactor the Base class (next Step) and move the donation related attributes and method (i.e. the variables target, totalDonated and the donations list,and the newDonation() method) into our DonationApp class.

This is a revised version of DonationApp - which now manages a list of donations. It also centralises the 'makeDonation' event implementing it as a method. Replace your donation with this one:

~~~java
package app.main;

import java.util.ArrayList;
import java.util.List;

import android.app.Application;
import android.util.Log;
import android.widget.Toast;
import app.models.Donation;

public class DonationApp extends Application
{
  public final int       target       = 10000;
  public int             totalDonated = 0;
  public List <Donation> donations    = new ArrayList<Donation>();
  
  public boolean newDonation(Donation donation)
  {
    boolean targetAchieved = totalDonated > target;
    if (!targetAchieved)
    {
      donations.add(donation);
      totalDonated += donation.amount;
    }
    else
    {
      Toast toast = Toast.makeText(this, "Target Exceeded!", Toast.LENGTH_SHORT);
      toast.show();
    }
    return targetAchieved;
  }
  
  @Override
  public void onCreate()
  {
    super.onCreate();
    Log.v("Donation", "Donation App Started");
  }
}
~~~

