With Robotium it is possible to run test cases on applications that are pre-installed.
For this to work you need to resign the pre-installed application with the same certificate signing of your test project. That requires you to have a rooted phone as you must have access to the /system/app folder on the device.

Observe that some pre-installed applications do not function properly when re-installed with a new certificate signing. An example is the contacts application (Contacts.apk) that does not show up when re-signed.


## Details ##

There are some steps that you need to follow to make it work:

1. Log in as root: adb root

2. Remount: adb remount

3. adb pull /system/app/X.apk (Replace X with the name of the application)

4. [Resign X.apk](http://code.google.com/p/robotium/wiki/RobotiumForAPKFiles) so that it has the same certificate signing as the test project

5. adb pull /data/system/packages.xml

6. Open packages.xml and remove: 

&lt;package name="com.X"&gt;

.....

&lt;/package&gt;



7. Push packages.xml back to device: adb push packages.xml /data/system

8. Restart your device

9. Push the resigned X.apk back to the device: adb push X.apk /system/app

10. Follow the [details section](http://code.google.com/p/robotium/wiki/RobotiumForAPKFiles)