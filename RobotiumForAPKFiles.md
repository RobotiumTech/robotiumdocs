With Robotium it is possible to run test cases on applications where you only have the apk file.

For step by step instructions with images download this [tutorial.](https://robotium.googlecode.com/files/TestAndroidCalculatorAPK-BlackBoxTesting-V1_0.pdf)

## Introduction ##

The .apk file has to have the same signature as your test project. If you do not have the signature key of the .apk file then you need to remove the signature and resign it with you own key, android debug key can be used. A drag and drop java tool can be downloaded [from here](http://recorder.robotium.com/downloads/re-sign.jar) which strips the apk file from its signature and then signs it with your android debug key. _If the new apk is not saved then try to run the re-sign tool as an administrator. In windows that would be done by right clicking the re-sign.jar and select run as administrator. In OS X it can be done by opening up the terminal and then "sudo java -jar re-sign.jar"._

The android debug key is used by Eclipse when signing applications and test projects before installing them on the emulator/device. Many times it is easier to just use that key when resigning the apk.


## Details ##

To make this work you need to know the package name and the launcher activity name. Those can be obtained by starting the application in the emulator and whatching the logs (adb logcat). The log shows what the package name and the activity name are. An example of how the log message can look like: "Starting activity: Intent { act=android.intent.action.MAIN cat=android.intent.category.LAUNCHER?  flg=0x10200000 cmp=com.example.android.notepad/.NotesList"

That means that the package name is: com.example.android.notepad and the launcher activity name (LAUNCHER\_ACTIVITY\_FULL\_CLASSNAME in the example below) is: com.example.android.notepad.NotesList


When you have that information you do the following:

In your test project's AndroidManifest.xml in Eclipse, set the target package to the package name you found above.

Write your test class like this:
(the example here is for NewsRob)

```
package com.yourcompany.yourtestname;

import com.jayway.android.robotium.solo.Solo;

import android.test.ActivityInstrumentationTestCase2;

@SuppressWarnings("rawtypes")
public class ReallyBlackboxTest extends ActivityInstrumentationTestCase2 {

	private static final String LAUNCHER_ACTIVITY_FULL_CLASSNAME = "com.newsrob.DashboardListActivity";

	private static Class<?> launcherActivityClass;
	static{
		try {
			launcherActivityClass = Class.forName(LAUNCHER_ACTIVITY_FULL_CLASSNAME);
		} catch (ClassNotFoundException e) {
			throw new RuntimeException(e);
		}
	}
	
	@SuppressWarnings("unchecked")
	public ReallyBlackboxTest() throws ClassNotFoundException {
		super(launcherActivityClass);
	}
	
	private Solo solo;
	
	@Override
	protected void setUp() throws Exception {
		solo = new Solo(getInstrumentation(), getActivity());
	}

	public void testCanOpenSettings(){
		solo.pressMenuItem(0);
	}


   @Override
   public void tearDown() throws Exception {
                solo.finishOpenedActivities();

  }


}
```


