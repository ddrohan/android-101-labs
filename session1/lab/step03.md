#Our version of "HelloWorld"

In this Step, you will be required to develop and run your own version of the "Hello World" Android Project from the lectures (as seen below).

![](../img/lab01.png)

Launch Eclipse and create a new Android Project called SayHello (as above) similar to what you did in Step 02. Name your package 'ie.wit' (or accept the default again). Accept all the defaults, and it's recommended you select <b>Android 4.4</b> as the launch target platform (but any target will suffice for this particular lab). It's also probably a good idea to run the App at this stage, so you can set up your AVD (if you haven't done so already).

Edit your "strings.xml" file (in your res folder) and replace the current "resources" tag with the following - be careful if you have created an app which contains a 'menu' folder, this also includes associated resources, so don't overwrite those resources, just add our ones at the end.

~~~xml
<resources>
    <string name="app_name">Say Hello Application</string>
    <string name="window_text">Press the button below to receive a friendly greeting from Android.</string>
    <string name="button_label">Show Greeting</string>
    <string name="greeting_text">Hello from Android!</string>
</resources>
~~~

If you return to the "Resources View" you can see the graphical representation of the String resources you have set up (and edit them here if you need to).

![](../img/lab102.png)


Edit your "activity_hello.xml" <u><i>in your <i>layout</i> folder</i></u> and replace with the following

~~~xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".HelloActivity" >

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/hello_world" />

    <TextView
        android:id="@+id/textView1"
        android:gravity="center"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"    
        android:layout_below="@+id/textView2"
        android:layout_marginTop="20dp"
        android:text="@string/window_text"
        android:textAppearance="?android:attr/textAppearanceMedium" />

    <Button
        android:id="@+id/greetingButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_centerHorizontal="true"
        android:layout_marginBottom="59dp"
        android:onClick="showGreeting"
        android:text="@string/button_label" />

</RelativeLayout>
~~~

This will give you the following layout:

![](../img/lab103.png)

Once again, it's worth running the app at this point to confirm everything is displayed the way we want it.

The last thing we need to do is add in our event handling code so that a short message is displayed when the user presses the 'Show Greeting' button.

Firstly, open up the "HelloActivity.java" source file and add the following method

~~~java
public void showGreeting(View v) {
        // TODO Auto-generated method stub
        String greetingText = getString(R.string.greeting_text);
        Toast tempMessage = Toast.makeText(this, greetingText, Toast.LENGTH_LONG);
        tempMessage.show();
    }
~~~

Note that we have no need for soem kind of Listener interface (ala swing developement) - our event handling is taken care of via the 'onClick' attribute in our xml layout, here's what your completed Activity class should look like.

![](../img/lab104.png)

We will investigate this code more closely in the lectures.