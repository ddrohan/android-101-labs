#Resetting the Target Amount

This is more of an interim step but is necessary to ensure the menu event handler for the 'Reset' option is working correctly.

First, edit <b>Donate.java</b> and introduce an implementation of the 'reset' method

~~~java
 @Override
  public void reset(MenuItem item)
  {
		// Your implementation goes here
  }
~~~

the

~~~java 
@Override 
~~~

annotation is important - can you explain why? 

So add in the code necessary to deal with the Reset Menu option being selected, and reset the <i>totalDonated</i> back to zero (0). You also need to update the Donate UI to reflect this reset, so try and have a go at that too.

Run the app again to confirm that the 'Reset' Menu option is now functioning.

