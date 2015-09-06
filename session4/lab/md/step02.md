#Refactored Donate

The Donate activity can now be completely refactored to make use of the Base class.

~~~java
public class Donate extends Base
{
  private RadioGroup   paymentMethod;
  private ProgressBar  progressBar;
  private NumberPicker amountPicker;
  private TextView     amountText;
  private TextView     amountTotal;
  
  @Override
  protected void onCreate(Bundle savedInstanceState)
  {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_donate);
    
    paymentMethod = (RadioGroup)   findViewById(R.id.paymentMethod);
    progressBar   = (ProgressBar)  findViewById(R.id.progressBar);
    amountPicker  = (NumberPicker) findViewById(R.id.amountPicker);
    amountText    = (TextView)     findViewById(R.id.amountText);
    amountTotal   = (TextView)     findViewById(R.id.amountTotal);
    
    amountPicker.setMinValue(0);
    amountPicker.setMaxValue(1000);
    progressBar.setMax(target);
  }
 
  public void donateButtonPressed (View view) 
  {
    String method = paymentMethod.getCheckedRadioButtonId() == R.id.PayPal ? "PayPal" : "Direct";
    int donatedAmount =  amountPicker.getValue();
    if (donatedAmount == 0)
    {
      String text = amountText.getText().toString();
      if (!text.equals(""))
        donatedAmount = Integer.parseInt(text);
    }
    if (donatedAmount > 0)
    {
      newDonation(new Donation(donatedAmount, method));
      progressBar.setProgress(totalDonated);
      String totalDonatedStr = "$" + totalDonated;
      amountTotal.setText(totalDonatedStr);
    }
   }
}

~~~

Replace your version with this and execute it - fix any missing import statements necessary.

Look carefully at the changes to this version over the previous attempt.

