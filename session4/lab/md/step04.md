#Refactored Report - New 'Class'

Finally, rework the Report class to remove the hard coded values - and use a different 'adapter'

~~~java
public class Report extends Base {
  private ListView listView;

  @Override
  public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_report);

    listView = (ListView) findViewById(R.id.reportList);
    DonationAdapter adapter = new DonationAdapter(this, donations);
    listView.setAdapter(adapter);
  }
}
~~~

This is the new adapter - DonationAdapter. You can place this at the end of the Report class (outside the closing brace) if you like:

~~~java
class DonationAdapter extends ArrayAdapter<Donation>
{
  private Context        context;
  public  List<Donation> donations;

  public DonationAdapter(Context context, List<Donation> donations)
  {
    super(context, R.layout.row_donate, donations);
    this.context   = context;
    this.donations = donations;
  }

  @Override
  public View getView(int position, View convertView, ViewGroup parent)
  {
    LayoutInflater inflater = (LayoutInflater) context.getSystemService(Context.LAYOUT_INFLATER_SERVICE);
 
    View     view       = inflater.inflate(R.layout.row_donate, parent, false);
    Donation donation   = donations.get(position);
    TextView amountView = (TextView) view.findViewById(R.id.row_amount);
    TextView methodView = (TextView) view.findViewById(R.id.row_method);
    
    amountView.setText("" + donation.amount);
    methodView.setText(donation.method);
    
    return view;
  }

  @Override
  public int getCount()
  {
    return donations.size();
  }
}
~~~

If all goes well - then you should be able to make donations, and then see a list of them in the report activity.

