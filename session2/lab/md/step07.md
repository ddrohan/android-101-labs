#Step 07 - Radio Button

In donateButtonPressed we need to discover which payment method has been selected. Our RadioGroup documentation is here:

- <http://developer.android.com/reference/android/widget/RadioGroup.html>

This looks like the method we need:

- [getCheckedRadioButtonId()](http://developer.android.com/reference/android/widget/RadioGroup.html#getCheckedRadioButtonId())

This is a revised version of donateButtonPressed()

~~~java
  public void donateButtonPressed (View view) 
  {
    int amount = amountPicker.getValue();
    int radioId = paymentMethod.getCheckedRadioButtonId();
    String method = "";
    if (radioId == R.id.PayPal)
    {
      method = "PayPal";
    }
    else
    {
      method = "Direct";
    }
    Log.v("Donate", "Donate Pressed! with amount " + amount + ", method: " + method);
   }
~~~

Run it now and verify we are getting the correct logs.

We can simplify it somewhat by reducing the if statement to a singlle line:

~~~java
    String method = radioId == R.id.PayPal ? "PayPal" : "Direct";
~~~

This is the Java ternary operator:

- <http://marxsoftware.blogspot.ie/2010/09/how-i-learned-to-stop-worrying-and-love.html>

This is the complete activity class:

~~~java
package com.example.donation;

import android.os.Bundle;
import android.app.Activity;
import android.content.res.Resources;
import android.util.Log;
import android.view.Menu;
import android.view.View;
import android.widget.Button;
import android.widget.RadioGroup;
import android.widget.NumberPicker;
import android.widget.ProgressBar;


public class Donate extends Activity
{
  private Button       donateButton;
  private RadioGroup   paymentMethod;
  private ProgressBar  progressBar;
  private NumberPicker amountPicker;
  
  @Override
  protected void onCreate(Bundle savedInstanceState)
  {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_donate);
    
    donateButton  = (Button)       findViewById(R.id.donateButton);
    paymentMethod = (RadioGroup)   findViewById(R.id.paymentMethod);
    progressBar   = (ProgressBar)  findViewById(R.id.progressBar);
    amountPicker  = (NumberPicker) findViewById(R.id.amountPicker);
    
    amountPicker.setMinValue(0);
    amountPicker.setMaxValue(1000);
  }

  @Override
  public boolean onCreateOptionsMenu(Menu menu)
  {
    getMenuInflater().inflate(R.menu.donate, menu);
    return true;
  }
  
  public void donateButtonPressed (View view) 
  {
    int amount = amountPicker.getValue();
    int radioId = paymentMethod.getCheckedRadioButtonId();
    String method = radioId == R.id.PayPal ? "PayPal" : "Direct";
    Log.v("Donate", "Donate Pressed! with amount " + amount + ", method: " + method);
   }
}
~~~

 
