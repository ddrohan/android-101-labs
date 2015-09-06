#Resetting the Donations

The last step in this lab involves deleting all the donations in the database when the user wishes to 'Reset'.

There's actually not a lot required in this step - all you need to do is call <b>reset()</b> on your datbase object when the user selects the Menu option, so modify your reset method (in your Donate.java) as follows:

~~~java
  @Override
  public void reset(MenuItem item)
  {
	  	app.dbManager.reset();
		app.totalDonated = 0;
		amountTotal.setText("$" + app.totalDonated);
  } 
~~~

You also need to update your <i>onPrepareOptionsMenu()</i> method in your <b>Base</b> class to handle the 'Reset' menu option being disabled/displayed properly, so refer to the lecture material for this.

That's about it - with one exception. There's a small bug in the app related to when the app restarts and the target HASN'T been reached. 

Can you find it, and more importantly, fix it?