# Install Instructions: #
**1. Verify [(Install if needed)](http://www.oracle.com/technetwork/java/javase/downloads/index.html) a Java JDK (not a JRE):**

The Java SDK should be version 1.6 or higher.

  * The System environment variable **JAVA\_HOME** should be set to the path to the Java SDK.
  * The System environment variable **PATH** should contain the path to the Java SDK **bin** subfolder.

**2. Verify [(Install if needed)](http://developer.android.com/sdk/index.html) the Android SDK:**

The recommended Android API Level supported should be 15 or higher.

  * The System environment variable **ANDROID\_HOME** should be set to the path to the Android SDK.
  * The System environment variable **PATH** should contain the paths to both the Android SDK's **tools** and **platform-tools** subfolders.

**NOTE:**

  * To test on an **Android Emulator**, you must verify/prepare an appropriate **AVD** with the **android** tool provided with the Android SDK.  Refer to the Android Developers documentation for details.
  * To test on a real device, you must verify/prepare any required connections and/or drivers for your device.  Refer to the Android Developers documentation for details.

**3. Verify [(Install if needed)](http://ant.apache.org/) Apache Ant:**

Ant should be version 1.8 or higher.

  * The System environment variable **ANT\_HOME** should be set to the path to the Ant SDK.
  * The System environment variable **PATH** should contain the path to the Ant SDK's **bin** subfolder.

**4. Double-click or otherwise extract the contents of the RobotiumRCRelease ZIP into a directory.:** `<workdir>`

**5. In a CMD/Shell/Terminal window navigate to the `<workdir>` directory and execute the appropriate installation script:**

> Windows: _Setup-Win.bat %ANDROID\_HOME% or `<path-to-android-sdk>`_

> Unix: _Setup-Unx.sh  $ANDROID\_HOME  or `<path-to-android-sdk>`_

> Mac: _Setup-Mac.sh  $ANDROID\_HOME  or `<path-to-android-sdk>`_

On Mac, and possibly some incantations of Unix, the user may be required to use **sudo** as follows:
> _sudo  ./Setup-Mac.sh  $ANDROID\_HOME_
or
> _sudo  ./Setup-Unx.sh  $ANDROID\_HOME_

If the script does not run at all:
> make sure the scripts are executable:
> > _chmod a+x `*`.sh_


> prefix the shell: _'/bin/sh Setup-Mac.sh'_
(Don't forget to use sudo, if necessary.)

**6. Rebuild SAFSTCPMessenger-debug.apk:**

Required only once to build with your tester/developer debug profile.

Go to the SAFSTCPMessenger project and verify/edit the file local.properties:

  * sdk.dir =`<path-to-android-sdk>`
  * safs.droid.automation.libs =`<path-to\RobotiumTestRunner\libs>`

In a **CMD/Shell/Terminal** window navigate to the **SAFSTCPMessenger** project directory.

Enter **ant debug** to build the **SAFSTCPMessenger-debug.apk**.

Verify the APK was built in the **SAFSTCPMessenger** **bin** subfolder.

**On Windows:**

If you receive a BUILD FAILED message along with "Could not create task or type of type: componentdef.":

There is a **CLASSPATH** issue which is usually resolved by eliminating the System **CLASSPATH** in the **CMD** window with:

> set **CLASSPATH**= (leave blank)

Then try the 'ant debug' command again in that same **CMD** window.

**7. Rebuild `RobotiumTestRunner-debug.apk:`**

Required only once to build with your tester/developer debug profile.

Go to the `RobotiumTestRunner project and verify/edit the file local.properties:`

**sdk.dir**=`<path-to-android-sdk>`

For a one-time `TestRunner build`, edit the `RobotiumTestRunner AndroidManifest.xml file:`
Within the **<instrumentation** element set the **android:targetPackage** attribute to match the package of the **AUT** you will be testing:

> android:targetPackage ="com.my.company.app.package"

(As an advanced feature, the framework can rebuild the `RobotiumTestRunner` at runtime to match the targetPackage of whatever AUT is specified for testing.)

In a CMD/Shell/Terminal window navigate to the `RobotiumTestRunner` project directory.

  * Enter 'ant debug' to build the `RobotiumTestRunner-debug.apk.`
  * Verify the APK was built in the `RobotiumTestRunner` 'bin' subfolder.

**On Windows:**
If you receive a **BUILD FAILED** message along with "Could not create task or type of type: componentdef.":

There is a **CLASSPATH** issue which is usually resolved by eliminating the System **CLASSPATH** in the **CMD** window with:

  * set **CLASSPATH** = (leave blank)

Then try the **ant debug** command again in that same **CMD** window.

**8. Repackage your**AUT APK**with your tester/developer debug profile(if needed):**

3rd-party 're-sign.jar' is located in the `SoloRemoteControl` **libs** subfolder.
> The re-sign application takes 2 parameters:

> `<in>` path to AUT apk to re-sign

> `<out>` path to newly created AUT-debug.apk

> In a **CMD/Shell/Terminal** window run the re-sign Java program:
(Practice on the `SampleSpinner` **APK** provided with RobotiumRC)

> `java -jar <path\to\re-sign.jar> <path\to\SpinnerActivity.apk> <out\to\SpinnerActivity-debug.apk>`

> Verify the **AUT-debug.apk** was built in the target output path.