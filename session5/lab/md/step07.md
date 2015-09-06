#Adding Database Support

Once you import the necessary Database classes, this step is relatively straight forward - all you have to do is replace the method calls that manages the <b><i>donationList</i></b> with the respective <b><i>dbManager</i></b> calls.

First thing to do is download the necessary database classes in the [database](../archives/database.zip) archive and add them to a new <i>app.db</i> package in your project.

Take a few moments to investigate the classes and familarise yourself with the methods you'll be using.

There are a few classes you'll need to modify to add database support to your project, but initially, you need to create an instance of <b><i>DBManager</i></b> in <b>Base.java</b> and both open/close the database when necessary, so refer to the Lecture Material to complete this.

Also, our Donation class needs a slight refactor, so replace the current class with this one.

~~~java
public class Donation
{
  public int    id;
  public int    amount;
  public String method;
  
  public Donation (int amount, String method)
  {
    this.amount = amount;
    this.method = method;
  }
  
  public Donation ()
  {
    this.amount = 0;
    this.method = "";
  }
  
  public String toString()
  {
    return id + ", " + amount + ", " + method;
  }
}

~~~

Once you make these changes, commenting out the donationList List, (and save the file) you'll get a number of errors, which actually indicates which classes you need to now update and add the database calls (and remove the donationList calls).

Each error requires only one line of code to be fixed, so have a go and updating each of the classes (and we'll have a look at the solution near the end of the Practical Lab).

Once you fix all the errors, and run the app again, you should still be able to make donations - but this time those donations are stored in a database.

And as a final check, if you shut down the app and restart it again, you should still be able to see the donations Report.

