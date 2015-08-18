# Test Development #
You can use the `SoloRemoteControl` project installed with `RobotiumRemote control` as a reference for your own Java development project. The `SoloRemoteControl/src` directory contains all the source code contained in the `robotium-remotecontrol.jar.`

**1. Create your Java development project and reference the following JAR files:**

These can be found in `SoloRemoteControl/libs:`

> `robotium-remotecontrol.jar`

> `safssockets.jar`

> `safsautoandroid.jar`

**2. Create your `MyTest` class:**

For simplicity, this class should extend the [SoloTest](http://safsdev.sourceforge.net/doc/com/jayway/android/robotium/remotecontrol/solo/SoloTest.html) class.
The source for `SoloTest` can be found in the `SoloRemoteControl/src` folder at:

> `com/jayway/android/robotium/remotecontrol/solo/SoloTest.java`

You can find the sample code below in the `SoloRemoteControl/src` folder at:

> `com/jayway/android/robotium/remotecontrol/MyTest.java`

Your **`MyTest`** class will need to minimally import a few classes:

> `import java.util.Properties;`

> `import com.jayway.android.robotium.remotecontrol.solo.Message;`

> `import com.jayway.android.robotium.remotecontrol.solo.SoloTest;`

> `import com.jayway.android.robotium.remotecontrol.solo.Solo;`

> `public class MyTest extends SoloTest{`

> }
**3. Override/Provide and invoke the same constructors as `SoloTest:`**

> `public MyTest(){ super(); `}

> `public MyTest(String[] args){ super(args); `}

> `public MyTest(String messengerApk, String testRunnerApk, String` `instrumentArg){`

> `super(messengerApk, testRunnerApk, instrumentArg);`

> }

**4. Override the static 'main' method for `MyTest`:**

> `public static void main(String[] args){`

> `SoloTest soloTest = new MyTest(args);`

> `soloTest.process();`

> }

**5. Override and implement your 'test()' method:**

This is where your remote control test code will go. Below is a simple example of using the remote control **API**:

> `protected void test(){`

> `try{`

> `String activityID = solo.getCurrentActivity();`

> `Properties props = solo._last_remote_result;`

> `String activityName = props.getProperty(Message.PARAM_NAME);`

> `String activityClass = props.getProperty(Message.PARAM_CLASS);`

> `System.out.println("CurrentActivity   UID: "+ activityID);`

> `System.out.println("CurrentActivity Class: "+ activityClass);`

> `System.out.println("CurrentActivity  Name: "+ activityName);`

> `}catch(Exception e){`

> `e.printStackTrace();`

> }

> }

> Refer to the [JavaDoc for Solo remote control](http://safsdev.sourceforge.net/doc/com/jayway/android/robotium/remotecontrol/solo/Solo.html) for the full API available.

**6. Compile your work appropriate for your development environment:**

Remember, the minimum JAR files needed in the Java build path (CLASSPATH):

> `robotium-remotecontrol.jar`

> `safsautoandroid.jar`

> `safssockets.jar`

(These can be found in the `SoloRemoteControl/libs` folder.)

**7. Run the test using all appropriate command-line parameters for `SoloTest`:**

Remember, the same **JAR** files needed for the build are needed in the **CLASSPATH** for execution.

For example, the following command (all on one line):

> `java com.jayway.android.robotium.remotecontrol.MyTest`

> `aut=<path-to-your/aut-debug.apk>`

> `messenger=<path-to/SAFSTCPMessenger-debug.apk>`

> `runner=<path-to/RobotiumTestRunner-debug.apk>`
> `instrument=com.jayway.android.robotium.remotecontrol.client/com.jayway.android.robotium.remotecontrol.client.RobotiumTestRunner`
> `avd=SprintEvo`

Then, hopefully, you should see a torrent of activity appear in the console and, eventually, the **`SAFS Messenger service`** go active on the device/emulator.  This would be followed by the launching of the **AUT**, a brief pause for the execution of the `getCurrentActivity` call, and then a shutdown of the **AUT** and **`SAFS Messenger service.`**