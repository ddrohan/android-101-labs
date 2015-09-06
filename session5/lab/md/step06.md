#Base Class Refactoring
 
The Base activity can now be completely refactored to make use of the DonationApp object.

This is our new Base class

~~~java
package app.activities;

import android.app.Activity;
import android.content.Intent;
import android.content.SharedPreferences;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import app.donation.R;
import app.main.DonationApp;

public class Base extends Activity {

  public DonationApp app;

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    
    app = (DonationApp) getApplication();
    
    app.dbManager.open();
    app.dbManager.setTotalDonated(this);
  }

  @Override
  protected void onDestroy() {
    super.onDestroy();
    app.dbManager.close();
  }
  
  @Override
    public boolean onCreateOptionsMenu(Menu menu)
    {
      getMenuInflater().inflate(R.menu.donate, menu);
      return true;
    }
  
  @Override
    public boolean onPrepareOptionsMenu (Menu menu){
        super.onPrepareOptionsMenu(menu);
        MenuItem report = menu.findItem(R.id.menuReport);
        MenuItem donate = menu.findItem(R.id.menuDonate);
        MenuItem reset = menu.findItem(R.id.menuReset);
        
        if(app.dbManager.getAll().isEmpty())
        {
             report.setEnabled(false);
             reset.setEnabled(false);
        }
        else {
          report.setEnabled(true); 
          reset.setEnabled(true);
        }
        if(this instanceof Donate){
            donate.setVisible(false);
            if(!app.dbManager.getAll().isEmpty())
            {
                  report.setVisible(true);
                  reset.setEnabled(true);
            }
          }
        else {
          report.setVisible(false);
          donate.setVisible(true);
          reset.setVisible(false);
          }
        
        return true;  
    }
      
    public void report(MenuItem item)
    {
      startActivity (new Intent(this, Report.class));
    }
    
    public void donate(MenuItem item)
    {
      startActivity (new Intent(this, Donate.class));
    }

  public void reset(MenuItem item) {}
}

~~~ 